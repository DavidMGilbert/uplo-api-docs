## /renter/fuse/unmount [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> -X POST "localhost:8480/renter/fuse/unmount?mount=/home/user/videos"
```

### Query String Parameters
### REQUIRED
**mount** | string  
Mountpoint that was used when mounting the fuse directory.

### Response

standard success or error response. See [standard
responses](#standard-responses).