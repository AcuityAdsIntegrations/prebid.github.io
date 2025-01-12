---
layout: userid
title: Intent IQ ID
description: Intent IQ ID User ID sub-module
useridmodule: intentIqIdSystem
bidRequestUserId: intentiqid
eidsource: intentiq.com
example: '"1111"'
---

# Intent IQ Universal ID module

By leveraging the Intent IQ identity graph, our module helps publishers, SSPs, and DSPs overcome the challenges of monetizing cookie-less inventory and preparing for a future without 3rd-party cookies. Our solution implements 1st-party data clustering and provides Intent IQ person IDs with over 90% coverage and unmatched accuracy in supported countries while remaining privacy-friendly and CCPA compliant. This results in increased CPMs, higher fill rates, and, ultimately, lifting overall revenue

# All you need is a few basic steps to start using our solution

## Registration

Navigate to [our portal](https://www.intentiq.com/) and contact our team for partner ID.
check our [documentation](https://pbmodule.documents.intentiq.com/) to get more information about our solution and how utilze it's full potential

## Integration

```bash
gulp build –modules=intentIqIdSystem
```

We recommend including the Intent IQ Analytics adapter module for improved visibility

## Configuration

### Parameters

Please find below list of parameters that could be used in configuring Intent IQ Universal ID module

{: .table .table-bordered .table-striped }
| Param under userSync.userIds[] | Scope    | Type     | Description                                                                                                                                                                                                                                                                                                                               | Example                                       |
| ------------------------------ | -------- |----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------|
| name                           | Required | String   | The name of this module: "intentIqId"                                                                                                                                                                                                                                                                                                     | `"intentIqId"`                                |
| params                         | Required | Object   | Details for IntentIqId initialization.                                                                                                                                                                                                                                                                                                    |                                               |
| params.partner                 | Required | Number   | This is the partner ID value obtained from registering with IntentIQ.                                                                                                                                                                                                                                                                     | `1177538`                                     |
| params.pcid                    | Optional | String   | This is the partner cookie ID, it is a dynamic value attached to the request.                                                                                                                                                                                                                                                             | `"g3hC52b"`                                   |
| params.pai                     | Optional | String   | This is the partner customer ID / advertiser ID, it is a dynamic value attached to the request.                                                                                                                                                                                                                                           | `"advertiser1"`                               |
| params.callback                | Required | Function | This is a callback which is trigered with data and AB group                                                                                                                                                                                                                                                                               | `(data, group) => console.log({ data, group })` |
| params.timeoutInMillis         | Optional | Number   | This is the timeout in milliseconds, which defines the maximum duration before the callback is triggered. The default value is 500.                                                                                                                                                                                                       | `450`                                         |
| params.browserBlackList        | Optional |  String  | This is the name of a browser that can be added to a blacklist.                                                                                                                                                                                                                                                                           | `"chrome"`                                    |
| params.manualWinReportEnabled  | Optional | Boolean  | This variable determines whether the bidWon event is triggered automatically. If set to false, the event will occur automatically, and manual reporting with reportExternalWin will be disabled. If set to true, the event will not occur automatically, allowing manual reporting through reportExternalWin. The default value is false. | `true`|
| params.domainName              | Optional | String   | Specifies the domain of the page in which the IntentIQ object is currently running and serving the impression. This domain will be used later in the revenue reporting breakdown by domain. For example, cnn.com. It identifies the primary source of requests to the IntentIQ servers, even within nested web pages.                     | `"currentDomain.com"`                         |

### Configuration example

```javascript
pbjs.setConfig({
    userSync: {
        userIds: [{
            name: "intentIqId",
            params: {
                partner: 123456,     // valid partner id
                timeoutInMillis: 500,
                browserBlackList: "chrome",
                callback: (data, group) => window.pbjs.requestBids(),
                manualWinReportEnabled: true,
                domainName: "currentDomain.com"
            },
            storage: {
                type: "html5",
                name: "intentIqId",    // set localstorage with this name
                expires: 0,
                refreshInSeconds: 0
            }
        }]
    }
});
```