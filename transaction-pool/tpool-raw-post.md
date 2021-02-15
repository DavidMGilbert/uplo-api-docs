## /tpool/raw [POST]
> curl example

```go
curl -A "Uplo-Agent" --data "<raw-encoded-tset>" "localhost:8480/tpool/raw"
```

submits a raw transaction to the transaction pool, broadcasting it to the
transaction pool's peers.

### Query String Parameters
### REQUIRED
**parents** | string  
JSON- or base64-encoded transaction parents

**transaction** | string  
JSON- or base64-encoded transaction

### Response

standard success or error response. See [standard
responses](#standard-responses).