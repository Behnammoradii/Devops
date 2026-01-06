#### Explanation:

pg_dump: This command creates a backup of the specified PostgreSQL 
database. 

$DATE: The current date is added to the backup filename for versioning. 

```bash
#!/bin/bash 
# Define database credentials and backup location 
DB_NAME="mydb" 
USER="postgres" 
BACKUP_DIR="/backups" 
DATE=$(date +%F) 
# Dump the PostgreSQL database 
pg_dump -U $USER $DB_NAME > $BACKUP_DIR/$DB_NAME-$DATE.sql 
```
