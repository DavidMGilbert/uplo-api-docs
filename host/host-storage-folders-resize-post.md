## /host/storage/folders/resize [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "path=foo/bar&newsize=1000000000000" "localhost:8480/host/storage/folders/resize"
```

Grows or shrinks a storage file in the manager. The manager may not check that
there is enough space on-disk to support growing the storasge folder, but should
gracefully handle running out of space unexpectedly. When shrinking a storage
folder, any data in the folder that needs to be moved will be placed into other
storage folders, meaning that no data will be lost. If the manager is unable to
migrate the data, an error will be returned and the operation will be stopped.

### Storage Folder Limits
See [/host/storage/folders/add](#host-storage-folders-add-post)

### Query String Parameters
### REQUIRED
**path** | string  
Local path on disk to the storage folder to resize.

**newsize** | bytes  
Desired new size of the storage folder. This will be the new capacity of the
storage folder.

### Response

standard success or error response. See standard responses.
