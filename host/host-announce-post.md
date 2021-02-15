## /host/announce [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> -X POST "localhost:8480/host/announce"
```
> curl example with a custom netaddress

```go
curl -A "Uplo-Agent" -u "":<apipassword> -X POST "localhost:8480/host/announce?netaddress=uplohost.example.net"
```

Announce the host to the network as a source of storage. Generally only needs to
be called once.

Note that even after the host has been announced, it will not accept new
contracts unless configured to do so. To configure the host to accept contracts,
see [/host](## /host [POST]).

### Query String Parameters
### OPTIONAL
**netaddress string** | string  
The address to be announced. If no address is provided, the automatically
discovered address will be used instead.

### Response

standard success or error response. See [standard
responses](#Standard-Responses).