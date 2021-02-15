## /wallet/verifypassword [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/wallet/verifypassword?password=<password>"
```

Takes a password and verifies if it is the password used to encrypt the wallet.

### Path Parameters
#### REQUIRED
**password** | string  
Password being checked.

### JSON Response
> JSON Response Example

```go
{
  "valid": true,
}
```
**valid** | boolean  
valid indicates if the password supplied is the password used to encrypt the
wallet.  