## /wallet/unlockconditions/:addr [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/wallet/unlockconditions/2d6c6d705c80f17448d458e47c3fb1a02a24e018a82d702cda35262085a3167d98cc7a2ba339"
```

Returns the unlock conditions of :addr, if they are known to the wallet.

### Path Parameters
### REQUIRED
**addr** | hash  
Unlock hash (i.e. wallet address) whose transactions are being requested.

### JSON Response
> JSON Response Example

```go
{
  "unlockconditions": {
    "timelock": 0,
    "publickeys": [{
      "algorithm": "ed25519",
      "key": "/XUGj8PxMDkqdae6Js6ubcERxfxnXN7XPjZyANBZH1I="
    }],
    "signaturesrequired": 1
  }
}
```
**timelock**  
The minimum blockheight required.

**signaturesrequired**  
The number of signatures required.

**publickeys** | UploPublicKey  
The set of keys whose signatures count towards signaturesrequired.  