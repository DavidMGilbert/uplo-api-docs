## /renter/backup [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "destination=/home/backups/01-01-1968.backup" "localhost:8480/renter/backup"
```

Creates a backup of all uplofiles in the renter at the specified path.

### Query String Parameters
### REQUIRED
**destination** | string  
The path on disk where the backup will be created. Needs to be an absolute path.

### OPTIONAL
**remote** | boolean  
flag indicating if the backup should be stored on hosts. If true,
**destination** is interpreted as the backup's name, not its path.

### Response

standard success or error response. See [standard
responses](#standard-responses).