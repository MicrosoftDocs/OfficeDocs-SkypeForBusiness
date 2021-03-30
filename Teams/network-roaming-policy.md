---
title: Network roaming policy
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: sonua
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

This policy enables you to assign settings to network sites. The Teams client will dynamically pick up the settings based on which network site it connects to. When the Teams client signs in from a network site with a roaming policy assigned, that policy will be used. If there is no policy assigned, the values set in the meeting policy will be used. For more information about meeting policy audio and video settings, see [Meeting policy settings - Audio & video](meeting-policies-in-teams#meeting-policy-settings---audio--video.md).

## Configure the TeamsNetworkRoamingPolicy

To configure the TeamsNetworkRoamingPolicy, you use the following PowerShell cmdlets:

```PowerShell
Get-CsTeamsNetworkRoamingPolicy
New-CsTeamsNetworkRoamingPolicy
Set-CsTeamsNetworkRoamingPolicy
Remove-CsTeamsNetworkRoamingPolicy
```

The TeamsNetworkRoamingPolicy contains the following parameters:

- AllowIPVideo - This setting controls whether video can be turned on in meetings hosted by a user and in 1:1 and group calls started by a user.

- MediaBitRateKb - This setting determines the total average media bit rate for audio, video, and video-based app sharing transmissions in calls and meetings for the user.

After you have configured the policy, you assign it to one or more network sites by using the following PowerShell cmdlet:

```PowerShell
 Set-CsTenantNetworkSite -NetworkRoamingPolicy
 ``` 
 
 To remove a policy from a network site, use the following cmdlet:
 
 ```PowerShell
 Set-CsTenantNetworkSite -NetworkRoamingPolicy $null
 ```

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

When specifying the New- and Get-CsTeamsNetworkRoamingPolicy in Teams Online PowerShell v 2.0.0, you will see extra data being displayed.


