---
title: "Deploy collaboration bars for Microsoft Teams"
ms.author: mitressl
author: flinchbot
manager: 
audience: ITPro
ms.reviewer: 
ms.topic: quickstart
ms.service: msteams
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection: 
  - M365-collaboration
ms.custom: 
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
description: "Read this article to learn about deploying Microsoft Teams Rooms."
---

# Deployment overview

Deployment of collaboration bars for Microsoft Teams essentially breaks down into phases:

- Confirming that your deployment locations (rooms) meet the deployment dependencies
- Creating Microsoft Teams and Exchange accounts and assigning them to the devices (see [Configure accounts for Microsoft Teams Rooms](rooms-configure-accounts.md))
- Setting up collaboration bars in rooms and connecting the peripheral devices you need (see the vendor's documentation for your collaboration bars)

## Site readiness 

While the ordered devices are being delivered to your organization, work with your networking, facilities, and AV teams to make sure that deployment dependencies are met and each site and room is ready in terms of power, networking, and display. In addition, make sure the physical installation requirements are met. For physical installation considerations, please visit the vendor’s site and leverage the experience of your AV team when installing and mounting screens and running cabling.

You can find out more about these dependencies in the planning guidance links below:

-   [Check network availability](rooms-prep.md#check-network-availability)
-   [Proxy](rooms-prep.md#proxy)

**Pro Tip** - If you intend to use proxy servers to provide access to Microsoft Teams, first [review this article](../proxy-servers-for-skype-for-business-online.md). Note that we recommend bypassing proxy servers altogether. Microsoft Teams traffic is already encrypted, so proxy servers don’t make it more secure. As part of your wider deployment, we recommend that you follow the guidance in [Prepare your network for Teams](../prepare-network.md) for bandwidth planning and assessing your network’s suitability for real-time traffic.

|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Confirm that your sites meet the key requirements for collaboration bars for Microsoft Teams.</li><li>Confirm that you've provided sufficient bandwidth for each site.</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your collaboration bar deployment and configuration.</li></ul>| 

## Service readiness

To prepare for your collaboration bars for Microsoft Teams deployment, do the following key tasks:

-   Define collaboration bars for Microsoft Teams Rooms resource accounts.
-   Prepare an Azure Active Directory group to hold your resource accounts.

### Define collaboration bars for Microsoft Teams resource account 

Depending on the collaboration scenarios that you’ve decided to enable with your collaboration bars for Microsoft Teams deployment, you’ll need to determine the features and capabilities that you assign to each collaboration bar for Microsoft Teams resource account that you enable.

| **Scenario** | **Description** | **Collaboration bars for Microsoft Teams resource account feature** |
|---------- |------------- | --- |
| Interactive meetings            | Using voice, video, and screen sharing; making the collaboration bars for Microsoft Teams a bookable resource                     | Enabled for Exchange (Resource Mailbox) |
| Dial-in conferencing            | Enable meetings started *directly* from the collaboration bars for Microsoft Teams console with dial-in conferencing coordinates | Enabled for Audio Conferencing                                          |
| Outbound/inbound PSTN Calling | Enable the collaboration bars for Microsoft Teams to make and receive PSTN calls                                         | Enabled for Phone System                                                |

For more information about collabortion bars for Microsoft Teams resource accounts, see [Configure accounts for Microsoft Teams Rooms](rooms-configure-accounts.md).


|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide which scenarios you’ll support, and identify licensing requirements for your collaboration bars for Microsoft Teams resourcee accounts.</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Prepare resource accounts.</li></ul>| 


## Configuration and deployment 

Planning for configuration and deployment covers the following key areas:

-   Resource account provisioning
-   Device deployment
-   Microsoft Teams Rooms application and peripheral device configuration
-   Testing
-   Asset management

### Account provisioning 

Collaboration bars for Microsoft Teams can use a dedicated and unique resource account, or a standard end-user account that must be enabled for both Microsoft Teams and Exchange. If using a dedicated resource account, calendar processing must be configured in Exchange so that the device can automatically accept incoming meeting requests. For more information about creating dedicated resource accounts, see [Configure accounts for Microsoft Teams Rooms](rooms-configure-accounts.md). 

**Pro Tip** – Make the display names for these accounts descriptive and easy to understand. These are the names that users will see when searching for and adding collaboration bars for Microsoft Teams to meetings. Some organizations use the convention *Site*-*Room Name*(*Max Room Capacity*), so for example Curie—a 12-person conference room in London—might have the display name LON-CURIE(12). 

|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide the naming convention for your dedicated collaboration bars for Microsoft Teams resource accounts.</li><li>Decide whether you’ll create individual accounts or use bulk-provisioning scripts.</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment.</li></ul>| 

### Collaboration bars for Microsoft Teams application configuration

After each collaboration bar for Microsoft Teams has been physically deployed, you’ll need to configure the collaboration bar to assign the resource account and password created earlier.
