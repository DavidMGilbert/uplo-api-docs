## /host/contracts [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/host/contracts"
```


Get contract information from the host database. This call will return all
storage obligations on the host. Its up to the caller to filter the contracts
based on their needs.

### JSON Response
> JSON Response Example

```go
{
  "contracts": [
    {
      "contractcost":             "1234",             // hastings
      "datasize":                 500000,             // bytes
      "lockedcollateral":         "1234",             // hastings
      "obligationid": "fff48010dcbbd6ba7ffd41bc4b25a3634ee58bbf688d2f06b7d5a0c837304e13", // hash
      "potentialaccountfunding":  "1234",             // hastings
      "potentialdownloadrevenue": "1234",             // hastings
      "potentialstoragerevenue":  "1234",             // hastings
      "potentialuploadrevenue":   "1234",             // hastings
      "riskedcollateral":         "1234",             // hastings
      "revisionnumber":           0,                  // int
      "sectorrootscount":         2,                  // int
      "transactionfeesadded":     "1234",             // hastings
      "expirationheight":         123456,             // blocks
      "negotiationheight":        123456,             // blocks
      "proofdeadline":            123456,             // blocks
      "obligationstatus":         "obligationFailed", // string
      "originconfirmed":          true,               // boolean
      "proofconfirmed":           true,               // boolean
      "proofconstructed":         true,               // boolean
      "revisionconfirmed":        false,              // boolean
      "revisionconstructed":      false,              // boolean
      "validproofoutputs":        [],                 // []UplocoinOutput
      "missedproofoutputs":       [],                 // []UplocoinOutput
    }
  ]
}
```
**contractcost** | hastings  
Amount in hastings to cover the transaction fees for this storage obligation.

**datasize** | bytes  
Size of the data that is protected by the contract.

**lockedcollateral** | hastings  
Amount that is locked as collateral for this storage obligation.

**obligationid** | hash  
Id of the storageobligation, which is defined by the file contract id of the
file contract that governs the storage obligation.

**potentialaccountfunding** | hastings  
Amount in hastings that went to funding ephemeral accounts with.

**potentialdownloadrevenue** | hastings  
Potential revenue for downloaded data that the host will receive upon successful
completion of the obligation.

**potentialstoragerevenue** | hastings  
Potential revenue for storage of data that the host will receive upon successful
completion of the obligation.

**potentialuploadrevenue** | hastings  
Potential revenue for uploaded data that the host will receive upon successful
completion of the obligation.

**riskedcollateral** | hastings  
Amount that the host might lose if the submission of the storage proof is not
successful.

**revisionnumber** | int  
The last revision of the contract

**sectorrootscount** | int  
Number of sector roots.

**transactionfeesadded** | hastings  
Amount for transaction fees that the host added to the storage obligation.

**expirationheight** | blockheight  
Expiration height is the height at which the storage obligation expires.

**negotiationheight** | blockheight  
Negotiation height is the height at which the storage obligation was negotiated.

**proofdeadline** | blockheight  
The proof deadline is the height by which the storage proof must be submitted.

**obligationstatus** | string  
Status of the storage obligation. There are 4 different statuses:
- `obligationFailed`:  the storage obligation failed, potential revenues and
  risked collateral are lost
- `obligationRejected`:  the storage obligation was never started, no revenues
  gained or lost
- `obligationSucceeded`: the storage obligation was completed, revenues were
  gained
- `obligationUnresolved`:  the storage obligation has an uninitialized value.
  When the **proofdeadline** is in the past this might be a stale obligation.

**originconfirmed** | hash  
Origin confirmed indicates whether the file contract was seen on the blockchain
for this storage obligation.

**proofconfirmed** | boolean  
Proof confirmed indicates whether there was a storage proof seen on the
blockchain for this storage obligation.

**proofconstructed** | boolean  
The host has constructed a storage proof

**revisionconfirmed** | boolean  
Revision confirmed indicates whether there was a file contract revision seen on
the blockchain for this storage obligation.

**revisionconstructed** | boolean  
Revision constructed indicates whether there was a file contract revision
constructed for this storage obligation.

**validproofoutputs** | []UplocoinOutput   
The payouts that the host and renter will receive if a valid proof is confirmed on the blockchain

**missedproofoutputs** | []UplocoinOutput  
The payouts that the host and renter will receive if a proof is not confirmed on the blockchain