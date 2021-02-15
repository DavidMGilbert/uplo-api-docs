## /gateway/connect/:*netaddress* [POST]
> curl example

```go
curl -A "Uplo-Agent" -X POST "localhost:8480/gateway/connect/123.456.789.0:8481"
```

connects the gateway to a peer. The peer is added to the node list if it is not
already present. The node list is the list of all nodes the gateway knows about,
but is not necessarily connected to.

### Path Parameters
### REQUIRED
netaddress is the address of the peer to connect to. It should be a reachable ip
address and port number, of the form `IP:port`. IPV6 addresses must be enclosed
in square brackets.

**netaddress** | string  
Example IPV4 address: 123.456.789.0:123  
Example IPV6 address: [123::456]:789

### Response
standard success or error response. See standard responses.
