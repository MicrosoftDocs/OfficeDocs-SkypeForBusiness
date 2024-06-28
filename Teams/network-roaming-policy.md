---
title: Network roaming policy
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: roykuntz
ms.date: 06/28/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: High
search.appverid: MET150
 
ms.custom: 

ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
description: Learn how to manage settings for the Teams network roaming policy.
---

# Manage video and media settings with the network roaming policy

In addition to managing video and media settings with meeting policies, you can dynamically control the use of the following attributes used by the Microsoft Teams client: 

- IP Video
- Media bit rate

The TeamsNetworkRoamingPolicy policy enables you to assign settings to network sites. The Teams client dynamically picks up the settings based on which network site it connects to. When the Teams client signs in from a network site with a roaming policy assigned, that policy is used. If there's no policy assigned, the values set in the meeting policy are used. For more information about meeting policy audio and video settings, see [Meeting policy settings for audio and video](meeting-policies-audio-and-video.md).

## Configure the TeamsNetworkRoamingPolicy

To configure the TeamsNetworkRoamingPolicy, use the following PowerShell cmdlets:

- [Get-CsTeamsNetworkRoamingPolicy](/powershell/module/teams/get-csteamsnetworkroamingpolicy)
- [New-CsTeamsNetworkRoamingPolicy](/powershell/module/teams/new-csteamsnetworkroamingpolicy)
- [Set-CsTeamsNetworkRoamingPolicy](/powershell/module/teams/set-csteamsnetworkroamingpolicy)
- [Remove-CsTeamsNetworkRoamingPolicy](/powershell/module/teams/remove-csteamsnetworkroamingpolicy)

The TeamsNetworkRoamingPolicy contains the following parameters:

- AllowIPVideo - This setting controls whether video can be turned on in meetings hosted by a user and in 1:1 and group calls started by a user.

- MediaBitRateKb - This setting determines the total average media bit rate for audio, video, and video-based app sharing transmissions in calls and meetings for the user.

After you configure the policy, assign it to one or more network sites by using the [Set-CsTenantNetworkSite](/powershell/module/teams/set-cstenantnetworksite) cmdlet as follows:

```PowerShell
 Set-CsTenantNetworkSite -Identity Burlington -NetworkRoamingPolicy LowBandwidthSite
 ``` 
 
 To remove a policy from a network site, use the following cmdlet:
 
 ```PowerShell
 Set-CsTenantNetworkSite -Identity Burlington -NetworkRoamingPolicy $null
 ```

To enable the network roaming policy for users who aren't enterprise voice enabled, you must also enable the AllowNetworkConfigurationSettingsLookup setting in TeamsMeetingPolicy. This setting is off by default.

For more information about creating network sites, see [Network settings for cloud voice features](cloud-voice-network-settings.md). 

## Examples

```PowerShell
New-CsTeamsNetworkRoamingPolicy -Identity LowBandwidthSite -AllowIPVideo $false -MediaBitRateKb 1000
```

```PowerShell
Set-CsTenantNetworkSite -Identity Burlington -NetworkRoamingPolicy LowBandwidthSite
```

## Supported clients

- Windows 
- macOS desktop

## Known issues

When specifying the New- and Get-CsTeamsNetworkRoamingPolicy in Teams Online PowerShell v 2.0.0, you'll see extra data being displayed.


## Related articles

- [Get-CsTeamsNetworkRoamingPolicy](/powershell/module/teams/get-csteamsnetworkroamingpolicy)
- [New-CsTeamsNetworkRoamingPolicy](/powershell/module/teams/new-csteamsnetworkroamingpolicy)
- [Set-CsTeamsNetworkRoamingPolicy](/powershell/module/teams/set-csteamsnetworkroamingpolicy)
- [Remove-CsTeamsNetworkRoamingPolicy](/powershell/module/teams/remove-csteamsnetworkroamingpolicy)
- [Set-CsTenantNetworkSite](/powershell/module/teams/set-cstenantnetworksite)
