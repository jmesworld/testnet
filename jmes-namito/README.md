# JMES-NAMITO

Testnet v0.47.x for JMES

## Prerequisites
* Go v1.21+ or higher
* Git
* curl
* jq

## How to Setup
See setup documentation at: https://docs.jmes.cloud/full-node/

```shell
$ git clone -b release/0.47.x https://github.com/jmesworld/core
$ cd core 
$ cd cmd/jmesd
$ go build

$ jmesd version --long
name: jmes
server_name: jmesd
version: v2.0.0-rc.0
commit: e993d6d4fa1447b338d88914dee5d1bab6560e82
build_tags: netgo
go: go version go1.18.2 linux/amd64

$ jmesd init [moniker] --chain-id jmes-namito
$ wget https://raw.githubusercontent.com/jmesworld/testnet/main/jmes-namito/genesis.json -O ~/.jmes/config/genesis.json
$ sed -i 's/minimum-gas-prices = "0ujmes"/minimum-gas-prices = "0.15ujmes"/g' ~/.jmes/config/app.toml

# This will prevent continuous reconnection try. (default P2P_PORT is 26656)
$ sed -i -e 's/external_address = \"\"/external_address = \"'$(curl httpbin.org/ip | jq -r .origin)':26656\"/g' ~/.jmes/config/config.toml

$ jmesd start
```

### Seed Nodes
```
70bf22e2a103e3a00065a540b3963663a34dec25@51.38.52.37:26656
```

### Known Peers
```
70bf22e2a103e3a00065a540b3963663a34dec25@51.38.52.37:26656
```
