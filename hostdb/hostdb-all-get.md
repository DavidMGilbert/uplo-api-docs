## /hostdb/all [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/hostdb/all"
```

Lists all of the hosts known to the renter. Hosts are not guaranteed to be in
any particular order, and the order may change in subsequent calls.

### JSON Response
Response is the same as [`/hostdb/active`](#hosts)