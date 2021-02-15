## /gateway/blocklist [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data '{"action":"append","addresses":["123.123.123.123","123.123.123.123","123.123.123.123"]}' "localhost:8480/gateway/blocklist"
```
```go
curl -A "Uplo-Agent" -u "":<apipassword> --data '{"action":"set","addresses":[]}' "localhost:8480/gateway/blocklist"
```

performs actions on the Gateway's blocklist. There are three `actions` that can
be performed. `append` and `remove` are used for appending or removing addresses
from the Gateway's blocklist. `set` is used to define all the addresses in the
blocklist. If a list of addresses is provided with `set`, that list of addresses
will become the Gateway's blocklist, replacing any blocklist that was currently
in place. To clear the Gateway's blocklist, submit an empty list with `set`.

### Path Parameters
### REQUIRED
**action** | string  
this is the action to be performed on the blocklist. Allowed inputs are
`append`, `remove`, and `set`.

**addresses** | string  
this is a comma separated list of addresses that are to be appended to or
removed from the blocklist. If the action is `append` or `remove` this field is
required.

### Response
standard success or error response. See [standard
responses](#standard-responses).

# Host

The host provides storage from local disks to the network. The host negotiates
file contracts with remote renters to earn money for storing other users' files.
The host's endpoints expose methods for viewing and modifying host settings,
announcing to the network, and managing how files are stored on disk.