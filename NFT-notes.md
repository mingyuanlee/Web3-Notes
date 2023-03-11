## Rentable NFT

1. ERC-4907 standardizes the way NFT rentals happen by separating the concept of user and owner.
1. A user has the ability to use the NFT, but does not have the permission to sell it. In addition, an expires function is introduced, so that the user only has temporary access to use the NFT.

### Set User

```
/// @notice set the user and expires of a NFT
/// @dev The zero address indicates there is no user
/// Throws if `tokenId` is not valid NFT
/// @param user  The new user of the NFT
/// @param expires  UNIX timestamp, The new user could use the NFT before expires
function setUser(uint256 tokenId, address user, uint64 expires) public virtual override {
  require(_isApprovedOrOwner(msg.sender, tokenId),"ERC721: transfer caller is not owner nor approved");
  UserInfo storage info = _users[tokenId];
  info.user = user;
  info.expires = expires;
  emit UpdateUser(tokenId, user, expires);
}
```

- ```_isApprovedOrOwner()``` comes from ERC721.

### isRentableNFT

1. To check the interface:
```
function isRentableNFT(address nftContract) public view returns (bool) {
    bool _isRentable = false;
    bool _isNFT = false;
    try IERC165(nftContract).supportsInterface(type(IERC4907).interfaceId) returns (bool rentable) {
        _isRentable = rentable;
    } catch {
        return false;
    }
    try IERC165(nftContract).supportsInterface(type(IERC721).interfaceId) returns (bool nft) {
        _isNFT = nft;
    } catch {
        return false;
    }
    return _isRentable && _isNFT;
}
```

## ERC721

1. Allows for the following behavior:
  - Transfer NFTs between accounts
  - Access control limiting who can transfer NFTs
  - Trade NFTs for other currencies
  - Identify the total supply of NFTs on a network
  - Query for the owners of a specific asset
1. Can be extended with:
  - Allow pausing of token transfers for all users (Pause extension)
  - Ability to burn NFTs (Burn extension)
  - Implement the ERC2981 NFT Royalty Standard (Royalty extension)

1. ```setApprovalForAll(address to, bool approved)```: Sets or unsets the approval of a given operator.  An operator is allowed to transfer all tokens of the sender on their behalf.
  - When you sell NFTs on a Marketplace, you need to authorize this marketplace to transfer sold items from your address to the buyer's address.
  - This is what SetApprovalForAll is used for: because you trust the marketplace, you "approve" it to sell your NFTs (not all your NFTs, but the NFTs you own in the context of this contract).
  - The marketplace is what is called the "operator" in the context of this API.
  - https://stackoverflow.com/questions/69854414/why-and-when-is-setapprovalforall-called
1. 



1. Install the OpenZeppelin package:
```npm i @openzeppelin/contracts```


1. Receiving contracts must implement IERC721Receiver to safely receive ERC721 NFTs.


## ERC-721a

1. ERC-721a is an extension of ERC-721 that provides significant gas-savings for batch-minting of NFTs while still being ERC-721 compliant.
1. Install the Azuki ERC-721a package with npm:
```npm install --save-dev erc721a```

## IERC721Receiver

1. Interface for any contract that wants to support safeTransfers from ERC721 asset contracts.

## ERC-1155 Multi-Token Standard

1. Interface for any contract that wants to support safeTransfers from ERC721 asset contracts.
1. Can transfer multiple NFTs in a single transaction (safeBatchTransferFrom() function).


## Metadata Standards

### Part One

1. In order to pull off-chain metadata, need to return URI of metadata.
1. Use ```tokenURI``` in ERC721 and ```uri``` in ERC1155 to find this URI. Should return HTTP or IPFS URL.
1. This URI should return a JSON blob of data (metadata).
1. Example tokenURI:
```
function tokenURI(uint256 _tokenId) public view returns (string) {
  return Strings.strConcat(
      baseTokenURI(),
      Strings.uint2str(_tokenId)
  );
}
```

### Part Two - Metadata standards

1. https://docs.opensea.io/docs/metadata-standards?ref=infura-blog

## R