## /miner/header [POST]
> curl example

```go
curl -A "Uplo-Agent" -data "<byte-encoded-header>" -u "":<apipassword> "localhost:8480/miner"
```

submits a header that has passed the POW.

### Byte Request
For efficiency headers are submitted as raw byte encodings of the header in the
body of the request, rather than as a query string parameter or path parameter.
The request body should contain only the 80 bytes of the encoded header. The
encoding is the same encoding used in `/miner/header [GET]` endpoint.

Blocks are mined by repeatedly changing the nonce of the header, hashing the
header's bytes, and comparing the resulting hash to the target. The block with
that nonce is valid if the hash is less than the target. If none of the 2^64
possible nonces result in a header with a hash less than the target, call
/miner/header [GET] again to get a new block header with a different merkle
root. The above process can then be repeated for the new block header.

The other fields can generally be ignored. The parent block ID field is the hash
of the parent block's header. Modifying this field will result in an orphan
block. The timestamp is the time at which the block was mined and is set by the
Uplo Daemon. Modifying this field can result in invalid block. The merkle root is
the merkle root of a merkle tree consisting of the timestamp, the miner outputs
(one leaf per payout), and the transactions (one leaf per transaction).
Modifying this field will result in an invalid block.

Field | Byte range within request | Byte range within header
-------------- | -------------- | --------------
target | [0-32)
header | [32-112)
parent block ID | [32-64) | [0-32)
nonce | [64-72) | [32-40)
timestamp | [72-80) | [40-48)
merkle root | [80-112) | [48-80)