## /wallet/address [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/wallet/address"
```

Gets a new address from the wallet generated by the primary seed. An error will
be returned if the wallet is locked.

### JSON Response
> JSON Response Example

```go
{
  "address": "1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef0123456789ab"
}
```
**address** | hash  
Wallet address that can receive uplocoins or uplofunds. Addresses are 76 character
long hex strings.  