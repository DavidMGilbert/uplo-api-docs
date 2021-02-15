## /renter/uploadedbackups [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/renter/uploadedbackups"
```

Lists the backups that have been uploaded to hosts.

### JSON Response
> JSON Response Example

```go
[
  {
    "name": "foo",                             // string
    "UID": "00112233445566778899aabbccddeeff", // string
    "creationdate": 1234567890,                // Unix timestamp
    "size": 8192                               // bytes
  }
]
```
**name** | string  
The name of the backup.

**UID** | string  
A unique identifier for the backup.

**creationdate** | string  
Unix timestamp of when the backup was created.

**size** Size in bytes of the backup.