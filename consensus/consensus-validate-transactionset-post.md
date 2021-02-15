## /consensus/validate/transactionset [POST]
> curl example

```go
curl -A "Uplo-Agent" --data "[JSON-encoded-txnset]" "localhost:8480/validate/transactionset"
```

validates a set of transactions using the current utxo set.

### Request Body Bytes

Since transactions may be large, the transaction set is supplied in the POST
body, encoded in JSON format.

### Response

standard success or error response. See [standard
responses](#standard-responses).