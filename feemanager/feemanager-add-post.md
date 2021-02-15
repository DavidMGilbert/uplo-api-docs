## /feemanager/add [POST]
> curl example

```go
// Required Fields Only
curl -A "Uplo-Agent" -u "":<apipassword> --data "amount=1000&address=1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef0123456789ab&appuid=supercoolapp" "localhost:8480/feemanager/add"

// All Fields
curl -A "Uplo-Agent" -u "":<apipassword> --data "amount=1000&address=1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef0123456789ab&appuid=supercoolapp&recurring=true" "localhost:8480/feemanager/add"
```
sets a fee and associates it with the provided application UID.

### Query String Parameters
### REQUIRED
**amount** | hastings  
The amount is how much the fee will charge the user.

**address** | address  
The address is the application developer's wallet address that the fee should be
paid out to.

**appuid** | string  
The unique application identifier for the application that set the fee.

### OPTIONAL
**recurring** | bool  
Indicates whether or not this fee will be a recurring fee.  
**NOTE:** This is only informational, the application charging the fee is
responsible for submitting the fee on the recurring interval.

### JSON Response
> JSON Response Example

```go
{
  "feeuid":"9ce7ff6c2b65a760b7362f5a041d3e84e65e22dd"  // string
}
```

**feeuid** | string  
This is the unique identifier for the fee that was just added