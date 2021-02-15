## /renter/downloadsync/*uplopath* [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/renter/downloadasync/myfile?destination=/home/myfile"
```

downloads a file to the local filesystem. The call will return immediately.

### Path Parameters
### REQUIRED
**uplopath** | string  
Path to the file in the renter on the network.

### Query String Parameters
### REQUIRED
**destination** | string  
Location on disk that the file will be downloaded to.

### Response

standard success or error response. See [standard
responses](#standard-responses).