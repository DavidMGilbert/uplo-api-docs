## /tpool/fee [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/tpool/fee"
```

returns the minimum and maximum estimated fees expected by the transaction pool.

### JSON Response
> JSON Response Example

```go
{
  "minimum": "1234", // hastings / byte
  "maximum": "5678"  // hastings / byte
}
```
**minimum** | hastings / byte  
the minimum estimated fee

**maximum** | hastings / byte  
the maximum estimated fee