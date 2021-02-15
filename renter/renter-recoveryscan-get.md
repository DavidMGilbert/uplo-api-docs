## /renter/recoveryscan [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/renter/recoveryscan"
```

Returns some information about a potentially ongoing recovery scan.

### JSON Response
> JSON Response Example

```go
{
  "scaninprogress": true // boolean
  "scannedheight" : 1000 // uint64
}
```
**scaninprogress** | boolean  
indicates if a scan for recoverable contracts is currently in progress.

**scannedheight** | uint64  
indicates the progress of a currently ongoing scan in terms of number of blocks
that have already been scanned.