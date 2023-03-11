## Counters

1. ```import "@openzeppelin/contracts/utils/Counters.sol";``` Counters
1. To use:
  - ```using Counters for Counters.Counter;```


1. ```import "@openzeppelin/contracts/interfaces/IERC165.sol";``` IERC165
1. ```import "@openzeppelin/contracts/interfaces/IERC721.sol";``` IERC721

## Reentrancy Gaurd

1. ```import "@openzeppelin/contracts/security/ReentrancyGuard.sol";``` 
1. To use ```nonReentrant()``` modifier

## Enumerable Set

1. ```import "@openzeppelin/contracts/utils/structs/EnumerableSet.sol";```
1. Properties:
  - Elements are added, removed, and checked for existence in constant time (O(1)).
  - Elements are enumerated in O(n). No guarantees are made on the ordering.
1. To use:
```
contract Example {
    // Add the library methods
    using EnumerableSet for EnumerableSet.AddressSet;
    using EnumerableSet for EnumerableSet.UintSet;

    // Declare a set state variable
    EnumerableSet.AddressSet private mySet;
}
```
1. https://docs.openzeppelin.com/contracts/3.x/api/utils#EnumerableSet

