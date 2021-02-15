## /miner/block [POST]
> curl example

```go
curl -A "Uplo-Agent" -data "<byte-encoded-block>" -u "":<apipassword> "localhost:8480/miner/block"
```

Submits a solved block and broadcasts it.

### Byte Request

For efficiency the block is submitted in a raw byte encoding using the Uplo
encoding.

### Response

standard success or error response. See [standard
responses](#standard-responses).