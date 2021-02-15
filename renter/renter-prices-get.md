## /renter/prices [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/renter/prices"
```

Lists the estimated prices of performing various storage and data operations. An
allowance can be submitted to provide a more personalized estimate. If no
allowance is submitted then the current set allowance will be used, if there is
no allowance set then sane defaults will be used. Submitting an allowance is
optional, but when submitting an allowance all the components of the allowance
are required. The allowance used to create the estimate is returned with the
estimate.

### Query String Parameters
### REQUIRED or OPTIONAL
Allowance settings, see the fields [here](#allowance)

### JSON Response
> JSON Response Example

```go
{
  "downloadterabyte":      "1234",  // hastings
  "formcontracts":         "1234",  // hastings
  "storageterabytemonth":  "1234",  // hastings
  "uploadterabyte":        "1234",  // hastings
  "funds":                 "1234",  // hastings
  "hosts":                     24,  // int
  "period":                  6048,  // blocks
  "renewwindow":             3024   // blocks
}
```
**downloadterabyte** | hastings  
The estimated cost of downloading one terabyte of data from the network.

**formcontracts** | hastings  
The estimated cost of forming a set of contracts on the network. This cost also
applies to the estimated cost of renewing the renter's set of contracts.

**storageterabytemonth** | hastings  
The estimated cost of storing one terabyte of data on the network for a month,
including accounting for redundancy.

**uploadterabyte** | hastings  
The estimated cost of uploading one terabyte of data to the network, including
accounting for redundancy.

The allowance settings used for the estimation are also returned, see the fields
[here](#allowance)