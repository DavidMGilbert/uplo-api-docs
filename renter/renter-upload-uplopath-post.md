## /renter/upload/*uplopath* [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "source=/home/myfile" "localhost:8480/renter/upload/myfile"
```

uploads a file to the network from the local filesystem.

### Path Parameters
### REQUIRED
**uplopath** | string  
Location where the file will reside in the renter on the network. The path must
be non-empty, may not include any path traversal strings ("./", "../"), and may
not begin with a forward-slash character.

### Query String Parameters
### REQUIRED
**source** | string  
Location on disk of the file being uploaded.

### OPTIONAL
**datapieces** | int  
The number of data pieces to use when erasure coding the file.

**paritypieces** | int  
The number of parity pieces to use when erasure coding the file. Total
redundancy of the file is (datapieces+paritypieces)/datapieces.

**force** | boolean  
Delete potential existing file at uplopath.

### Response

standard success or error response. See standard responses.
