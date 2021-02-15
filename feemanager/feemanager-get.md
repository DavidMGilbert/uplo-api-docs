# FeeManager

The feemanager allows applications built on top of Uplo to charge the Uplo user a
fee. The feemanager's API endpoints expose methods for viewing information about
the feemanager and for adding and canceling fees.

## /feemanager [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/feemanager"
```

returns information about the feemanager.

### JSON Response
> JSON Response Example

```go
{
  "payoutheight":249854 // blockheight
}
```

**payoutheight** | blockheight  
Height at which the FeeManager will payout the pending fees.