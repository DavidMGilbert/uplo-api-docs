## /feemanager/cancel [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "feeuid=9ce7ff6c2b65a760b7362f5a041d3e84e65e22dd" "localhost:8480/feemanager/cancel"
```

cancels a fee.

### Query String Parameters
### REQUIRED
**feeuid** | string  
The unique identifier for the fee.

### Response

standard success or error response. See standard responses.