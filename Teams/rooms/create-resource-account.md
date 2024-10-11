---
title: Create resource accounts for rooms and shared Teams devices
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: sohailta
ms.date: 05/31/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.custom: seo-marvel-apr2020
ms.assetid: f09f4c2a-2608-473a-9a27-f94017d6e9dd
description: Read this article for information on how to create resource accounts for Teams rooms and shared devices. These devices include Microsoft Teams Rooms, Teams panels, and Surface Hub.
---

# Create and configure resource accounts for rooms and shared Teams devices

This article provides steps to create resource accounts for shared spaces and devices, and it includes steps to configure resource accounts for Microsoft Teams Rooms on Windows, Teams Rooms on Android, & Teams panels.

Microsoft 365 resource accounts are mailbox and Teams accounts that are dedicated to specific resources, such as a room or projector. These resource accounts can automatically respond to meeting invites using rules you define when they're created. For example, if you have a common resource such as a conference room, you can set up a resource account for that conference room which will automatically accept or decline meeting invites depending on its calendar availability.

Every resource account is unique to a single Microsoft Teams Rooms installation or Teams device implementation.

[!INCLUDE [mtr-device-config-account-include](../includes/m365-teams-resource-account-difference.md)]

> [!NOTE]
> If using Microsoft Teams panels, the same Teams Rooms resource account signs in to the Teams Rooms device and any associated Teams panels.

## Before you begin

### Requirements

Depending on your environment, you may need one or more roles to create resource accounts.

| Environment | Required Roles |
|-----|-----|
|Microsoft Entra ID |Global admin or User admin |
|On-premises Active Directory |Active Directory Enterprise Admins, Domain Admins, or have delegated rights to create users. Microsoft Entra Connect Sync rights. |
|Exchange Online |Global Administrator or Exchange Administrator  |
|Exchange Server |Exchange Organization Management or Recipient Management  |
|Licensing |Global admin or Billing admin |
|Teams |Global admin or Teams admin |

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

## Get the right license

[!INCLUDE [mtr-device-config-license-include](../includes/mtr-device-config-license-include.md)]

## Create resource account & assign the license

[!INCLUDE [mtr-device-config-account-include](../includes/mtr-device-config-account-include.md)]

> [!IMPORTANT]
> If you're creating resource accounts for Teams Rooms, the resource account's UPN must match the SMTP address of the resource account.

## Configure Exchange mailbox properties

[!INCLUDE [mtr-device-config-mailbox-include](../includes/mtr-device-config-mailbox-include.md)]

## Turn off password expiration

[!INCLUDE [mtr-device-config-password-include](../includes/mtr-device-config-password-include.md)]

## Next steps

### Teams policies

[!INCLUDE [mtr-device-config-policies-include](../includes/mtr-device-config-policies-include.md)]

### Calling

Resource accounts can be enabled for public switched telephone network (PSTN) the same way you enable a regular user. For more information, see [Calling in Microsoft Teams](/microsoftteams/cloud-voice-landing-page).

> [!NOTE]
> We recommend turning off voicemail for shared devices by assigning a calling policy to the resource accounts. See [Calling policies in Teams](../teams-calling-policy.md) for more information.

### Conditional Access

Resource accounts for Teams devices can be impacted by conditional access. You may need to make modifications to your existing policies to ensure your resource accounts are secure and functional. For more information on supported configurations and changes you may need to make, see [Conditional access for Teams devices](/microsoftteams/rooms/conditional-access-and-compliance-for-devices).

> [!NOTE]
> Teams shared devices do not support Security defaults in Microsoft Entra ID. Use conditional access to secure your environment and Teams shared devices.

### Exchange Room Finder & Microsoft Places

[!INCLUDE [mtr-device-config-calendar-include](../includes/mtr-device-config-calendar-include.md)]

## Related articles

[Plan for Microsoft Teams Rooms](rooms-plan.md)

[Deploy Microsoft Teams Rooms](rooms-deploy.md)

[Manage Microsoft Teams Rooms](rooms-manage.md)

[Microsoft Teams Rooms Licensing](rooms-licensing.md)
