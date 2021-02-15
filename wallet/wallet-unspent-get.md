## /wallet/unspent [GET]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/wallet/unspent"
```

Returns a list of outputs that the wallet can spend.

### JSON Response
> JSON Response Example

```go
{
  "outputs": [
    {
      "id": "1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef",
      "fundtype": "uplocoin output",
      "confirmationheight": 50000,
      "unlockhash": "1234567890abcdef0123456789abcdef0123456789abcdef0123456789abcdef0123456789ab",
      "value": "1234", // big int
      "iswatchonly": false
    }
  ]
}
```
**outputs**  
Array of outputs that the wallet can spend.

**id**  
The id of the output.

**fundtype**  
Type of output, either 'uplocoin output' or 'uplofund output'.

**confirmationheight**  
Height of block in which the output appeared. To calculate the number of
confirmations, subtract this number from the current block height.

**unlockhash**  
Hash of the output's unlock conditions, commonly known as the "address".

**value** | big int  
Amount of funds in the output; hastings for uplocoin outputs, and uplofunds for
uplofund outputs.

**iswatchonly** | Boolean  
Whether the output comes from a watched address or from the wallet's seed.  