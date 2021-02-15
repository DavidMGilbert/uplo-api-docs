## /renter/stream/*uplopath* [GET]
> curl example

```sh
curl -A "Uplo-Agent" "localhost:8480/renter/stream/myfile"
```  

> The file can be streamed partially by using standard partial http requests
> which means setting the "Range" field in the http header.

```sh
curl -A "Uplo-Agent" -H "Range: bytes=0-1023" "localhost:8480/renter/stream/myfile"
```

downloads a file using http streaming. This call blocks until the data is
received. The streaming endpoint also uses caching internally to prevent uplod
from re-downloading the same chunk multiple times when only parts of a file are
requested at once. This might lead to a substantial increase in ram usage and
therefore it is not recommended to stream multiple files in parallel at the
moment. This restriction will be removed together with the caching once partial
downloads are supported in the future. If you want to stream multiple files you
should increase the size of the Renter's `streamcachesize` to at least 2x the
number of files you are steaming.

### Path Parameters
### REQUIRED
**uplopath** | string  
Path to the file in the renter on the network.

### OPTIONAL
**disablelocalfetch** | boolean  
If disablelocalfetch is true, downloads won't be served from disk even if the
file is available locally.

**root** | boolean  
If root is true, the provided uplopath will not be prefixed with /home/user but is instead taken as an absolute path.

### Response

standard success or error response. See [standard
responses](#standard-responses).