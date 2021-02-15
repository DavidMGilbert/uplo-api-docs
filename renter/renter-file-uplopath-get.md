## /renter/file/*uplopath* [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/renter/file/myfile"
```

Lists the status of specified file.

### Path Parameters
### REQUIRED
**uplopath** | string  
Path to the file in the renter on the network.

### JSON Response
Same response as [files](#files)