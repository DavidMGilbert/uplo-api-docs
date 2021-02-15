## /host/storage/folders/remove [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "path=foo/bar&force=false" "localhost:8480/host/storage/folders/remove"
```

Remove a storage folder from the manager. All storage on the folder will be
moved to other stoarge folders, meaning that no data will be lost. If the
manager is unable to save data, an error will be returned and the operation will
be stopped.

### Query String Parameters
### REQUIRED
**path** | string  
Local path on disk to the storage folder to removed.

### OPTIONAL
**force** | boolean  
If `force` is true, the storage folder will be removed even if the data in the
storage folder cannot be moved to other storage folders, typically because they
don't have sufficient capacity. If `force` is true and the data cannot be moved,
data will be lost.

### Response

standard success or error response. See standard responses.