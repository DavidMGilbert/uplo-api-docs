## /hostdb/filtermode [POST]
> curl example

```go
curl -A "Uplo-Agent" --user "":<apipassword> --data '{"filtermode" : "whitelist","hosts" : ["ed25519:1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef","ed25519:1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef","ed25519:1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef"]}' "localhost:8480/hostdb/filtermode"
```  
```go
curl -A "Uplo-Agent" --user "":<apipassword> --data '{"filtermode" : "disable"}' "localhost:8480/hostdb/filtermode"
```
Lets you enable and disable a filter mode for the hostdb. Currently the two
modes supported are `blacklist` mode and `whitelist` mode. In `blacklist` mode,
any hosts you identify as being on the `blacklist` will not be used to form
contracts. In `whitelist` mode, only the hosts identified as being on the
`whitelist` will be used to form contracts. In both modes, hosts that you are
blacklisted will be filtered from your hostdb. To enable either mode, set
`filtermode` to the desired mode and submit a list of host pubkeys as the
corresponding `blacklist` or `whitelist`. To disable either list, the `host`
field can be left blank (e.g. empty slice) and the `filtermode` should be set to
`disable`.

**NOTE:** Enabling and disabling a filter mode can result in changes with your
current contracts with can result in an increase in contract fee spending. For
example, if `blacklist` mode is enabled, any hosts that you currently have
contracts with that are also on the provide list of `hosts` will have their
contracts replaced with non-blacklisted hosts. When `whitelist` mode is enabled,
contracts will be replaced until there are only contracts with whitelisted
hosts. Even disabling a filter mode can result in a change in contracts if there
are better scoring hosts in your hostdb that were previously being filtered out.


### Query String Parameters
### REQUIRED
**filtermode** | string  
Can be either whitelist, blacklist, or disable.

**hosts** | array of string  
Comma separated pubkeys.

### Response

standard success or error response. See [standard
responses](#standard-responses).