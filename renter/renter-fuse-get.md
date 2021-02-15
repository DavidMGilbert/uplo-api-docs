## /renter/fuse [GET]
> curl example

```bash
curl -A "Uplo-Agent" "localhost:8480/renter/fuse"
```

Lists the set of folders that have been mounted to the user's filesystem and
which mountpoints have been used for each mount.

### JSON Response
> JSON Response Example

```go
{
  "mountpoints": [ // []modules.MountInfo
    {
      "mountpoint": "/home/user/uplovideos", // string
      "uplopath": "/videos",                 // modules.UploPath

      "mountoptions": { // []modules.MountOptions
          "allowother": false, // bool
          "readonly": true,    // bool
        },
    },
  ]
}
```
**mountpoint** | string  
The system path that is being used to mount the fuse folder.

**uplopath** | string  
The uplopath that has been mounted to the mountpoint.