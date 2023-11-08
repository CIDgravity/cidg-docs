---
title: "Deal filter return codes"
description: "When a proposal is analysed by the CIDgravity deal filter, the response can lead to multiple codes."
lead: "When a proposal is analysed by the CIDgravity deal filter, the response can lead to multiple codes."
draft: false
images: []
menu:
    connector:
        parent: "connector-troubleshooting"
        identifier: "connector-error-codes"
weight: 100
toc: true
---

This section will explain all available return codes to help you understand and find the origin of a problem
We will only address the case where the proposal is rejected.

# Available error codes

|Code                       | Explanation |
|---------------------------|-------------|
|SERVICE_UNAVAILABLE        | You should try to send your deal later, or contact the provider |
|INVALID_CLIENT_ADDR        | The client address provided in the proposal has invalid format |
|CLIENT_NOT_AUTHORIZED      | The client address provided isn't authorized to send deal to this provider |
|BUSY                       | The provider to which you are trying to send a deal is currently busy (hourly limits reached ...) |
|START_EPOCH_TOO_EARLY      | The start epoch of the deal sent is too close to now, (refer to the minimum required start epoch in the response) |
|DEAL_TYPE_NOT_ACCEPTED     | This type of deal is not accepted by the provider |
|PRICE_TOO_LOW              | This type of deal is accepted by the provider, but the price offered is too low (refer to the minimum required price in the response) |