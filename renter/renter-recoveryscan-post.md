## /renter/recoveryscan [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> -X POST "localhost:8480/renter/recoveryscan"
```

starts a rescan of the whole blockchain to find recoverable contracts. The
contractor will periodically try to recover found contracts every 10 minutes
until they are recovered or expired.

### Response

standard success or error response. See standard responses.