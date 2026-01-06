#### Explanation:

### ping -c 4 $TARGET_HOST: Pings the target host to measure network latency.
 
### awk -F '/' '{print $5}': Extracts the average latency. 


### mail -s "Network Latency Alert": Sends an alert if the latency exceeds the threshold. 

```bash

#!/bin/bash 

# Define the target host and acceptable latency threshold 

TARGET_HOST="google.com" 

LATENCY_THRESHOLD=100 

# Get the network latency in milliseconds 

LATENCY=$(ping -c 4 $TARGET_HOST | tail -1| awk -F '/' '{print $5}') 

# Check if latency exceeds the threshold 

if [ $(echo "$LATENCY > $LATENCY_THRESHOLD" | bc) -eq 1 ]; then 

echo "High network latency detected: $LATENCY ms" | mail -s "Network 

Latency Alert" admin@example.com 

echo "Latency is high. Alert sent." 

else 

echo "Network latency is normal: $LATENCY ms" 

fi 

```


