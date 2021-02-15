## /daemon/update [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/daemon/update"
```
Returns the the status of any updates available for the daemon

### JSON Response
> JSON Response Example

```go
{
  "available": false, // boolean
  "version": "1.4.0"  // string
}
```

**available** | boolean  
Available indicates whether or not there is an update available for the daemon.

**version** | string  
Version is the version of the latest release.