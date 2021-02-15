## /renter/dir/*uplopath* [GET]
> curl example

> The root uplodir path is "" so submitting the API call without an empty uplopath
will return the root uplodir information.

```go
curl -A "Uplo-Agent" "localhost:8480/renter/dir/"
```  
```go
curl -A "Uplo-Agent" "localhost:8480/renter/dir/mydir"
```

retrieves the contents of a directory on the uplo network

### Path Parameters
### REQUIRED
**uplopath** | string  
Path to the directory on the uplo network

### OPTIONAL
**root** | bool  
Whether or not to treat the uplopath as being relative to the user's home
directory. If this field is not set, the uplopath will be interpreted as
relative to 'home/user/'.

### JSON Response
> JSON Response Example

```go
{
  "directories": [
    {
      "aggregatehealth":              1.0,  // float64
      "aggregatelasthealthchecktime": "2018-09-23T08:00:00.000000000+04:00" // timestamp
      "aggregatemaxhealth":           1.0,  // float64
      "aggregatemaxhealthpercentage": 1.0,  // float64
      "aggregateminredundancy":       2.6,  // float64
      "aggregatemostrecentmodtime":   "2018-09-23T08:00:00.000000000+04:00" // timestamp
      "aggregatenumfiles":            2,    // uint64
      "aggregatenumstuckchunks":      4,    // uint64
      "aggregatenumsubdirs":          4,    // uint64
      "aggregaterepairsize":          4096, // uint64
      "aggregatesize":                4096, // uint64
      "aggregatestuckhealth":         1.0,  // float64
      "aggregatestucksize":           4096, // uint64
      
      "aggregateskynetfiles": 40,   // uint64
      "aggregateskynetsize":  4096, // uint64

      "health":              1.0,      // float64
      "lasthealthchecktime": "2018-09-23T08:00:00.000000000+04:00" // timestamp
      "maxhealth":           0.5,      // float64
      "maxhealthpercentage": 1.0,      // float64
      "minredundancy":       2.6,      // float64
      "mode":                0666,     // uint32
      "mostrecentmodtime":   "2018-09-23T08:00:00.000000000+04:00" // timestamp
      "numfiles":            3,        // uint64
      "numstuckchunks":      3,        // uint64
      "numsubdirs":          2,        // uint64
      "repairsize":          4096,     // uint64
      "uplopath":             "foo/bar" // string
      "size":                4096,     // uint64
      "stuckhealth":         1.0,      // float64
      "stucksize":           4096,     // uint64

      "UID": "9ce7ff6c2b65a760b7362f5a041d3e84e65e22dd", // string
      
      "skynetfiles": 40,   // uint64
      "skynetsize":  4096, // uint64
    }
  ],
  "files": []
}
```

**directories**\
An array of uplo directories. Directories contain directory level metadata and
aggregate metadata for the subtree of the filesystem of which the directory
is the root of.

**aggregatehealth** | **health** | float64\
This is the worst health of any of the files or subdirectories. Health is the
percent of parity pieces missing.
- health = 0 is full redundancy
- health <= 1 is recoverable
- health > 1 needs to be repaired from disk

**aggregatelasthealthchecktime** | **lasthealthchecktime** | timestamp\
The oldest time that the health of the directory or any of its files or sub
directories' health was checked.

**aggregatemaxhealth** | **maxhealth** | float64\
This is the worst health when comparing stuck health vs health

**aggregatemaxhealthpercentage** | **maxhealthpercentage** | float64\
This is the `maxhealth` displayed as a percentage. Since health is the amount
of redundancy missing, files can have up to 25% of the redundancy missing and
still be considered 100% healthy.

**aggregateminredundancy** | **minredundancy** | float64\
The lowest redundancy of any file or directory in the sub directory tree

**mode** | unit32\
The filesystem mode of the directory. There is no corresponding aggregate
field for mode.

**aggregatemostrecentmodtime** | **mostrecentmodtime** | timestamp\
The most recent mod time of any file or directory in the sub directory tree

**aggregatenumfiles** | **numfiles** | uint64\
The total number of files in the sub directory tree

**aggregatenumstuckchunks** | **aggregatenumstuckchunks** | uint64\
The total number of stuck chunks in the sub directory tree

**aggregatenumsubdirs** | **numsubdirs** | uint64\
The number of directories in the directory

**aggregaterepairsize** | **repairsize** | uint64\
The total size in bytes that needs to be handled by the repair loop. This
does not include files that only have less than 25% of the redundancy missing
as the repair loop will ignore these files until they lose more redundancy.
This also does not include any stuck data.

**uplopath** | string\
The path to the directory on the uplo network. There is no corresponding
aggregate value for uplopath.

**aggregatesize** | **size** | uint64\
The total size in bytes of files in the sub directory tree

**aggregatestuckhealth** | **stuckhealth** | floatt64\
The health of the most in need stuck uplofile in the directory

**aggregatestucksize** | **stucksize** | uint64\
The total size in bytes that needs to be handled by the stuck loop. This does
include files that only have less than 25% of the redundancy missing as the
stuck loop does not take into account the health of the stuck file.

**UID** | string\
The unique identifier for the directory in the filesystem. There is no corresponding aggregate field for UID.

**aggregateskynetfiles** | **skynetfiles** | uint64\
The total number of skyfiles. This includes skyfile uploads and uplofile to
skyfile conversions.

**aggregateskynetsize** | **skynetsize** | uint64\
The total size in bytes that corresponds to a skyfile. This includes skyfile
uploads and uplofile to skyfile conversions.

**files** Same response as [files](#files)