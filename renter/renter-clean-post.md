## /renter/clean [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword>  "localhost:8480/renter/clean"
```

clears any lost files from the renter. A lost file is a file that is viewed as
unrecoverable. A file is unrecoverable when there is not a local copy on disk
and the file's redundancy is less than 1. This means the file can not be
repaired.

### Response

standard success or error response. See standard responses.