# Introduction

## Welcome to the Uplo Storage Platform API!
Uplo uses semantic versioning and aims to remain backwards compatible to version v1.0.1.

API calls return either JSON or no content. Success is indicated by 2xx HTTP
status codes, while errors are indicated by 4xx and 5xx HTTP status codes. If an
endpoint does not specify its expected status code refer to [standard
responses](#Standard-Responses).

There may be functional API calls which are not documented. These are not
guaranteed to be supported beyond the current release, and should not be used in
production.

**Notes:**

- Requests must set their User-Agent string to contain the substring
  "Uplo-Agent".
- By default, uplod listens on "localhost:8480". This can be changed using the
  `--api-addr` flag when running uplod.
- **Do not bind or expose the API to a non-loopback address unless you are aware
  of the possible dangers.**

> Example GET curl call

```go
curl -A "Uplo-Agent" -u "":<apipassword> "localhost:8480/wallet/transactions?startheight=1&endheight=250"
```

> Example POST curl call with data

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "amount=123&destination=abcd" "localhost:8480/wallet/uplocoins"
```

> Example POST curl call without data or authentication

```go
curl -A "Uplo-Agent" -X POST "localhost:8480/gateway/connect/123.456.789.0:8481"
```
