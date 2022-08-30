---
title: Plan for Microsoft Teams Rooms
ms.author: dstrome
author: dstrome
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.assetid: b4e0ad1e-12e5-4130-aec1-d8c9cd3a5965
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Teams_ITAdmin_Rooms
description: This article explains the relevant planning considerations for deploying Microsoft Teams Rooms, the next generation of Skype Room Systems.
---

# Plan Microsoft Teams Rooms

This article introduces an end-to-end approach to planning, delivering, and operating Microsoft Teams Rooms as part of your overall meeting and conference room strategy.

You'll find planning information below covering the recommended approach and key decisions that you need to make, with links to supporting technical information. We recommend that you review the Plan, Deploy, and Manage sections even if you're already fully deployed.

## Overview of Microsoft Teams Rooms

Microsoft Teams Rooms provides a complete meeting experience that brings HD video, audio, and content sharing to meetings of all sizes, from small huddle areas to large conference rooms.

![A user taps a Teams Rooms console, with a display in the background.](../media/room-systems-image1.jpg "A user taps a Teams Rooms console, with a display in the background")
[Microsoft Teams Rooms help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2) is a great resource to find out more about Microsoft Teams Rooms and how it can add value as part of your deployment.

## Microsoft Teams Rooms components

Microsoft Teams Rooms includes the following key components to deliver a great user experience:

- Touchscreen console
- Compute module
- Microsoft Teams Rooms application
- Peripheral devices (camera, microphone, speaker)
- External screens (maximum of two)
- HDMI input

You can procure these components as preinstalled bundles from a number of vendors, or you can purchase the supported components individually by following the [requirements documented in this article](requirements.md).

## Teams Rooms licensing

Each meeting room device, such as a Teams Rooms console, Surface Hub, and Teams panel, needs a Teams Rooms license. Teams provides two licenses for Teams Rooms: Microsoft Teams Rooms Pro and Microsoft Teams Rooms Basic.

Microsoft Teams Rooms Pro is great for organizations that have 25 or more meeting room devices or who want the most comprehensive meeting and device management experiences. Hybrid Teams meetings become more immersive with features like Front row, Content camera, AI-powered noise suppression, and other features available with Microsoft Teams Rooms Pro. Teams Rooms admins can centrally manage all their certified Teams Rooms devices from the Teams admin center from configuring conditional access policies to analyzing rich telemetry about device health and meeting quality.

Microsoft Teams Rooms Basic is available for organizations that only have a few meeting room devices and who only need basic meeting and management functionality. Microsoft Teams Rooms Basic lets you join meetings, share content and live video, join Zoom and Webex meetings with Direct Guest Join, and perform basic device inventory and monitoring in the Teams admin center.

Before you can use a meeting room device, you need to assign a license to it. For more information, see [Microsoft Teams Rooms licenses](rooms-licensing.md).

[!INCLUDE [mtr-user-licensing](../includes/mtr-user-licensing.md)]

| &nbsp;   |  &nbsp;   |
|-----------|------------|
|![decide deployment.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Will you deploy Microsoft Teams Rooms in your organization? </li><li>How will you procure your Microsoft Teams Rooms systems?</li></ul> |
| ![identify activities.](../media/audio_conferencing_image9.png)<br/>Next steps | <ul><li>Identify who will undertake the key activities throughout your deployment.</li><li>Review the meeting rooms you have (and plan to set up) to understand where you want to deploy Microsoft Teams Rooms and the peripheral devices that would be appropriate for the room size.</li></ul> |
| | |

## Identify who will undertake the key activities throughout your deployment

Use the approach illustrated below to guide you through your deployment, and customize the sample outputs provided as needed for your organization.

Begin with understanding what conference rooms you have and envisioning what would work best for you in the future, then move through selecting and procuring the equipment you need, readying your sites, configuring and deploying your service, managing change and user adoption, and developing operations and maintenance procedures.

![Begin with understanding what you have and envisioning what would work best for you, then move through selecting and procuring the equipment you need, readying your sites, configuring and deploying your service, managing change and user adoption, and developing operations and maintenance procedures.](../media/room-systems-image2.png "Begin with understanding what you have and envisioning what would work best for you, then move through selecting and procuring the equipment you need, readying your sites, configuring and deploying your service, managing change and user adoption, and developing operations and maintenance procedures.")

You might need to coordinate these activities across several teams. We provide a high-level view of the main activities that you should cover, and also suggestions for the teams who are typically involved in deploying and managing conference room systems, to help you decide who you need to work with.

| Task                       | Who might undertake the task           | Assigned to | Links to this content |
|----------------------------|----------------------------------------|-------------|-----------------------|
| Inventory rooms            | Facilities / AV team / IT Project Team |             | [Room inventory and capability planning](#room-inventory-and-capability-planning) |
| Plan capabilities          | IT Project Team                        |             | [Room inventory and capability planning](#room-inventory-and-capability-planning) |
| Device selection           | IT Project Team / AV Team              |             | [Device selection](#device-selection) |
| Procurement                | IT Project Team / AV Team              |             | [Procurement](#procurement) |
| Site readiness             | Facilities / AV team / IT Project Team |             | [Site readiness](rooms-deploy.md#site-readiness) |
| Service readiness          | IT Project Team                        |             | [Service readiness](rooms-deploy.md#service-readiness) |
| Configuration              | IT Project Team                        |             | [Configuration and deployment](rooms-deploy.md#configuration-and-deployment) |
| Deployment                 | Facilities / AV team / IT Project Team |             | [Deployment checklist](console.md#microsoft-teams-rooms-deployment-checklist) |
| Adoption                   | Facilities / AV team / IT Project Team |             | [Adoption](#plan-for-adoption-and-change-management) |
| Maintenance and operations | AV team / IT Project Team              |             | [Management overview](rooms-manage.md) |

## Room inventory and capability planning

The first step is to inventory your organization's existing meeting spaces and conference rooms to understand their environment, room size, layout, and purpose. You can then identify the capabilities you want each room to have such as intelligent cameras, whiteboarding, content camera, etc.

After you create an inventory of the equipment and capabilities in each existing room, your requirements for that room feed into your device selection planning to create a rich conferencing solution. The modalities (audio, video) needed for each room—in addition to room size and purpose—all play an important role in deciding which solution is most appropriate for each room.

As part of your discovery, it's key to consider room acoustics and layout. For example, check that the chairs in the room won't block the camera view. Verify that the room doesn't have excessive echo or noisy air conditioning, and that it does have sufficient power for the screens and Microsoft Teams Rooms. There are many factors to consider that your audio-visual (AV) team or partner will be able to advise on.

| &nbsp;   | &nbsp;    |
|-----------|------------|
| ![deplyment rooms.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Review the rooms in scope, and define Microsoft Teams Rooms configurations for them.</li></ul>|

_Sample meeting/conference room inventory_

| Site      | Room name | Room type | Number of people | In scope? | Current room capabilities           | Future room capabilities |
|-----------|-----------|-----------|------------------|-----------|-------------------------------------|--------------------------|
| London HQ | Curie     | Medium    | 6&ndash;12       | Yes       | Speakerphone                        | 1 screen, audio and video plus presentation<br>PSTN Access |
| Sydney HQ | Hill      | Large     | 12&ndash;16      | Yes       | Legacy AV unit, 1 screen and camera | 2 screens, audio and video plus presentation<br>PSTN Access |

## Device selection

Evaluate which Microsoft Teams Rooms solution is the most suitable for each room based on the future capabilities you want for the room. Decide which AV peripheral devices are the best fit, depending on room size and layout.

For guidance for the type of system and peripheral devices by room type and size, see the [Microsoft Teams Rooms requirements](requirements.md) article.

Based on the vendor you prefer, use the information provided in the requirements article to define your Microsoft Teams Rooms and supported peripheral device configuration per room type, and use this as a template for your deployment.

**Pro Tip** – Some room types might not be applicable for your deployment.

| &nbsp; | &nbsp; |
|---|---|
| ![rooms in scope.](../media/audio_conferencing_image7.png) <br/>Decision points | <ul><li>From your inventory, which types of rooms are in scope for your deployment?</li><li>Which systems will you deploy for each room type?</li></ul> |
| ![gather material.](../media/audio_conferencing_image9.png)<br/>Next steps | <ul><li>Start to gather key operational material for your chosen systems, and engage your procurement team.</li></ul> |

_Sample Microsoft Teams Rooms deployment template for your organization_

| Room type/size     | Number of people | Microsoft Teams Rooms system | Peripheral devices | Display(s)      |
|--------------------|------------------|------------------------------|--------------------|-----------------|
| Focus 10' by 9'    | 2&ndash;4        |                              |                    |                 |
| Small 16' by 16'   | 4&ndash;6        |                              |                    |                 |
| Medium 18' by 20'  | 6&ndash;12       |                              |                    |                 |
| Large 15' by 32'   | 12&ndash;16      |                              |                    |                 |

**Pro Tip –** Now is a great time to start gathering information about the Microsoft Teams Rooms solution you've chosen.

## Procurement

You can procure your chosen system as a bundle or an integrated solution via device partners.

You can acquire Microsoft Teams Rooms from a number of partners who are listed in the [requirements article](requirements.md). Please visit the partners' websites to learn more about these solutions and procurement options.

Depending on your deployment scale and approach, you might decide to have the Microsoft Teams Rooms and supported peripheral devices shipped to a central location for initial configuration and assignment. This might be a good approach for a staged rollout across many sites. Or, you might choose to ship the bundles directly to your sites.

| &nbsp; | &nbsp; |
|---|---|
| ![ship components.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Will you ship the components directly to a site or to a staging facility?</li><li>Who will manage the staging facility (if you decide to use one)?</li></ul> |
| ![plan operations.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Plan for operations.</li><li>Plan for adoption and change management.</li></ul> |

## Plan for operations

Your organization must execute monitoring, administration, and management tasks on an ongoing basis, and it's key to agree who will undertake these tasks early in your deployment.

Many organizations have an AV team or partner who manages their conference rooms and devices. Or you can have Microsoft help manage Teams Rooms by leveraging Microsoft Teams Rooms Premium. Decide who will manage the Microsoft Teams Rooms devices going forward to monitor performance as well as deploy software updates and hotfixes.

Consider which helpdesk queue you'll route Microsoft Teams Rooms-related calls to, and provide an FAQ to the helpdesk team so they can better understand how to use Microsoft Teams Rooms and the key troubleshooting steps they can take. A good starting point for this FAQ is the [user help](https://support.microsoft.com/office/microsoft-teams-rooms-help-e667f40e-5aab-40c1-bd68-611fe0002ba2) and [Known issues](known-issues.md).

| &nbsp; | &nbsp; |
|---|---|
| ![choose manager.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide who will manage Microsoft Teams Rooms.</li><li>Decide which helpdesk queue to route Microsoft Teams Rooms–related calls to.</li></ul> |
| ![prepare host accounts.](../media/audio_conferencing_image9.png)<br/>Next steps |<ul><li>Prepare to host accounts.</li></ul> |

## Plan for adoption and change management

Microsoft Teams Rooms systems introduce new capabilities to your users. It's important that you recognize that this will be a change for your users, and you should ensure your internal marketing campaign identifies the benefits the new system will have for your users and the key talking points leads can use to discuss with their teams.

Consider scheduling show-and-tell events and poster drops at each site to inform your users of the new capabilities. You might also create in-room "quick start guides." Consider finding a meetings champion at each site who can help others get up to speed and start using the devices.
