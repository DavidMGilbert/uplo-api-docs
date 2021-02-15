
## /host/storage [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/host/storage"
```

Gets a list of folders tracked by the host's storage manager.

### JSON Response
> JSON Response Example

```go
{
  "folders": [
    {
      "path":              "/home/foo/bar", // string
      "capacity":          50000000000,     // bytes
      "capacityremaining": 100000,          // bytes

      "failedreads":      0,  // int
      "failedwrites":     1,  // int
      "successfulreads":  2,  // int
      "successfulwrites": 3,  // int
    }
  ]
}
```
**path** | string  
Absolute path to the storage folder on the local filesystem.

**capacity** | bytes  
Maximum capacity of the storage folder in bytes. The host will not store more
than this many bytes in the folder. This capacity is not checked against the
drive's remaining capacity. Therefore, you must manually ensure the disk has
sufficient capacity for the folder at all times. Otherwise you risk losing
renter's data and failing storage proofs.

**capacityremaining** | bytes  
Unused capacity of the storage folder in bytes.

**failedreads, failedwrites** | int  
Number of failed disk read & write operations. A large number of failed reads or
writes indicates a problem with the filesystem or drive's hardware.

**successfulreads, successfulwrites** | int  
Number of successful read & write operations.  