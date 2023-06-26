---
title: Teams Rooms meetings with SIP and H.323 devices
ms.author: tonysmit
author: tonysmit
manager: serdars
audience: ITPro
ms.reviewer: naforer
ms.date: 06/16/2023
ms.topic: quickstart
ms.service: msteams
ms.subservice: itpro-rooms
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - Tier1
  - M365-collaboration
  - Teams_ITAdmin_Rooms
description: Learn about how to set up Teams Rooms to receive and place calls to and from approved SIP and H.323 devices.
---

# Teams Rooms on Windows with SIP and H.323 devices

SIP and H.323 dialing is a feature only available on Microsoft Teams Rooms on Windows with a Microsoft Teams Pro license assigned. This feature lets calls between Teams Rooms devices and other conferencing devices that support either SIP or the H.323 protocol. By turning this feature on, it will let Teams Rooms interoperate with approved SIP and H.323 meeting devices to place, receive, or block calls from meeting endpoints that are internal or external to your organization. However, SIP and H.323 dialing is disabled by default in your organization so to enable this, you must use Microsoft Teams PowerShell.

> [!IMPORTANT]
>
> This feature is only available for Microsoft Teams Rooms for Windows and won't work with Teams Rooms for Android or other SIP devices in your organization.

If you have multiple Teams Rooms all with a Pro licenses deployed in your organization, you can configure SIP and H.323 dialing for one or all of your Teams Rooms. 

## Requirements

To enable your Teams Rooms on Windows to use SIP and H.323 dialing:

1. The Teams Room account that is used to sign in to the device must have a Teams Room Pro license assigned.
2. You must have an signed agreement with one of the certified [Cloud Video Interop providers](../cloud-video-interop.md) (CVI). However, you have two options:
- **Option 1:** Sign up for a calling plan from a CVI provider that supports SIP and H.323 dialing.
- **Option 2:** Buy your own licenses from a CVI provider that supports SIP and H.323 dialing. 

## How to configure a Teams Room

> [!Note]
>
> Currently, there isn't a way to turn this on or off in the Teams Admin Center so you must use Microsoft Teams PowerShell. 

You must create a new Teams Room Video Teleconferencing policy and set the parameters to enable SIP and H.323 dialing.

In this example below, you will create a new policy and then set the parameters to turn on SIP and H.323 dialing.

### Using Windows PowerShell

If you haven't use Microsoft Teams PowerShell before, start by going over here to [learn more and how to install it](../teams-powershell-install.md). 

To create a new policy, use the Microsoft Teams PowerShell and run:

```PowerShell
New-CsTeamsRoomVideoTeleConferencingPolicy -Identity "TurnOnSIPH323" -Enabled $true -AreaCode `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx` -ReceiveExternalCalls Enabled -ReceiveInternalCalls Enabled -PlaceExternalCalls Enabled -PlaceInternalCalls Enabled
```
>[!Important]
>
> The `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx` entry in the command is a placeholder for a GUID that is provided by the CVI vendor.

>[!Note]
>
> `ReceiveExternalCalls`, `ReceiveInternalCalls`, `PlaceExternalCalls` and `laceInternalCalls` parameters are disabled by default. They take only two values either `Enabled` or `Disabled`. If it is set to `Enabled`, then the `AreaCode` parameter is required. This value is provided by your CVI partner.

To get all available Teams Room TeleConferencing policies in your organzation, you need to run the following command:

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

To apply a policy to a Teams Rooms devie, you need to run the following command.

```PowerShell
Grant-CsTeamsRoomVideoTeleConferencingPolicy -Identity "<room alias>" -PolicyName "TurnOnSIPH323"
```
