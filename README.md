---
description: >-
  Whether you're brand new to Uplo or just need a refresher on the
  basics, this article will get you up to speed.
---

# Introduction

## Welcome to the Uplo Storage Platform API!

{% hint style="info" %}
Uplo is still under development. Please be sure to visit Uplo on facebook for regular updates and get notified the moment Uplo is officially released!

[Click here to visit Uplo on Facebook!](https://www.facebook.com/Uplo-101419761988838)
{% endhint %}

Uplo uses semantic versioning and aims to remain backwards compatible to version v1.0.1.

API calls return either JSON or no content. Success is indicated by 2xx HTTP
status codes, while errors are indicated by 4xx and 5xx HTTP status codes. If an
endpoint does not specify its expected status code refer to standard responses.

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



Uplo is a decentralized cloud storage platform secured by blockchain technology. The Uplo storage network leverages underutilized hard drive capacity around the world to create a data storage marketplace that is more reliable and lower cost than traditional cloud storage providers. Uplo has its own blockchain, and a utility token that powers it – the UploCoin.

Your data is truly private and gets stored across the globe to eliminate any single point of failure and ensure the highest possible uptime. Since you hold the keys, you own your data. No outside company can access or control your files.

Data cannot be de-platformed. Files can not be hacked.

## Build your next app with us!

If you are a developer, you will find that the UploAPI offers un-parallelled convenience and capabilities to supercharge your projects and help you rapidly deploy feature-rich applications built in conjunction with the Uplo blockchain and decentralised storage platform.

Use the menu to the left to see specific information and calls that you can use with your Uplo installation.