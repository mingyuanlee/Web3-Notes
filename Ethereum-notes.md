1. ERCs are application level standards that establish a shared interface for contracts and dapps to reliably interact with each other. 



1. ERC-165: a standard to publish and detect what interfaces a smart contract implements.
```
// ERC165/ERC165.sol
pragma solidity 0.5.8;
interface ERC165 {
  function supportsInterface(bytes4 interfaceID) 
    external view returns (bool);
}
```
1. So in order for the Store contract to publish that it supports StoreInterface, it needs to implement the supportsInterface function to return true if the input interfaceID is the interface ID of StoreInterface, and return false if the interface ID is something else.
1. Calculate the interface id: ERC165 defines that an interface ID can be calculated as the XOR of all function selectors in the interface.

