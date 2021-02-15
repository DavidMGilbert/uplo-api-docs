## /host/bandwidth [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/host/bandwidth"
```

returns the total upload and download bandwidth usage for the host

### JSON Response
```go
{
  "download":  12345                                  // bytes
  "upload":    12345                                  // bytes
  "starttime": "2018-09-23T08:00:00.000000000+04:00", // Unix timestamp
}
```

**download** | bytes  
the total number of bytes that have been sent from the host to renters since the
starttime.

**upload** | bytes  
the total number of bytes that have been received by the host from renters since the
starttime.

**starttime** | Unix timestamp  
the time at which the host started monitoring the bandwidth, since the
bandwidth is not currently persisted this will be startup timestamp.