## /renter/contracts [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/renter/contracts?disabled=true&expired=true&recoverable=false"
```

Returns the renter's contracts. Active, passive, and refreshed contracts are
returned by default. Active contracts are contracts that the Renter is currently
using to store, upload, and download data. Passive contracts are contracts that
are no longer GoodForUpload but are GoodForRenew. This means the data will
continue to be available to be downloaded from. Refreshed contracts are
contracts that ran out of funds and needed to be renewed so more money could be
added to the contract with the host. The data reported in these contracts is
duplicate data and should not be included in any accounting. Disabled contracts
are contracts that are in the current period and have not yet expired that are
not being used for uploading as they were replaced instead of renewed. Expired
contracts are contracts with an `EndHeight` in the past, where no more data is
being stored and excess funds have been released to the renter. Expired
Refreshed contracts are contracts that were refreshed at some point in a
previous period. The data reported in these contracts is duplicate data and
should not be included in any accounting. Recoverable contracts are contracts
which the contractor is currently trying to recover and which haven't expired
yet.

| Type              | GoodForUpload | GoodForRenew | Endheight in the Future | Data Counted Elsewhere Already|
| ----------------- | :-----------: | :----------: | :---------------------: | :---------------------------: |
| Active            | Yes           | Yes          | Yes                     | No                            |
| Passive           | No            | Yes          | Yes                     | No                            |
| Refreshed         | No            | No           | Yes                     | Yes                           |
| Disabled          | No            | No           | Yes                     | No                            |
| Expired           | No            | No           | No                      | No                            |
| Expired Refreshed | No            | No           | No                      | Yes                           |

**NOTE:** No spending is double counted anywhere in the contracts, only the data
is double counted in the refreshed contracts. For spending totals in the current
period, all spending in active, passive, refreshed, and disabled contracts
should be counted. For data totals, the data in active and passive contracts is
the total uploaded while the data in disabled contracts is wasted uploaded data.

### Query String Parameters
### OPTIONAL
**disabled** | boolean  
flag indicating if disabled contracts should be returned.

**expired** | boolean  
flag indicating if expired contracts should be returned.

**recoverable** | boolean  
flag indicating if recoverable contracts should be returned.

### JSON Response
> JSON Response Example

```go
{
  "activecontracts": [
    {
      "downloadspending": "1234", // hastings
      "endheight":        50000,  // block height
      "fees":             "1234", // hastings
      "hostpublickey": {
        "algorithm": "ed25519",   // string
        "key": "RW50cm9weSBpc24ndCB3aGF0IGl0IHVzZWQgdG8gYmU=" // hash
      },
      "hostversion":      "1.4.0",  // string
      "id": "1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef", // hash
      "lasttransaction": {},                // transaction
      "netaddress":       "12.34.56.78:9",  // string
      "renterfunds":      "1234",           // hastings
      "size":             8192,             // bytes
      "startheight":      50000,            // block height
      "storagespending":  "1234",           // hastings
      "totalcost":        "1234",           // hastings
      "uploadspending":   "1234"            // hastings
      "goodforupload":    true,             // boolean
      "goodforrenew":     false,            // boolean
      "badcontract":      false,            // boolean
    }
  ],
  "passivecontracts": [],
  "refreshedcontracts": [],
  "disabledcontracts": [],
  "expiredcontracts": [],
  "expiredrefreshedcontracts": [],
  "recoverablecontracts": [],
}
```
**downloadspending** | hastings  
Amount of contract funds that have been spent on downloads.

**endheight** | block height  
Block height that the file contract ends on.

**fees** | hastings  
Fees paid in order to form the file contract.

**hostpublickey** | UploPublicKey  
Public key of the host that the file contract is formed with.

**hostversion** | string  
The version of the host.

**algorithm** | string  
Algorithm used for signing and verification. Typically "ed25519".

**key** | hash  
Key used to verify signed host messages.

**id** | hash  
ID of the file contract.

**lasttransaction** | transaction  
A signed transaction containing the most recent contract revision.

**netaddress** | string  
Address of the host the file contract was formed with.

**renterfunds** | hastings  
Remaining funds left for the renter to spend on uploads & downloads.

**size** | bytes  
Size of the file contract, which is typically equal to the number of bytes that
have been uploaded to the host.

**startheight** | block height  
Block height that the file contract began on.

**storagespending** | hastings  
Amount of contract funds that have been spent on storage.

**totalcost** | hastings  
Total cost to the wallet of forming the file contract. This includes both the
fees and the funds allocated in the contract.

**uploadspending** | hastings  
Amount of contract funds that have been spent on uploads.

**goodforupload** | boolean  
Signals if contract is good for uploading data.

**goodforrenew** | boolean  
Signals if contract is good for a renewal.

**badcontract** | boolean  
Signals whether a contract has been marked as bad. A contract will be marked as
bad if the contract does not make it onto the blockchain or otherwise gets
double spent. A contract can also be marked as bad if the host is refusing to
acknowldege that the contract exists.