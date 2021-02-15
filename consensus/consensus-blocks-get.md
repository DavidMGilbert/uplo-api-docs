## /consensus/blocks [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/consensus/blocks?height=20032"
```
```go
curl -A "Uplo-Agent" "localhost:8480/consensus/blocks?id=00000000000033b9eb57fa63a51adeea857e70f6415ebbfe5df2a01f0d0477f4"
```

Returns the block for a given id or height.

### Query String Parameters
### REQUIRED
One of the following parameters must be specified.

**id** | blockID  
BlockID of the requested block.

**height** | blockheight  
BlockHeight of the requested block.

### JSON Response
> JSON Response Example

```go
{
    "height": 20032, // block height
    "id": "00000000000033b9eb57fa63a51adeea857e70f6415ebbfe5df2a01f0d0477f4", // hash
    "minerpayouts": [ // []UplocoinOutput
        {
            "unlockhash": "c199cd180e19ef7597bcf4beecdd4f211e121d085e24432959c42bdf9030e32b9583e1c2727c",
            "value": "279978000000000000000000000000"
        }
    ],
    "nonce": [4,12,219,7,0,0,0,0], // [8]byte
    "parentid": "0000000000009615e8db750eb1226aa5e629bfa7badbfe0b79607ec8b918a44c", // hash
    "difficulty": "440908097469850", // arbitrary-precision integer
    "timestamp": 1444516982, // timestamp
    "transactions": [ // []ConsensusBlocksGetTxn
        {
            "arbitrarydata": [],          // [][]byte
            "filecontractrevisions": [],  // []FileContractRevision
            "filecontracts": [],          // []ConsensusBlocksGetFileContract
            "minerfees": [],              // []Currency
            "uplocoininputs": [            // []UplocoinInput
                {
                    "parentid": "24cbeb9df7eb2d81d0025168fc94bd179909d834f49576e65b51feceaf957a64",
                    "unlockconditions": {
                        "publickeys": [
                            {
                                "algorithm": "ed25519",
                                "key": "QET8w7WRbGfcnnpKd1nuQfE3DuNUUq9plyoxwQYDK4U="
                            }
                        ],
                        "signaturesrequired": 1,
                        "timelock": 0
                    }
                }
            ],
            "uplocoinoutputs": [ // []UplocoinOutput
                {
                    "unlockhash": "d54f500f6c1774d518538dbe87114fe6f7e6c76b5bc8373a890b12ce4b8909a336106a4cd6db",
                    "value": "1010000000000000000000000000"
                },
                {
                    "unlockhash": "48a56b19bd0be4f24190640acbd0bed9669ea9c18823da2645ec1ad9652f10b06c5d4210f971",
                    "value": "5780000000000000000000000000"
                }
            ],
            "uplofundinputs": [],          // []UplofundInput
            "uplofundoutputs": [],         // []UplofundOutput
            "storageproofs": [],          // []StorageProof
            "transactionsignatures": [    // []TransactionSignature
                {
                    "coveredfields": {
                        "arbitrarydata": [],
                        "filecontractrevisions": [],
                        "filecontracts": [],
                        "minerfees": [],
                        "uplocoininputs": [],
                        "uplocoinoutputs": [],
                        "uplofundinputs": [],
                        "uplofundoutputs": [],
                        "storageproofs": [],
                        "transactionsignatures": [],
                        "wholetransaction": true
                    },
                    "parentid": "24cbeb9df7eb2d81d0025168fc94bd179909d834f49576e65b51feceaf957a64",
                    "publickeyindex": 0,
                    "signature": "pByLGMlvezIZWVZmHQs/ynGETETNbxcOY/kr6uivYgqZqCcKTJ0JkWhcFaKJU+3DEA7JAloLRNZe3PTklD3tCQ==",
                    "timelock": 0
                }
            ]
        },
        {
          // ...
        }
    ]
}
```
**height** | block height  
Height of the block

**id** | hash  
ID of the block

**minerpayouts** |  UplocoinOutput  
Uplocoin output that holds the amount of uplocoins spent on the miner payout

**nonce** | bytes  
Block nonce

**parentid** | hash  
ID of the previous block

**difficulty** | arbitrary-precision integer  
Historic difficulty at height of the block

**timestamp** | timestamp  
Block timestamp

**transactions** | ConsensusBlocksGetTxn  
Transactions contained within the block