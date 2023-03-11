

1. Load the compiled contract Json:
```
const contractJson = require("../build/contracts/Infura721NFT.json");
```
1. Create new contract:
```
const contract = new web3.eth.Contract(
  contractJson.abi,
  CONTRACT_ADDRESS // this is the address generated when running migrate
);
```
1. Get the current network name:
```
const network = await web3.eth.net.getNetworkType();
```
1. Generate a transaction:
```
const tx = contract.methods.mintNFT(PUBLIC_ADDRESS);
```
1. Send the transaction:
```
const receipt = await tx
  .send({
    from: (await web3.eth.getAccounts())[0], // uses the first account in the HD wallet
    gas: await tx.estimateGas(),
  })
  .on("transactionHash", (txhash) => {
   
  })
  .on("error", function (error) {

  })
  .then(function (receipt) {

  })

```

1. Contract.methods.myMethod.send will return ```Promise combined event emitter```:
```
web3.eth.sendTransaction({from: '0x123...', data: '0x432...'})
.once('sending', function(payload){ ... })
.once('sent', function(payload){ ... })
.once('transactionHash', function(hash){ ... })
.once('receipt', function(receipt){ ... })
.on('confirmation', function(confNumber, receipt, latestBlockHash){ ... })
.on('error', function(error){ ... })
.then(function(receipt){
    // will be fired once the receipt is mined
});
```