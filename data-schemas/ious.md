---
label: IOUs
order: -2
---

IOUs are implemented as ERC20 (fungible) tokens, to maximize both compatibility with existing tools and to streamline the transferability of IOUs before they are redeemed for Change Credits.

IOUs are minted according the the below specification:

`Token Name` | CC IOU | \{Good Generator\} \{Index\}
:   The token name assigned to each batch of IOUs always begins with "CC IOU". This is then followed by the name of the Good Generator and an index. The purpose of the index is to differentiate between different projects from one Good Generator.

`Token Symbol` | CC-IOU-\{ProjectID\}
:   The abbreviated token symbol begins "CC-IOU" and is followed by a project ID, where the project ID is composed of the unique ID assigned to the project's Good Generator followed by the project's index value.

`Total Supply`
:   The supply of a project's IOUs will vary over its lifecycle. Initially, a target number of tokens as specified in the project's hypercert will be minted and held in the project's token bound account. As IOUs are redeemed for Change Credits, the IOUs returned to the TBA are subsequently burned.

`Supply Cap`
:   IOUs are implemented including the `ERC20Capped` extension. As such, the Good Generator can specify that the supply of all IOUs is capped at the initial supply set in their target.

For more information regarding the ERC20 token standard, we refer you to documentation maintained by OpenZeppelin [here](https://docs.openzeppelin.com/contracts/5.x/api/token/erc20).