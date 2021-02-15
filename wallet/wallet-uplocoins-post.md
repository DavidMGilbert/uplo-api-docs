## /wallet/uplocoins [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "amount=1000&destination=c134a8372bd250688b36867e6522a37bdc391a344ede72c2a79206ca1c34c84399d9ebf17773" "localhost:8480/wallet/uplocoins"
```

Sends uplocoins to an address or set of addresses. The outputs are arbitrarily
selected from addresses in the wallet. If 'outputs' is supplied, 'amount',
'destination' and 'feeIncluded' must be empty.

### Query String Parameters
### REQUIRED
Amount and Destination or Outputs are required

**amount** | hastings  
Number of hastings being sent. A hasting is the smallest unit in Uplo. There are
10^24 hastings in a uplocoin.

**destination** | address  
Address that is receiving the coins.

**OR**

**outputs**  
JSON array of outputs. The structure of each output is: {"unlockhash":
"<destination>", "value": "<amount>"}

### OPTIONAL
**feeIncluded** | boolean  
Take the transaction fee out of the balance being submitted instead of the fee being additional.

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
  "transactionids": [
    "1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef",
    "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb"
  ]
}
```
**transactions** Array of transactions that were created when sending the coins.
The last transaction contains the output headed to the 'destination'.
Transaction IDs are 64 character long hex strings.

**transactionids**  
Array of IDs of the transactions that were created when sending the coins.