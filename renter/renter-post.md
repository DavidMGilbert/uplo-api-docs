## /renter [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "period=12096&renewwindow=4032&funds=1000&hosts=50" "localhost:8480/renter"
```

Modify settings that control the renter's behavior.

### Query String Parameters
### REQUIRED
When setting the allowance the Funds and Period are required. Since these are
the two required fields, the allowance can be canceled by submitting the zero
values for these fields.

### OPTIONAL
Any of the renter settings can be set, see fields [here](#settings)

**checkforipviolation** | boolean  
Enables or disables the check for hosts using the same ip subnets within the
hostdb. It's turned on by default and causes Uplo to not form contracts with
hosts from the same subnet and if such contracts already exist, it will
deactivate the contract which has occupied that subnet for the shorter time.

### Response

standard success or error response. See standard responses.