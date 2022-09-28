---
title: Create resource accounts for rooms and shared Teams devices
ms.author: dstrome
author: dstrome
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.service: msteams
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Rooms
ms.custom: seo-marvel-apr2020
ms.assetid: f09f4c2a-2608-473a-9a27-f94017d6e9dd
description: Read this article for information on how to create resource accounts for rooms and shared devices, including Microsoft Teams Rooms, Teams Rooms on Surface Hub, and hot-desking on Teams displays.
---

# Create and configure resource accounts for rooms and shared Teams devices

This article provides steps to create resource accounts for shared spaces and devices, and it includes steps to configure resource accounts for Microsoft Teams Rooms on Windows, Teams Rooms on Android, Teams Rooms on Surface Hub, and hot-desking on Teams displays.

Microsoft 365 resource accounts are mailbox and Teams accounts that are dedicated to specific resources, such as a room or projector. These resource accounts can automatically respond to meeting invites using rules you define when they're created. For example, if you have a common resource such as a conference room, you can set up a resource account for that conference room that will automatically accept or decline meeting invites depending on its calendar availability. 

Every resource account is unique to a single Microsoft Teams Rooms installation or Teams display hot-desking implementation.

[!INCLUDE [m365-teams-resource-account-difference](../includes/m365-teams-resource-account-difference.md)]

> [!NOTE]
> If using Microsoft Teams panels, the Teams Rooms resource account signs in to both Teams Rooms and associated Teams panels.

> [!NOTE]
> **Skype for Business** <br><br>
> If you need to enable your resource account to work with Skype for Business, see [Deploy Microsoft Teams Rooms with Skype for Business Server](with-skype-for-business-server-2015.md)

## Before you begin

### Requirements

Depending on your environment, you need one or more roles to create resource accounts.

|**Environment**|**Required Roles**|
|-----|-----|
|Azure Active Directory  <br/> |Global Administrator or User Administrator  <br/> |
|Active Directory  <br/> |Active Directory Enterprise Admins, Domain Admins, or have delegated rights to create users. Azure Active Directory Connect Sync rights.  <br/> |
|Exchange Online  <br/> |Global Administrator or Exchange Administrator   <br/> |
|Exchange Server  <br/> |Exchange Organization Management or Recipient Management   <br/> |

If you're creating resource accounts for Teams Rooms, the UPN must match the SMTP address of the resource account. See [Microsoft Teams Rooms requirements](requirements.md) before you deploy Teams Rooms.

### What license do you need?

[!INCLUDE [mtr-device-config-license-include](../includes/mtr-device-config-license-include.md)]

## Create a resource account

[!INCLUDE [mtr-device-config-account-include](../includes/mtr-device-config-account-include.md)]

## Configure mailbox properties

[!INCLUDE [mtr-device-config-mailbox-include](../includes/mtr-device-config-password-include.md)]

## Turn off password expiration

[!INCLUDE [mtr-device-config-password-include](../includes/mtr-device-config-password-include.md)]

## Assign a meeting room license

[!INCLUDE [mtr-device-config-assign-include](../includes/mtr-device-config-assign-include.md)]

## Next steps

### Meeting policies

[!INCLUDE [mtr-device-config-policies-include](../includes/mtr-device-config-policies-include.md)]

### Calling

There are no unique requirements to enable calling with resource accounts. You enable the resource account for calling in the same way you enable a regular user.

> [!NOTE]
> We recommend turning off voice mail for shared devices by assigning a calling policy to the device resource accounts. See [Calling and call-forwarding in Teams](../teams-calling-policy.md) for more information.

[!INCLUDE [mtr-device-config-calendar-include](../includes/mtr-device-config-calendar-include.md)]

## Related articles

[Configure accounts for Microsoft Teams Rooms](rooms-configure-accounts.md)

[Plan for Microsoft Teams Rooms](rooms-plan.md)

[Deploy Microsoft Teams Rooms](rooms-deploy.md)

[Manage Microsoft Teams Rooms](rooms-manage.md)

[Microsoft Teams Rooms Licensing](rooms-licensing.md)
