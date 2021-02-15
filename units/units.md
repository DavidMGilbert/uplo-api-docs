# Units

Unless otherwise noted, all parameters should be identified in their smallest
possible unit. For example, size should always be specified in bytes and
Uplocoins should always be specified in hastings. JSON values returned by the API
will also use the smallest possible unit, unless otherwise noted.

If a number is returned as a string in JSON, it should be treated as an
arbitrary-precision number (bignum), and it should be parsed with your
language's corresponding bignum library. Currency values are the most common
example where this is necessary.