---
title: Set up for live events in Microsoft Teams
author: tonysmith
ms.author: tonysmit
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: tonysmit
search.appverid: MET150
description: Learn the steps to set up live for events in Microsoft Teams, including preparing your network, assigning licenses, enabling live event scheduling for users, and setting up an eCDN provider.
appliesto: 
- Microsoft Teams
---

# Set up for live events in Microsoft Teams
> [!INCLUDE [Preview customer token](../includes/preview-feature.md)]

When you are setting up for live events, there are several steps that you must take:

## Step 1: Set up your network for live events in Microsoft Teams
The quick start live events require you to [prepare your organization's network for Microsoft Teams](https://docs.microsoft.com/microsoftteams/prepare-network).  

## Step 2: Get and assign licenses
Ensure you have correct license assignments for [Who can create and schedule live events?](#who-can-create-and-schedule-live-events) and [Who can watch live events?](#who-can-watch-live-events).

## Step 3: Enable live event scheduling for users
Live event scheduling is enabled by default for Teams users but if you are wanting users to schedule external encoder events there are additional steps that you must do.

### For quick start events
Use the setting *AllowBroadcastScheduling* in **TeamsMeetingBroadcastPolicy** in Teams PowerShell to control whether the user can create live events in Teams or not. You can learn more about managing TeamsMeetingBroadcastPolicy [here](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

 If you haven't assigned a custom policy assigned to the users, the users will get the *Global* policy, which has recording enabled by default.

Verify that *AllowBroadcastScheduling* parameter is set to *True*:
```
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```
Then assign the user to the *Global* policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

#### User scenarios
**You want all users in your company to be able to create live events.**

If users are assigned the *Glocal* policy, run and verify that *AllowBroadcastScheduling* *is set to *True*:
```
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```
If the users are assigned a policy other than the *Global* policy, run the following and verify that *-AllowBroadcastScheduling* is set to *True*:
```
Get-CsTeamsMeetingBroadcastPolicy -identity {policy name}
```

**You want live event scheduling to be 100% disabled across your organization.**

Disable broadcast scheduling, run:
```
Set-CsTeamsMeetingBroadcastPolicy -identity Global -AllowBroadcastScheduling $false
```
Assign all users in your organization to the *Global* policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

**You want a large number of users to be able to create live events, but want to prevent a set of users from creating them.**

Assign the *Global* policy using the **Grant-CsTeamsMeetingBroadcastPolicy** for some of the users (that you want enabled) but first run the following and verify that *AllowBroadcastScheduling* is set to *True*:
```
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```
Then assign a user or users to the *Global* policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```
Create and assign a policy for disabling scheduling using the  **Grant-CsTeamsMeetingBroadcastPolicy** cmdlet to the other users (you want disabled). 

Create the new policy with it disabled, run:
```
New-CSTeamsMeetingBroadcastPolicy -identity DisabledBroadcastSchedulingpolicy
```
Disable scheduling, run:
```
Set-CsTeamsMeetingBroadcastPolicy -identity DisabledBroadcastSchedulingpolicy -AllowBroadcastScheduling $false
```
Then assign users to this policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName DisabledBroadcastSchedulingpolicy -Verbose
```
**You want live events to be disabled for a large number of the users, but want to allow a set of users to create them.**

Disable broadcast scheduling, run:
```
Set-CsTeamsMeetingBroadcastPolicy -identity Global -AllowBroadcastScheduling $false
```
Then assign those users to the *Global* policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```
Create and assign a policy for enabling scheduling, run:
```
New-CSTeamsMeetingBroadcastPolicy -identity EnableBroadcastSchedulingpolicy
```
Enable scheduling, run:
```
Set-CsTeamsMeetingBroadcastPolicy -identity EnableBroadcastSchedulingpolicy -AllowBroadcastScheduling $true
```
Then assign users to this policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName EnableBroadcastSchedulingpolicy -Verbose
```

### For external encoder events
You must do the following to enable live event scheduling for those users.

#### Step 1: Enable Microsoft Stream for users in your organization**
Microsoft Stream is available as part of eligible Office 365 subscriptions or as a standalone service. See [Stream licensing overview](https://docs.microsoft.com/stream/license-overview) for more details.

> ![NOTE]
> Microsoft Stream is not included in Business Essentials or Business Premium plans.  

Learn more about how you can [assign licenses to users in Office 365](https://support.office.com/article/Assign-licenses-to-users-in-Office-365-for-business-997596B5-4173-4627-B915-36ABAC6786DC) so that users can access Microsoft Stream. Ensure Microsoft Stream is not blocked for the users as defined in [this article](https://docs.microsoft.com/stream/disable-user-organization).

#### Step 2: Ensure users have live event creation permission in Microsoft Stream**
By default, administrators can create external encoder live events. Microsoft Stream administrator can [enable additional users for live event creation](https://docs.microsoft.com/stream/live-event-administration#enabling-and-restricting-users-to-creating) in Stream.  

#### Step 3: Ensure live event organizers have consented to the company policy set by Stream admin**
If a Microsoft Stream administrator has [set up a company guidelines policy](https://docs.microsoft.com/stream/company-policy-and-consent) and requires employees to accept this policy before saving content, then users must do so before creating a live event (with External Encoder production) in Teams. Before you rollout the live events feature in the organization, make sure users who will be creating these live events have consented to the policy. 

## Step 4: Set up eCDN provider for live events in Microsoft Teams 
Playback of live event videos uses adaptive bitrate streaming (ABR) but it is a unicast stream, meaning every viewer is getting their own video stream from the internet. For live events or videos sent out to large portions of your organization, there could be a significant amount of internet bandwidth consumed by viewers. For organizations that want to reduce this internet traffic for live events, live events solutions are integrated with Microsoft's trusted video delivery partners offering software defined networks (SDNs) or enterprise content delivery networks (eCDNs). These SDN / eCDN platforms enable organizations to optimize network bandwidth without sacrificing end user viewing experiences. Our partners can help enable a more scalable and efficient video distribution across your enterprise network.

**Purchase & setup your solution outside of Microsoft Teams**
Get expert help with scaling video delivery by leveraging Microsoft’s trusted video delivery partners. Before you can enable a video delivery provider to be used with Teams you must purchase and setup the SDN/eCDN solution outside and separate from Teams.

The following SDN/eCDN solutions are pre-integrated and can be setup to be used with Microsoft Stream.

- **Hive Streaming** provides a simple and powerful solution for live and on-demand enterprise video distribution. Hive is a software-based solution that requires no additional hardware or bandwidth and provides a secure way to enable thousands of simultaneous video viewers without impact to your network. For customers looking to understand the impact video is having on their network prior to purchasing an SDN/eCDN solution, Hive Streaming also provides a browser-based analytics solution for Microsoft customers. [Learn more](https://www.hivestreaming.com/partners/integration-partners/microsoft/).
 
- **Kollective** is a cloud-based, smart peering distribution platform that leverages your existing network infrastructure to deliver content, in many forms, (live streaming video, on-demand video, software updates, security patches, etc.) faster, more reliably and with less bandwidth. Our secure platform is trusted by the world’s largest financial institutions and with no additional hardware, setup and maintenance are easy. [Learn more](http://www.kollective.com).
 
- **Ramp OmniCache** provides next-generation network distribution and ensures seamless delivery of video content across global WANs, helping event producers optimize network bandwidth and support successful live event broadcasts and on-demand streaming. The support for Ramp OmniCache for quick start live events is coming soon.  [Learn more](http://www.ramp.com). 
 
> [!NOTE] 
> Your chosen eCDN solution is subject to the selected **3rd party provider’s terms of service and privacy policy**, which will governs your use of the eCDN provider’s solution. Your use of the eCDN provider’s solution will not be subject to the Microsoft volume licensing terms or Online Services Terms. If you do not agree to the **3rd party provider’s terms**, then don't enable the eCDN solution in Teams. 

**Set up an eCDN for "Quick start" live events** 
You can configure eCDN provider for live events in Teams using PowerShell. 

> [!NOTE] 
> A single eCDN provider can be configured for your organization. 

***Hive*** 
You can use [Set-CsTeamsMeetingBroadcastConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingbroadcastconfiguration?view=skype-ps) PowerShell cmdlet to configure eCDN provider. First obtain the license ID and API template URL from your Hive contact then run the following:
```
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName hive -SdnLicenseId {license ID GUID provided by Hive} -SdnApiTemplateUrl “{API template URL provided by Hive}”
```
***Kollective*** 
You can use [Set-CsTeamsMeetingBroadcastConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingbroadcastconfiguration?view=skype-ps) PowerShell cmdlet to configure eCDN provider. First obtain the API token and the API template URL from your Kollective contact, then run the following:
```
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName kollective -SdnApiTemplateUrl "{API template URL provided by Kollective}" -SdnApiToken {API token GUID provided by Kollective}
```
**Set up an eCDN for "External encoder" live events** 

If you plan to create live events that use external encoders, you will need to [configure your eCDN provider with Microsoft Stream](https://docs.microsoft.com/stream/network-caching) as well. 

## Next steps
Go to [Confgure Teams live events](configure-teams-live-events.md).
