## /renter/uploads/pause [POST]
> curl example

```go
curl -A "Uplo-Agent" -u "":<apipassword> --data "duration=10m" "localhost:8480/renter/uploads/pause"
```

This endpoint will pause any future uploads or repairs for the duration
requested. Any in progress chunks will finish. This can be used to free up
the workers to exclusively focus on downloads. Since this will pause file
repairs it is advised to not pause for too long. If no duration is supplied
then the default duration of 600 seconds will be used. If the uploads are
already paused, additional calls to pause the uploads will result in the
duration of the pause to be reset to the duration supplied as opposed to
pausing for an additional length of time.

### Path Parameters
#### OPTIONAL
**duration** | string  
duration is how long the repairs and uploads will be paused in seconds. If no
duration is supplied the default pause duration will be used.

### Response
standard success or error response. See [standard
responses](#standard-responses).