## /wallet/transaction/:*id* [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/wallet/transaction/22e8d5428abc184302697929f332fa0377ace60d405c39dd23c0327dc694fae7"
```

Gets the transaction associated with a specific transaction id.

### Path Parameters
### REQUIRED
**id** | hash  
ID of the transaction being requested.

### JSON Response
> JSON Response Example

```go
{
  "transaction": {
    "transaction": {
      // See types.Transaction in https://github.com/uplo-tech/uplo/blob/master/types/transactions.go
    },
    "transactionid":         "1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef",
    "confirmationheight":    50000,
    "confirmationtimestamp": 1257894000,
    "inputs": [
      {
        "parentid":       "1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef",
        "fundtype":       "uplocoin input",
        "walletaddress":  false,
        "relatedaddress": "1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef0123456789ab",
        "value":          "1234", // hastings or uplofunds, depending on fundtype, big int
      }
    ],
    "outputs": [
      {
        "id":             "1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef",
        "fundtype":       "uplocoin output",
        "maturityheight": 50000,
        "walletaddress":  false,
        "relatedaddress": "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "value":          "1234", // hastings or uplofunds, depending on fundtype, big int
      }
    ]
  }
}
```
**transaction**  
Raw transaction. The rest of the fields in the response are determined from this
raw transaction. It is left undocumented here as the processed transaction (the
rest of the fields in this object) are usually what is desired.

See types.Transaction in
https://github.com/uplo-tech/uplo/blob/master/types/transactions.go

**transactionid**  
ID of the transaction from which the wallet transaction was derived.

**confirmationheight**  
Block height at which the transaction was confirmed. If the transaction is
unconfirmed the height will be the max value of an unsigned 64-bit integer.

**confirmationtimestamp**  
Time, in unix time, at which a transaction was confirmed. If the transaction is
unconfirmed the timestamp will be the max value of an unsigned 64-bit integer.

**inputs**  
Array of processed inputs detailing the inputs to the transaction.

**parentid**  
The id of the output being spent.

**fundtype**  
Type of fund represented by the input. Possible values are 'uplocoin input' and
'uplofund input'.

**walletaddress** | boolean  
true if the address is owned by the wallet.

**relatedaddress**  
Address that is affected. For inputs (outgoing money), the related address is
usually not important because the wallet arbitrarily selects which addresses
will fund a transaction.

**value** | hastings or uplofunds, depending on fundtype, big int  
Amount of funds that have been moved in the input.

**outputs**  
Array of processed outputs detailing the outputs of the transaction. Outputs
related to file contracts are excluded.

**id**  
The id of the output that was created.

**fundtype**  
Type of fund is represented by the output. Possible values are 'uplocoin output',
'uplofund output', 'claim output', and 'miner payout'. Uplocoin outputs and claim
outputs both relate to uplocoins.

Uplofund outputs relate to uplofunds.

Miner payouts point to uplocoins that have been spent on a miner payout. Because
the destination of the miner payout is determined by the block and not the
transaction, the data 'maturityheight', 'walletaddress', and 'relatedaddress'
areleft blank.

**maturityheight**  
Block height the output becomes available to be spent. Uplocoin outputs and
uplofund outputs mature immediately - their maturity height will always be the
confirmation height of the transaction. Claim outputs cannot be spent until they
have had 144 confirmations, thus the maturity height of a claim output will
always be 144 larger than the confirmation height of the transaction.

**walletaddress** | boolean  
true if the address is owned by the wallet.

**relatedaddress**  
Address that is affected. For outputs (incoming money), the related address
field can be used to determine who has sent money to the wallet.

**value** | hastings or uplofunds, depending on fundtype, big int  
Amount of funds that have been moved in the output.  