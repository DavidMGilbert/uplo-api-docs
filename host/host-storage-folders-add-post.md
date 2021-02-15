## /host/storage/folders/add [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "path=foo/bar&size=1000000000000" "localhost:8480/host/storage/folders/add"
```

adds a storage folder to the manager. The manager may not check that there is
enough space available on-disk to support as much storage as requested

### Storage Folder Limits
A host can only have 65536 storage folders in total which have to be between 256
MiB and 16 PiB in size

### Query String Parameters
### REQUIRED
**path** | string  
Local path on disk to the storage folder to add.

**size** | bytes  
Initial capacity of the storage folder. This value isn't validated so it is
possible to set the capacity of the storage folder greater than the capacity of
the disk. Do not do this.

### Response

standard success or error response. See [standard
responses](#standard-responses).