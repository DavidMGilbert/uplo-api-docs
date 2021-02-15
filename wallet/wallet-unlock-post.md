## /wallet/unlock [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "encryptionpassword=<password>" "localhost:8480/wallet/unlock"
```

Unlocks the wallet. The wallet is capable of knowing whether the correct
password was provided.

### Query String Parameters
### REQUIRED
**encryptionpassword** | string  
Password that gets used to decrypt the file. Most frequently, the encryption
password is the same as the primary wallet seed.

### Response

standard success or error response. See standard responses.