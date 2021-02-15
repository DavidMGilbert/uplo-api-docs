## /wallet/transactions/:addr [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/wallet/transactions/abf1ba4ad65820ce2bd5d63466b8555d0ec9bfe5f5fa920b4fef6ad98f443e2809e5ae619b74"
```

Returns all of the transactions related to a specific address.

### Path Parameters
### REQUIRED
**addr** | hash  
Unlock hash (i.e. wallet address) whose transactions are being requested.

### JSON Response
> JSON Response Example

```go
{
  "transactions": [
    {
      // See the documentation for '/wallet/transaction/:id' for more information.
    }
  ]
}
```
**transactions**  
Array of processed transactions that relate to the supplied address.

See the documentation for '/wallet/transaction/:id' for more information.  