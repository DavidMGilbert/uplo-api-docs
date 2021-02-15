## /renter/file/*uplopath* [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "trackingpath=/home/myfile" "localhost:8480/renter/file/myfile"
```

endpoint for changing file metadata.

### Path Parameters
### REQUIRED
**uplopath** | string  
UploPath of the file on the network. The path must be non-empty, may not include
any path traversal strings ("./", "../"), and may not begin with a forward-slash
character.

### Query String Parameters
### OPTIONAL
**trackingpath** | string  
If provided, this parameter changes the tracking path of a file to the
specified path. Useful if moving the file to a different location on disk.

**stuck** | bool  
if set a file will be marked as either stuck or not stuck by marking all of
its chunks.

**root** | bool  
Whether or not to treat the uplopath as being relative to the user's home
directory. If this field is not set, the uplopath will be interpreted as
relative to 'home/user/'.

### Response

standard success or error response. See standard responses.