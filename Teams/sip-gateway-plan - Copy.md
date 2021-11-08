---
title: Configure SIP Gateway
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 09/30/2021
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
ms.reviewer: crowe
search.appverid: MET150
f1.keywords:
- NOCSH
- ms.teamsadmincenter.directrouting.overview
description: Learn how to configure SIP Gateway.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Configure SIP Gateway

This article explains how to configure SIP Gateway so you can get the most out of it. To learn more about SIP Gateway, see [Plan for SIP Gateway](/sip-gateway-plan/)

## Verify that SIP Gateway is available for your tenant

1. Log in to the [Teams admin center](https://admin-teams.microsoft.net/).

2. At the left, select **Teams devices** and see if the **SIP devices** tab is visible. If it is, the SIP Gateway service is enabled for your tenant.

## Configure SIP Gateway provisioning server for each SIP device

1. Reset each SIP device you want to use with SIP Gateway to its factory default settings. To learn how to do that, see your device manufacturer’s instructions.

2. For each device, configure the following SIP Gateway provisioning server URL:
    - EMEA: [http://emea.ipp.sdg.teams.microsoft.com](http://emea.ipp.sdg.teams.microsoft.com)
    - Americas: [http://noam.ipp.sdg.teams.microsoft.com](http://noam.ipp.sdg.teams.microsoft.com)

> [!NOTE]
> - Only compatible devices can be onboarded to SIP Gateway. Users who work from home must manually configure the provisioning server URL above into their SIP device through its web browser. 
> - Cisco IP phones must be flashed to multiplatform firmware before they can be onboarded. Read this guide to learn how:|[Cisco firmware conversion guide](https://www.cisco.com/c/en/us/products/collateral/collaboration-endpoints/unified-ip-phone-7800-series/guide-c07-742786.html)| 
> - Some Yealink models also require a license to migrate from Skype for Business firmware to SIP.

## Enroll SIP devices

A Teams administrator can provision SIP devices in the Teams admin center either individually or in batches by uploading a list of devices to be provisioned. [How?] The administrator can generate a one-time password for each onboarded device. [How?] A technician can enroll an onboarded device by dialing a feature code followed by the one-time password. For example:,if the feature code for enrollment is *55*, and the one-time password is 123456, the technician would dial *55*123456 to enroll the device. [We need step-by-step details here.] Once the device is successfully enrolled,t shows up in Teams admin Center inventory and is enabled for remote sign-in.

> [!NOTE]
> A SIP device must be onboarded before it can be enrolled.

## Other considerations

SIP Gateway authenticates SIP Phones with Azure Active Directory, so if your tenant uses conditional access for devices in the corporate network, then it should exclude the following IP addresses: 
- North America:
    - East US: 52.170.38.140
    - West US: 40.112.144.212
-   EMEA region:
    - North EU: 40.112.71.149
    - North EU: 40.112.71.149

For more information, see [IP address ranges](https://docs.microsoft.com/en-in/azure/active-directory/conditional-access/location-condition#ip-address-ranges)

## View and monitor your SIP devices

Teams administrators can view and monitor their SIP device inventory in the Teams admin center after the devices' users sign in at least once. Here's how:

1. Log in to the [Teams admin center](https://admin-teams.microsoft.net/).

2. Select **Teams devices** -> **SIP devices**. All signed-in SIP devices are listed on the right.

## Sync policy changes to SIP devices to enforce policies

User details and policies will be fetched to SIP devices when users sign in. Any policy changes thereafter for signed-in users will be synced to the device within one hour. Sync will be triggered with registration refresh. [What does this mean?]

## Restart a SIP device

1. Log in to the [Teams admin center](https://admin-teams.microsoft.net/).

2. Select **Teams devices** -> **SIP devices**. 

3. Select the SIP device you want to restart and ?

## Report problems to Microsoft

- To report problems, contact [Microsoft Support](https://support.microsoft.com)