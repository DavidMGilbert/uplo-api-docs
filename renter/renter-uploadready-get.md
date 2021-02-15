## /renter/uploadready [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/renter/uploadready?datapieces=10&paritypieces=20"
```

Returns the whether or not the renter is ready for upload.

### Path Parameters
### OPTIONAL
datapieces and paritypieces are both optional, however if one is supplied then
the other needs to be supplied. If neither are supplied then the default values
for the erasure coding will be used

**datapieces** | int  
The number of data pieces to use when erasure coding the file.

**paritypieces** | int  
The number of parity pieces to use when erasure coding the file.

### JSON Response
> JSON Response Example

```go
{
"ready":false,            // bool
"contractsneeded":30,     // int
"numactivecontracts":20,  // int
"datapieces":10,          // int
"paritypieces":20         // int 
}
```
**ready** | boolean  
ready indicates if the renter is ready to fully upload a file based on the
erasure coding.

**contractsneeded** | int  
contractsneeded is how many contracts are needed to fully upload a file.

**numactivecontracts** | int  
numactivecontracts is the number of active contracts the renter has.

**datapieces** | int  
The number of data pieces to use when erasure coding the file.

**paritypieces** | int  
The number of parity pieces to use when erasure coding the file.