# send-email-everytime-storage-consumed-at-20-
#!/bin/bash
# check-storage.sh

# Get the current disk usage, this is got in percentages 
disk_usage=$(df -h | awk '$NF=="/"{printf "%s", $5}')

# Set the maximum apex for storage usage to trigger the email
threshold=20

# Check if the current disk usage is greater than or equal to the threshold
if (( $(echo "$disk_usage >= $threshold" | bc -l) )); then
    # Send an email to the Linux administrator
    echo "Warning: The storage usage has reached $disk_usage%." | mail -s "Storage Alert" aimableclass@gmail.com
fi
