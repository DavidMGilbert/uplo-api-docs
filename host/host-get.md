## /host [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/host"
```

fetches status information about the host.

### JSON Response
> JSON Response Example

```go
{
  "externalsettings": {
    "acceptingcontracts":   true,                 // boolean
    "maxdownloadbatchsize": 17825792,             // bytes
    "maxduration":          25920,                // blocks
    "maxrevisebatchsize":   17825792,             // bytes
    "netaddress":           "123.456.789.0:8482", // string
    "remainingstorage":     35000000000,          // bytes
    "sectorsize":           4194304,              // bytes
    "totalstorage":         35000000000,          // bytes
    "unlockhash":           "0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef0123456789ab", // hash
    "windowsize":           144,  // blocks

    "collateral":    "57870370370",                     // hastings / byte / block
    "maxcollateral": "100000000000000000000000000000",  // hastings

    "contractprice":          "30000000000000000000000000", // hastings
    "downloadbandwidthprice": "250000000000000",            // hastings / byte
    "storageprice":           "231481481481",               // hastings / byte / block
    "uploadbandwidthprice":   "100000000000000",            // hastings / byte

    "registrysize":       16384,  // int
    "customregistrypath": ""      // string
    "revisionnumber":     0,      // int
    "version":            "1.0.0" // string
  },

  "financialmetrics": {
    "contractcount":                 2,     // int
    "contractcompensation":          "123", // hastings
    "potentialcontractcompensation": "123", // hastings

    "lockedstoragecollateral": "123", // hastings
    "lostrevenue":             "123", // hastings
    "loststoragecollateral":   "123", // hastings
    "potentialstoragerevenue": "123", // hastings
    "riskedstoragecollateral": "123", // hastings
    "storagerevenue":          "123", // hastings
    "transactionfeeexpenses":  "123", // hastings

    "downloadbandwidthrevenue":          "123", // hastings
    "potentialdownloadbandwidthrevenue": "123", // hastings
    "potentialuploadbandwidthrevenue":   "123", // hastings
    "uploadbandwidthrevenue":            "123"  // hastings
  },

  "internalsettings": {
    "acceptingcontracts":   true,                 // boolean
    "maxdownloadbatchsize": 17825792,             // bytes
    "maxduration":          25920,                // blocks
    "maxrevisebatchsize":   17825792,             // bytes
    "netaddress":           "123.456.789.0:8482", // string
    "windowsize":           144,                  // blocks
    
    "collateral":       "57870370370",                     // hastings / byte / block
    "collateralbudget": "2000000000000000000000000000000", // hastings
    "maxcollateral":    "100000000000000000000000000000",  // hastings
    
    "minbaserpcprice":           "123",                        //hastings
    "mincontractprice":          "30000000000000000000000000", // hastings
    "mindownloadbandwidthprice": "250000000000000",            // hastings / byte
    "minsectoraccessprice":      "123",                        //hastings
    "minstorageprice":           "231481481481",               // hastings / byte / block
    "minuploadbandwidthprice":   "100000000000000"             // hastings / byte

    "ephemeralaccountexpiry":     "604800",                          // seconds
    "maxephemeralaccountbalance": "2000000000000000000000000000000", // hastings
    "maxephemeralaccountrisk":    "2000000000000000000000000000000", // hastings
  },

  "networkmetrics": {
    "downloadcalls":     0,   // int
    "errorcalls":        1,   // int
    "formcontractcalls": 2,   // int
    "renewcalls":        3,   // int
    "revisecalls":       4,   // int
    "settingscalls":     5,   // int
    "unrecognizedcalls": 6    // int
  },

  "connectabilitystatus": "checking", // string
  "workingstatus":        "checking"  // string
  "publickey": {
    "algorithm": "ed25519", // string
    "key":       "RW50cm9weSBpc24ndCB3aGF0IGl0IHVzZWQgdG8gYmU=" // string
  },

"pricetable": {
  "uid":                        "00000000000000000000000000000000", // types.Specifier
  "validity":                   60000000000, // time.Duration
  "hostblockheight":            0, // types.BlockHeight

  "updatepricetablecost":       "1", // types.Currency
  "accountbalancecost":         "1", // types.Currency
  "fundaccountcost":            "1", // types.Currency
  "latestrevisioncost":         "151200000000000000", // types.Currency
  "initbasecost":               "100000000000000000", // types.Currency
  "memorytimecost":             "1", // types.Currency
  "collateralcost":             "0", // types.Currency
  "downloadbandwidthcost":      "25000000000000", // types.Currency
  "uploadbandwidthcost":        "1000000000000", // types.Currency
  "dropsectorsbasecost":        "1", // types.Currency
  "dropsectorsunitcost":        "1", // types.Currency
  "hassectorbasecost":          "1", // types.Currency
  "readbasecost":               "2000000000000000000", // types.Currency
  "readlengthcost":             "1", // types.Currency
  "revisionbasecost":           "0", // types.Currency
  "swapsectorcost":             "1", // types.Currency
  "writebasecost":              "1", // types.Currency
  "writelengthcost":            "1", // types.Currency
  "writestorecost":             "11574074074", // types.Currency

  "txnfeeminrecommended":       "10000000000000000000", // types.Currency
  "txnfeemaxrecommended":       "30000000000000000000", // types.Currency

  "registryentriesleft":        1024, // uint64
  "registryentriestotal":       1024, // uint64
  },
}
```
**externalsettings**    
The settings that get displayed to untrusted nodes querying the host's status.

**acceptingcontracts** | boolean  
Whether or not the host is accepting new contracts.

**maxdownloadbatchsize** | bytes  
The maximum size of a single download request from a renter. Each download
request has multiple round trips of communication that exchange money. Larger
batch sizes mean fewer round trips, but more financial risk for the host - the
renter can get a free batch when downloading by refusing to provide a signature.


**maxduration** | blocks  
The maximum duration that a host will allow for a file contract. The host
commits to keeping files for the full duration under the threat of facing a
large penalty for losing or dropping data before the duration is complete. The
storage proof window of an incoming file contract must end before the current
height + maxduration.

**maxrevisebatchsize** | bytes  
The maximum size of a single batch of file contract revisions. The renter can
perform DoS attacks on the host by uploading a batch of data then refusing to
provide a signature to pay for the data. The host can reduce this exposure by
limiting the batch size. Larger batch sizes allow for higher throughput as there
is significant communication overhead associated with performing a batch upload.


**netaddress** | string  
The IP address or hostname (including port) that the host should be contacted
at.

**remainingstorage** | bytes  
The amount of unused storage capacity on the host in bytes. It should be noted
that the host can lie.

**sectorsize** | bytes  
The smallest amount of data in bytes that can be uploaded or downloaded when
performing calls to the host.

**totalstorage** | bytes  
The total amount of storage capacity on the host. It should be noted that the
host can lie.

**unlockhash** | hash  
The unlock hash is the address at which the host can be paid when forming file
contracts.

**windowsize** | blocks  
The storage proof window is the number of blocks that the host has to get a
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

**registrysize** | int  
The size of the registry in bytes. One entry requires 256 bytes of storage on
disk and the size of the registry needs to be a multiple of 64 entries.
Therefore any provided number >0 bytes will be rounded to the nearest 16kib.
The default is 0 which means no registry.

**customregistrypath** | string  
The path of the registry on disk. If it's empty, it uses the default location
relative to uplod's host folder. Otherwise the provided path will be used.
Changing it will trigger a registry migration which takes an arbitrary amount
of time depending on the size of the registry.

**revisionnumber** | int  
The revision number indicates to the renter what iteration of settings the host
is currently at. Settings are generally signed. If the renter has multiple
conflicting copies of settings from the host, the renter can expect the one with
the higher revision number to be more recent.

**version** | string  
The version of external settings being used. This field helps coordinate updates
while preserving compatibility with older nodes.

**financialmetrics**    
The financial status of the host.

**contractcount** | int  
Number of open file contracts.

**contractcompensation** | hastings  
The amount of money that renters have given to the host to pay for file
contracts. The host is required to submit a file contract revision and a storage
proof for every file contract that gets created, and the renter pays for the
miner fees on  these objects.

**potentialcontractcompensation** | hastings  
The amount of money that renters have given to the host to pay for file
contracts which have not been confirmed yet. The potential compensation becomes
compensation after the storage proof is submitted.

**lockedstoragecollateral** | hastings  
The amount of storage collateral which the host has tied up in file contracts.
The host has to commit collateral to a file contract even if there is no
storage, but the locked collateral will be returned even if the host does not
submit a storage proof - the collateral is not at risk, it is merely set aside
so that it can be put at risk later.

**lostrevenue** | hastings  
The amount of revenue, including storage revenue and bandwidth revenue, that has
been lost due to failed file contracts and failed storage proofs.

**loststoragecollateral** | hastings  
The amount of collateral that was put up to protect data which has been lost due
to failed file contracts and missed storage proofs.

**potentialstoragerevenue** | hastings  
The amount of revenue that the host stands to earn if all storage proofs are
submitted correctly and in time.

**riskedstoragecollateral** | hastings  
The amount of money that the host has risked on file contracts. If the host
starts missing storage proofs, the host can forfeit up to this many coins. In
the event of a missed storage proof, locked storage collateral gets returned,
but risked storage collateral does not get returned.

**storagerevenue** | hastings  
The amount of money that the host has earned from storing data. This money has
been locked down by successful storage proofs.

**transactionfeeexpenses** | hastings  
The amount of money that the host has spent on transaction fees when submitting
host announcements, file contract revisions, and storage proofs.

**downloadbandwidthrevenue** | hastings  
The amount of money that the host has made from renters downloading their files.
This money has been locked in by successsful storage proofs.

**potentialdownloadbandwidthrevenue** | hastings  
The amount of money that the host stands to make from renters that downloaded
their files. The host will only realize this revenue if the host successfully
submits storage proofs for the related file contracts.

**potentialuploadbandwidthrevenue** | hastings  
The amount of money that the host stands to make from renters that uploaded
files. The host will only realize this revenue if the host successfully submits
storage proofs for the related file contracts.

**uploadbandwidthrevenue** | hastings  
The amount of money that the host has made from renters uploading their files.
This money has been locked in by successful storage proofs.

**internalsettings**    
The settings of the host. Most interactions between the user and the host occur
by changing the internal settings.

**acceptingcontracts** | boolean  
When set to true, the host will accept new file contracts if the terms are
reasonable. When set to false, the host will not accept new file contracts at
all.

**maxdownloadbatchsize** | bytes  
The maximum size of a single download request from a renter. Each download
request has multiple round trips of communication that exchange money. Larger
batch sizes mean fewer round trips, but more financial risk for the host - the
renter can get a free batch when downloading by refusing to provide a signature.


**maxduration** | blocks  
The maximum duration of a file contract that the host will accept. The storage
proof window must end before the current height + maxduration.

**maxrevisebatchsize** | bytes  
The maximum size of a single batch of file contract revisions. The renter can
perform DoS attacks on the host by uploading a batch of data then refusing to
provide a signature to pay for the data. The host can reduce this exposure by
limiting the batch size. Larger batch sizes allow for higher throughput as there
is significant communication overhead associated with performing a batch upload.


**netaddress** | string  
The IP address or hostname (including port) that the host should be contacted
at. If left blank, the host will automatically figure out its ip address and use
that. If given, the host will use the address given.

**windowsize** | blocks  
The storage proof window is the number of blocks that the host has to get a
storage proof onto the blockchain. The window size is the minimum size of window
that the host will accept in a file contract.

**collateral** | hastings / byte / block  
The maximum amount of money that the host will put up as collateral per byte per
block of storage that is contracted by the renter.

**collateralbudget** | hastings  
The total amount of money that the host will allocate to collateral across all
file contracts.

**maxcollateral** | hastings  
The maximum amount of collateral that the host will put into a single file
contract.

**minbaserpcprice** | hastings  
The minimum price that the host will demand from a renter for interacting with
the host. This is charged for every interaction a renter has with a host to pay
for resources consumed during the interaction. It is added to the
`mindownloadbandwidthprice` and `minuploadbandwidthprice` when uploading or
downloading files from the host.

**mincontractprice** | hastings  
The minimum price that the host will demand from a renter when forming a
contract. Typically this price is to cover transaction fees on the file contract
revision and storage proof, but can also be used if the host has a low amount of
collateral. The price is a minimum because the host may automatically adjust the
price upwards in times of high demand.

**mindownloadbandwidthprice** | hastings / byte  
The minimum price that the host will demand from a renter when the renter is
downloading data. If the host is saturated, the host may increase the price from
the minimum.

**minsectoraccessprice** | hastings  
The minimum price that the host will demand from a renter for accessing a sector
of data on disk. Since the host has to read at least a full 4MB sector from disk
regardless of how much the renter intends to download this is charged to pay for
the physical disk resources the host uses. It is multiplied by the number of
sectors read then added to the `mindownloadbandwidthprice` when downloading a
file.

**minstorageprice** | hastings / byte / block  
The minimum price that the host will demand when storing data for extended
periods of time. If the host is low on space, the price of storage may be set
higher than the minimum.

**minuploadbandwidthprice** | hastings / byte  
The minimum price that the host will demand from a renter when the renter is
uploading data. If the host is saturated, the host may increase the price from
the minimum.

**ephemeralaccountexpiry** | seconds  
The  maximum amount of time an ephemeral account can be inactive before it is
considered to be expired and gets deleted. After an account has expired, the
account owner has no way of retrieving the funds. Setting this value to 0 means
ephemeral accounts never expire, regardless of how long they have been inactive.

**maxephemeralaccountbalance** | hastings  
The maximum amount of money that the host will allow a user to deposit into a
single ephemeral account.

**maxephemeralaccountrisk** | hastings  
To increase performance, the host will allow a user to withdraw from an
ephemeral account without requiring the user to wait until the host has
persisted the updated ephemeral account balance to complete a transaction. This
means that the user can perform actions such as downloads with significantly
less latency. This also means that if the host loses power at that exact moment,
the host will forget that the user has spent money and the user will be able to
spend that money again.

maxephemeralaccountrisk is the maximum amount of money that the host is willing
to risk to a system failure. The account manager will keep track of the total
amount of money that has been withdrawn, but has not yet been persisted to disk.
If a user's withdrawal would put the host over the maxephemeralaccountrisk, the
host will wait to complete the user's transaction until it has persisted the
widthdrawal, to prevent the host from having too much money at risk.

Note that money is only at risk if the host experiences an unclean shutdown
while in the middle of a transaction with a user, and generally the amount at
risk will be minuscule unless the host experiences an unclean shutdown while in
the middle of many transactions with many users at once. This value should be
larger than maxephemeralaccountbalance but does not need to be significantly
larger.

**networkmetrics**    
Information about the network, specifically various ways in which renters have
contacted the host.

**downloadcalls** | int  
The number of times that a renter has attempted to download something from the
host.

**errorcalls** | int  
The number of calls that have resulted in errors. A small number of errors are
expected, but a large number of errors indicate either buggy software or
malicious network activity. Usually buggy software.

**formcontractcalls** | int  
The number of times that a renter has tried to form a contract with the host.

**renewcalls** | int  
The number of times that a renter has tried to renew a contract with the host.

**revisecalls** | int  
The number of times that the renter has tried to revise a contract with the
host.

**settingscalls** | int  
The number of times that a renter has queried the host for the host's settings.
The settings include the price of bandwidth, which is a price that can adjust
every few minutes. This value is usually very high compared to the others.

**unrecognizedcalls** | int  
The number of times that a renter has attempted to use an unrecognized call.
Larger numbers typically indicate buggy software.

**connectabilitystatus** | string  
connectabilitystatus is one of "checking", "connectable", or "not connectable",
and indicates if the host can connect to itself on its configured NetAddress.

**workingstatus** | string  
workingstatus is one of "checking", "working", or "not working" and indicates if
the host is being actively used by renters.

**publickey** | UploPublicKey  
Public key used to identify the host.

**uid** | types.Specifier  
UID of the current price table. Only filled in for renters over the
peer-to-peer protocol. In the API it's always zeros.

**valdity** | time.Duration  
The duration for which a fresh price table is valid.

**hostblockheight** | types.BlockHeight  
Blockheight as seen by the host at the last time the table was updated.

**updatepricetablecost** | types.Currency  
Cost for the UpdatePriceTable RPC.

**accountbalanceCost** | types.Currency  
Cost for the AccountBalance RPC.

**fundaccountcost** | types.Currency  
Cost for the FundAccount RPC.

**latestrevisioncost** | types.Currency  
Cost for the LatestRevision RPC.

**initbasecost** | types.Currency  
InitBaseCost is the amount of cost that is incurred when an MDM program
starts to run. This doesn't include the memory used by the program data. The
total cost to initialize a program is calculated as
InitCost = InitBaseCost + MemoryTimeCost * Time

**memorytimecost** | types.Currency  
MemoryTimeCost is the amount of cost per byte per time that is incurred by
the memory consumption of the program.

**collateralcost** | types.Currency  
CollateralCost is the amount of money per byte the host is promising to lock
away as collateral when adding new data to a contract.

**downloadbandwidthcost** | types.Currency  
Cost per byte of downloading from a host.

**uploadbandwidthcost** | types.Currency  
Cost per byte of uploading from a host.

**dropsectorbasecost** | types.Currency  
Base cost of a drop sector MDM instruction.

**dropsectorunitcost** | types.Currency  
Additional per-sector cost of a drop sector MDM instruction.

**hassectorbasecost** | types.Currency  
Cost of a has sector MDM instruction.

**readbasecost** | types.Currency  
Base cost of a read instruction.

**readlengthcost** | types.Currency  
Additional per-byte cost of a read instruction.

**revisionbasecost** | types.Currency  
Cost of a revision instruction.

**swapsectorcost** | types.Currency  
Cost of swapping 2 sectors with a swap sector instruction.

**writebasecost** | types.Currency  
Base cost of a write instruction.

**writelengthcost** | types.Currency  
Additional per-byte cost of a write instruction.

**writestorecost** | types.Currency  
Addition per-byte per-block cost of a write instruction. Only applies to
adding new data, not overwriting data.

**txnfeeminrecommended** | types.Currency  
Minimum per-byte txnfee recommendation as seen by the host's transaction
pool.

**txnfeemaxrecommended** | types.Currency  
Maximum per-byte txnfee recommendation as seen by the host's transaction
pool.

**registryentriesleft** | uint64  
number of registry entries not in use.

**registryentriestotal** | uint64  
total number of registry entries the host has allocated.