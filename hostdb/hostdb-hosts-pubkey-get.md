## /hostdb/hosts/:*pubkey* [GET]
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/hostdb/hosts/ed25519:8a95848bc71e9689e2f753c82c35dc47a1d62867f77c0113ebb6fa5b51723215"
```

fetches detailed information about a particular host, including metrics
regarding the score of the host within the database. It should be noted that
each renter uses different metrics for selecting hosts, and that a good score on
in one hostdb does not mean that the host will be successful on the network
overall.

### Path Parameters
> curl example

```go
curl -A "Uplo-Agent" "localhost:8480/hostdb/hosts/<pubkey>"
```
### REQUIRED
**pubkey**  
The public key of the host. Each public key identifies a single host.

Example Pubkey:
ed25519:1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef

### JSON Response
> JSON Response Example

```go
{
  "entry": {
    // same as hosts
  },
  "scorebreakdown": {
    "score":                      1,        // big int
    "acceptcontractadjustment":   1,        // float64
    "ageadjustment":              0.1234,   // float64
    "basepriceadjustment":        1,        // float64
    "burnadjustment":             0.1234,   // float64
    "collateraladjustment":       23.456,   // float64
    "conversionrate":             9.12345,  // float64
    "durationadjustment":         1,        // float64
    "interactionadjustment":      0.1234,   // float64
    "priceadjustment":            0.1234,   // float64
    "storageremainingadjustment": 0.1234,   // float64
    "uptimeadjustment":           0.1234,   // float64
    "versionadjustment":          0.1234,   // float64
  }
}
```
Response is the same as [`/hostdb/active`](#hosts) with the additional of the
**scorebreakdown**

**scorebreakdown**  
A set of scores as determined by the renter. Generally, the host's final score
is all of the values multiplied together. Modified renters may have additional
criteria that they use to judge a host, or may ignore certin criteia. In
general, these fields should only be used as a loose guide for the score of a
host, as every renter sees the world differently and uses different metrics to
evaluate hosts.

**score** | big int  
The overall score for the host. Scores are entriely relative, and are consistent
only within the current hostdb. Between different machines, different
configurations, and different versions the absolute scores for a given host can
be off by many orders of magnitude. When displaying to a human, some form of
normalization with respect to the other hosts (for example, divide all scores by
the median score of the hosts) is recommended.

**acceptcontractadjustment** | float64  
The multiplier that gets applied to the host based on whether its accepting contracts or not. Typically "1" if they do and "0" if they don't.

**ageadjustment** | float64  
The multiplier that gets applied to the host based on how long it has been a
host. Older hosts typically have a lower penalty.

**basepriceadjustment** | float64  
The multiplier that gets applied to the host based on if the `BaseRPCPRice` and
the `SectorAccessPrice` are reasonable.

**burnadjustment** | float64  
The multiplier that gets applied to the host based on how much proof-of-burn the
host has performed. More burn causes a linear increase in score.

**collateraladjustment** | float64  
The multiplier that gets applied to a host based on how much collateral the host
is offering. More collateral is typically better, though above a point it can be
detrimental.

**conversionrate** | float64  
conversionrate is the likelihood that the host will be selected by renters
forming contracts.

**durationadjustment** | float64  
The multiplier that gets applied to a host based on the max duration it accepts
for file contracts. Typically '1' for hosts with an acceptable max duration, and
'0' for hosts that have a max duration which is not long enough.

**interactionadjustment** | float64  
The multipler that gets applied to a host based on previous interactions with
the host. A high ratio of successful interactions will improve this hosts score,
and a high ratio of failed interactions will hurt this hosts score. This
adjustment helps account for hosts that are on unstable connections, don't keep
their wallets unlocked, ran out of funds, etc.

**pricesmultiplier** | float64  
The multiplier that gets applied to a host based on the host's price. Lower
prices are almost always better. Below a certain, very low price, there is no
advantage.

**storageremainingadjustment** | float64  
The multiplier that gets applied to a host based on how much storage is
remaining for the host. More storage remaining is better, to a point.

**uptimeadjustment** | float64  
The multiplier that gets applied to a host based on the uptime percentage of the
host. The penalty increases extremely quickly as uptime drops below 90%.

**versionadjustment** | float64  
The multiplier that gets applied to a host based on the version of Uplo that they
are running. Versions get penalties if there are known bugs, scaling
limitations, performance limitations, etc. Generally, the most recent version is
always the one with the highest score.  