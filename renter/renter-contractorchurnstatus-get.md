## /renter/contractorchurnstatus [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/renter/contractorchurnstatus"
```

Returns the churn status for the renter's contractor.

### JSON Response
> JSON Response Example

```go
{
  "aggregatecurrentperiodchurn": 500000,   // uint64
  "maxperiodchurn":              50000000, // uint64
}
```

**aggregatecurrentperiodchurn** | uint64  
Aggregate size of files stored in file contracts that were churned (i.e. not
marked for renewal) in the current period.


**maxperiodchurn** | uint64  
Maximum allowed aggregate churn per period.