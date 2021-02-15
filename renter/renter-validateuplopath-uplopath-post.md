## /renter/validateuplopath/*uplopath* [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/renter/validateuplopath/isthis-aval_iduplopath"
```

validates whether or not the provided uplopath is a valid uplopath. Every path
valid under Unix is valid as a UploPath.

### Path Parameters
### REQUIRED
**uplopath** | string  
uplopath to test.

### Response
standard success or error response, a successful response means a valid uplopath.
See [standard responses](#standard-responses).