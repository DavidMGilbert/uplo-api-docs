## /gateway/disconnect/:*netaddress* [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> -X POST "localhost:8480/gateway/disconnect/123.456.789.0:8481"
```

disconnects the gateway from a peer. The peer remains in the node list.
Disconnecting from a peer does not prevent the gateway from automatically
connecting to the peer in the future.

### Path Parameters
### REQUIRED
netaddress is the address of the peer to connect to. It should be a reachable ip
address and port number, of the form `IP:port`. IPV6 addresses must be enclosed
in square brackets.

**netaddress** | string  
Example IPV4 address: 123.456.789.0:123  
Example IPV6 address: [123::456]:789

### Response
standard success or error response. See [standard
responses](#standard-responses).