# Consensus

The consensus set manages everything related to consensus and keeps the
blockchain in sync with the rest of the network. The consensus set's API
endpoint returns information about the state of the blockchain.

## /consensus [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/consensus"
```

Returns information about the consensus set, such as the current block height.
Also returns the set of constants in use in the consensus code.

### JSON Response
> JSON Response Example

```go
{
  "synced":       true, // boolean
  "height":       62248, // blockheight
  "currentblock": "00000000000008a84884ba827bdc868a17ba9c14011de33ff763bd95779a9cf1", // hash
  "target":       [0,0,0,0,0,0,11,48,125,79,116,89,136,74,42,27,5,14,10,31,23,53,226,238,202,219,5,204,38,32,59,165], // hash
  "difficulty":   "1234" // arbitrary-precision integer

  "foundationprimaryunlockhash":  "b4bf662170622944a7c838c7e75665a9a4cf76c4cebd97d0e5dcecaefad1c8df312f90070966",
  "foundationfailsafeunlockhash": "17d25299caeccaa7d1598751f239dd47570d148bb08658e596112d917dfa6bc8400b44f239bb",

  "blockfrequency":         600,        // seconds per block
  "blocksizelimit":         2000000,    // bytes
  "extremefuturethreshold": 10800,      // seconds
  "futurethreshold":        10800,      // seconds
  "genesistimestamp":       1257894000, // Unix time
  "maturitydelay":          144,        // blocks
  "mediantimestampwindow":  11,         // blocks
  "uplofundcount":           "10000",    // uplofund
  "uplofundportion":         "39/1000",  // fraction

  "initialcoinbase": 300000, // Uplocoins (see note in Daemon.md)
  "minimumcoinbase": 30000,  // Uplocoins (see note in Daemon.md)

  "roottarget": [0,0,0,0,32,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0], // hash
  "rootdepth":  [255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255],  // hash

  "uplocoinprecision": "1000000000000000000000000" // hastings per uplocoin
}
```
**synced** | boolean  
True if the consensus set is synced with the network, e.g. it has downloaded the
entire blockchain.

**height** | blockheight  
Number of blocks preceding the current block.

**currentblock** | hash  
Hash of the current block.

**target** | hash  
An immediate child block of this block must have a hash less than this target
for it to be valid.

**difficulty** | arbitrary-precision integer  
The difficulty of the current block target.

**blockfrequency** | blocks / second  
Target for how frequently new blocks should be mined.

**blocksizelimit** | bytes  
Maximum size, in bytes, of a block. Blocks larger than this will be rejected by
peers.

**extremefuturethreshold** | seconds  
Farthest a block's timestamp can be in the future before the block is rejected
outright.

**futurethreshold** | seconds  
How far in the future a block can be without being rejected. A block further
into the future will not be accepted immediately, but the daemon will attempt to
accept the block as soon as it is valid.

**genesistimestamp** | unix timestamp  
Timestamp of the genesis block.

**maturitydelay** | number of blocks  
Number of children a block must have before it is considered "mature."

**mediantimestampwindow** | number of blocks  
Duration of the window used to adjust the difficulty.

**uplofundcount** | uplofunds  
Total number of uplofunds.

**uplofundportion** | fraction  
Fraction of each file contract payout given to uplofund holders.

**initialcoinbase** | uplocoin  
Number of coins given to the miner of the first block. Note that elsewhere in
the API currency is typically returned in hastings and as a bignum. This is not
the case here.

**minimumcoinbase** | uplocoin  
Minimum number of coins paid out to the miner of a block (the coinbase decreases
with each block). Note that elsewhere in the API currency is typically returned
in hastings and as a bignum. This is not the case here.

**roottarget** | hash  
Initial target.

**rootdepth** | hash  
Initial depth.

**uplocoinprecision** | hastings per uplocoin  
Number of Hastings in one Uplocoin.