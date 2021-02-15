## /wallet/watch [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "<requestbody>" "localhost:8480/wallet/watch"
```

Update the set of addresses for the wallet to watch.

### Request Body
> Request Body Example

```go
{
  "addresses": [    // []hash
    "1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef",
    "abcdef0123456789abcdef0123456789abcd1234567890ef0123456789abcdef"
  ],
  "remove": false,  // boolean
  "unused": true,   // boolean
```

**addresses** | hashes  
The addresses to add or remove from the current set.

**remove** | boolean  
If true, remove the addresses instead of adding them.

**unused** | boolean  
If true, the wallet will not rescan the blockchain. Only set this flag if the
addresses have never appeared in the blockchain.

### Response

standard success or error response. See standard responses.