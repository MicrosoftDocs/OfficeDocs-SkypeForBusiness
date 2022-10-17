---
title: "Call sharing and group call pickup"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 02/19/2019
ms.reviewer: srividhc
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
 - CSH
ms.custom: 
 - ms.teamsadmincenter.users.voice.groupcallpickup.tooltip
 - ms.teamsadmincenter.users.voice.callorderanddelay.tooltip
 - Phone System
 - seo-marvel-mar2020
description: "Call sharing and group call pickup let users share incoming calls with colleagues so that calls can be captured when the user is unavailable."
---

# Call sharing and group call pickup in Microsoft Teams

The call sharing and group call pickup features of Microsoft Teams let users share their incoming calls with colleagues so that the colleagues can answer calls that occur while the user is unavailable.

Group call pickup is less disruptive to recipients than other forms of call sharing (such as call forwarding or simultaneous ringing) because users can configure how they want to be notified of an incoming shared call (via audio and visual notification, visual only, or banner in the Teams app), and they can decide whether to answer it.

The order of which the members of the call group are notified about the incoming call can be specified as simultaneous or in order (with 5 or less members).

> [!IMPORTANT]
> Users, the call group owner, and members of the call group must be in Teams Only deployment mode. For more details on Teams deployment modes, see [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md).

## License required

Users must be assigned a Microsoft Teams Phone System license to set up and use call sharing and group call pickup. For additional details on the licensing model, see [Here's what you get with Phone System](/MicrosoftTeams/here-s-what-you-get-with-phone-system).

## Limitations

Each configured call group can have a maximum of 25 users or 32,768 characters. A given user can be a member of maximum 25 call groups.

Note that mobile devices will only get notified if they're set for banner and ringtone.

## Enabling the use of group call pickup
Admins should enable call groups via the **TeamsCallingPolicy AllowCallGroups** setting for a user either via Teams admin center or via PowerShell for this feature to work.

When enabled by policy, the configured user can configure their call groups via the client directly. Admin or end users cannot block the configuration by each other, but Teams admin center and Teams client should show this relationship accurately in both places. 

Important: When admins turn off call groups for users (after it has been turned on and the call group relationships are configured), the admins have to clean up the call group relationships for users in the Teams admin center to avoid incorrect call routing. 

## Configure group call pickup using Teams admin center
Administrators can configure group call pickup for users via Teams admin center as described in [Configure call settings for your users](/MicrosoftTeams/user-call-settings).

## Configure group call pickup using PowerShell
You can use PowerShell to configure call groups for users using the following Teams PowerShell Module cmdlets:

- [Set-CsUserCallingSettings](/powershell/module/teams/set-csusercallingsettings)

- [Get-CsUserCallingSettings](/powershell/module/teams/get-csusercallingsettings)

### Examples

#### Set members of a call group

In the following example, the tenant administrator creates a call group for user1@contoso.com with the members user2@contoso.com and user3@contoso.com and
sets immediate call forwarding to the call group for user1@contoso.com.

```powershell
$cgm = @("sip:user2@contoso.com","sip:user3@contoso.com")
Set-CsUserCallingSettings -Identity user1@contoso.com -CallGroupOrder InOrder -CallGroupTargets $cgm
Set-CsUserCallingSettings -Identity user1@contoso.com -IsForwardingEnabled $true -ForwardingType Immediate -ForwardingTargetType Group
```

#### Change membership of the call group
This example shows how to update the call group of user1@contoso.com to add user5@contoso.com and remove user6@contoso.com.

```powershell
$ucs = Get-CsUserCallingSettings -Identity user1@contoso.com
$cgt = {$ucs.CallGroupTargets}.Invoke()
$cgt.Add("sip:user5@contoso.com")
$cgt.Remove("sip:user6@contoso.com")
Set-CsUserCallingSettings -Identity user1@contoso.com -CallGroupOrder $ucs.CallGroupOrder -CallGroupTargets $cgt
```

For additional information and examples see the PS cmdlet pages above.

## More information

[Call forwarding and simultaneous ring in Teams](https://support.office.com/article/call-forwarding-and-simultaneous-ring-in-teams-a88da9e8-1343-4d3c-9bda-4b9615e4183e)

[Teams calling policy](/MicrosoftTeams/teams-calling-policy)

[New-CsTeamsCallingPolicy](/powershell/module/skype/new-csteamscallingpolicy)

[Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy)
