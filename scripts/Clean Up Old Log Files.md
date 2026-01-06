#### Explanation: 

### find $LOG_DIR -type f -name "*.log" -mtime +$DAYS_TO_KEEP: 
### Finds log files older than the specified number of days. 

### -exec rm -f {}: Deletes each found file.

```bash
#!/bin/bash 
# Define the log directory and number of days to retain logs 
LOG_DIR="/var/log/myapp" 
DAYS_TO_KEEP=30 
# Find and delete log files older than the specified number of days 
find $LOG_DIR -type f -name "*.log" -mtime +$DAYS_TO_KEEP -exec rm -f {} 
\; 
# Print a success message 
echo "Old log files deleted."
```