## /renter/workers [GET]

**UNSTABLE - subject to change**

> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/renter/workers"
```

returns the the status of all the workers in the renter's workerpool.

### JSON Response
> JSON Response Example

```go
{
  "numworkers":            2, // int
  "totaldownloadcooldown": 0, // int
  "totalmaintenancecooldown": 0, // int
  "totaluploadcooldown":   0, // int
  
  "workers": [ // []WorkerStatus
    {
      "contractid": "e93de33cc04bb1f27a412ecdf57b3a7345b9a4163a33e03b4cb23edeb922822c", // hash
      "contractutility": {      // ContractUtility
        "goodforupload": true,  // boolean
        "goodforrenew":  true,  // boolean
        "badcontract":   false, // boolean
        "lastooserr":    0,     // BlockHeight
        "locked":        false  // boolean
      },
      "hostpubkey": {
        "algorithm": "ed25519", // string
        "key": "BervnaN85yB02PzIA66y/3MfWpsjRIgovCU9/L4d8zQ=" // hash
      },
      
      "downloadcooldownerror": "",                   // string
      "downloadcooldowntime":  -9223372036854775808, // time.Duration
      "downloadoncooldown":    false,                // boolean
      "downloadqueuesize":     0,                    // int
      "downloadterminated":    false,                // boolean
      
      "uploadcooldownerror": "",                   // string
      "uploadcooldowntime":  -9223372036854775808, // time.Duration
      "uploadoncooldown":    false,                // boolean
      "uploadqueuesize":     0,                    // int
      "uploadterminated":    false,                // boolean
      
      "balancetarget":       "0", // hastings

      "downloadsnapshotjobqueuesize": 0 // int
      "uploadsnapshotjobqueuesize": 0   // int

      "maintenanceoncooldown": false,                      // bool
      "maintenancerecenterr": "",                          // string
      "maintenancerecenterrtime": "0001-01-01T00:00:00Z",  // time

      "accountstatus": {
        "availablebalance": "1000000000000000000000000", // hasting
        "negativebalance": "0",                          // hasting
        "recenterr": "",                                 // string
        "recenterrtime": "0001-01-01T00:00:00Z"          // time
        "recentsuccesstime": "0001-01-01T00:00:00Z"      // time
      },

      "pricetablestatus": {
        "expirytime": "2020-06-15T16:17:01.040481+02:00", // time
        "updatetime": "2020-06-15T16:12:01.040481+02:00", // time
        "active": true,                                   // boolean
        "recenterr": "",                                  // string
        "recenterrtime": "0001-01-01T00:00:00Z"           // time
      },

      "readjobsstatus": {
        "avgjobtime64k": 0,                               // int
        "avgjobtime1m": 0,                                // int
        "avgjobtime4m": 0,                                // int
        "consecutivefailures": 0,                         // int
        "jobqueuesize": 0,                                // int
        "recenterr": "",                                  // string
        "recenterrtime": "0001-01-01T00:00:00Z"           // time
      },

      "hassectorjobsstatus": {
        "avgjobtime": 0,                                  // int
        "consecutivefailures": 0,                         // int
        "jobqueuesize": 0,                                // int
        "recenterr": "",                                  // string
        "recenterrtime": "0001-01-01T00:00:00Z"           // time
      }
    }
  ]
}
```


**numworkers** | int  
Number of workers in the workerpool

**totaldownloadcooldown** | int  
Number of workers on download cooldown

**totalmaintenancecooldown** | int  
Number of workers on maintenance cooldown

**totaluploadcooldown** | int  
Number of workers on upload cooldown

**workers** | []WorkerStatus  
List of workers

**contractid** | hash  
The ID of the File Contract that the worker is associated with

**contractutility** | ContractUtility

**goodforupload** | boolean  
The worker's contract can be uploaded to

**goodforrenew** | boolean  
The worker's contract will be renewed

**badcontract** | boolean  
The worker's contract is marked as bad and won't be used

**lastooserr** | BlockHeight  
The blockheight when the host the worker represents was out of storage

**locked** | boolean  
The worker's contract's utility is locked

**hostpublickey** | UploPublicKey  
Public key of the host that the file contract is formed with.

**downloadcooldownerror** | error  
The error reason for the worker being on download cooldown

**downloadcooldowntime** | time.Duration  
How long the worker is on download cooldown

**downloadoncooldown** | boolean  
Indicates if the worker is on download cooldown

**downloadqueuesize** | int  
The size of the worker's download queue

**downloadterminated** | boolean  
Downloads for the worker have been terminated

**uploadcooldownerror** | error  
The error reason for the worker being on upload cooldown

**uploadcooldowntime** | time.Duration  
How long the worker is on upload cooldown

**uploadoncooldown** | boolean  
Indicates if the worker is on upload cooldown

**uploadqueuesize** | int  
The size of the worker's upload queue

**uploadterminated** | boolean  
Uploads for the worker have been terminated

**availablebalance** | hastings  
The worker's Ephemeral Account available balance

**balancetarget** | hastings  
The worker's Ephemeral Account target balance

**downloadsnapshotjobqueuesize** | int  
The size of the worker's download snapshot job queue

**uploadsnapshotjobqueuesize** | int  
The size of the worker's upload snapshot job queue

**maintenanceoncooldown** | boolean  
Indicates if the worker is on maintenance cooldown

**maintenancecooldownerror** | string  
The error reason for the worker being on maintenance cooldown

**maintenancecooldowntime** | time.Duration  
How long the worker is on maintenance cooldown

**accountstatus** | object
Detailed information about the workers' ephemeral account status

**pricetablestatus** | object
Detailed information about the workers' price table status

**readjobsstatus** | object
Details of the workers' read jobs queue

**hassectorjobsstatus** | object
Details of the workers' has sector jobs queue