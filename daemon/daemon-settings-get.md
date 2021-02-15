## /daemon/settings [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/daemon/settings"
```
Returns the settings for the daemon

### JSON Response
> JSON Response Example

```go
{
  "maxdownloadspeed": 0,  // bytes per second
  "maxuploadspeed":   0,  // bytes per second
  "modules": { 
    "consensus":       true,  // bool
    "explorer":        false, // bool
    "feemanager":      true,  // bool
    "gateway":         true,  // bool
    "host":            true,  // bool
    "miner":           true,  // bool
    "renter":          true,  // bool
    "transactionpool": true,  // bool
    "wallet":          true   // bool

  } 
}
```

**maxdownloadspeed** | bytes per second  
Is the maximum download speed that the daemon can reach. 0 means there is no
limit set.

**maxuploadspeed** | bytes per second  
Is the maximum upload speed that the daemon can reach. 0 means there is no limit
set.

**modules** | struct  
Is a list of the uplod modules with a bool indicating if the module was launched.