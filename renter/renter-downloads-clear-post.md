## /renter/downloads/clear [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> -X POST "localhost:8480/renter/downloads/clear?before=1551398400&after=1552176000"
```

Clears the download history of the renter for a range of unix time stamps.  Both
parameters are optional, if no parameters are provided, the entire download
history will be cleared.  To clear a single download, provide the timestamp for
the download as both parameters.  Providing only the before parameter will clear
all downloads older than the timestamp. Conversely, providing only the after
parameter will clear all downloads newer than the timestamp.

### Query String Parameters
### OPTIONAL
**before** | unix timestamp  
unix timestamp found in the download history

**after** | unix timestamp  
unix timestamp found in the download history

### Response

standard success or error response. See [standard
responses](#standard-responses).