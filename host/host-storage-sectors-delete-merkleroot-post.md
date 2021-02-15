## /host/storage/sectors/delete/:*merkleroot* [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> -X POST "localhost:8480/host/storage/sectors/delete/[merkleroot]"
```

Deletes a sector, meaning that the manager will be unable to upload that sector
and be unable to provide a storage proof on that sector. This endpoint is for
removing the data entirely, and will remove instances of the sector appearing at
all heights. The primary purpose is to comply with legal requests to remove
data.

### Path Parameters
### REQUIRED
**merkleroot** | merkleroot  
Merkleroot of the sector to delete.

### Response

standard success or error response. See standard responses.