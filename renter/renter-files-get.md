## /renter/files [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/renter/files?cached=false"
```

### Query String Parameters
### OPTIONAL
**cached** | boolean  
determines whether cached values should be returned or if the latest values
should be computed. Cached values speed the endpoint up significantly. The
default value is 'false'.

lists the status of all files.

### JSON Response
> JSON Response Example

```go
{
  "files": [
    {
      "accesstime":       12578940002019-02-20T17:46:20.34810935+01:00,  // timestamp
      "available":        true,                 // boolean
      "changetime":       12578940002019-02-20T17:46:20.34810935+01:00,  // timestamp
      "ciphertype":       "threefish",          // string   
      "createtime":       12578940002019-02-20T17:46:20.34810935+01:00,  // timestamp
      "expiration":       60000,                // block height
      "filesize":         8192,                 // bytes
      "health":           0.5,                  // float64
      "localpath":        "/home/foo/bar.txt",  // string
      "maxhealth":        0.0,                  // float64  
      "maxhealthpercent": 100%,                 // float64
      "modtime":          12578940002019-02-20T17:46:20.34810935+01:00,  // timestamp
      "numstuckchunks":   0,                    // uint64
      "ondisk":           true,                 // boolean
      "recoverable":      true,                 // boolean
      "redundancy":       5,                    // float64
      "renewing":         true,                 // boolean
      "uplopath":          "foo/bar.txt",        // string
      "stuck":            false,                // bool
      "stuckhealth":      0.0,                  // float64
      "uploadedbytes":    209715200,            // total bytes uploaded
      "uploadprogress":   100,                  // percent
    }
  ]
}
```
**files**

**accesstime** | timestamp  
indicates the last time the uplofile was accessed

**available** | boolean  
true if the file is available for download. A file is available to download once
it has reached at least 1x redundancy. Files may be available before they have
reached 100% upload progress as upload progress includes the full expected
redundancy of the file.

**changetime** | timestamp  
indicates the last time the uplofile metadata was updated

**ciphertype** | string  
indicates the encryption used for the uplofile

**createtime** | timestamp  
indicates when the uplofile was created

**expiration** | block height  
Block height at which the file ceases availability.

**filesize** | bytes  
Size of the file in bytes.

**health** | float64 health is an indication of the amount of redundancy missing
where 0 is full redundancy and >1 means the file is not available. The health of
the uplofile is the health of the worst unstuck chunk.

**localpath** | string  
Path to the local file on disk.  
**NOTE** `uplod` will set the localpath to an empty string if the local file is
not found on disk. This is done to avoid the uplofile being corrupted in the
future by a different file being placed on disk at the original localpath
location.

**maxhealth** | float64  
the maxhealth is either the health or the stuckhealth of the uplofile, whichever
is worst

**maxhealthpercent** | float64  
maxhealthpercent is the maxhealth converted to be out of 100% to be more easily
understood

**modtime** | timestamp  
indicates the last time the uplofile contents where modified

**numstuckchunks** | uint64  
indicates the number of stuck chunks in a file. A chunk is stuck if it cannot
reach full redundancy

**ondisk** | boolean  
indicates if the source file is found on disk

**recoverable** | boolean  
indicates if the uplofile is recoverable. A file is recoverable if it has at
least 1x redundancy or if `uplod` knows the location of a local copy of the file.

**redundancy** | float64  
When a file is uploaded, it is first broken into a series of chunks. Each chunk
goes on a different set of hosts, and therefore different chunks of the file can
have different redundancies. The redundancy of a file as reported from the API
will be equal to the lowest redundancy of any of  the file's chunks.

**renewing** | boolean  
true if the file's contracts will be automatically renewed by the renter.

**uplopath** | string  
Path to the file in the renter on the network.

**stuck** | bool  
a file is stuck if there are any stuck chunks in the file, which means the file
cannot reach full redundancy

**stuckhealth** | float64  
stuckhealth is the worst health of any of the stuck chunks.

**uploadedbytes** | bytes  
Total number of bytes successfully uploaded via current file contracts. This
number includes padding and rendundancy, so a file with a size of 8192 bytes
might be padded to 40 MiB and, with a redundancy of 5, encoded to 200 MiB for
upload.

**uploadprogress** | percent  
Percentage of the file uploaded, including redundancy. Uploading has completed
when uploadprogress is 100. Files may be available for download before upload
progress is 100.  