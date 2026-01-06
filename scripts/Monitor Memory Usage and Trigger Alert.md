### Explanation: 

#### free: Displays memory usage statistics. 
#### awk '{print $3/$2 * 100.0}': Calculates the percentage of used memory. 
#### bc -l: This command-line calculator is used for floating-point comparison.

```bash
#!/bin/bash 
THRESHOLD=90 
MEMORY_USAGE=$(free | grep Mem | awk '{print $3/$2 * 100.0}') 
if (( $(echo "$MEMORY_USAGE > $THRESHOLD" | bc -l) )); then 
echo "Memory usage is high: $MEMORY_USAGE%" | mail -s "Alert: High 
Memory Usage" admin@example.com 
fi 
```

