## /gateway [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "maxdownloadspeed=1000000&maxuploadspeed=20000" "localhost:8480/gateway"
```

Modify settings that control the gateway's behavior.

### Query String Parameters
### OPTIONAL
**maxdownloadspeed** | bytes per second  
Max download speed permitted in bytes per second

**maxuploadspeed** | bytes per second  
Max upload speed permitted in bytes per second

### Response

standard success or error response. See standard responses.