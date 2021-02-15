## /daemon/constants [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/daemon/constants"
```

Returns the some of the constants that the Uplo daemon uses.

### JSON Response
> JSON Response Example

```go
{
  "blockfrequency":600,           // blockheight
  "blocksizelimit":2000000,       // uint64
  "extremefuturethreshold":18000, // timestamp
  "futurethreshold":10800,        // timestamp
  "genesistimestamp":1433600000,  // timestamp
  "maturitydelay":144,            // blockheight
  "mediantimestampwindow":11,     // uint64
  "uplofundcount":"10000",         // uint64
  "uplofundportion":"39/1000",     // big.Rat
  "targetwindow":1000,            // blockheight
  
  "initialcoinbase":300000, // uint64
  "minimumcoinbase":30000,  // uint64
  
  "roottarget": // target
  [0,0,0,0,32,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],
  "rootdepth":  // target
  [255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255],
  
  "defaultallowance":  // allowance
    {
      "funds":"250000000000000000000000000000",  // currency
      "hosts":50,                       // uint64
      "period":12096,                   // blockheight
      "renewwindow":4032,               // blockheight
      "expectedstorage":1000000000000,  // uint64
      "expectedupload":2,               // uint64
      "expecteddownload":1,             // uint64
      "expectedredundancy":3            // uint64
    },
  
  "maxtargetadjustmentup":"5/2",    // big.Rat
  "maxtargetadjustmentdown":"2/5",  // big.Rat
  
  "uplocoinprecision":"1000000000000000000000000"  // currency
}
```
**blockfrequency** | blockheight  
BlockFrequency is the desired number of seconds that should elapse, on average,
between successive Blocks.

**blocksizelimit** | uint64  
BlockSizeLimit is the maximum size of a binary-encoded Block that is permitted
by the consensus rules.

**extremefuturethreshold** | timestamp  
ExtremeFutureThreshold is a temporal limit beyond which Blocks are discarded by
the consensus rules. When incoming Blocks are processed, their Timestamp is
allowed to exceed the processor's current time by a small amount. But if the
Timestamp is further into the future than ExtremeFutureThreshold, the Block is
immediately discarded.

**futurethreshold** | timestamp  
FutureThreshold is a temporal limit beyond which Blocks are discarded by the
consensus rules. When incoming Blocks are processed, their Timestamp is allowed
to exceed the processor's current time by no more than FutureThreshold. If the
excess duration is larger than FutureThreshold, but smaller than
ExtremeFutureThreshold, the Block may be held in memory until the Block's
Timestamp exceeds the current time by less than FutureThreshold.

**genesistimestamp** | timestamp  
GenesisBlock is the first block of the block chain

**maturitydelay** | blockheight  
MaturityDelay specifies the number of blocks that a maturity-required output is
required to be on hold before it can be spent on the blockchain. Outputs are
maturity-required if they are highly likely to be altered or invalidated in the
event of a small reorg. One example is the block reward, as a small reorg may
invalidate the block reward. Another example is a uplofund payout, as a tiny
reorg may change the value of the payout, and thus invalidate any transactions
spending the payout. File contract payouts also are subject to a maturity delay.

**mediantimestampwindow** | uint64  
MedianTimestampWindow tells us how many blocks to look back when calculating the
median timestamp over the previous n blocks. The timestamp of a block is not
allowed to be less than or equal to the median timestamp of the previous n
blocks, where for Uplo this number is typically 11.

**uplofundcount** | currency  
UplofundCount is the total number of Uplofunds in existence.

**uplofundportion** | big.Rat  
UplofundPortion is the percentage of uplocoins that is taxed from FileContracts.

**targetwindow** | blockheight  
TargetWindow is the number of blocks to look backwards when determining how much
time has passed vs. how many blocks have been created. It's only used in the
old, broken difficulty adjustment algorithm.

**initialcoinbase** | uint64  
InitialCoinbase is the coinbase reward of the Genesis block.

**minimumcoinbase** | uint64  
MinimumCoinbase is the minimum coinbase reward for a block. The coinbase
decreases in each block after the Genesis block, but it will not decrease past
MinimumCoinbase.

**roottarget** | target  
RootTarget is the target for the genesis block - basically how much work needs
to be done in order to mine the first block. The difficulty adjustment algorithm
takes over from there.

**rootdepth** | target  
RootDepth is the cumulative target of all blocks. The root depth is essentially
the maximum possible target, there have been no blocks yet, so there is no
cumulated difficulty yet.

**defaultallowance** | allowance  
DefaultAllowance is the set of default allowance settings that will be used when
allowances are not set or not fully set. See [/renter GET](#renter-get) for an
explanation of the fields.

**maxtargetadjustmentup** | big.Rat  
MaxTargetAdjustmentUp restrict how much the block difficulty is allowed to
change in a single step, which is important to limit the effect of difficulty
raising and lowering attacks.

**maxtargetadjustmentdown** | big.Rat  
MaxTargetAdjustmentDown restrict how much the block difficulty is allowed to
change in a single step, which is important to limit the effect of difficulty
raising and lowering attacks.

**uplocoinprecision** | currency  
UplocoinPrecision is the number of base units in a uplocoin. The Uplo network has a
very large number of base units. We call 10^24 of these a uplocoin.# Authentication
API authentication is enabled by default, using a password stored in a flat
file. The location of this file is:

- Linux:   `$HOME/.uplo/apipassword`
- MacOS:   `$HOME/Library/Application Support/Uplo/apipassword`
- Windows: `%LOCALAPPDATA%\Uplo\apipassword`


Note that the file contains a trailing newline, which must be trimmed before
use.

> Example POST curl call with Authentication

```go
curl -A "Uplo-Agent" --user "":<apipassword> --data "amount=123&destination=abcd" "localhost:8480/wallet/uplocoins"
```

Authentication is HTTP Basic Authentication as described in [RFC
2617](https://tools.ietf.org/html/rfc2617), however, the username is the empty
string. The flag does not enforce authentication on all API endpoints. Only
endpoints that expose sensitive information or modify state require
authentication.

For example, if the API password is "foobar" the request header should include

`Authorization: Basic OmZvb2Jhcg==`

And for a curl call the following would be included

`--user "":<apipassword>`

Authentication can be disabled by passing the `--authenticate-api=false` flag to
uplod. You can change the password by modifying the password file, setting the
`UPLO_API_PASSWORD` environment variable, or passing the `--temp-password` flag
to uplod.