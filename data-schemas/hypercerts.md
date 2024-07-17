---
label: Hypercerts
order: -1
---

Change Code leverages the Hypercerts protocol developed from the ERC1155 token standard for semi-fungible tokens. While adhering to the requirements of the standard, Change Code modifies *how* some of the schema fields are used, adapting them to our theory of change and implementation needs.

## ERC1155 Fields

`Name` | CC Hypercert | \{Good Generator\} \{Index\}
:   The Hypercert name mirrors the name used for a project's IOUs. The concept of an index is again used to support single organizations implementing multiple, distinct impact initiatives.   

`Description`
:   A description, not exceeding 200 characters, of the work to be done by the project.

`Image`
:   While the image field is required by the Hypercerts standard, we do not believe a single immutable image to be valuable for the purposes of veracious impact validation. To satisfy this requirement, the Changescape backend will automatically generate and provide an image to satisfy the requirement.

## Hypercert Dimensions

`work_scope`
:   A list of tasks to be done by the project. In economic development parlance, this is a list of *outputs*--e.g. # of solar panels installed, kilos of supplies, $ of direct aid, # of medicine doses.

`work_timeframe`
:   The time period during which the project work will be carried out. In line with the Hypercerts standard, this is represented as an ordered pair of UTC timestamps.

`impact_scope`
:   Inside the Changescape `impact scope` is used to refer thematically to projects by category. For example, the [UN Sustainable Development Goals (SDGs)](https://sdgs.un.org/goals) or the [Ecological Benefits Framework (EBF)](https://ebfcommons.org/lex-icons/). Because the Hypercerts data is only aspirational, it would be premature to immutably publish indicators, which are instead reserved to be published only once verified inside Change Credits.

`impact_timeframe`
:   The time period during which impact *outcomes* will be measured and calculated. For Hypercerts inside the Changescape, the start time is set equal to the start time for the `work_timeframe` while the end time is set for the end of the work period plus five (5) years. Again this data is represented as an ordered pair of UTC timestamps.

`contributors`
:   A list of participants (organizations) that are contributing to the work done in the project. Each element in the list is composed of an on-chain address, a name, and a weight. The purpose of the weight is to signal relative contribution and may optionally be used to weight distributions among contributors.

`rights`
:   As of version 1.0 of the Hypercerts standard, this value can only be set to *public display*. As this is a required field, Change Code applies the default value but does not otherwise use this information.

`hidden_properties`
:   In development

## Sample Hypercert Dimensions

```json
"hypercert": {
    "work_scope": {
        "name": "Work Scope",
        "value": ["sustainable land management"],
        "excludes": [],
        "display_value": "sustainable land management"
    },
    "impact_scope": {
        "name": "Impact Scope",
        "value": [SDG 13], [SDG 15]
        "excludes": [],
        "display_value": "SDG 13 - Climate Action", "SDG 15 - Life on Land"
    },    
    "work_timeframe": {
        "name": "Work Timeframe",
        "value": [1704096000, 1735711200],
        "display_value": "2024-01-01 -> 2024-12-31"
    },
    "impact_timeframe": {
        "name": "Impact Timeframe",
        "value": [1704096000, 1893477600],
        "display_value": "2024-01-01 -> 2030-12-31"
    },
    "contributors": {
        "name": "Contributors",
        "value": ["0xa1fa1fa000000000000000000000000000000000", "Project Developer", 0.9], ["0xa1fa1fa000000000000000000000000000000000", "Carbon Standards Body", 0.1]
        "display_value": "Project Developer", "Carbon Standards Body"
    },
    "rights": {
        "name": "Rights",
        "value": ["Public Display"],
        "display_value": "Public Display"
    }
}
```

Additional details on the Hypercerts implementation can be found in the documentation [here](https://hypercerts.org/docs/implementation/metadata).
