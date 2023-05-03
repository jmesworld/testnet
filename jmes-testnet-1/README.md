# JMES-888

Testnet for JMES.
## Prerequisites
* Go v1.18+ or higher
* Git
* curl
* jq

## How to Setup
See setup documentation at: https://docs.jmes.cloud/full-node/

```shell
$ git clone -b cosmwasm https://github.com/jmesworld/core
$ cd core 
$ cd app
$ go build

$ jmesd version --long
name: jmes
server_name: jmesd
version: v2.0.0-rc.0
commit: e993d6d4fa1447b338d88914dee5d1bab6560e82
build_tags: netgo
go: go version go1.18.2 linux/amd64

$ jmesd init [moniker] --chain-id jmes-888
$ wget https://raw.githubusercontent.com/jmesworld/testnet/main/jmes-888/genesis.json -O ~/.jmes/config/genesis.json
$ sed -i 's/minimum-gas-prices = "0ujmes"/minimum-gas-prices = "0.15ujmes"/g' ~/.jmes/config/app.toml

# This will prevent continuous reconnection try. (default P2P_PORT is 26656)
$ sed -i -e 's/external_address = \"\"/external_address = \"'$(curl httpbin.org/ip | jq -r .origin)':26656\"/g' ~/.jmes/config/config.toml

$ jmesd start
```

### Seed Nodes
```
c08d5b3d253bea18b24593a894a0aa6e168079d3@34.232.34.124:26656
```

### Known Peers
```
c3fa45f72c551a115dce166b77efb297e7d0a864@51.38.52.37:26656
24ef20ecc3fc8c34755fad4af92c67eaf6a7b795@164.90.208.140:26656
```
