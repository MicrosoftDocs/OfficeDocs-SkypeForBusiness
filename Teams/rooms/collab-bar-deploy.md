---
title: "Deploy collaboration bars for Microsoft Teams"
ms.author: mitressl
author: flinchbot
manager: ericwe
audience: ITPro
ms.reviewer: payurevi
ms.topic: quickstart
ms.service: msteams
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection: 
  - M365-collaboration
ms.custom: 
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
description: "Read this article to learn about deploying collaboration bars for Microsoft Teams."
---

# Deployment overview

Deployment of collaboration bars for Microsoft Teams essentially breaks down into phases:

- Confirming that your deployment locations (rooms) meet the deployment dependencies
- Creating resource accounts and assigning them to the devices ([see Create a resource account using the Microsoft 365 admin center](resource-account-ui.md)). Note that you can also use a properly licensed end user account to sign in to collaboration bars.
- Setting up collaboration bars in rooms and connecting the peripheral devices you need (see the vendor's documentation for your collaboration bars)

## Site readiness 

While the ordered devices are being delivered to your organization, work with your networking, facilities, and AV teams to make sure that deployment dependencies are met and each site and room is ready in terms of power, networking, and display. We recommend touch-enabled displays for collaboration bars. In addition, make sure the physical installation requirements are met. For physical installation considerations, please visit the vendor’s site and leverage the experience of your AV team when installing and mounting screens and running cabling.

**Pro Tip** - If you intend to use proxy servers to provide access to Microsoft Teams, first [review this article](../proxy-servers-for-skype-for-business-online.md). Note that we recommend bypassing proxy servers altogether. Microsoft Teams traffic is already encrypted, so proxy servers don’t make it more secure. As part of your wider deployment, we recommend that you follow the guidance in [Prepare your network for Teams](../prepare-network.md) for bandwidth planning and assessing your network’s suitability for real-time traffic.

|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Confirm that your sites meet the site readiness requirements for collaboration bars for Microsoft Teams.</li><li>Confirm that you've provided sufficient bandwidth for each site.</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your collaboration bar deployment and configuration.</li></ul>| 

## Service readiness

To prepare for your collaboration bars for Microsoft Teams deployment, do the following key tasks:

-   Decide if  collaboration bars for Microsoft Teams Rooms will use resource accounts, end-user accounts, or a mixture of both.
-   Prepare an Azure Active Directory group to hold your resource accounts to simplify assignment of Intune management policies.

### Define collaboration bars for Microsoft Teams resource account 

Depending on the collaboration scenarios that you’ve decided to enable with your collaboration bars for Microsoft Teams deployment, you’ll need to determine the features and capabilities that you assign to each resource account that you enable.

| **Scenario** | **Description** | **Collaboration bars for Microsoft Teams resource account feature** |
|---------- |------------- | --- |
| Interactive meetings            | Using voice, video, and screen sharing; making the collaboration bars for Microsoft Teams a bookable resource                     | Enabled for Exchange (Resource Mailbox) |
| Dial-in conferencing            | Enable meetings started *directly* from the collaboration bars for Microsoft Teams console with dial-in conferencing coordinates | Enabled for Audio Conferencing                                          |
| Outbound/inbound PSTN Calling | Enable the collaboration bars for Microsoft Teams to make and receive PSTN calls                                         | Enabled for Phone System                                                |

For more information about collaboration bars for Microsoft Teams resource accounts, see [Create a resource account using the Microsoft 365 admin center](resource-account-ui.md).


|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide which scenarios you’ll support, and identify licensing requirements for your collaboration bars for Microsoft Teams resource accounts.</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Prepare resource accounts.</li></ul>| 


## Configuration and deployment 

Planning for configuration and deployment covers the following key areas:

-   Resource account provisioning
-   Device deployment
-   Collaboration bars for Microsdoft Teams application and peripheral device configuration
-   Testing
-   Asset management

### Account provisioning 

Collaboration bars for Microsoft Teams can use a dedicated and unique resource account, or a standard end-user account that must be enabled for both Microsoft Teams and Exchange. If using a dedicated resource account, calendar processing must be configured in Exchange so that the device can automatically accept incoming meeting requests. For more information about creating dedicated resource accounts, see [Create a resource account using the Microsoft 365 admin center](resource-account-ui.md). 

**Pro Tip** – Make the display names for these accounts descriptive and easy to understand. These are the names that users will see when searching for and adding collaboration bars for Microsoft Teams to meetings. You could use a convention like *Site*-*Room Name*(*Max Room Capacity*), so for example Curie—a 12-person conference room in London—might have the display name LON-CURIE(12). 

|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide the naming convention for your dedicated collaboration bars for Microsoft Teams resource accounts.</li><li>Decide whether you’ll create individual accounts or use bulk-provisioning scripts.</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment.</li></ul>| 

### Collaboration bars for Microsoft Teams application configuration

After each collaboration bar for Microsoft Teams has been physically deployed, you’ll need to configure the collaboration bar to assign the resource account and password created earlier. Alternately, an end-use can sign in using their personal credentials.

**Pro Tip** - Each Microsoft Teams Rooms must have a valid and unique machine name on your network. Many monitoring and alerting systems display the machine name as a key identifier, so it's important to develop a naming convention for Microsoft Teams Rooms deployments that allows support personnel to easily locate the Microsoft Teams Rooms that has been flagged as requiring an action. An example might be using a pattern of MTR-*Site*-*Room Name* (MTR-LON-CURIE). 


|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide the Microsoft Teams Rooms device-naming convention to be used during your deployment.</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment approach.</li></ul>| 


### Device deployment

Next, you need to create your plan to ship the devices and their assigned peripheral devices to your rooms, and then proceed to installation and configuration. 


|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide who will manage the site-by-site deployment.</li><li> Identify the resources who will install the Microsoft Teams Rooms devices on site and undertake the configuration and testing.</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start device testing.</li></ul>| 

### Testing

After the collaboration bars for Microsoft Teams has been deployed, you should test it. Check that the expected capabilities are working on the deployed device. We highly recommend that the deployment team verify that the collaboration bars for Microsoft Teams Rooms are appearing in the collaboration bars section under the Devices tab of Microsoft Teams admin center. It's also important that you make a number of test calls and meetings to check quality. 

We recommend that as part of the general Microsoft Teams rollout, you configure building files for Call Quality Dashboard (CQD), monitor quality trends, and engage in the Quality of Experience Review process. For more information, see the [Quality of Experience Review Guide](https://aka.ms/qerguide). 

### Asset management

As part of the deployment, you'll want to update your asset register with the room name, signed-in Microsoft Teams Rooms resource account, and assigned peripheral devices (and which USB ports they use). 



