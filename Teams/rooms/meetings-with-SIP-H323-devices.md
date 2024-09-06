---
title: SIP and H.323 calling with Teams Rooms
ms.author: tonysmit
author: mstonysmith
manager: pamgreen
ms.reviewer: naforer
ms.date: 08/21/2024
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
description: Learn about how to set up Teams Rooms to receive and place calls using SIP and H.323.
---

# SIP and H.323 Calling with Teams Rooms

SIP and H.323 calling is available on Microsoft Teams Rooms on Windows devices licensed with a Microsoft Teams Rooms Pro license. This functionality used the existing Cloud Video Interop provider in your tenant. 

This feature enables calls between Teams Rooms devices and other conferencing endpoints that support either the SIP or the H.323 protocol. By turning on this feature, Teams Rooms can interoperate with SIP and H.323 video endpoints to place or receive calls. The SIP and H.323 endpoints can be either internal or external to your organization. SIP and H.323 dialing is disabled by default in your organization. You must follow the steps in this document to enable this functionality using Microsoft Teams PowerShell. SIP & H.323 calls from your Teams Rooms device are Teams calls to the Microsoft 365 cloud which then communicates with your CVI provider. No other network or firewall rules are required to enable this functionality if you already have working Teams Rooms devices deployed.

If you have multiple Teams Rooms all with a Pro licenses deployed in your organization, you can configure SIP and H.323 dialing for one or all of your Teams Rooms. 

> [!IMPORTANT]
>
> This feature is only available for Microsoft Teams Rooms devices licensed with a Teams Rooms Pro license and is only availble for Teams Rooms on Windows device. This won't work with Teams Rooms on Android devices.

## Requirements

To enable your Teams Rooms device to use SIP and H.323 calling:

1. The Teams Rooms resource account must have a Teams Rooms Pro license assigned.
2. You must have an agreement with one of the certified [Cloud Video Interop providers](../cloud-video-interop.md) (CVI) that offers this feature and have CVI deployed in your organization. Reach out to your CVI provider for more information.
3. Information from your CVI provider on the "AreaCode" to use when configuring SIP & H.323 calling in Microsoft Teams (the "AreaCode" may match the "TenantKey" used when you configured CVI).
4. You must create and assign a Teams Room Video Teleconferencing Policy your Teams Rooms resource accounts.

## How to configure a SIP & H.323 Video Teleconferencing Policy

SIP & H.323 calling on Teams Rooms devices is enabled by the Teams Room Video Teleconferencing Policy. By default no policies are configured in an organizations tenant so you must first create a new Teams Room Video Teleconferencing policy and set the parameters to enable SIP and H.323 dialing. If you have multiple CVI providers in your organizations tenant, you can configure multiple Video Teleconferencing policies and assign different policies to difference Teams Room resource accounts, although you can only have one Global policy, individual policies take precedence if directly assigned to an account.

> [!Note]
>
> These features can only be configured using Microsoft Teams PowerShell module. 

### Creating a new Teleconference Policy

If necessary, update or install the Teams PowerShell module and sign in to Teams PowerShell following these instructions: [Microsoft Teams PowerShell](../teams-powershell-install.md). 

Once signed in, you need to create a new Video Teleconferencing policy, using the [Set-CsTeamsRoomVideoTeleConferencingPolicy cmdlet](/powershell/module/teams/set-csteamsroomvideoteleconferencingpolicy.md). You can create a single "Global" policy which will apply to all Teams Rooms resource accounts, allowing SIP & H.323 calling on all devices. Or you can create an individual policy, which needs to be assigned to each Teams Rooms resource account you want to have this ability.

Global Policy Example:

```PowerShell
New-CsTeamsRoomVideoTeleConferencingPolicy -Identity Global -Enabled $true -AreaCode "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx" -ReceiveExternalCalls Enabled -ReceiveInternalCalls Enabled
```

Individual Policy Example:

```PowerShell
New-CsTeamsRoomVideoTeleConferencingPolicy -Identity "TurnOnSIPH323" -Enabled $true -AreaCode "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx" -ReceiveExternalCalls Enabled -ReceiveInternalCalls Enabled 
```

>[!Important]
>
>The `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx` entry in the command is a placeholder for a GUID that is provided by the CVI provider that offers this feature.

>[!Note]
>
>If the Policy is set to `Enabled`, then the `AreaCode` parameter is required. This value is provided by the CVI provider that offers this feature.
>`ReceiveExternalCalls` and `ReceiveInternalCalls` parameters are disabled by default. They take only two values either `Enabled` or `Disabled`. 

### Viewing existing or newly created Teleconference Policies
Once you create a Teams Room Teleconferencing policy in your organization, or to view all existing policies, run the [Get-CsTeamsRoomVideoTeleConferencingPolicy cmdlet](/powershell/module/teams/get-csteamsroomvideoteleconferencingpolicy.md).

```PowerShell
Get-CsTeamsRoomVideoTeleConferencingPolicy
```
### Assigning a Teleconference Policy
To apply a policy to a Teams Rooms device, you need to run the [Grant-CsTeamsRoomVideoTeleConferencingPolicy cmdlet](/powershell/module/teams/grant-csteamsroomvideoteleconferencingpolicy.md).

```PowerShell
Grant-CsTeamsRoomVideoTeleConferencingPolicy -Identity "<resource account UPN>" -PolicyName "TurnOnSIPH323"
```

### Modifying a Teleconference Policy
If you've created a policy and wish to modify it you can do so with the [Set-CsTeamsRoomVideoTeleConferencingPolicy cmdlet](/powershell/module/teams/set-csteamsroomvideoteleconferencingpolicy.md). This example blocks external inbound calling.

```PowerShell
Set-CsTeamsRoomVideoTeleConferencingPolicy -Identity `TurnOnSIPH323` -ReceiveExternalCalls `Disabled` 
```


