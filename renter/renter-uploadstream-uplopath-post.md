## /renter/uploadstream/*uplopath* [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/renter/uploadstream/myfile?datapieces=10&paritypieces=20" --data-binary @myfile.dat

curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/renter/uploadstream/myfile?repair=true" --data-binary @myfile.dat
```

uploads a file to the network using a stream. If the upload stream POST call
fails or quits before the file is fully uploaded, the file can be repaired by a
subsequent call to the upload stream endpoint using the `repair` flag.

### Path Parameters
### REQUIRED
**uplopath** | string  
Location where the file will reside in the renter on the network. The path must
be non-empty, may not include any path traversal strings ("./", "../"), and may
not begin with a forward-slash character.

### Query String Parameters
### OPTIONAL
**datapieces** | int  
The number of data pieces to use when erasure coding the file.

**paritypieces** | int  
The number of parity pieces to use when erasure coding the file. Total
redundancy of the file is (datapieces+paritypieces)/datapieces.

**force** | boolean  
Delete potential existing file at uplopath.

**repair** | boolean  
Repair existing file from stream. Can't be specified together with datapieces,
paritypieces and force.

### Response

standard success or error response. See standard responses.