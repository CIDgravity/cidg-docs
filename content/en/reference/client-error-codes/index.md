---
title: "Error codes"
description: "This section contains reference information for the CIDgravity services and API."
draft: false
images: []
menu:
    reference:
        parent: "reference-client-error-codes"
        identifier: "reference-client-error-codes-list"
weight: 100
toc: true
---

In this section, we will provide a comprehensive overview of all available return codes, specifically focusing on cases where a proposal is rejected. 
This information will aid in understanding and pinpointing the root causes of rejection issues.

# Available error codes

|Code                       | Explanation |
|---------------------------|-------------|
|SERVICE_UNAVAILABLE        | You should try to send your deal later, or contact the provider |
|INVALID_CLIENT_ADDR        | The client address provided in the proposal has an invalid format |
|CLIENT_NOT_AUTHORIZED      | The client address provided isn't authorized to send a deal to this provider |
|BUSY                       | The provider you are attempting to send a deal to is currently busy, possibly having reached hourly limits, etc. |
|START_EPOCH_TOO_EARLY      | The start epoch of the deal sent is too close to the current chain epoch. Please refer to the minimum required in the response |
|DEAL_TYPE_NOT_ACCEPTED     | The provider does not accept this type of deal |
|PRICE_TOO_LOW              | The provider accepts this type of deal, but the price offered is too low. Refer to the minimum required price in the response |