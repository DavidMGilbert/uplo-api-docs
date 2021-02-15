## /renter/setmaxperiodchurn [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/renter/setmaxperiodchurn?newmax=123456789"
```

sets the new max churn per period.

### Query String Parameters
**newmax** | uint64  
New maximum churn per period.

### Response

standard success or error response. See [standard responses](#standard-responses).