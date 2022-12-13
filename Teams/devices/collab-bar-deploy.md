---
title: Deploy Microsoft Teams Rooms on Android
ms.author: dstrome
author: dstrome
manager: serdars
audience: ITPro
ms.reviewer: payurevi
ms.topic: quickstart
ms.service: msteams
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Devices
ms.custom: 
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
description: Read this article to learn about deploying Microsoft Teams Rooms on Android.
---

# Deploy Microsoft Teams Rooms on Android

Deployment of Microsoft Teams Rooms on Android can be broken down into the following phases:

- **Site readiness** Confirm that your deployment locations (rooms) meet the deployment requirements.
- **Service readiness** Create resource accounts and assign them to the devices ([see Create a resource account using the Microsoft 365 admin center](resource-account-ui.md)). While we recommend using a dedicated room license, a properly licensed end user account can also sign in to Teams Rooms on Android.
- **Configuration and deployment** Set up Teams Rooms and connect the peripheral devices you need (see the manufacturer's documentation for details).

To manage Teams Rooms, you need to be a Global admin, Teams Service admin, or Teams Device admin. For more information about admin roles, see [Use Microsoft Teams administrator roles to manage Teams](../using-admin-roles.md).

## Site readiness

While the ordered devices are being delivered to your organization, work with your networking, facilities, and audio-visual teams to make sure that deployment requirements are met and each site and room is ready in terms of power, networking, and display.

Our recommendations for collaboration bar sites are:

- Rooms up to 5 people in size
- Dedicated resource accounts
- Touch-enabled displays
- Ethernet cabling
- Quality of Service (QoS) enabled on the network for Microsoft Teams media

For physical installation considerations, see the manufacturer's documentation and, if you have one, leverage the experience of your audio-visual team before you install and mount screens and run cabling.

> [!TIP]
> Be sure to check out [Prepare your network for Teams](../prepare-network.md) for bandwidth planning and assessing your network’s suitability for real-time traffic.
>
> We don't recommend placing proxy servers between Teams devices and the Internet. For more information about proxy servers and Teams, check out [Proxy servers for Teams](../proxy-servers-for-skype-for-business-online.md).

|&nbsp;|&nbsp;|
|-----------|------------|
| ![An icon depicting decision points.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Confirm that your sites meet the site readiness requirements for collaboration bars for Microsoft Teams.</li><li>Confirm that you've provided sufficient bandwidth for each site.</li></ul>|
| ![An icon depicting next steps.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your collaboration bar deployment and configuration.</li></ul>|

## Service readiness

Before you deploy Teams Rooms, you need to decide if they'll use Microsoft 365 resource accounts, end-user accounts, or a mixture of both. Microsoft 365 resource accounts are mailbox and Teams accounts that are dedicated to specific resources, such as a room, projector, and so on. These resource accounts can automatically respond to meeting invites using rules you define when they're created. Unless Teams Rooms is dedicated to a specific individual for their private use, we recommend setting up a Microsoft 365 resource account for it.

### Using a resource account

If you decide to set up a Microsoft 365 resource account, you'll need to purchase a Meeting Room license for it. The Meeting Room license includes a resource mailbox that enables people in your organization to book the meeting room via Outlook or Teams. The license also enables video and audio conferencing and screen sharing among meeting participants.

If you need to receive or make calls to or from an external telephone number, you may need a Calling Plan or Microsoft 365 Business Voice [add-on license](../teams-add-on-licensing/microsoft-teams-add-on-licensing.md?tabs=small-business). If you have Direct Routing enabled in your organization, you only need the Meeting Room SKU.

When you create a resource account, you can choose whether to let the account automatically accept or decline meeting requests, allow recurring meetings, specify how far in advance people can book the resource, and so on.

[!INCLUDE [m365-teams-resource-account-difference](../includes/m365-teams-resource-account-difference.md)]

For more information about Microsoft 365 resource accounts, see [Create a resource account using the Microsoft 365 admin center](resource-account-ui.md).

|&nbsp;|&nbsp;|
|-----------|------------|
| ![An icon depicting decision points.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide whether you want to make or receive external phone calls and identify licensing requirements for your resource accounts.</li></ul>|
| ![An icon depicting next steps.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Prepare resource accounts.</li></ul>|

## Configuration and deployment

Planning for configuration and deployment covers the following key areas:

- Resource account provisioning
- Device deployment
- Teams Rooms application and peripheral device configuration
- Testing
- Asset management

### Account provisioning

If you plan on using Microsoft 365 resource accounts to let users book collaboration bars, follow the instructions in [Create a resource account using the Microsoft 365 admin center](resource-account-ui.md) to create a Microsoft 365 resource account for each collaboration bar that needs one. This is also where you'll need to add a Meeting Room license to the resource account and, if you want to make or receive calls to or from external phone numbers, a Calling Plan or Business Voice license if your organization is not using Direct Routing.

If you want to assign Teams Rooms to individual users for their private use, you don't need to set up any additional accounts. Users can sign into collaboration bars using their personal accounts.

> [!TIP]
> Make the display names for your Microsoft 365 resource accounts descriptive and easy to understand. These are the names that users will see when searching for and adding Teams Rooms to meetings. You could use a convention like *Site*-*Room Name*(*Max Room Capacity*), so for example Curie, a 4-person meeting room in London, might have the display name LON-CURIE(4).

|&nbsp;|&nbsp;|
|-----------|------------|
| ![An icon depicting decision points.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide the naming convention for your dedicated resource accounts.</li><li>Decide whether you’ll create individual accounts or use bulk-provisioning scripts.</li></ul>|
| ![An icon depicting next steps.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment.</li></ul>|

### Device deployment

Next, you need to create your plan to deliver the devices and their assigned peripheral devices to your rooms, and then proceed with installation and configuration.

|&nbsp;|&nbsp;|
|-----------|------------|
| ![An icon depicting decision points.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide who will manage the site-by-site deployment.</li><li> Identify the resources who will install Teams Rooms on site and undertake the configuration and testing.</li></ul>|
| ![An icon depicting next steps.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start device testing.</li></ul>|

### Testing

After you have deployed Teams Rooms, you should test them. Sign in to Teams Rooms and check that the expected capabilities are working. We highly recommend that you verify that they are appearing in the **Collaboration bars** section under the **Teams Devices** tab of Microsoft Teams admin center. It's also important that you make a number of test calls and meetings to check quality and performance.

We recommend that as part of the general Microsoft Teams rollout, you configure building files for Call Quality Dashboard (CQD), monitor quality trends, and engage in the Quality of Experience Review process. For more information, see the [Quality of Experience Review Guide](../quality-of-experience-review-guide.md).

### Asset management

As part of the deployment, you'll want to update your asset register with the room name, signed-in resource account, and assigned peripheral devices.

## Related topics

[Create resource accounts for rooms and shared Teams devices](../rooms/with-office-365.md)