## Start

1. Create a new project: ```truffle init my-project```
1. Create a contract: ```truffle create contract ERC4907```
1. Create a test: ```truffle create test TestXXX```

## Openzeppelin Contracts

1. Install: ```npm i @openzeppelin/contracts@4.8.0```


## Migrations

1. Migrations are JavaScript files that help you deploy contracts to the Ethereum network.
1. Run migrations: ```truffle migrate```
1. Example migration file ```1_deploy_contract.js```:
```
const RentableNFT = artifacts.require("RentableNFT");

module.exports = function (deployer) {
  deployer.deploy(RentableNFT);
};
```

## Ganache

1. Run ganache: ```ganache```



1. Interactive consoles:
  - Truffle Console: basic interactive console connecting to any Ethereum client.
  - Truffle Develop: interactive console that also spawns a development blockchain.

## Scripts

1. Need to export a function
```
module.exports = async function (callback) {
};
```
1. Inside the function, web3 in injected by Truffle.
1. Run the script:
```truffle exec scripts/mintNFT.js --network rinkeby```


## Network Config

1. Rinkeby with infura
```
rinkeby: {
 provider: () => new HDWalletProvider(mnemonic, infuraURL),
 network_id: 4, // Rinkeby's id
 gas: 15500000, // Rinkeby has a lower block limit than mainnet
 confirmations: 2, // # of confs to wait between deployments. (default: 0)
 timeoutBlocks: 200, // # of blocks before a deployment times out  (minimum/default: 50)
 skipDryRun: true, // Skip dry run before migrations? (default: false for public nets )
},
```

## Verify

1. https://github.com/rkalis/truffle-plugin-verify

## Common Problems

1. Truffle stack smashing detected in WSL2. Related to stack size limit. Use ```ulimit -s 65532```

