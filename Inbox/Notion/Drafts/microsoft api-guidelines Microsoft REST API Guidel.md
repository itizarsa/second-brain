# microsoft/api-guidelines: Microsoft REST API Guidelines

Source: Notes
Status: Unprocessed
URL: https://github.com/microsoft/api-guidelines

[https://opengraph.githubassets.com/fbb7e5e91f2c4785aa0970a199d9553850543cf6ea11900bd5e6ec71d6afed54/microsoft/api-guidelines](https://opengraph.githubassets.com/fbb7e5e91f2c4785aa0970a199d9553850543cf6ea11900bd5e6ec71d6afed54/microsoft/api-guidelines)

---

[api-guidelines](microsoft%20api-guidelines%20Microsoft%20REST%20API%20Guidel%20c24bdb3c32b44eaca215eb8fb111dca1/api-guidelines)

# Microsoft REST API Guidelines

The [Microsoft REST API Guidelines](https://github.com/microsoft/api-guidelines/blob/vNext/Guidelines.md) are Microsoft's internal company-wide REST API design guidelines. Teams at Microsoft typically reference this document when setting API design policy. They may additionally create documents specific to their team, adding further guidance or making adjustments as appropriate to their circumstances.

We publish these guidelines here with the aim of fostering dialogue and learning in the API community at large. We further hope that these guidelines may encourage other organizations to create guidelines that are appropriate for them and in turn, if they are able, to publish theirs.

### Additional guidance for Azure service teams

Azure service teams should reference the companion documents, [Azure REST API Guidelines](https://github.com/microsoft/api-guidelines/blob/vNext/azure/Guidelines.md) and [Considerations for Service Design](https://github.com/microsoft/api-guidelines/blob/vNext/azure/ConsiderationsForServiceDesign.md), when building or modifying their services. These documents provide a refined set of guidance targeted specifically for Azure services. For more information please refer to the [README](https://github.com/microsoft/api-guidelines/blob/vNext/azure/README.md) in the Azure folder.

[microsoft%20api-guidelines%20Microsoft%20REST%20API%20Guidel%20c24bdb3c32b44eaca215eb8fb111dca1/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4c6963656e73652d43432532304259253230342e302d6c69676874677265792e737667](microsoft%20api-guidelines%20Microsoft%20REST%20API%20Guidel%20c24bdb3c32b44eaca215eb8fb111dca1/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4c6963656e73652d43432532304259253230342e302d6c69676874677265792e737667)

## Code of Conduct

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## This repository

This repository contains a collection of documents and related materials supporting the overall Microsoft REST API Guidelines initiative. To contribute to this repository, please see the [contribution guidelines](https://github.com/microsoft/api-guidelines/blob/vNext/CONTRIBUTING.md).

Service providers are unclear if they should return 404s when collection searches have no results. Per the advice in the issue 217 thread the recommendation is to NOT return a 404 in these cases and instead maintain consistency in their response and signifying no results as *value* containing an empty array.

"We would always say that should return a 200 with an empty collection. The call succeeded, the collection exists. There's just nothing in it.

Given we always follow the convention of having the array itself be a 'value' property on a top-level object representing the collection itself, there's also the ability to return collection metadata that is valid regardless of whether there is anything in the collection, e.g. MaxItems." -- Gareth Jones