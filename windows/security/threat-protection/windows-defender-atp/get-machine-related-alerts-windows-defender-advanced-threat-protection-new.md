---
title: Get machine related alerts API
description: Retrieves a collection of alerts related to a given machine ID.
keywords: apis, graph api, supported apis, get, machines, related, alerts
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
ms.date: 12/08/2017
---

# Get machine related alerts  API

[!include[Prerelease information](prerelease.md)]

**Applies to:**

- Windows Defender Advanced Threat Protection (Windows Defender ATP)
Retrieves a collection of alerts related to a given machine ID.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Windows Defender ATP APIs](apis-intro.md)

Permission type |	Permission	|	Permission display name
:---|:---|:---
Application |	Alert.Read.All |	'Read all alerts'
Application |	Alert.ReadWrite.All |	'Read and write all alerts'
Delegated (work or school account) | Alert.Read | 'Read alerts'
Delegated (work or school account) | Alert.ReadWrite | 'Read and write alerts'

>[!Note]
> When obtaining a token using user credentials:
>- The user needs to have at least the following role permission: 'View Data' (See [Create and manage roles](user-roles-windows-defender-advanced-threat-protection.md) for more information)
>- User needs to have access to the machine, based on machine group settings (See [Create and manage machine groups](machine-groups-windows-defender-advanced-threat-protection.md) for more information)

## HTTP request
```
GET /api/machines/{id}/alerts
```

## Request headers

Name | Type | Description
:---|:---|:---
Authorization | String | Bearer {token}. **Required**.


## Request body
Empty

## Response
If successful and machine and alert exists - 200 OK with list of [alert](alerts-windows-defender-advanced-threat-protection-new.md) entities in the body. If no machine or no alerts found - 404 Not Found.


## Example

**Request**

Here is an example of the request.

[!include[Improve request performance](improverequestperformance-new.md)]


```
GET https://api.securitycenter.windows.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/alerts
```

**Response**

Here is an example of the response.


```
HTTP/1.1 200 OK
Content-type: application/json
{    
    "@odata.context": "https://api.securitycenter.windows.com/api/$metadata#Alerts",
    "value": [
        {
            "id": "636692391408655573_2010598859",
            "severity": "Low",
            "status": "New",
            "description": "test alert",
            "recommendedAction": "do this and that",
            "alertCreationTime": "2018-08-07T11:45:40.0199932Z",
            "category": "None",
            "title": "test alert",
            "threatFamilyName": null,
            "detectionSource": "CustomerTI",
            "classification": null,
            "determination": null,
            "assignedTo": null,
            "resolvedTime": null,
            "lastEventTime": "2018-08-03T16:45:21.7115182Z",
            "firstEventTime": "2018-08-03T16:45:21.7115182Z",
            "actorName": null,
            "machineId": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07"
        }
    ]
}
```
