## /consensus/subscribe/:id [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/consensus/subscribe/0000000000000000000000000000000000000000000000000000000000000000"
```

Streams a series of consensus changes, starting from the provided change ID.

### Path Parameters
### REQUIRED
**id** | string
The consensus change ID to subscribe from. There are two sentinel values:
to subscribe from the genesis block use:
```
0000000000000000000000000000000000000000000000000000000000000000
```
To skip all existing blocks and subscribe only to subsequent changes, use:
```
0100000000000000000000000000000000000000000000000000000000000000
```
In addition, each consensus change contains its own ID.

### Response

A concatenation of Uplo-encoded (binary) modules.ConsensusChange objects.