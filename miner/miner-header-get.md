## /miner/header [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/miner/header"
```

provides a block header that is ready to be grinded on for work.

### Byte Response
For efficiency the header for work is returned as a raw byte encoding of the
header, rather than encoded to JSON.

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

Field | Byte range within response | Byte range within header
-------------- | -------------- | --------------
target | [0-32)
header | [32-112)
parent block ID | [32-64) | [0-32)
nonce | [64-72) | [32-40)
timestamp | [72-80) | [40-48)
merkle root | [80-112) | [48-80)