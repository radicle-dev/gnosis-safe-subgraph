
# Gnosis Safe subgraph

This Subgraph dynamically tracks activity on any Gnosis Safe multisignature wallets deployed through the factory.

### Networks:

- Ropsten https://thegraph.com/explorer/subgraph/radicle-dev/gnosis-safe-ropsten
- Mainnet https://thegraph.com/explorer/subgraph/radicle-dev/gnosis-safe

## Prerequiste

- libsecret-1-dev (ubuntu)
```
$ sudo apt-get install libsecret-1-dev
```

- yarn
```
$ sudo apt-get install yarn
```

- graph-cli

```
$ yarn global add @graphprotocol/graph-cli
```

## Getting started

0. Get the source and install the dependencies

```
$ git git@github.com:radicle-dev/gnosis-safe-subgraph.git
$ cd ./gnosis-safe-subgraph
$ npm install
```

1. Build

```
$ ./script/build.sh [--reset] [--code-gen] [--network mainnet|rinkeby|ropsten]
```

- `--reset -r` deletes the build and generated code folders [optional, default: false]
- `--code-gen -c` (re)generate code from schema [optional, default: false]
- `--network -n` select a target network (mainnet, ropsten or rinkeby) [optional, default: mainnet]


## Deployment

1. Authenticate to a graph node

```
$ graph auth https://api.thegraph.com/deploy/ <token>
```

2. Deploy

```
$ ./script/deploy.sh [--network mainnet|rinkeby|ropsten] [--local]
```

- `--network -n` select a target network (mainnet, ropsten or rinkeby) [optional, default: mainnet]
- `--local -l`  deploy on a local node instead of a TheGraph node (https://api.thegraph.com/deploy/) [optional, default: false]


## Model

- Wallet
    -  Transaction

## Query samples

### Get Wallet details

```graphql
{
  wallet(id: "0x12312312.....") {
    id
    creator
    network
    stamp
    hash
    factory
    owners
    threshold
    transactions {
      id
      stamp
      hash
      status
      value
      destination
      data
      signatures
      nonce
      operation
      estimatedSafeTxGas
      estimatedBaseGas
      estimatedGasPrice
      gasToken
      refundReceiver
      gasUsed
      gasPrice
    }
  }
}

```
## Copyright

(c) 2021 Greg Jeanmart
