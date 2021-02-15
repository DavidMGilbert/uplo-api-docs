## /wallet/seed [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "seed=<seed>" "localhost:8480/wallet/seed"
```

Gives the wallet a seed to track when looking for incoming transactions. The
wallet will be able to spend outputs related to addresses created by the seed.
The seed is added as an auxiliary seed, and does not replace the primary seed.
Only the primary seed will be used for generating new addresses.

### Query String Parameters
### REQUIRED
[Required Wallet Parameters](#required-wallet-parameters)

### OPTIONAL | string
[Optional Wallet Parameters](#optional-wallet-parameters)

### Response

standard success or error response. See [standard
responses](#standard-responses).