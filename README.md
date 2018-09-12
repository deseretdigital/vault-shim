# Vault shim

This script does a few housekeeping items to make use of the vault CLI a little easier:

  1. Creates a `.vault` directory to contain the actual binary
  2. Looks for a `.tkn` file in a `.priv` directory matching either a name given by a `VT` environment variable or defaulting to `root` and reads the `token` line from the file to use as the vault token

## Usage

To get started do something like:

```sh
$ cd /opt
$ git clone github.com:ev0rtex/vault-shim.git
$ echo "export PATH=$PATH:/opt/vault-shim" >> ~/.bashrc
```

This script automatically creates a `.priv` directory if it doesn't exist but in order to use vault with this you need to add a `.tkn` file in that directory that contains the output from the `vault token create` command or at a minimum has a line such as:

```
token 6e2a85d1-87a1-35f7-38b4-28c56e727b98
```

A simple example might be something like this:

```sh
$ echo "token 6e2a85d1-87a1-35f7-38b4-28c56e727b98" > .priv/root.tkn
$ vault auth list
$ echo "token f5892e9b-fa96-1107-15b1-b00a10ce60e3" > .priv/other.tkn
$ VT=other vault auth list
```
