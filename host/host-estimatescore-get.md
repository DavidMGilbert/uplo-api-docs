
## /host/estimatescore [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/host/estimatescore"
```

Returns the estimated HostDB score of the host using its current settings,
combined with the provided settings.

### Query String Parameters
### OPTIONAL
See [host internal settings](#internalsettings)
- acceptingcontracts
- maxdownloadbatchsize
- maxduration
- maxrevisebatchsize
- netaddress
- windowsize
- collateral
- collateralbudget
- maxcollateral
- mincontractprice
- mindownloadbandwidthprice
- minstorageprice
- minuploadbandwidthprice
- ephemeralaccountexpiry
- maxephemeralaccountbalance
- maxephemeralaccountrisk

### JSON Response
> JSON Response Example

```go
{
  "estimatedscore": "123456786786786786786786786742133",  // big int
  "conversionrate": 95  // float64
}
```
**estimatedscore** | big int  
estimatedscore is the estimated HostDB score of the host given the settings
passed to estimatescore.

**conversionrate** | float64  
conversionrate is the likelihood given the settings passed to estimatescore that
the host will be selected by renters forming contracts.