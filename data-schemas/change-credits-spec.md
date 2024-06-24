---
label: Change Credits
order: -4
---

Change Credits are non-fungible (NFT) tokens implemented according to the ERC721 standard, the most commonly used NFT standard in web3. The motivation to use non-fungible tokens, used most commonly as digital collectibles or as tools to control membership access, is two fold.

First, Good Generators may elect to confer invitations to events or provide partner only forms of communication or community. These uses of "token gating" are well solved by NFTs as they provide clearest binary between partners (those who hold a project's NFT) and others. The second consideration for constructing Change Credits as NFTs is admittedly more abstract. While there is no ignoring the fact that larger contributions to projects can have a larger impact, it is important to emphasize and embrace the idea that simply partnering for impact in the first place and at any level of contribution is the most important step one can take.

Change Credits are implemented as follows:

`Name` | CC | \{Good Generator\} \{Index\}
:   The token name assigned to each set of Change Credits always begins with "CC". This is then followed by the name of the Good Generator and an index. The purpose of the index is to differentiate between different projects from one Good Generator.

`Symbol` | CC-\{ProjectID\}
:   The abbreviated token symbol begins "CC-IOU" and is followed by a project ID, where the project ID is composed of the unique ID assigned to the project's Good Generator followed by the project's index value.

`tokenURI`
:   The `tokenURI` sets the IPFS link to the metadata (defined below) with further details of the NFT. The Change Credit implementation includes the [`ERC721URIStorage`](https://docs.openzeppelin.com/contracts/5.x/api/token/erc721#ERC721URIStorage) extension so that each instance of token in the set can have its own unique metadata.

`Metadata`
:   Included here is the json schema for the metadata stored at the NFT's `tokenURI`. The first 4 properties are included to comply with the metadata structure set by NFT marketplaces and viewers such as [OpenSea](https://docs.opensea.io/docs/metadata-standards). 
```json
{
  "description": "{A description, not exceeding 200 characters, of the work accomplished by the project}", 
  "external_url": "{Unique Changescape URL}", 
  "image": "{link to Hypercert Image URL}", 
  "name": "CC | {Good Generator} {Index} {Serial #}",
  "attributes": [
    {
        "display_type": "number",
        "trait_type": "Contribution",
        "value": "{Total value of the contribution behind the Change Credit}"
    },
    {
        "display_type": "number",
        "trait_type": "Retirement",
        "value": "{Portion of the Change Credit that has already been retired by the Good Generator}"
    },
    {
        "display_type": "number",
        "trait_type": "Redemption",
        "value": "{Portion of the Change Credit that has already been redeemed by the holder}"
    }]
}
```