## /renter/fuse/mount [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> -X POST "localhost:8480/renter/fuse/mount?readonly=true"
```

Mounts a Uplo directory to the local filesystem using FUSE.

### Query String Parameters
### REQUIRED
**mount** | string  
Location on disk to use as the mountpoint.

**readonly** | bool  
Whether the directory should be mounted as ReadOnly. Currently, readonly is a
required parameter and must be set to true.

### OPTIONAL
**uplopath** | string  
Which path should be mounted to the filesystem. If left blank, the user's home
directory will be used.

**allowother** | boolean  
By default, only the system user that mounted the fuse directory will be allowed
to interact with the directory. Often, applications like Plex run as their own
user, and therefore by default are banned from viewing or otherwise interacting
with the mounted folder. Setting 'allowother' to true will allow other users to
see and interact with the mounted folder.

On Linux, if 'allowother' is set to true, /etc/fuse.conf needs to be modified so
that 'user_allow_other' is set. Typically this involves uncommenting a single
line of code, see the example below of an /etc/fuse.conf file that has
'use_allow_other' enabled.

```bash
# /etc/fuse.conf - Configuration file for Filesystem in Userspace (FUSE)

# Set the maximum number of FUSE mounts allowed to non-root users.
# The default is 1000.
#mount_max = 1000

# Allow non-root users to specify the allow_other or allow_root mount options.
user_allow_other
```

### Response

standard success or error response. See [standard
responses](#standard-responses).