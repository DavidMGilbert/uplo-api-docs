## /hostdb/filtermode [GET]
> curl example

```go
curl -A "Uplo-Agent" --user "":<apipassword> "localhost:8480/hostdb/filtermode"
```  
Returns the current filter mode of the hostDB and any filtered hosts.

### JSON Response
> JSON Response Example

```go
{
  "filtermode": "blacklist",  // string
  "hosts":
    [
      "ed25519:122218260fb74b20a8be3000ad56a931f7461ea990a6dc5676c31bdf65fc668f"  // string
    ]
}

```
**filtermode** | string  
Can be either whitelist, blacklist, or disable.

**hosts** | array of strings  
Comma separated pubkeys.  