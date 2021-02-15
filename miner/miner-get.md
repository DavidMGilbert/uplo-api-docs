# Miner

The miner provides endpoints for getting headers for work and submitting solved
headers to the network. The miner also provides endpoints for controlling a
basic CPU mining implementation.

## /miner [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/miner"
```
returns the status of the miner.

### JSON Response
> JSON Response Example

```go
{
  "blocksmined":      9001,   // int
  "cpuhashrate":      1337,   // hashes / second
  "cpumining":        false,  // boolean
  "staleblocksmined": 0,      // int
}
```
**blocksmined** | int  
Number of mined blocks. This value is remembered after restarting.

**cpuhashrate** | hashes / second  
How fast the cpu is hashing, in hashes per second.

**cpumining** | boolean  
true if the cpu miner is active.

**staleblocksmined** | int  
Number of mined blocks that are stale, indicating that they are not included in
the current longest chain, likely because some other block at the same height
had its chain extended first.  