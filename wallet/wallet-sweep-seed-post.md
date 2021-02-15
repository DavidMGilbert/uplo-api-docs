## /wallet/sweep/seed [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "seed=<seed>" "localhost:8480/wallet/sweep/seed"
```

Scans the blockchain for outputs belonging to a seed and send them to an address
owned by the wallet.

### Query String Parameters
### REQUIRED
**seed** | string  
Dictionary-encoded phrase that corresponds to the seed being added to the
wallet.

### OPTIONAL
**dictionary** | string  
Name of the dictionary that should be used when decoding the seed. 'english' is
the most common choice when picking a dictionary.

### JSON Response
> JSON  Response Example

```go
{
"coins": "123456", // hastings, big int
"funds": "1",      // uplofunds, big int
}
```
**coins** | hastings, big int  
Number of uplocoins, in hastings, transferred to the wallet as a result of the
sweep.

**funds** | uplofunds, big int  
Number of uplofunds transferred to the wallet as a result of the sweep.  