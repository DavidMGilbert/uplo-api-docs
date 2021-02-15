## /daemon/version [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/daemon/version"
```

Returns the version of the Uplo daemon currently running.

### JSON Response
> JSON Response Example

```go
{
"version": "1.0.1" // string
}
```
**version** | string  
This is the version number that is visible to its peers on the network.
