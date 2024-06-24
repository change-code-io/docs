---
label: Attestation Schemas
order: -3
---

The Changescape leverage the Ethereum Attestation Service (EAs) to manage both initial claims of quantifiable impact as well as the verification of any claimed impact. The schemas for representing both of these attestations are specified below while an excellent overview around attestations and schemas can be found in the [EAS documentation](https://docs.attest.org/docs/category/core-concepts).

## Claim Schema

Before data can be verified it must first be attested to (or claimed) by the Good Generator(s). It is important to note that this is a separate requirement from the creation of a project's Hypercert. As can be seen from Change Code's Hypercert [specification](./hypercerts.md), the Hypercert is published before a project's work begins and accordingly would not have any information regarding results.

hypercertID | `bytes32`
:   Every attestation must link to the Hypercert of the project for which it is claiming impact. This is accomplished by including the Hypercert's unique 32 byte identifier.

impactUnit | `string[]`
:   The unit according to which the impact or positive externality is quantified--e.g. metric tons of carbon sequestered, liters of clean water, vaccine doses administered, etc.

impactQuantity | `int64[]`
:   The quantity of impact claimed according to the unit specified in the attestation.

evidenceDocumentation | `bytes32[]`
:   IPFS reference to any documentation the Good Generator wishes for the verifiers to review in order to assess the claims made.

!!!info Note
As each project (with a single Hypercert) may very well have more than one quantifiable metric, *impactValue*, *impactUnit*, and *evidenceDocumentation* can each support arrays or multiple entries each. This is indicated by the inclusion of `[]` in each.
!!!

While not explicitly part of the attestation schema, claim attestations made inside the Changescape include a modified version of the [`Attestor Resolver`](https://docs.attest.org/docs/tutorials/resolver-contracts#attester-resolver) contract in order to allow Good Generator's submitting claims to name specific Verifiers along with a quorum of those Verifiers required for the claim to be considered verified.

!!!warning Acknowledgement
We recognize that having Good Generator's list allowed Verifiers may create issues of objectivity or conflict. In future versions of the Changescape, this setup will be replaced with a form of token gating through which only recognized experts can stake a form of reputation to evaluate projects. 
!!!

## Verification Schema

The second attestation schema structures verifications (or refutations) in reference to impact claims so that Change Credits can be appropriately issued.

hypercertID | `bytes32`
:   Every attestation must link to the Hypercert of the project being reviewed. As with the claim schema, this is accomplished by including the Hypercert's unique 32 byte identifier.

impactUnit | `bool[]`
:   This boolean field is used by Verifiers to either accept (true) or reject (false) the proposed set of impact units.

impactQuantity | `int64[]`
:   Provided an impact unit is accepted, this field captures the quantity of impact produced according to the attesting Verifier.

evidenceDocumentation | `bytes32[]`
:   IPFS reference to any documentation the Verifier wishes to provide.

As described in the Change Credit [verification flow](../change-credits/verification.md), data may be provided by a Good Generator periodically across multiple submissions as the project progresses over time. Because of this flexibility, a single Hypercert may see multiple claim attestations made, consequently the hypercertID is not sufficient to uniquely identify a claim. To resolve this, each verification attestation points to a corresponding claim attestation through an [`refUID`](https://docs.attest.org/docs/tutorials/referenced-attestations).

## Data Storage

Because the Changescape is designed as a cross-chain or multi-chain protocol, the matter of data storage for attestations is especially important. EAS supports either on-chain or off-chain attestation storage, with the former option being both more expensive and more conducive to a single chain experience.

Changescape attestations are instead stored off-chain via the [Ceramic Network](https://developers.ceramic.network/docs/introduction/intro), a decentralized database network that supports InterPlanetary File System (IPFS). While remaining chain-agonistic for both writing and reading data, Ceramic manages to provide immutability by periodically [merklizing](https://docs.attest.org/docs/tutorials/ceramic-storage#ceramic-as-a-data-ledger) all updates and publishing the root to the Ethereum chain.