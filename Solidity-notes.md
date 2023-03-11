
1. All functions in interface contracts are automatically considered virtual. So you need to use ```override``` to implement interface functions.
1. ```block.timestamp```: current block timestamp as seconds since unix epoch in ```uint256```.
1. If the key is not in the mapping, the default value will be returned. If the value is a struct, all the values of the struct will be the default value. The default value of address will be address(0).
1. ```super```: call parent contract methods.
1. ```constant``` for function seems to be an alias of ```view```.
1. Solidity doesn't allow for map iterability, so use EnumerableSet to track map keys and iterate set.
1. For an integer type ```X```, you can use ```type(X).min``` and ```type(X).max``` to access the minimum and maximum value representable by the type.
1. For a contract ```C``` you can use ```type(C)``` to access type information about the contract.
  1. Following properties are available for type Contract:
    - type(C).name: the name of the contract.
    - type(C).creationCode: memory byte array that contains the creation bytecode of the contract.
    - type(C).runtimeCode: memory byte array that contains the runtime bytecode of the contract.
  1. Following properties are available for type Interface:
    - type(I).interfaceId: A bytes4 value containing the EIP-165 interface identifier of the given interface I.
  1. https://docs.soliditylang.org/en/v0.8.17/units-and-global-variables.html#meta-type
1. When non-pure or non-view solidity function is called off-chain, the return value is always the hash of the transaction, not the intended return value of the function.
1. memory or storage: required for arrays, strings, mappings and structs
1. When using structs and arrays within the function, need to declare the data location. memory: passed by value; storage: passed by reference. 
1. keccak256 expects a single parameter of type bytes. This means that we have to "pack" any parameters before calling keccak256. Like ```keccak256(abi.encodePacked("aaaab"));```
1. Interface: 
    - contracts without implementation
    - only declare functions
    - no state variables / constructors / inherit from other contracts
    - all functions must be external
1. To compare strings, we have to compare their hashes.
1. Using uint8 instead of uint won't save any gas. There's an exception: inside structs. When having multiple uints inside a struct, use smaller-sized uint when possible will allow Solidity to pack these variables together to save storage. Also put identical data types next to each other.
1. calldata is somehow similar to memory, but it's only available to external functions.
1. Use read-only external view functions wherever possible: view functions don't cost any gas when they're called externally by a user. So marking a function with view tells web3.js that it only needs to query your local Ethereum node to run the function, and it doesn't actually have to create a transaction on the blockchain (which would need to be run on every single node, and cost gas).
1. When view functions are called internally, they still cost gas.
1. One of the more expensive operations in Solidity is using storage — particularly writes.
1. memory arrays must be created with a length argument (in this example, 3). They currently cannot be resized like storage arrays can with array.push(), although this may be changed in a future version of Solidity.
1. looping through memory arrays uses less gas than storage arrays. sometimes you'll want to use a for loop to build the contents of an array in a function rather than simply saving that array to storage.
1. Create a memory string: ```uint[] memory values = new uint[](3)```
1. When we declare using SafeMath for uint, the uint we call the function on (test) is automatically passed in as the first argument.
1. The difference between assert and require is that require will refund the user the rest of their gas when a function fails, whereas assert will not.

