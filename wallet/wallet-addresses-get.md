## /wallet/addresses [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/wallet/addresses"
```

Fetches the list of addresses from the wallet. If the wallet has not been
created or unlocked, no addresses will be returned. After the wallet is
unlocked, this call will continue to return its addresses even after the wallet
is locked again.

### JSON Response
> JSON Response Example

```go
{
  "addresses": [ // []hash
    "1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef0123456789ab",
    "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb"
  ]
}
```
**addresses** | hashes  
Array of wallet addresses owned by the wallet.  