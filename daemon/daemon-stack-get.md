## /daemon/stack [GET]
**UNSTABLE**
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/daemon/stack"
```
Returns the daemon's current stack trace. The maximum buffer size that will be
returned is 64MB. If the stack trace is larger than 64MB the first 64MB are
returned.

### JSON Response
> JSON Response Example

```go
{
  "stack": [1,2,21,1,13,32,14,141,13,2,41,120], // []byte
}
```

**stack** | []byte  
Current stack trace. 