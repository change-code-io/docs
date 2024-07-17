---
label: Change Credit Retirement
order: -4
---

When a Good Generator can concurrently generate positive impact and traditional revenue, an opportunity emerges to further align interests between themselves and their Partners. These social enterprises may leverage Change Credits to jump-start their work in producing green energy, developing affordable housing, lowering the cost of healthcare or education, or achieving almost any other means of positive change that can also produce revenue.

A more traditional model for these social enterprises would be to offer equity or debt from their organizations where the positive impact is seen and structured as merely an ancillary benefit. The shortcoming of such a model is that there is no economic value ascribed to the impact externality itself, but the cost is still present. Imagine a company that made tables and chairs but could only sell its tables, while being expected to produce and distribute its chairs without payment. Would this company be able to effectively compete for capital against a business that produced and sold only tables without the deadweight of chair production?

The Changescape is different. Inside the Changescape, positive externalities are seen as economic goods in their own right. In support of this paradigm shift, instead of selling equity or debt with *blended returns* (eg. dividends alongside an annual impact report), social enterprises can commit funds to repurchase and retire their Change Credits.

## Retirement Flow

```mermaid
sequenceDiagram
    actor Good Generator
    participant Treasury Account
    actor Partner
    Good Generator->>Treasury Account: fund for retirement
    Partner-->Treasury Account: signal interest in retirement
    Treasury Account->>Partner: distribute funds and update Change Credit
```

The above sequence diagram offers an overview of Change Credit retirement, which is described in greater detail in the following 5 steps:

1. Before any of the above interactions take place, the Good Generator has the option to specify a target or even guarantee an amount of funds that will be used to repurchase and retire its Change Credits. This target can be published as part of deploying the project inside the Changescape or can be disseminated through the organization's usual communication channels.
2. Once funds are available (and after Change Credits have already begun to be distributed), the Good Generator remits funds into the project's Treasury Account.
3. With funds available in the account, the Good Generator must specify how retirement will occur—declaring the price they are willing to pay for each Change Credit and optionally setting a maximum fraction of each Change Credit that may be retired.
4. Partners holding Change Credits then signal themselves as interested in retirement, optionally setting their maximum retirement portion.
5. As Partners signal interest in retirement, the Treasury Account automatically distributes funds and updates the `Balance` and `Retirement` values of participating Change Credits accordingly.
