## /host [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> -X POST "localhost:8480/host?acceptingcontracts=true&maxduration=12096&windowsize=1008"
```

Configures hosting parameters. All parameters are optional; unspecified
parameters will be left unchanged.

### Query String Parameters
### OPTIONAL
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
// The storage proof window is the number of blocks that the host has to get a
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

**minsectoraccessprice** | hastings  
The minimum price that the host will demand from a renter for accessing a sector
of data on disk. Since the host has to read at least a full 4MB sector from disk
regardless of how much the renter intends to download this is charged to pay for
the physical disk resources the host uses. It is multiplied by the number of
sectors read then added to the `mindownloadbandwidthprice` when downloading a
file.

**mindownloadbandwidthprice** | hastings / byte  
The minimum price that the host will demand from a renter when the renter is
downloading data. If the host is saturated, the host may increase the price from
the minimum.

**minstorageprice** | hastings / byte / block  
The minimum price that the host will demand when storing data for extended
periods of time. If the host is low on space, the price of storage may be set
higher than the minimum.

**minuploadbandwidthprice** | hastings / byte  
The minimum price that the host will demand from a renter when the renter is
uploading data. If the host is saturated, the host may increase the price from
the minimum.

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

Note that money is only at risk if the host experiences an
unclean shutdown while in the middle of a transaction with a user, and generally
the amount at risk will be minuscule unless the host experiences an unclean
shutdown while in the middle of many transactions with many users at once. This
value should be larger than 'maxephemeralaccountbalance but does not need to be
significantly larger.

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

### Response

standard success or error response. See standard responses.