## /wallet [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/wallet"
```

Returns basic information about the wallet, such as whether the wallet is locked
or unlocked.

### JSON Response
> JSON Response Example

```go
{
  "encrypted":  true,   // boolean
  "unlocked":   true,   // boolean
  "rescanning": false,  // boolean

  "confirmeduplocoinbalance":     "123456", // hastings, big int
  "unconfirmedoutgoinguplocoins": "0",      // hastings, big int
  "unconfirmedincominguplocoins": "789",    // hastings, big int

  "uplofundbalance":      "1",    // uplofunds, big int
  "uplocoinclaimbalance": "9001", // hastings, big int

  "dustthreshold": "1234", // hastings / byte, big int
}
```
**encrypted** | boolean  
Indicates whether the wallet has been encrypted or not. If the wallet has not
been encrypted, then no data has been generated at all, and the first time the
wallet is unlocked, the password given will be used as the password for
encrypting all of the data. 'encrypted' will only be set to false if the wallet
has never been unlocked before (the unlocked wallet is still encryped - but the
encryption key is in memory).

**unlocked** | boolean  
Indicates whether the wallet is currently locked or unlocked. Some calls become
unavailable when the wallet is locked.

**rescanning** | boolean  
Indicates whether the wallet is currently rescanning the blockchain. This will
be true for the duration of calls to /unlock, /seeds, /init/seed, and
/sweep/seed.

**confirmeduplocoinbalance** | hastings, big int  
Number of uplocoins, in hastings, available to the wallet as of the most recent
block in the blockchain.

**unconfirmedoutgoinguplocoins** | hastings, big int  
Number of uplocoins, in hastings, that are leaving the wallet according to the
set of unconfirmed transactions. Often this number appears inflated, because
outputs are frequently larger than the number of coins being sent, and there is
a refund. These coins are counted as outgoing, and the refund is counted as
incoming. The difference in balance can be calculated using
'unconfirmedincominguplocoins' - 'unconfirmedoutgoinguplocoins'

**unconfirmedincominguplocoins** | hastings, big int  
Number of uplocoins, in hastings, are entering the wallet according to the set of
unconfirmed transactions. This number is often inflated by outgoing uplocoins,
because outputs are frequently larger than the amount being sent. The refund
will be included in the unconfirmed incoming uplocoins balance.

**uplofundbalance** | big int  
Number of uplofunds available to the wallet as of the most recent block in the
blockchain.

**uplocoinclaimbalance** | hastings, big int  
Number of uplocoins, in hastings, that can be claimed from the uplofunds as of the
most recent block. Because the claim balance increases every time a file
contract is created, it is possible that the balance will increase before any
claim transaction is confirmed.

**dustthreshold** | hastings / byte, big int  
Number of uplocoins, in hastings per byte, below which a transaction output
cannot be used because the wallet considers it a dust output.  