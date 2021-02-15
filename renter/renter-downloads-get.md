## /renter/downloads [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/renter/downloads"
```

Lists all files in the download queue.

### Query String Parameters
### REQUIRED
**root** | boolean  
If root is set, the downloads will contain their absolute paths instead of
the relative ones starting at home/user.

### JSON Response
> JSON Response Example

```go
{
  "downloads": [
    {
      "destination":     "/home/users/alice/bar.txt", // string
      "destinationtype": "file",                      // string
      "length":          8192,                        // bytes
      "offset":          2000,                        // bytes
      "uplopath":         "foo/bar.txt",               // string

      "completed":           true,                    // boolean
      "endtime":             "2009-11-10T23:10:00Z",  // RFC 3339 time
      "error":               "",                      // string
      "received":            8192,                    // bytes
      "starttime":           "2009-11-10T23:00:00Z",  // RFC 3339 time
      "totaldatatransfered": 10031                    // bytes
    }
  ]
}
```
**destination** | string  
Local path that the file will be downloaded to.

**destinationtype** | string  
What type of destination was used. Can be "file", indicating a download to disk,
can be "buffer", indicating a download to memory, and can be "http stream",
indicating that the download was streamed through the http API.

**length** | bytes  
Length of the download. If the download was a partial download, this will
indicate the length of the partial download, and not the length of the full
file.

**offset** | bytes  
Offset within the file of the download. For full file downloads, the offset will
be '0'. For partial downloads, the offset may be anywhere within the file.
offset+length will never exceed the full file size.

**uplopath** | string  
Uplopath given to the file when it was uploaded.

**completed** | boolean  
Whether or not the download has completed. Will be false initially, and set to
true immediately as the download has been fully written out to the file, to the
http stream, or to the in-memory buffer. Completed will also be set to true if
there is an error that causes the download to fail.

**endtime** | date, RFC 3339 time  
Time at which the download completed. Will be zero if the download has not yet
completed.

**error** | string  
Error encountered while downloading. If there was no error (yet), it will be the
empty string.

**received** | bytes  
Number of bytes downloaded thus far. Will only be updated as segments of the
file complete fully. This typically has a resolution of tens of megabytes.

**starttime** | date, RFC 3339 time  
Time at which the download was initiated.

**totaldatatransfered** | bytes  
The total amount of data transferred when downloading the file. This will
eventually include data transferred during contract + payment negotiation, as
well as data from failed piece downloads.  
