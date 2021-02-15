## /wallet/watch [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/wallet/watch"
```

Returns the set of addresses that the wallet is watching. This set only includes
addresses that were explicitly requested to be watched; addresses that were
generated automatically by the wallet, or by /wallet/address, are not included.

### JSON Response
> JSON Response Example

```go
{
  "addresses": [ // []hash
    "1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef",
    "abcdef0123456789abcdef0123456789abcd1234567890ef0123456789abcdef"
  ]
}
```
**addresses** | hashes  
The addresses currently watched by the wallet.  