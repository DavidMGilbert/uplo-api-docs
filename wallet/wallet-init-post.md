## /wallet/init [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "encryptionpassword=<password>&force=false" "localhost:8480/wallet/init"
```

Initializes the wallet. After the wallet has been initialized once, it does not
need to be initialized again, and future calls to /wallet/init will return an
error. The encryption password is provided by the api call. If the password is
blank, then the password will be set to the same as the seed.

### Query String Parameters
### OPTIONAL WALLET PARAMETERS
**encryptionpassword** | string  
Password that will be used to encrypt the wallet. All subsequent calls should
use this password. If left blank, the seed that gets returned will also be the
encryption password.

**dictionary** | string  
Name of the dictionary that should be used when encoding the seed. 'english' is
the most common choice when picking a dictionary.

**force** | boolean  
When set to true /wallet/init will Reset the wallet if one exists instead of
returning an error. This allows API callers to reinitialize a new wallet.

### JSON Response
> JSON Response Example

```go
{
  "primaryseed": "hello world hello world hello world hello world hello world hello world hello world hello world hello world hello world hello world hello world hello world hello world hello"
}
```
**primaryseed**  
Wallet seed used to generate addresses that the wallet is able to spend.  