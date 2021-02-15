## /wallet/backup [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/wallet/backup?destination=/home/wallet-settings.backup"
```

Creates a backup of the wallet settings file. Though this can easily be done
manually, the settings file is often in an unknown or difficult to find
location. The /wallet/backup call can spare users the trouble of needing to find
their wallet file.

### Query String Parameters
### REQUIRED
**destination**  
Path to the location on disk where the backup file will be saved.

### Response

standard success or error response. See [standard
responses](#standard-responses).