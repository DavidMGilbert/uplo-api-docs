## /tpool/confirmed/:id [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/tpool/confirmed/22e8d5428abc184302697929f332fa0377ace60d405c39dd23c0327dc694fae7"
```

returns whether the requested transaction has been seen on the blockchain. Note,
however, that the block containing the transaction may later be invalidated by a
reorg.

### Path Parameters
### REQUIRED
**id** | hash  
id of the transaction being queried

### JSON Response
> JSON Response Example

```go
{
  "confirmed": true // boolean
}
```
**confirmed** | boolean  
indicates if a transaction is confirmed on the blockchain