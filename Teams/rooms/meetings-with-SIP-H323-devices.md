---
title: Teams Rooms meetings with SIP and H.323 devices
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
description: Learn about how to set up Teams Rooms to receive and place calls to and from approved SIP and H.323 devices.
---

# Teams Rooms on Windows with SIP and H.323 devices

SIP and H.323 dialing is a feature that is only available on Microsoft Teams Rooms on Windows and each of those devices that will use SIP and H.323 dialing must have a Microsoft Teams Pro license assigned. 

This feature enables calls between Teams Rooms devices and other conferencing devices that support either SIP or the H.323 protocol. By turning this feature on, it will let Teams Rooms interoperate with approved SIP and H.323 meeting devices to place, receive, or block calls from meeting endpoints that can be both internal or external to your organization. However, SIP and H.323 dialing is disabled by default in your organization so to enable this, you must use Microsoft Teams PowerShell.

If you have multiple Teams Rooms all with a Pro licenses deployed in your organization, you can configure SIP and H.323 dialing for one or all of your Teams Rooms. 

> [!IMPORTANT]
>
> This feature is only available for Microsoft Teams Rooms for Windows and won't work with Teams Rooms for Android in your organization.

## Requirements

To enable your Teams Rooms on Windows to use SIP and H.323 dialing:

1. The Teams Rooms account that is used to sign in to the device must have a Teams Rooms Pro license assigned.
2. You must have a signed agreement with one of the certified [Cloud Video Interop providers](../cloud-video-interop.md) (CVI) that offers this feature like for example, Poly and Pexip. Please reach out to your chosen CVI provider for more information.

## How to configure a Teams Room

> [!Note]
>
> Currently, there isn't a way to turn this on or off in the Teams Admin Center so you must use Microsoft Teams PowerShell. 

You must first create a new Teams Room Video Teleconferencing policy using Teams PowerShell and then set the parameters to enable SIP and H.323 dialing.

### Using Windows PowerShell

If you haven't use Microsoft Teams PowerShell before, start by going over here to [learn more and how to install it](../teams-powershell-install.md). 

To create a new policy, use the Microsoft Teams PowerShell and run:

```PowerShell
New-CsTeamsRoomVideoTeleConferencingPolicy -Identity "TurnOnSIPH323" -Enabled $true -AreaCode "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx" -ReceiveExternalCalls Enabled -ReceiveInternalCalls Enabled 
```
>[!Important]
>
> The `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx` entry in the command is a placeholder for a GUID that is provided by the CVI provider that offers this feature.

>[!Note]
>
> `ReceiveExternalCalls` and `ReceiveInternalCalls` parameters are disabled by default. They take only two values either `Enabled` or `Disabled`. If it is set to `Enabled`, then the `AreaCode` parameter is required. This value is provided by the CVI provider that offers this feature.

To get all available Teams Room TeleConferencing policies in your organization, you need to run the following command:

```PowerShell
Get-CsTeamsRoomVideoTeleConferencingPolicy
```
To block receiving external calls on the policy, you need to run the following command. 

```PowerShell
Set-CsTeamsRoomVideoTeleConferencingPolicy -Identity `TurnOnSIPH323` -ReceiveExternalCalls `Disabled` 
```
>[!Note]
>
> Identity is required.

To apply a policy to a Teams Rooms device, you need to run the following command.

```PowerShell
Grant-CsTeamsRoomVideoTeleConferencingPolicy -Identity "<room alias>" -PolicyName "TurnOnSIPH323"
```
