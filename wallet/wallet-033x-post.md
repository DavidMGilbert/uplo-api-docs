## /wallet/033x [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "source=/home/legacy-wallet&encryptionpassword=mypassword" "localhost:8480/wallet/033x"
```

Loads a v0.3.3.x wallet into the current wallet, harvesting all of the secret
keys. All spendable addresses in the loaded wallet will become spendable from
the current wallet.

### Query String Parameters
### REQUIRED
**source**  
Path on disk to the v0.3.3.x wallet to be loaded.

**encryptionpassword**  
Encryption key of the wallet.

### Response

standard success or error response. See [standard
responses](#standard-responses).