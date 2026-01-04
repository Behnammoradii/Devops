#### Explanation:

###uptime: This command shows how long the system has been running and the system load averages. 

###awk -F'load average: ': Extracts the load average from the output. 

###cut -d, -f1: Gets the 1-minute load average. 

```bash
#!/bin/bash 
THRESHOLD=80 
LOAD=$(uptime | awk -F'load average: ' '{ print $2 }' | cut -d, -f1 | tr -d ' ') 
if (( $(echo "$LOAD > $THRESHOLD" | bc -l) )); then 
echo "High system load: $LOAD" | mail -s "Alert: High System Load" 
admin@example.com 
fi 
```