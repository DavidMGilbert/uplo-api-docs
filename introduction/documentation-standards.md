## Documentation Standards

The following details the documentation standards for the API endpoints.

- Endpoints should follow the structure of:
    - Parameters
    - Response
- Each endpoint should have a corresponding curl example
    - For formatting there needs to be a newline between `> curl example` and the
      example
- All non-standard responses should have a JSON Response example with units
    - For formatting there needs to be a newline between `> JSON Response
      Example` and the example
- There should be detailed descriptions of all JSON response fields
- There should be detailed descriptions of all query string parameters
- Query String Parameters should be separated into **REQUIRED** and
  **OPTIONAL** sections
- Detailed descriptions should be structured as "**field** | units"
    - For formatting there needs to be two spaces after the units so that the
      description is on a new line
- All code blocks should specify `go` as the language for consistent formatting

Contributors should follow these standards when submitting updates to the API
documentation.  If you find API endpoints that do not adhere to these
documentation standards please let the Uplo team know by submitting an issue
[here](https://github.com/uplo-tech/uplo/issues)