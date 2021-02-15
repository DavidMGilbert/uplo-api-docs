## /renter/contractstatus [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/renter/contractstatus?id=<filecontractid>"
```

### Query String Parameters
**id** | hash
ID of the file contract

### JSON Response
> JSON Response Example

```go
{
  "archived":                  true, // boolean
  "formationsweepheight":      1234, // block height
  "contractfound":             true, // boolean
  "latestrevisionfound",       55,   // uint64
  "storageprooffoundatheight": 0,    // block height
  "doublespendheight":         0,    // block height
  "windowstart":               5000, // block height
  "windowend":                 5555, // block height
}
```
**archived** | boolean  
Indicates whether or not this contract has been archived by the watchdog. This
is done when a file contract's inputs are double-spent or if the storage proof
window has already elapsed.

**formationsweepheight** | block height  
The block height at which the renter's watchdog will try to sweep inputs from
the formation transaction set if it hasn't been confirmed on chain yet.

**contractfound** | boolean  
Indicates whether or not the renter watchdog found the formation transaction set
on chain.

**latestrevisionfound** | uint64  
The highest revision number found by the watchdog for this contract on chain.

**storageprooffoundatheight** | block height  
The height at which the watchdog found a storage proof for this contract on
chain.

**doublespendheight** | block height  
The height at which a double-spend for this transactions formation transaction
was found on chain.

**windowstart** | block height  
The height at which the storage proof window for this contract starts.

**windowend** | block height  
The height at which the storage proof window for this contract ends.