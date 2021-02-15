## /daemon/stop [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/daemon/stop"
```

Cleanly shuts down the daemon. This may take a few seconds.

### Response
standard success or error response. See [standard
responses](#standard-responses).