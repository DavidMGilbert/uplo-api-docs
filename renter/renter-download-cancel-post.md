## /renter/download/cancel [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/renter/download/cancel?id=<downloadid>"
```

cancels the download with the given id.

### Query String Parameters
**id** | string  
ID returned by the /renter/download/*uplopath* endpoint. It is set in the http
header's 'ID' field.

### Response

standard success or error response. See standard responses.