---
label: Foundations
order: -1
---

Change Credits are a novel *financial* primitive supporting resource allocation, verification, and tracking of positive externalities (social and environmental impact).

They are the basis and grounding of Change Code's economic engine, providing a real-world tangible link to underpin a new form of beneficial currency.

## Supporting Primitives and Infrastructure

Before expanding on the architecture and processes involved in Change Credits directly, we should first recap (or introduce) some of the existing open-source tools and standards leveraged here.

### Hypercerts

Hypercerts are on-chain, tokenized claims of positive impact. To be more precise, hypercerts represent *claims* of *work* to be done toward some beneficial outcome, be that work toward social or environmental impact or the building of a public good.

!!!
It is worth noting that the relationship between Hypercerts and the status of positive impact is not currently settled. Some usages lean toward only representing work already done while other implementations represent plans for future work as Hypercerts instead. Inside the Change Code implementation, we will default to the latter interpretation, with Hypercerts issued as a way to commit to future work.
!!!

A complete list of the on-chain token data and off-chain metadata included in a hypercert can be found in the [documentation](https://hypercerts.org/docs/implementation/metadata). Importantly, for our purposes and designs, there is no included support for verification that the work was completed or efficacious. This will therefore be addressed using another foundation public good, the Ethereum Attestation Service (EAS). However, the hypercerts specification does include a field for a list of contributors. Change Credits takes advantage of this encoding to record contributions of the actual work done, while tracking *financial partners* through ownership of Change Credits themselves.

### Ethereum Attestation Service (EAS)

Change Code leverages the EAS to allow experts and representatives of affected communities to verify (attest to) any work done that is claimed to be impactful or contribute to a public good.

While not tokens themselves (more on that [here](https://docs.attest.org/docs/core--concepts/attestations-vs-x)), these attestations are cryptographically secured and can be used by project partners and the public to confirm all verifications of a project's work.

### Token Standards

To maintain maximum compatibility across existing wallets and infrastructure, the Change Credits architecture leverages only broadly accepted ERC token standards. Change Credits themselves are minted as NFTs (non-fungible tokens) through the ERC721 standard.

+++ ERC721
ERC721 is the most widely adopted token standard for NFTs. The standard is well-tested, and enjoys near-universal support across wallet implementations.
+++ ERC1155
Hypercerts adhere to the ERC1155 standard for semi-fungible tokens. This mixed standard, existing in the divide between fungible and non-fungible tokens, offers ideal flexibility for the unique requirements of the hypercerts standard.
+++ ERC20
ERC20 tokens are fully fungible and well suited for liquidity and open exchange. IOUs issued in anticipation of Change Credits are minted as ERC20 tokens to support the emergence of free exchange by holders who may wish to access liquidity.
+++ ERC6551
Referred to as "token bound accounts" (TBAs), ERC6551 tokens function as a form of smart contract wallet where an account is simultaneously able hold or mint tokens itself and be considered a token (an NFT more specifically) in its own right. Change Code leverages TBAs to serve as *treasury accounts* for the receipt of funds into projects and the minting of Change Credits.
+++

### Network Infrastructure

To maximize the reach of our work and do our best to always meet changemakers where they are, the Changescape is designed as a cross-chain or multi-chain protocol. Leveraging shared tools and being available to existing communities across different ecosystems is among our most important design considerations.

#### Blockchain

##### Optimism
Initial smart contracts for the Changescape are being deployed onto the Optimism L2 mainnet. The Optimism community has demonstrated a deep commitment toward positive impact, both inside of and beyond climate specific initiatives. Moreover, the technology involved in the [OP Stack](https://docs.optimism.io/stack/getting-started) is among the most closely aligned with the the Ethereum core and its roadmap prioritizes key pieces of the Ethereum ecosystem that are critical to Change Code, such as [EAS](https://docs.attest.org/docs/quick--start/contracts#optimism).

##### Celo
For years the Celo blockchain stood out as the largest layer 1 blockchain network focused around positive impact. The network is currently undergoing a transition to enter the Optimism orbit as a part of the upcoming Optimism [Superchain](https://docs.optimism.io/stack/explainer). Change Code is closely following the advances of both [Celo](https://forum.celo.org/t/clabs-proposes-migrating-celo-to-an-ethereum-l2-leveraging-the-op-stack/7902) and the Superchain to eventually migrate our primary deployments when the time is right.

##### Aztec
While not currently emphasized in many circles focused on ReFi (regenerative finance) or public goods, the issue of privacy is something that we view as central to our long term vision and needs. It is often neglected that working for the benefit of all is a privilege and that while it may be safe for those in the *West* or the *Global North* to advance climate initiatives, engage in investigative journalism, or attempt to advocate for peace, many are not as fortunate. There are many situations in which climate action can be and is met with threats and physical violence, where educating women or ethnic minorities can make one a target of ideologues, or where it is impossible to mediate for peace without being at risk from extremists on either side of the divide.

For these reasons and many more, Change Code has a long term interest in the use of zero-knowledge and other privacy preserving technology. We are actively researching to eventually upgrade our protocol to support project deployments where any identifying information about participants can be publicly shielded while still enabling robust verification. [Aztec](https://docs.aztec.network/), together with it's smart contract language Noir, presents the ideal route to achieve this vision.

#### Interoperability

Beyond any choices for which networks may be used to deploy the *logic* for the Changescape, is the question of where various tokens--IOUs, Change Credits, and Mutual Money--may be accessed. To make Change Credit tokens accessible across chains, while avoiding centralized bridges and potential honeypots which can be drained by attackers, Change Code is integrating [LayerZero](https://layerzero.network/how-it-works) for cross-chain token transfers.

While this list will grow overtime, Change Code is currently prioritizing building connections to make our tokens available on Arbitrum and Solana as both chains have substantial ReFi and public goods communities.