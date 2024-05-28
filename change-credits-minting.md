# Change Credits

Change Credits are a novel *financial* primitive supporting resource allocation, verification, and tracking of positive externalities (social and environmental impact).

They are the basis and grounding of Change Code's economic engine, providing a real-world tangible link to underpin a new form of beneficial currency.

## Foundation

Before expanding on the architecture and processes involved in Change Credits directly, we should first recap (or introduce) some of the existing open-source tools and standards leveraged here.

### Hypercerts

Hypercerts are on-chain, tokenized claims of positive impact. To be more precise, hypercerts represent *claims* of *work* done toward some beneficial outcome, be that work toward social or environmental impact or the building of a public good.

A complete list of the on-chain token data and off-chain metadata included in a hypercert can be found in the [documentation]().


*Token Standards*
+++ ERC1155
This is Tab 1
+++ ERC20
This is another Tab
+++ ERC6551
+++


```mermaid
sequenceDiagram
    actor Verifier
    actor Good Generator
    create participant hypercert
    Good Generator->>hypercert: mint impact goal
    actor Change Code
    Change Code--xhypercert: review impact goal
    create participant Token Bound Account
    Change Code->>Token Bound Account: deploy account
    actor donor
    loop
        donor->>Token Bound Account: send $
        Token Bound Account->>donor: mint IOU
        Token Bound Account->>Good Generator: remit funding received
    end
    loop
        Good Generator-->Good Generator: implement project
        Good Generator->>hypercert: submit evidence
        Verifier--xhypercert: review evidence
        Change Code--xhypercert: determine quantity
        Change Code->>Token Bound Account: mint Change Credits
    end
    Loop
        donor->>Token Bound Account: return IOUs
        Token Bound Account->>donor: receive Change Credits
    end
```

