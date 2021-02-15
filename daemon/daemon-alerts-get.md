# Daemon

The daemon is responsible for starting and stopping the modules which make up
the rest of Uplo.

## /daemon/alerts [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/daemon/alerts"
```

Returns all alerts of all severities of the Uplo instance sorted by severity from highest to lowest in `alerts` and the alerts of the Uplo instance sorted by category in `criticalalerts`, `erroralerts` and `warningalerts`.

### JSON Response
> JSON Response Example

```go
{
    "alerts": [
    {
      "cause": "wallet is locked",
      "msg": "user's contracts need to be renewed but a locked wallet prevents renewal",
      "module": "contractor",
      "severity": "warning",
    }
  ],
  "criticalalerts": [],
  "erroralerts": [],
  "warningalerts": [
    {
      "cause": "wallet is locked",
      "msg": "user's contracts need to be renewed but a locked wallet prevents renewal",
      "module": "contractor",
      "severity": "warning",
    }
  ]
}
```
**cause** | string  
Cause is the cause for the information contained in msg if known.

**msg** | string  
Msg contains information about an issue.

**module** | string  
Module is the module which caused the alert.

**severity** | string  
Severity is either "warning", "error" or "critical" where "error" might be a
lack of internet access and "critical" would be a lack of funds and contracts
that are about to expire due to that.