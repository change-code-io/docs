---
label: Minting Change Credits
order: -2
---

Because Change Credits are only minted following confirmation of realized, tangible, and verifiable impact, the process by which these assets are created follows a number of steps and involves multiple types of actors.

## Participants

Good Generator
:   A Good Generator is the implementing organization responsible for seeing the planned impact results achieved. It is through the actions of this entity, often an NGO or social enterprise, that positive externalities are produced. Because contributions and funds can be seamlessly fractionalized and divided, a Good Generator can also be a collection of multiple contributors working collaboratively.

Change Code
:   Change Code acts to provide all necessary infrastructure for the creation and management of Change Credits through its *Changescape*. While Change Code is not involved in the measurement or verification of any results produced, it is responsible for assessing the legitimacy and compliance of any organizations seeking to mint Change Credits.

Partner
:   Partners financially contribute to the positive externalities embodied in Change Credits. They fund the delivery of impact by pre-purchasing Change Credits in advance.

Verifier
:   Verifiers exist to both validate, measure, and quantify any impact produced. Verifiers are defined by the Good Generator of the project with a focus on local context and relevant expertise. Verification can be conducted by a single individual or organization or the responsibility can be dispersed through a set of Verifiers with a specified quorum required.

## Minting Flow

```mermaid
sequenceDiagram
    actor Verifier
    actor Good Generator
    actor Change Code
    Good Generator-->Change Code: propose impact goal for review
    participant EAS
    create participant hypercert (ERC1155)
    Good Generator->>hypercert (ERC1155): mint impact goal
    actor Change Code
    create participant Treasury Account (ERC6551)
    Change Code->>Treasury Account (ERC6551): deploy treasury account
    actor Partner
    loop
        Partner->>Treasury Account (ERC6551): send $
        Treasury Account (ERC6551)->>Partner: mint IOUs (ERC20)
        Treasury Account (ERC6551)->>Good Generator: remit funding received
    end
    Good Generator-->Good Generator: implement project
    loop
        Good Generator->>EAS: publish claim attestation
        Verifier--xEAS: review evidence
        Verifier->>EAS: publish verification attestation
        Change Code->>Treasury Account (ERC6551): mint Change Credits (ERC721)
    end
    Loop
        Partner->>Treasury Account (ERC6551): return IOUs
        Treasury Account (ERC6551)->>Partner: receive Change Credits
    end
```

The above sequence diagram overviews how Change Credits are created. While the system supports alternative flows to facilitate various forms of financing, we can consider this base form to have x steps.

1. The Good Generator submits an impact goal and plan for review by Change Code, as part of their onboarding process. Once approved to mint via the Changescape, the Good Generator mints their hypercert, signaling the beginning for their project.
2. After the projects' hypercert has been deployed, Change Code deploys an associated Token Bound Account (ERC6511) to act as a treasury for the project to receive funds into and mint tokens from.
3. Partners begin contributing funds into the project's TBA in exchange for IOUs redeemable for Change Credits once the latter begin to be minted. These funds are then remitted to an account from which the Good Generator can spend to cover the costs of their work. This process can be done in an open-ended asynchronous manner, with funds being contributed to the project through the project's lifespan.
4. As the Good Generator carries out their work to produce impact, they periodically submit evidence for review. This evidence is published via the Ethereum Attestation Service (EAS). These claims are then reviewed and approved or rejected by Verifiers.
5. Once evidence is confirmed by Verifiers, Change Code intakes the data provided to assign a quantity of Change Credits to be created and mints them via the project's TBA.
6. With Change Credits minted and available via the TBA, the project's Partners can redeem their IOUs and receive their proportional share of Change Credits.

## Change Credit Ownership

Beyond forming the economic basis for [Mutual Money](../mutual-money/currency-minting.md), Change Credits create a special relationship between Partners and the Good Generators they back. As can be seen in the [schema](../data-schemas/change-credits-spec.md) for Change Credits, contributions to project's are represented as NFTs, meaning that each contribution, regardless of size, still creates a single token. The reasoning behind this decision is, at least in part, a statement of values from Change Code that all contributions matter and should be recognized.

When it comes to the rights conferred to Change Credit holders (Partners), each project's Good Generator is required to specify. They can choose to select and calibrate any (or all) of the following.

##### Voting Power
Good Generators can use Change Credits to include their Partners in decision making processes. These can be small decisions or large decisions, implemented on a one-time or ongoing basis. Additionally, Good Generators can select how to allocate voting power. Each NFT holder can be given a single vote or alternatively the `Balance` can be used so that Partners representing larger economic interest are given larger influence.

##### Exclusive Access
It is not uncommon for organizations producing positive externalities host events, whether social, cultural, or academic, where attendance is in high demand. Change Credits can be used to grant access to these events.

##### Credit Retirement
Certain Good Generators may be social enterprises, capable of producing both profit and positive externalities, or may be engaged in various forms of blended finance. In either case, there will be Good Generators who may be both capable of and interested in offering an economic incentive to further entice Partners to support their positive work. One means to realize this alignment is through Change Credit [retirement](./cc-retirement.md).