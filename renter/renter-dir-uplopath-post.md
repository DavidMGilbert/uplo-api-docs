## /renter/dir/*uplopath* [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "action=delete" "localhost:8480/renter/dir/mydir"
```

performs various functions on the renter's directories

### Path Parameters
### REQUIRED
**uplopath** | string  
Location where the directory will reside in the renter on the network. The path
must be non-empty, may not include any path traversal strings ("./", "../"), and
may not begin with a forward-slash character.

### OPTIONAL
**root** | bool  
Whether or not to treat the uplopath as being relative to the user's home
directory. If this field is not set, the uplopath will be interpreted as
relative to 'home/user/'.

### Query String Parameters
### REQUIRED
**action** | string  
Action can be either `create`, `delete` or `rename`.
- `create` will create an empty directory on the uplo network
- `delete` will remove a directory and its contents from the uplo network. Will
  return an error if the target is a file.
- `rename` will rename a directory on the uplo network

**newuplopath** | string  
The new uplopath of the renamed folder. Only required for the `rename` action.

### OPTIONAL
**mode** | uint32  
The mode can be specified in addition to the `create` action to create the
directory with specific permissions. If not specified, the default permissions
0755 will be used.

### Response

standard success or error response. See standard responses.