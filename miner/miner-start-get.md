## /miner/start [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/miner/start"
```

Starts a single threaded CPU miner. Does nothing if the CPU miner is already
running.

### Response

standard success or error response. See [standard
responses](#standard-responses).