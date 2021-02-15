## /renter/contract/cancel [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "id=bd7ef21b13fb85eda933a9ff2874ec50a1ffb4299e98210bf0dd343ae1632f80" "localhost:8480/renter/contract/cancel"
```

cancels a specific contract of the Renter.

### Query String Parameters
### REQUIRED
**id** | hash  
ID of the file contract

### Response

standard success or error response. See standard responses.