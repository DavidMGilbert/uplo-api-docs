## /gateway [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/gateway"
```

returns information about the gateway, including the list of connected peers.

### JSON Response
> JSON Response Example

```go
{
    "netaddress":"333.333.333.333:8481",  // string
    "peers":[
        {
            "inbound":    false,                   // boolean
            "local":      false,                   // boolean
            "netaddress": "222.222.222.222:8481",  // string
            "version":    "1.0.0",                 // string
        },
    ],
    "online":           true,  // boolean
    "maxdownloadspeed": 1234,  // bytes per second
    "maxuploadspeed":   1234,  // bytes per second
}
```
**netaddress** | string  
netaddress is the network address of the gateway as seen by the rest of the
network. The address consists of the external IP address and the port Uplo is
listening on. It represents a `modules.NetAddress`.

**peers** | array  
peers is an array of peers the gateway is connected to. It represents an array
of `modules.Peer`s.

**inbound** | boolean  
inbound is true when the peer initiated the connection. This field is exposed as
outbound peers are generally trusted more than inbound peers, as inbound peers
are easily manipulated by an adversary.

**local** | boolean  
local is true if the peer's IP address belongs to a local address range such as
192.168.x.x or 127.x.x.x

**netaddress** | string  
netaddress is the address of the peer. It represents a `modules.NetAddress`.

**version** | string  
version is the version number of the peer.

**online** | boolean  
online is true if the gateway is connected to at least one peer that isn't
local.

**maxdownloadspeed** | bytes per second   
Max download speed permitted in bytes per second

**maxuploadspeed** | bytes per second   
Max upload speed permitted in bytes per second