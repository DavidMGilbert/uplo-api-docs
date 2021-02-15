## /wallet/init/seed [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "seed=<seed>&encryptionpassword=<password>&force=false" "localhost:8480/wallet/init/seed"
```

Initializes the wallet using a preexisting seed. After the wallet has been
initialized once, it does not need to be initialized again, and future calls to
/wallet/init/seed will return an error. The encryption password is provided by
the api call. If the password is blank, then the password will be set to the
same as the seed. Note that loading a preexisting seed requires scanning the
blockchain to determine how many keys have been generated from the seed. For
this reason, /wallet/init/seed can only be called if the blockchain is synced.

### Query String Parameters
### REQUIRED WALLET PARAMETERS
**seed** | string  
Dictionary-encoded phrase that corresponds to the seed being used to initialize
the wallet.

### OPTIONAL
[Optional Wallet Parameters](#optional-wallet-parameters)

### Response

standard success or error response. See standard responses.