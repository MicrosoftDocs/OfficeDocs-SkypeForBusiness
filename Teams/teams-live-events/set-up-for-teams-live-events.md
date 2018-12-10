---
title: Set up for live events in Microsoft Teams
author: tonysmith
ms.author: tonysmit
manager: serdars
ms.date: 10/23/2018
ms.topic: article
ms.service: msteams
ms.reviewer: tonysmit
search.appverid: MET150
localization_priority: Normal
MS.collection: Teams_ITAdmin_Help
description: Learn the steps to set up live for events in Teams, including preparing your network, assigning licenses, using policies to enable live event features and scheduling for users, and setting up a third-party distribution provider.
f1keywords: ms.teamsadmincenter.liveevents.policies
appliesto: 
- Microsoft Teams
---

# Set up for live events in Microsoft Teams

> [!INCLUDE [Preview customer token](../includes/preview-feature.md)]

When you're setting up for live events, there are several steps that you must take:

## Step 1: Set up your network for live events in Microsoft Teams
Quick start live events require you to [prepare your organization's network for Microsoft Teams](https://docs.microsoft.com/microsoftteams/prepare-network).  

## Step 2: Get and assign licenses
Ensure you have correct license assignments for [who can create and schedule live events](plan-for-teams-live-events.md#who-can-create-and-schedule-live-events) and [who can watch live events](plan-for-teams-live-events.md#who-can-watch-live-events).

## Step 3: Set up live events policies
Live events policies are used to control who in your organization can hold live events and the features that are available in the events they create. You can use the default policy or create one or more custom live events policies. After you create a custom policy, assign it to a user or groups of users in your organization.

> [!NOTE]
> Users in your organization will get the global policy unless you create and assign a custom policy. By default in the global policy, live event scheduling is enabled for Teams users, transcription is turned off, everyone in the organization can join live events, and the recording setting is set to always record. 

### Create or edit a live events policy

**![teams-logo-30x30.png](../media/teams-logo-30x30.png) Using the Microsoft Teams & Skype for Business admin center**

1. In the left navigation, go to **Meetings** > **Live events policies**. 
2. Do one of the following:
- If you want to edit the existing default policy, choose **Global (Org-wide default)**. 
- If you want to create a new custom policy, choose **New policy**. 
- If you want to edit a custom policy, select the policy, and then choose **Edit**. 

    Here are the settings you can change to fit the needs of your organization.

    ![Screen shot of live events policy settings](../media/teams-live-events-policies.png "Screen shot of live events policy settings in the Microsoft Teams & Skype for Business admin center") 

|Setting  |Description  |
|---------|---------|
|**Name**     |This is the name of the policy that appears on the live events policies page. It can't be longer than 64 characters or have any special characters.          |
|**Description**    |Use this to add a friendly description for the policy.         |
|**Allow scheduling**     |Turning this on lets users in your organization create and schedule live events in Teams. It's important to know that if you want users to schedule external encoder live events, there are additional steps you must do. To learn more, see  [Enable users to schedule external encoder events](#enable-users-to-schedule-external-encoder-events).     |
|**Allow transcription for attendees** (coming soon) |This setting can only be applied to quick start events. Turning this on enables live event attendees to see real-time captions and translation during the event.         |
|**Who can join scheduled live events**    |Choose one of the following.<br> <br> **Everyone** Users can create live events that everyone, including people outside your organization, can attend. <br> **Everyone in the organization** Users can create live events that only people in your organization can attend. Users can't create live events that are attended by anonymous users. <br> **Specific users or groups** Users can create live events that only specific users or groups in your organization can attend. Users can't create live events that are attended by everyone in your organization or by anonymous users.        |
|**Recording setting**  <br>     | This setting can only be applied to quick start events. Choose one of the following. <br><br> **Always record** Live events created by users are always recorded. After the event is over, event team members can download the recording and attendees can watch the event. <br> **Never record** Live events created by users are never recorded. <br>**Organizer can record or not** Users can decide whether to record the live event. If it's recorded, after the event is over, event team members can download the recording and attendees can watch the event.      

You can also do this by using Windows PowerShell. For more information, see [Use PowerShell to set live events policies in Teams](set-teams-live-events-policies-using-powershell.md). 

### Assign a live events policy to users 

If you created a custom live events policy, assign it to users for the policy to be active. 

![teams-logo-30x30.png](../media/teams-logo-30x30.png) Using the Microsoft Teams & Skype for Business admin center

1. In the left navigation, go to **Users**, and then select the user.
2. Next to **Assigned policies**, choose **Edit**. 
3. Select the live events policy you want to assign, and then choose **Save**. 

### Enable users to schedule external encoder events

For users to schedule external encoder events, you must also do the following:

1. Enable Microsoft Stream for users in your organization. Microsoft Stream is available as part of eligible Office 365 subscriptions or as a standalone service. Microsoft Stream isn't included in Business Essentials or Business Premium plans. See [Stream licensing overview](https://docs.microsoft.com/stream/license-overview) for more details.

      Learn more about how you can [assign licenses to users in Office 365](https://support.office.com/article/Assign-licenses-to-users-in-Office-365-for-business-997596B5-4173-4627-B915-36ABAC6786DC) so that users can access Microsoft Stream. Ensure Microsoft Stream isn't blocked for the users as defined in [this article](https://docs.microsoft.com/stream/disable-user-organization).

2. Ensure users have live event creation permission in Microsoft Stream. By default, administrators can create external encoder live events. Microsoft Stream administrator can [enable additional users for live event creation](https://docs.microsoft.com/stream/live-event-administration#enabling-and-restricting-users-to-creating) in Stream.  

3. Ensure live event organizers have consented to the company policy set by Stream admin. If a Microsoft Stream administrator has [set up a company guidelines policy](https://docs.microsoft.com/stream/company-policy-and-consent) and requires employees to accept this policy before saving content, then users must do so before creating a live event (with External Encoder production) in Teams. Before you roll out the live events feature in the organization, make sure users who will be creating these live events have consented to the policy. 

## Step 4: Set up a video distribution solution for live events in Teams
Playback of live event videos uses adaptive bitrate streaming (ABR) but it's a unicast stream, meaning every viewer is getting their own video stream from the internet. For live events or videos sent out to large portions of your organization, there could be a significant amount of internet bandwidth consumed by viewers. For organizations that want to reduce this internet traffic for live events, live events solutions are integrated with Microsoft's trusted video delivery partners offering software defined networks (SDNs) or enterprise content delivery networks (eCDNs). These SDN/eCDN platforms enable organizations to optimize network bandwidth without sacrificing end user viewing experiences. Our partners can help enable a more scalable and efficient video distribution across your enterprise network.

**Purchase and set up your solution outside of Teams**
Get expert help with scaling video delivery by leveraging Microsoft’s trusted video delivery partners. Before you can enable a video delivery provider to be used with Teams you must purchase and set up the SDN/eCDN solution outside and separate from Teams.

The following SDN/eCDN solutions are pre-integrated and can be set up to be used with Microsoft Stream.

- **Hive Streaming** provides a simple and powerful solution for live and on-demand enterprise video distribution. Hive is a software-based solution that requires no additional hardware or bandwidth and provides a secure way to enable thousands of simultaneous video viewers without impact to your network. For customers looking to understand the impact video is having on their network prior to purchasing an SDN/eCDN solution, Hive Streaming also provides a browser-based analytics solution for Microsoft customers. [Learn more](https://www.hivestreaming.com/partners/integration-partners/microsoft/).
 
- **Kollective** is a cloud-based, smart peering distribution platform that leverages your existing network infrastructure to deliver content, in many forms, (live streaming video, on-demand video, software updates, security patches, etc.) faster, more reliably and with less bandwidth. Our secure platform is trusted by the world’s largest financial institutions and with no additional hardware, setup and maintenance are easy. [Learn more](http://www.kollective.com).
 
- **Ramp OmniCache** provides next-generation network distribution and ensures seamless delivery of video content across global WANs, helping event producers optimize network bandwidth and support successful live event broadcasts and on-demand streaming. The support for Ramp OmniCache for quick start live events is coming soon.  [Learn more](http://www.ramp.com). 
 
> [!NOTE] 
> Your chosen SDN or eCDN solution is subject to the selected **3rd party provider’s terms of service and privacy policy**, which will governs your use of the provider’s solution. Your use of the provider’s solution will not be subject to the Microsoft volume licensing terms or Online Services Terms. If you do not agree to the **3rd party provider’s terms**, then don't enable the solution in Teams. 

After you set up the SDN or eCDN solution, you're ready to configure the provider for live events in Teams. 

## Next steps
Go to [Configure live events settings in Teams](configure-teams-live-events.md).

### Related topics
- [What are Teams live events?](what-are-teams-live-events.md)
- [Plan for Teams live events](plan-for-teams-live-events.md)
- [Configure live events settings in Teams](configure-teams-live-events.md)

