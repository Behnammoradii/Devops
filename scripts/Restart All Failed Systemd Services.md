#### Purpose: Restarts all failed systemd services.

Use: Ensures that any failed services on a Linux system are automatically 
restarted.

```bash
#!/bin/bash 
for SERVICE in $(systemctl --failed --no-legend | awk '{print $1}'); do 
systemctl restart $SERVICE 
done 
```
