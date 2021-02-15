## /wallet/transactions [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/wallet/transactions"
```

Returns a list of transactions related to the wallet in chronological order.

### Query String Parameters
### REQUIRED
**startheight** | block height  
Height of the block where transaction history should begin.

**endheight** | block height  
Height of of the block where the transaction history should end. If 'endheight'
is greater than the current height, or if it is '-1', all transactions up to and
including the most recent block will be provided.

### JSON Response
> JSON Response Example

```go
{
  "confirmedtransactions": [
    {
      // See the documentation for '/wallet/transaction/:id' for more information.
    }
  ],
  "unconfirmedtransactions": [
    {
      // See the documentation for '/wallet/transaction/:id' for more information.
    }
  ]
}
```
**confirmedtransactions**  
All of the confirmed transactions appearing between height 'startheight' and
height 'endheight' (inclusive).

See the documentation for '/wallet/transaction/:id' for more information.

**unconfirmedtransactions**  
All of the unconfirmed transactions.

See the documentation for '/wallet/transaction/:id' for more information.  