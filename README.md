# Vault shim

This script does a few housekeeping items to make use of the vault CLI a little easier:

  1. Creates a `.vault` directory to contain the actual binary
  2. Looks for a `.tkn` file in a `.priv` directory matching either a name given by a `VT` environment variable or defaulting to `root` and reads the `token` line from the file to use as the vault token

