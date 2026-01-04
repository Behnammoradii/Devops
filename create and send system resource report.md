#### Explanation:

### df -h: Provides a human-readable disk usage report. 

### free -h: Shows memory usage in a human-readable format. 

### top -n 1: Captures CPU usage from the top command. 

```bash
#!/bin/bash 
# Define the report file 
REPORT_FILE="/tmp/system_report.txt" 
# Collect system information 
echo "System Resource Report - $(date)" > $REPORT_FILE 
echo "------------------------------" >> $REPORT_FILE 
echo "Disk Usage:" >> $REPORT_FILE 
df -h >> $REPORT_FILE 
echo "" >> $REPORT_FILE 
echo "Memory Usage:" >> $REPORT_FILE 
free -h >> $REPORT_FILE 
echo "" >> $REPORT_FILE 
echo "CPU Usage:" >> $REPORT_FILE 
top -n 1 | grep "Cpu(s)" >> $REPORT_FILE 
echo "" >> $REPORT_FILE 
# Send the report via email 
mail -s "System Resource Report" user@example.com < $REPORT_FILE 
# Clean up 
rm $REPORT_FILE 
echo "System resource report has been sent." 
```