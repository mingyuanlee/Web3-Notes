## Browsers

1. Brave


## Filecoin

1. The Filecoin network is a great building block for any decentralized storage system.
1. Filecoin's proving algorithms:
  - Proof of Replication: proves that a given storage provider is storing a unique copy of a client's original data.
  - Proof of Spacetime: proves that the client's data is stored continuously over time.


## NFT.Storage

### Upload images, assets and metadata

1. Expects the metadata to conform to the ERC-1155 metadata schema.
```
const nft = {
    image, // use image Blob as `image` field
    name: "Storing the World's Most Valuable Virtual Assets with NFT.Storage",
    description: "The metaverse is here. Where is it all being stored?",
    properties: {
      type: "blog-post",
      origins: {
        http: "https://blog.nft.storage/posts/2021-11-30-hello-world-nft-storage/",
        ipfs: "ipfs://bafybeieh4gpvatp32iqaacs6xqxqitla4drrkyyzq6dshqqsilkk3fqmti/blog/post/2021-11-30-hello-world-nft-storage/"
      },
      authors: [{ name: "David Choi" }],
      content: {
        "text/markdown": "The last year has witnessed the explosion of NFTs onto the world’s mainstage. From fine art to collectibles to music and media, NFTs are quickly demonstrating just how quickly grassroots Web3 communities can grow, and perhaps how much closer we are to mass adoption than we may have previously thought. <... remaining content omitted ...>"
      }
    }
  }
```
1. Use ```const metadata = await client.store(nft)```.

### Content Archive (CAR)
1. The type of data stored in CARs is defined by IPLD.
1. Create and interact with CAR files (Command line)
  - ipfs-car
    1. install: ```npm install -g ipfs-car```
    1. create a new CAR file: ```ipfs-car --pack path/to/files --output path/to/write/a.car```
    1. extract files from CAR: ```ipfs-car --unpack path/to/my.car --output /path/to/unpack/files/to```
    1. list the contents of a CAR: ```ipfs-car --list path/to/my.car```
1. Work with CAR files in applications:
  - ipfs-car: includes library functions for packing and unpacking files into CARs, using the IPFS UnixFs data model.
  - go-car: provides the main Golang implementation of the CAR specification.

### Gateways

1. To make IPFS data accessible outside of the peer-to-peer network, special IPFS nodes called "gateways" act as bridges between the HTTP protocol that all web browsers understand and the peer-to-peer Bitswap protocol.

### Javascript client library

### UCAN