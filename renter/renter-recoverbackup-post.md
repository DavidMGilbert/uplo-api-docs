## /renter/recoverbackup [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "source=/home/backups/01-01-1968.backup" "localhost:8480/renter/recoverbackup"
```

Recovers an existing backup from the specified path by adding all the uplofiles
contained within it to the renter. Should a uplofile for a certain path already
exist, a number will be added as a suffix. e.g. 'myfile_1.uplo'

### Query String Parameters
### REQUIRED
**source** | string  
The path on disk where the backup will be recovered from. Needs to be an
absolute path.

### OPTIONAL
**remote** | boolean  
flag indicating if the backup is stored on hosts. If true, **source** is
interpreted as the backup's name, not its path.

### Response

standard success or error response. See standard responses.