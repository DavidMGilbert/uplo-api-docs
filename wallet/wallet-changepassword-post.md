## /wallet/changepassword [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> -X POST "localhost:8480/wallet/changepassword?encryptionpassword=<currentpassword>&newpassword=<newpassword>"
```

Changes the wallet's encryption key.

### Query String Parameters
### REQUIRED
**encryptionpassword** | string  
encryptionpassword is the wallet's current encryption password or primary seed.


**newpassword** | string  
newpassword is the new password for the wallet.

### Response

standard success or error response. See [standard
responses](#standard-responses).