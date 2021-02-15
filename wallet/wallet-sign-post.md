## /wallet/sign [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "<requestbody>" "localhost:8480/wallet/sign"
```

Signs a transaction. The wallet will attempt to sign each input specified. The
transaction's TransactionSignatures should be complete except for the Signature
field. If `tosign` is provided, the wallet will attempt to fill in signatures
for each TransactionSignature specified. If `tosign` is not provided, the wallet
will add signatures for every TransactionSignature that it has keys for.

### Request Body
> Request Body Example

```go
{
  // Unsigned transaction
  "transaction": {
    "uplocoininputs": [
      {
        "parentid": "af1a88781c362573943cda006690576b150537c1ae142a364dbfc7f04ab99584",
        "unlockconditions": {
          "timelock": 0,
          "publickeys": [ "ed25519:8b845bf4871bcdf4ff80478939e508f43a2d4b2f68e94e8b2e3d1ea9b5f33ef1" ],
          "signaturesrequired": 1
        }
      }
    ],
    "uplocoinoutputs": [
      {
        "value": "5000000000000000000000000",
        "unlockhash": "17d25299caeccaa7d1598751f239dd47570d148bb08658e596112d917dfa6bc8400b44f239bb"
      },
      {
        "value": "299990000000000000000000000000",
        "unlockhash": "b4bf662170622944a7c838c7e75665a9a4cf76c4cebd97d0e5dcecaefad1c8df312f90070966"
      }
    ],
    "minerfees": [ "1000000000000000000000000" ],
    "transactionsignatures": [
      {
        "parentid": "af1a88781c362573943cda006690576b150537c1ae142a364dbfc7f04ab99584",
        "publickeyindex": 0,
        "coveredfields": {"wholetransaction": true}
      }
    ]
  },

  // Optional IDs to sign; each should correspond to a parentid in the transactionsignatures.
  "tosign": [
    "af1a88781c362573943cda006690576b150537c1ae142a364dbfc7f04ab99584"
  ]
}
```

### JSON Response
> JSON Response Example

```go
{
  // signed transaction
  "transaction": {
    "uplocoininputs": [
      {
        "parentid": "af1a88781c362573943cda006690576b150537c1ae142a364dbfc7f04ab99584",
        "unlockconditions": {
          "timelock": 0,
          "publickeys": [ "ed25519:8b845bf4871bcdf4ff80478939e508f43a2d4b2f68e94e8b2e3d1ea9b5f33ef1" ],
          "signaturesrequired": 1
        }
      }
    ],
    "uplocoinoutputs": [
      {
        "value": "5000000000000000000000000",
        "unlockhash": "17d25299caeccaa7d1598751f239dd47570d148bb08658e596112d917dfa6bc8400b44f239bb"
      },
      {
        "value": "299990000000000000000000000000",
        "unlockhash": "b4bf662170622944a7c838c7e75665a9a4cf76c4cebd97d0e5dcecaefad1c8df312f90070966"
      }
    ],
    "minerfees": [ "1000000000000000000000000" ],
    "transactionsignatures": [
      {
        "parentid": "af1a88781c362573943cda006690576b150537c1ae142a364dbfc7f04ab99584",
        "publickeyindex": 0,
        "coveredfields": {"wholetransaction": true},
        "signature": "CVkGjy4The6h+UU+O8rlZd/O3Gb1xRJdyQ2vzBFEb/5KveDKDrrieCiFoNtUaknXEQbdxlrDqMujc+x3aZbKCQ=="
      }
    ]
  }
}
```