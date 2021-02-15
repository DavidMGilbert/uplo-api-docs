# Renter

The renter manages the user's files on the network. The renter's API endpoints
expose methods for managing files on the network and managing the renter's
allocated funds.

## /renter [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/renter"
```

Returns the current settings along with metrics on the renter's spending.

### JSON Response
> JSON Response Example

```go
{
  "settings": {
    "allowance": {
      "funds":              "1234",         // hastings
      "hosts":              24,             // int
      "period":             6048,           // blocks
      "renewwindow":        3024            // blocks
      "expectedstorage":    1000000000000,  // uint64
      "expectedupload":     2,              // uint64
      "expecteddownload":   1,              // uint64
      "expectedredundancy": 3               // uint64
    },
    "maxuploadspeed":     1234, // BPS
    "maxdownloadspeed":   1234, // BPS
    "streamcachesize":    4     // int
  },
  "financialmetrics": {
    "contractfees":     "1234", // hastings
    "contractspending": "1234", // hastings (deprecated, now totalallocated)
    "downloadspending": "5678", // hastings
    "storagespending":  "1234", // hastings
    "totalallocated":   "1234", // hastings
    "uploadspending":   "5678", // hastings
    "unspent":          "1234"  // hastings
  },
  "currentperiod":  6000  // blockheight
  "nextperiod":    12248  // blockheight
  "uploadsstatus": {
    "pause":        false,       // boolean
    "pauseendtime": 1234567890,  // Unix timestamp
  }
}
```
**settings**    
Settings that control the behavior of the renter.

**allowance**   
Allowance dictates how much the renter is allowed to spend in a given period.
Note that funds are spent on both storage and bandwidth.

**funds** | hastings  
Funds determines the number of uplocoins that the renter will spend when forming
contracts with hosts. The renter will not allocate more than this amount of
uplocoins into the set of contracts each billing period. If the renter spends all
of the funds but then needs to form new contracts, the renter will wait until
either until the user increase the allowance funds, or until a new billing
period is reached. If there are not enough funds to repair all files, then files
may be at risk of getting lost.

**hosts** | int  
Hosts sets the number of hosts that will be used to form the allowance. Uplo
gains most of its resiliancy from having a large number of hosts. More hosts
will mean both more robustness and higher speeds when using the network, however
will also result in more memory consumption and higher blockchain fees. It is
recommended that the default number of hosts be treated as a minimum, and that
double the default number of default hosts be treated as a maximum.

**period** | blocks  
The period is equivalent to the billing cycle length. The renter will not spend
more than the full balance of its funds every billing period. When the billing
period is over, the contracts will be renewed and the spending will be reset.

**renewwindow** | blocks  
The renew window is how long the user has to renew their contracts. At the end
of the period, all of the contracts expire. The contracts need to be renewed
before they expire, otherwise the user will lose all of their files. The renew
window is the window of time at the end of the period during which the renter
will renew the users contracts. For example, if the renew window is 1 week long,
then during the final week of each period the user will renew their contracts.
If the user is offline for that whole week, the user's data will be lost.

Each billing period begins at the beginning of the renew window for the previous
period. For example, if the period is 12 weeks long and the renew window is 4
weeks long, then the first billing period technically begins at -4 weeks, or 4
weeks before the allowance is created. And the second billing period begins at
week 8, or 8 weeks after the allowance is created. The third billing period will
begin at week 20.

**expectedstorage** | bytes  
Expected storage is the amount of storage that the user expects to keep on the
Uplo network. This value is important to calibrate the spending habits of uplod.
Because Uplo is decentralized, there is no easy way for uplod to know what the
real world cost of storage is, nor what the real world price of a uplocoin is. To
overcome this deficiency, uplod depends on the user for guidance.

If the user has a low allowance and a high amount of expected storage, uplod will
more heavily prioritize cheaper hosts, and will also be more comfortable with
hosts that post lower amounts of collateral. If the user has a high allowance
and a low amount of expected storage, uplod will prioritize hosts that post more
collateral, as well as giving preference to hosts better overall traits such as
uptime and age.

Even when the user has a large allowance and a low amount of expected storage,
uplod will try to optimize for saving money; uplod tries to meet the users storage
and bandwidth needs while spending significantly less than the overall
allowance.

**expectedupload** | bytes  
Expected upload tells uplod how many bytes per block the user expects to upload
during the configured period. If this value is high, uplod will more strongly
prefer hosts that have a low upload bandwidth price. If this value is low, uplod
will focus on metrics other than upload bandwidth pricing, because even if the
host charges a lot for upload bandwidth, it will not impact the total cost to
the user very much.

The user should not consider upload bandwidth used during repairs, uplod will
consider repair bandwidth separately.

**expecteddownload** | bytes  
Expected download tells uplod how many bytes per block the user expects to
download during the configured period. If this value is high, uplod will more
strongly prefer hosts that have a low download bandwidth price. If this value is
low, uplod will focus on metrics other than download bandwidth pricing, because
even if the host charges a lot for downloads, it will not impact the total cost
to the user very much.

The user should not consider download bandwidth used during repairs, uplod will
consider repair bandwidth separately.

**expectedredundancy** | bytes  
Expected redundancy is used in conjunction with expected storage to determine
the total amount of raw storage that will be stored on hosts. If the expected
storage is 1 TB and the expected redundancy is 3, then the renter will calculate
that the total amount of storage in the user's contracts will be 3 TiB.

This value does not need to be changed from the default unless the user is
manually choosing redundancy settings for their file. If different files are
being given different redundancy settings, then the average of all the
redundancies should be used as the value for expected redundancy, weighted by
how large the files are.

**maxuploadspeed** | bytes per second  
MaxUploadSpeed by default is unlimited but can be set by the user to manage
bandwidth.

**maxdownloadspeed** | bytes per second  
MaxDownloadSpeed by default is unlimited but can be set by the user to manage
bandwidth.

**streamcachesize** | int  
The StreamCacheSize is the number of data chunks that will be cached during
streaming.

**financialmetrics**    
Metrics about how much the Renter has spent on storage, uploads, and downloads.


**contractfees** | hastings  
Amount of money spent on contract fees, transaction fees and uplofund fees.

**contractspending** | hastings, (deprecated, now totalallocated)  
How much money, in hastings, the Renter has spent on file contracts, including
fees.

**downloadspending** | hastings  
Amount of money spent on downloads.

**storagespending** | hastings  
Amount of money spend on storage.

**totalallocated** | hastings  
Total amount of money that the renter has put into contracts. Includes spent
money and also money that will be returned to the renter.

**uploadspending** | hastings  
Amount of money spent on uploads.

**unspent** | hastings  
Amount of money in the allowance that has not been spent.

**currentperiod** | blockheight  
Height at which the current allowance period began.

**nextperiod** | blockheight  
Height at which the next allowance period began.

**uploadsstatus**  
Information about the renter's uploads.

**paused** | boolean  
Indicates whether or not the uploads and repairs are paused.

**pauseendtime** | unix timestamp  
The time at which the pause will end.  