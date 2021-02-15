## /renter/delete/*uplopath* [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> -X POST "localhost:8480/renter/delete/myfile"
```

deletes a renter file entry. Does not delete any downloads or original files,
only the entry in the renter. Will return an error if the target is a folder.

### Path Parameters
### REQUIRED
**uplopath** | string  
Path to the file in the renter on the network.

### OPTIONAL
**root** | bool  
Whether or not to treat the uplopath as being relative to the user's home
directory. If this field is not set, the uplopath will be interpreted as relative
to 'home/user/'.

### Response

standard success or error response. See standard responses.