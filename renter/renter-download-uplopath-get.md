## /renter/download/*uplopath* [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/renter/download/myfile?httpresp=true"
```

downloads a file to the local filesystem. The call will block until the file has
been downloaded.

### Path Parameters
### REQUIRED
**uplopath** | string  
Path to the file in the renter on the network.

### Query String Parameters
### REQUIRED (Either one or the other)
**destination** | string  
Location on disk that the file will be downloaded to.

**httpresp** | boolean  
If httresp is true, the data will be written to the http response.

### OPTIONAL
**async** | boolean  
If async is true, the http request will be non blocking. Can't be used with
httpresp.

**disablelocalfetch** | boolean  
If disablelocalfetch is true, downloads won't be served from disk even if the
file is available locally.

**root** | boolean  
If root is true, the provided uplopath will not be prefixed with /home/user but is instead taken as an absolute path.

**length** | bytes  
Length of the requested data. Has to be <= filesize-offset.

**offset** | bytes  
Offset relative to the file start from where the download starts.

### Response

Unlike most responses, this response modifies the http response header. The
download will set the 'ID' field in the http response header to a unique
identifier which can be used to cancel an async download with the
/renter/download/cancel endpoint and retrieve a download's info from the
download history using the /renter/downloadinfo endpoint. Apart from that the
response is a standard success or error response. See standard responses.