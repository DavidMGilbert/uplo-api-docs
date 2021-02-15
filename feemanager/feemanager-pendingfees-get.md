## /feemanager/pendingfees [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/feemanager/pendingfees"
```

returns the pending fees that the feemanager is managing.

### JSON Response
> JSON Response Example

```go
{
  "pendingfees": [
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

**pendingfees** | []AppFee  
List of pending fees that the FeeManager is managing that will pay out this
period.

**address** | address  
The application developer's wallet address that the fee should be paid out to.

**amount** | hastings  
The number of hastings the fee will charge the user.

**appuid** | string  
The unique application identifier for the application that set the fee.

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

# Gateway

The gateway maintains a peer to peer connection to the network and provides a
method for calling RPCs on connected peers. The gateway's API endpoints expose
methods for viewing the connected peers, manually connecting to peers, and
manually disconnecting from peers. The gateway may connect or disconnect from
peers on its own.