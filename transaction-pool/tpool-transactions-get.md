## /tpool/transactions [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/tpool/transactions"
```

returns the transactions of the transaction pool.

### JSON Response
> JSON Response Example

```go
{
  "transactions": [     
    {
      "uplocoininputs":  [ // []UplocoinInput
        {
          "parentid": "b44db5d70f50b5c81b81d049fbdf9af27b4468f877d26c23a04c1093a7c4b541",
          "unlockconditions": {
            "publickeys": [
               {
                "algorithm": "ed25519",
                "key": "EKjiRsUyMOLER+8u3uXxemOEKMxRc2TxCh0QkcSCVHY="
               }
              ],
            "signaturesrequired": 1,
            "timelock": 0
          }
        },
      ]      
      "uplocoinoutputs": []        // []UplocoinOutput        
      "filecontracts":  []        // []FileContract
      "filecontractrevisions": [] // []FileContractRevision 
      "storageproofs":  []        // []StorageProof         
      "uplofundinputs":  []        // []UplofundInput
      "uplofundoutputs": []        // []UplofundOutput      
      "minerfees": [              // []Currency   
        "61440000000000000000000"
      ],          
      "arbitrarydata": [          // [][]byte
        "RkNJZGVudGlmaWVyAAAAACYzhrmGh2OL2Y9eBn5UYIFxCi4HKFvtR43pEgaBpkDqEa3LrQlWGyk+a0tBXi4nkIIaISIfTJMZs3sBgi0PFl4NyGOgqYppVQGaYnPuaRZKONJWE2jYZUu/iY3xLvpYIciu5JVlRIStwfGepaPWW4jLe4tf3AabKINgFk6p52m6"
      ],
      "transactionsignatures": [ // []TransactionSignature
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
                        "parentid": "b44db5d70f50b5c81b81d049fbdf9af27b4468f877d26c23a04c1093a7c4b541",
                        "publickeyindex": 0,
                        "signature": "QAVQSrcTv2xBHjWiTuuxVgWtUYECEZNbud41u7wgFIGcsKuBnbtT2yaH/GMw00/aMCpZ70qqBpQwQ/akAn/pAA==",
                        "timelock": 0
                    },
    }
  ]
}
```
See [/wallet/transaction/:id](#wallettransactionid-get) for description of
transaction fields.