# Host DB

The hostdb maintains a database of all hosts known to the network. The database
identifies hosts by their public key and keeps track of metrics such as price.

## /hostdb [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/hostdb"
```

Shows some general information about the state of the hostdb.

### JSON Response
> JSON Response Example

```go
{
    "initialscancomplete": false  // boolean
}
```
**initialscancomplete** | boolean  
indicates if all known hosts have been scanned at least once.