## /wallet/verify/address/:addr [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/wallet/verify/address/75d9a7351022681ba3539d7e0c5699d143ab5a7747604998cace1299ab6c04c5ea2aa2e87aac"
```

Takes the address specified by :addr and returns a JSON response indicating if
the address is valid.

### Path Parameters
### REQUIRED
**addr** | hash  
Unlock hash (i.e. wallet address) whose transactions are being requested.

### JSON Response
> JSON Response Example

```go
{
  "valid": true
}
```
**valid**  
valid indicates if the address supplied to :addr is a valid UnlockHash.  