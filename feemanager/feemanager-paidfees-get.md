## /feemanager/paidfees [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/feemanager/paidfees"
```

returns the paid fees that the feemanager managed.

### JSON Response
> JSON Response Example

```go
{
  "paidfees": [
    {
      "address":            "f063edc8412e3d17f0e130f38bc6f25d134fae46b760b829e09a762c400fbd641a0c1539a056", // hash
      "amount":             "1000",  // hastings
      "appuid":             "okapp", // string
      "feeuid":             "9ce7ff6c2b65a760b7362f5a041d3e84e65e22dd" // string
      "paymentcompleted":   true,    // bool
      "payoutheight":       12345,   // types.BlockHeight
      "recurring":          false,   // bool
      "timestamp":          "2018-09-23T08:00:00.000000000+04:00",     // Unix timestamp
      "transactioncreated": true,    // bool
    }
  ]
}

```

**paidfees** | []AppFee  
List of historical fees that have been paid out by the FeeManager.

**address** | address  
The application developer's wallet address that the fee should be paid out to.

**amount** | hastings  
The number of hastings the fee will charge the user.

**appuid** | string  
Indicates the uid of the application requesting the fee.

**feeuid** | string  
This is the unique identifier for the fee

**paymentcompleted** | bool  
Indicates whether or not the payment has been confirmed on-chain

**payoutheight** | bool  
Indicates the height at which the fee is supposed to be paid out. The fee may be
paid out (or have been paid out for completed fees) at a later height than this,
but not earlier.

**recurring** | bool  
Indicates whether or not this fee will be a recurring fee.

**timestamp** | Unix timestamp  
This is the moment that the fee was requested.

**transactioncreated** | bool  
Indicates whether the transaction to pay the fee has been created. If this is
set to true and paymentcompleted is set to false, it means that the transaction
has not yet been confirmed on-chain  