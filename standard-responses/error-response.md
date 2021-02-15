## Error

The standard error response indicating the request failed for any reason, is a
4xx or 5xx HTTP status code with an error JSON object describing the error.

```go
{
    "message": String

    // There may be additional fields depending on the specific error.
}
```

### Module Not Loaded

A module that is not reachable due to not being loaded by uplod will return
the custom status code `490 ModuleNotLoaded`. This is only returned during
startup. Once the startup is complete and the module is still not available,
ModuleDisabled will be returned.

### Module Disabled

A module that is not reachable due to being disabled, will return the custom
status code `491 ModuleDisabled`.