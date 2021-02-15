## /gateway/blocklist [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/gateway/blocklist"
```

fetches the list of blocklisted addresses.

### JSON Response
> JSON Response Example

```go
{
  "blocklist":
    [
    "123.123.123.123",  // string
    "123.123.123.123",  // string
    "123.123.123.123",  // string
    ],
}
```
**blocklist** | string  
blocklist is a list of blocklisted address