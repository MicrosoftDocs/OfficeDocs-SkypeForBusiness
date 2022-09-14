---
title: Network roaming policy
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: roykuntz
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
localization_priority: Priority
search.appverid: MET150
 
ms.custom: 

ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
description: Learn how to manage settings for the Teams network roaming policy.
---

# Manage video and media settings with the network roaming policy

In addition to managing video and media settings with meeting policies, you can now dynamically control the use of the following attributes used by the Microsoft Teams client by using the TeamsNetworkRoamingPolicy: 

- IP Video
- Media bit rate

This policy enables you to assign settings to network sites. The Teams client will dynamically pick up the settings based on which network site it connects to. When the Teams client signs in from a network site with a roaming policy assigned, that policy will be used. If there is no policy assigned, the values set in the meeting policy will be used. For more information about meeting policy audio and video settings, see [Meeting policy settings for audio and video](meeting-policies-audio-and-video.md).

## Configure the TeamsNetworkRoamingPolicy

To configure the TeamsNetworkRoamingPolicy, use the following PowerShell cmdlets:

- [Get-CsTeamsNetworkRoamingPolicy](/powershell/module/skype/get-csteamsnetworkroamingpolicy)
- [New-CsTeamsNetworkRoamingPolicy](/powershell/module/skype/new-csteamsnetworkroamingpolicy)
- [Set-CsTeamsNetworkRoamingPolicy](/powershell/module/skype/set-csteamsnetworkroamingpolicy)
- [Remove-CsTeamsNetworkRoamingPolicy](/powershell/module/skype/remove-csteamsnetworkroamingpolicy)

The TeamsNetworkRoamingPolicy contains the following parameters:

- AllowIPVideo - This setting controls whether video can be turned on in meetings hosted by a user and in 1:1 and group calls started by a user.

- MediaBitRateKb - This setting determines the total average media bit rate for audio, video, and video-based app sharing transmissions in calls and meetings for the user.

After you've configured the policy, assign it to one or more network sites by using the [Set-CsTenantNetworkSite](/powershell/module/skype/set-cstenantnetworksite) cmdlet as follows:

```PowerShell
 Set-CsTenantNetworkSite -Identity Burlington -NetworkRoamingPolicy LowBandwidthSite
 ``` 
 
 To remove a policy from a network site, use the following cmdlet:
 
 ```PowerShell
 Set-CsTenantNetworkSite -Identity Burlington -NetworkRoamingPolicy $null
 ```

To enable the network roaming policy for users who are not enterprise voice enabled, you must also enable the AllowNetworkConfigurationSettingsLookup setting in TeamsMeetingPolicy. This setting is off by default.

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
- MacOS desktop

## Known issues

When specifying the New- and Get-CsTeamsNetworkRoamingPolicy in Teams Online PowerShell v 2.0.0, you'll see extra data being displayed.


## Related topics

- [Get-CsTeamsNetworkRoamingPolicy](/powershell/module/skype/get-csteamsnetworkroamingpolicy)
- [New-CsTeamsNetworkRoamingPolicy](/powershell/module/skype/new-csteamsnetworkroamingpolicy)
- [Set-CsTeamsNetworkRoamingPolicy](/powershell/module/skype/set-csteamsnetworkroamingpolicy)
- [Remove-CsTeamsNetworkRoamingPolicy](/powershell/module/skype/remove-csteamsnetworkroamingpolicy)
- [Set-CsTenantNetworkSite](/powershell/module/skype/set-cstenantnetworksite)
