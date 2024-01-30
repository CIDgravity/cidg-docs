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

As a Filecoin client, you receive unified rejection code when :
 - a deal you are trying to place to a storage provider using CIDgravity is rejected (using boost or any clients)
 - calling our API to verify miner availability
 
In this section, we will provide a comprehensive overview of all available return codes.
These codes will not change overtime and are designed to give to clients the ability to build automation.

# Available error codes

|Code                       | Explanation |
|---------------------------|-------------|
|SERVICE_UNAVAILABLE        | Miner is temporary unavailable, you should retry sending deals later |
|INVALID_CLIENT_ADDR        | The client address provided within the proposal has an invalid format |
|CLIENT_NOT_AUTHORIZED      | The client address provided is not authorized to send a deal to this provider, you should contact the storage provider to be authorized |
|BUSY                       | The storage provider pipeline is currently full, you should try sending deals later |
|START_EPOCH_TOO_EARLY      | The storage provider explicitly asks for more time to seal that deal. Please refer to the minimum time required in the response |
|DEAL_TYPE_NOT_ACCEPTED     | The provider does not accept this type of deal (verified / transport / size / diration / etc... ), either try changing parameters or contact the storage provider |
|PRICE_TOO_LOW              | The provider accepts this type of deal, but the price offered is too low. Refer to the minimum required price in the response |
|PIECE_CID_DUPLICATED       | This provider has already received a deal from your address with the piece CID (API only)|
