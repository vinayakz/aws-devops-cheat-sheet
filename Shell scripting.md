## 1. Automating Server Provisioning (AWS EC2 Launch)

```sh
#!/bin/bash

# Variables
INSTANCE_TYPE="t2.micro"
AMI_ID="ami-0c55b1e7cb4970865" # Replace with the correct AMI ID

KEY_NAME="my-key-pair" # Replace with your key pair name
SECURITY_GROUP="sg-0123456789abcdef0" # Replace with your security
group ID
SUBNET_ID="subnet-0abc1234def567820" # Replace with your subnet ID
REGION="us-west-2" # Replace with your AWS region


# Launch EC2 instance
aws ec2 run-instances --image-id $AMI_ID --count 1 --instance-type
$INSTANCE_TYPE \
--key-name $KEY_NAME --security-group-ids $SECURITY_GROUP --subnet-id
$SUBNET_ID --region $REGION
echo "EC2 instance launched successfully!"
```

## 2. System Monitoring (CPU Usage Alert)
```sh
#!/bin/bash

# Threshold for CPU usage
CPU_THRESHOLD=80

# Get the current CPU usage
CPU_USAGE=$(top -bn1 | grep "Cpu(s)" | sed "s/.*, *\([0-9.]*\)%* id.*/\1/" | awk
'{print 100 - $1}')


# Check if CPU usage exceeds threshold
if (( $(echo "$CPU_USAGE > $CPU_THRESHOLD" | bc -l) )); then
echo "Alert: CPU usage is above $CPU_THRESHOLD%. Current usage is
$CPU_USAGE%" | mail -s "CPU Usage Alert" vinoo160496@gmail.com
fi
```

## 3. Backup Automation (Postgres Backup) and upload on AWS s3
```db_backup.sh```
```sh
#!/bin/bash

# === LOAD SECRETS ===
./db_secrets.sh

# === CONFIG ===
TMP_DIR="/tmp/pg_backups"
DATE=$(date +%F_%H-%M-%S)
TMP_BACKUP_FILE="$TMP_DIR/${DB_NAME}_backup_$DATE.sql"
LOG_FILE="/home/ubuntu/backup_script/db_backup.log"

# === CREATE TEMP DIRECTORY IF NEEDED ===
mkdir -p "$TMP_DIR"

# === START BACKUP ===
echo "[$(date)] Starting backup..." | tee -a "$LOG_FILE"
pg_dump -U "$DB_USER" -h "$DB_HOST" "$DB_NAME" > "$TMP_BACKUP_FILE"

# === CHECK IF BACKUP SUCCEEDED ===
if [ $? -ne 0 ]; then
    echo "[$(date)]  Backup failed!" | tee -a "$LOG_FILE"
    echo "Database backup failed at $(date)" | mail -s " DB Backup Failed on EC2" "$EMAIL_TO"
    rm -f "$TMP_BACKUP_FILE"
    exit 1
fi

# === UPLOAD TO S3 ONLY ===
aws s3 cp "$TMP_BACKUP_FILE" "s3://$S3_BUCKET/" --storage-class STANDARD_IA
if [ $? -ne 0 ]; then
    echo "[$(date)]  S3 Upload failed!" | tee -a "$LOG_FILE"
    echo "S3 upload failed for backup at $(date)" | mail -s " S3 Upload Failed on EC2" "$EMAIL_TO"
    rm -f "$TMP_BACKUP_FILE"
    exit 2
fi

# === CLEANUP LOCAL TEMP FILE ===
rm -f "$TMP_BACKUP_FILE"

# === DONE ===
echo "[$(date)] Backup uploaded to S3 and local file deleted." | tee -a "$LOG_FILE"
```

```db_secrets.sh```
```sh
# Database secrets
export DB_NAME="db_name"
export DB_USER="root"
export DB_HOST="db_host"
export PGPASSWORD="root"
export S3_BUCKET="s3_bucket_path"
export EMAIL_TO="vinoo160496@gmail.com"
```

## 4. Security Audits (Check for Open Ports)

```sh
#!/bin/bash

# Check for open ports
OPEN_PORTS=$(netstat -tuln)

# Check if any ports are open (excluding localhost)
if [[ $OPEN_PORTS =~ "0.0.0.0" || $OPEN_PORTS =~ "127.0.0.1" ]]; then
echo "Security Alert: Open ports detected!"
echo "$OPEN_PORTS" | mail -s "Open Ports Security Alert" user@example.com
else
  echo "No open ports detected."
Fi

```
