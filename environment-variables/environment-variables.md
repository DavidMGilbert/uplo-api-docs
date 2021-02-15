# Environment Variables
There are a number of environment variables supported by uplod and uploc.

- `UPLO_API_PASSWORD` is the environment variable that sets a custom API
  password if the default is not used
- `UPLO_DATA_DIR` is the environment variable that tells uplod where to put the
  general uplo data, e.g. api password, configuration, logs, etc.
- `UPLOD_DATA_DIR` is the environment variable that tells uplod where to put the
  uplod-specific data
- `UPLO_WALLET_PASSWORD` is the environment variable that can be set to enable
  auto unlocking the wallet
- `UPLO_EXCHANGE_RATE` is the environment variable that can be set (e.g. to
  "0.00018 mBTC") to extend the output of some uploc subcommands when displaying
  currency amounts