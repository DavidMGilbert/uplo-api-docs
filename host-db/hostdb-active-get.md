## /hostdb/active [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/hostdb/active"
```

lists all of the active hosts known to the renter, sorted by preference.

### Query String Parameters
### OPTIONAL
**numhosts** | int  
Number of hosts to return. The actual number of hosts returned may be less if
there are insufficient active hosts. Optional, the default is all active hosts.


### JSON Response
> JSON Response Example

```go
{
  "hosts": [
        {
      "acceptingcontracts":     true,                 // boolean
      "maxdownloadbatchsize":   17825792,             // bytes
      "maxduration":            25920,                // blocks
      "maxrevisebatchsize":     17825792,             // bytes
      "netaddress":             "123.456.789.0:8482"  // string 
      "remainingstorage":       35000000000,          // bytes
      "sectorsize":             4194304,              // bytes
      "totalstorage":           35000000000,          // bytes
      "unlockhash": "0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef0123456789ab", // hash
      "windowsize":             144,                            // blocks
      "collateral":             "20000000000"                   // hastings / byte / block
      "maxcollateral":          "1000000000000000000000000000"  // hastings
      "contractprice":          "1000000000000000000000000"     // hastings
      "downloadbandwidthprice": "35000000000000"                // hastings / byte
      "storageprice":           "14000000000"                   // hastings / byte / block
      "uploadbandwidthprice":   "3000000000000"                 // hastings / byte
      "revisionnumber":         12733798,                       // int
      "version":                "1.3.4"                         // string
      "firstseen":              160000,                         // blocks
      "historicdowntime":       0,                              // nanoseconds
      "historicuptime":         41634520900246576,              // nanoseconds
      "scanhistory": [
        {
          "success": true,  // boolean
          "timestamp": "2018-09-23T08:00:00.000000000+04:00"  // unix timestamp
        },
        {
          "success": true,  // boolean
          "timestamp": "2018-09-23T06:00:00.000000000+04:00"  // unix timestamp
        },
        {
          "success": true,  // boolean// boolean
          "timestamp": "2018-09-23T04:00:00.000000000+04:00"  // unix timestamp
        }
      ],
      "historicfailedinteractions":     0,      // int
      "historicsuccessfulinteractions": 5,      // int
      "recentfailedinteractions":       0,      // int
      "recentsuccessfulinteractions":   0,      // int
      "lasthistoricupdate":             174900, // blocks
      "ipnets": [
        "1.2.3.0",  // string
        "2.1.3.0"   // string
      ],
      "lastipnetchange": "2015-01-01T08:00:00.000000000+04:00", // unix timestamp
      "publickey": {
        "algorithm": "ed25519", // string
        "key":       "RW50cm9weSBpc24ndCB3aGF0IGl0IHVzZWQgdG8gYmU=" // string
      },
      "publickeystring": "ed25519:1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef",  // string
      "filtered": false, // boolean
    }
  ]
}
```

**hosts**  
**acceptingcontracts** | boolean  
true if the host is accepting new contracts.

**maxdownloadbatchsize** | bytes  
Maximum number of bytes that the host will allow to be requested by a single
download request.

**maxduration** | blocks  
Maximum duration in blocks that a host will allow for a file contract. The host
commits to keeping files for the full duration under the threat of facing a
large penalty for losing or dropping data before the duration is complete. The
storage proof window of an incoming file contract must end before the current
height + maxduration.

There is a block approximately every 10 minutes. e.g. 1 day = 144 blocks

**maxrevisebatchsize** | bytes  
Maximum size in bytes of a single batch of file contract revisions. Larger batch
sizes allow for higher throughput as there is significant communication overhead
associated with performing a batch upload.

**netaddress** | string  
Remote address of the host. It can be an IPv4, IPv6, or hostname, along with the
port. IPv6 addresses are enclosed in square brackets.

**remainingstorage** | bytes  
Unused storage capacity the host claims it has.

**sectorsize** | bytes  
Smallest amount of data in bytes that can be uploaded or downloaded to or from
the host.

**totalstorage** | bytes  
Total amount of storage capacity the host claims it has.

**unlockhash** | hash  
Address at which the host can be paid when forming file contracts.

**windowsize** | blocks  
A storage proof window is the number of blocks that the host has to get a
storage proof onto the blockchain. The window size is the minimum size of window
that the host will accept in a file contract.

**collateral** | hastings / byte / block  
The maximum amount of money that the host will put up as collateral for storage
that is contracted by the renter.

**maxcollateral** | hastings  
The maximum amount of collateral that the host will put into a single file
contract.

**contractprice** | hastings  
The price that a renter has to pay to create a contract with the host. The
payment is intended to cover transaction fees for the file contract revision and
the storage proof that the host will be submitting to the blockchain.

**downloadbandwidthprice** | hastings / byte  
The price that a renter has to pay when downloading data from the host.

**storageprice** | hastings / byte / block  
The price that a renter has to pay to store files with the host.

**uploadbandwidthprice** | hastings / byte  
The price that a renter has to pay when uploading data to the host.

**revisionnumber** | int  
The revision number indicates to the renter what iteration of settings the host
is currently at. Settings are generally signed. If the renter has multiple
conflicting copies of settings from the host, the renter can expect the one with
the higher revision number to be more recent.

**version** | string  
The version of the host.

**firstseen** | blocks  
Firstseen is the last block height at which this host was announced.

**historicdowntime** | nanoseconds  
Total amount of time the host has been offline.

**historicuptime** | nanoseconds  
Total amount of time the host has been online.

**scanhistory** Measurements that have been taken on the host. The most recent
measurements are kept in full detail.

**historicfailedinteractions** | int  
Number of historic failed interactions with the host.

**historicsuccessfulinteractions** | int Number of historic successful
interactions with the host.

**recentfailedinteractions** | int  
Number of recent failed interactions with the host.

**recentsuccessfulinteractions** | int  
Number of recent successful interactions with the host.

**lasthistoricupdate** | blocks  
The last time that the interactions within scanhistory have been compressed into
the historic ones.

**ipnets**  
List of IP subnet masks used by the host. For IPv4 the /24 and for IPv6 the /54
subnet mask is used. A host can have either one IPv4 or one IPv6 subnet or one
of each. E.g. these lists are valid: [ "IPv4" ], [ "IPv6" ] or [ "IPv4", "IPv6"
]. The following lists are invalid: [ "IPv4", "IPv4" ], [ "IPv4", "IPv6", "IPv6"
]. Hosts with an invalid list are ignored.

**lastipnetchange** | date  
The last time the list of IP subnet masks was updated. When equal subnet masks
are found for different hosts, the host that occupies the subnet mask for a
longer time is preferred.

**publickey** | UploPublicKey  
Public key used to identify and verify hosts.

**algorithm** | string  
Algorithm used for signing and verification. Typically "ed25519".

**key** | hash  
Key used to verify signed host messages.

**publickeystring** | string  
The string representation of the full public key, used when calling
/hostdb/hosts.

**filtered** | boolean  
Indicates if the host is currently being filtered from the HostDB