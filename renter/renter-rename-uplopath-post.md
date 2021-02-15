## /renter/rename/*uplopath* [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "newuplopath=myfile2" "localhost:8480/renter/rename/myfile"

curl -A "Uplo-Agent" -u "":<apipassword> --data "newuplopath=myfile2&root=true" "localhost:8480/renter/rename/myfile"
```

change the uploPath for a file that is being managed by the renter.

### Path Parameters
### REQUIRED
**uplopath** | string  
Path to the file in the renter on the network.

### Query String Parameters
### REQUIRED
**newuplopath** | string  
New location of the file in the renter on the network.

### OPTIONAL
**root** | bool  
Whether or not to treat the uplopath as being relative to the user's home
directory. If this field is not set, the uplopath will be interpreted as
relative to 'home/user/'.

### Response

standard success or error response. See [standard
responses](#standard-responses).