## /wallet/lock [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> -X POST "localhost:8480/wallet/lock"
```

Locks the wallet, wiping all secret keys. After being locked, the keys are
encrypted. Queries for the seed, to send uplofunds, and related queries become
unavailable. Queries concerning transaction history and balance are still
available.

### Response

standard success or error response. See standard responses.
