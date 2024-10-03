---
title: Set up for live events in Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: christi.balaki
ms.date: 10/3/2024
audience: admin
search.appverid: MET150
f1.keywords:
- CSH
ms.localizationpriority: medium
ms.collection: 
- M365-collaboration
- m365initiative-meetings
- m365initiative-meetings-enabler
- enabler-strategic
- highpri
description: Set up for live events in Teams, including set up your network, assign licenses, enable live event features and scheduling, and video distribution solutions.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Set up for live events in Microsoft Teams

> [!NOTE]
> Teams live events are no longer going away on September 30, 2024. While we still recommend you to upgrade to [Teams town hall](../plan-town-halls.md) when ready to take advantage of new features and experiences, your users can continue to schedule events beyond September 2024. For more information, see [Updates for Town Hall in Microsoft Teams and Teams Live Events](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/extension-for-teams-live-events-retirement/ba-p/4148352).

When you're setting up for live events, there are several steps that you must take.

## Step 1: Set up your network for live events in Teams

Live events produced in Teams require you to [prepare your organization's network for Teams](../prepare-network.md).  

## Step 2: Get and assign licenses

Ensure you have correct license assignments for [who can create and schedule live events](plan-for-teams-live-events.md#who-can-attend-create-and-schedule-live-events) and [who can watch live events](plan-for-teams-live-events.md#who-can-watch-live-events).

## Step 3: Set up live events policies

Live events policies control which users in your organization can hold live events and specify the features that are available during these events. You can use the default policy or create one or more custom live events policies. After you create a custom policy, assign it to a user or groups of users in your organization.

> [!NOTE]
> Users in your organization get the global (Org-wide default) policy unless you create and assign a custom policy. By default, in the global policy, live event scheduling is turned on for Teams users, while live captions and subtitles (transcription) is turned off. Everyone in the organization can join live events, and the recording setting is set to always record.

### Create or edit a live events policy

<a name="bkcreatepolicy"> </a>

1. In the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Live events policies** > **Manage Policies** tab.
2. Do one of the following options:

    - If you want to edit the existing default policy, choose **Global (Org-wide default)**.
    - If you want to create a new custom policy, choose **+Add**.
    - If you want to edit a custom policy, select the policy, and then choose **Edit**.

    Here are the settings you can change to fit the needs of your organization.

    :::image type="content" source="../media/live-event-policies-tac-small.png" alt-text="Screen shot of live events policy settings in the Microsoft Teams admin center." lightbox="../media/live-event-policies-tac-expand.png":::

|Setting  |Description  |
|---------|---------|
|**Title**     |The policy's title that appears on the live events policies page. It can't be longer than 64 characters or have any special characters.          |
|**Description**    |Add a description so you know why this policy was created.         |
|**Live events scheduling**     |Toggling this setting **On** lets users in your organization create and schedule live events in Teams.     |
|**Transcription for attendees** |This setting can only be applied to events produced in Teams. Turning this on enables live event attendees to see live captions and subtitles during the event.         |
|**Who can join scheduled live events**    |Choose one of the following options:<br><br>**Everyone** Users can create live events that everyone, including people outside your organization, can attend. This setting turns on the **Public** permission type in Teams when a user schedules a live event.<br> **Everyone in the organization** Users can create live events that people in your organization, including [guests](../add-guests.md) added to your organization, can attend. Users can't create live events that anonymous users can attend. This setting turns on the **Org-wide** permission type in Teams when a user schedules a live event.<br> **Specific users or groups** Users can create live events that only specific users or groups in your organization can attend. Users can't create live events that everyone in your organization or anonymous users can attend. This setting turns on the **People and groups** permission type in Teams when a user schedules a live event.       |
|**Recording an event**  <br>     | This setting can only be applied to events produced in Teams. Choose one of the following. <br><br> **Always record**- Live events that users with this policy create are always recorded. After the event is over, event team members can download the recording and attendees can watch the event. <br> **Never record**- Live events that users with this policy create are never recorded. <br>**Organizer can record**- Users with this policy can decide whether to record live events that they create. If the event is recorded, after the event is over, event team members can download the recording and attendees can watch the event.

You can also manage live event policies using Windows PowerShell, and, currently, GCC High and DoD customers must use this method. For more information, see [Use PowerShell to set live events policies in Teams](set-teams-live-events-policies-using-powershell.md).

### Assign a live events policy to users

If you created a custom live events policy, assign it to users for the policy to be active. <br><br>[!INCLUDE [assign-policy](../includes/assign-policy.md)]

## Step 4: Set up a video distribution solution for live events in Teams

Playback of live event videos uses adaptive bitrate streaming (ABR) but it's a unicast stream, meaning every viewer is getting their own video stream from the internet. For live events or videos sent out to large portions of your organization, there could be a significant amount of internet bandwidth consumed by viewers. For organizations that want to reduce this internet traffic for live events, Microsoft offers a first-party solution, [Microsoft eCDN](/ecdn) (enterprise content delivery network). Live events solutions are also integrated with Microsoft's trusted video delivery partners offering software defined networks (SDNs) or eCDNs. These SDN/eCDN platforms allow organizations to optimize network bandwidth without sacrificing end-user viewing experiences. These solutions can help create a more scalable and efficient video distribution across your enterprise network.

- **Microsoft eCDN**
Microsoft eCDN is integrated into Teams and is also compatible with Stream and Viva Engage. It employs peer-to-peer technology within a corporate network to offload bandwidth from the WAN connection.

- **Purchase and set up your solution outside of Teams**
Get expert help with scaling video delivery by using Microsoft's trusted video delivery partners. 

The following SDN/eCDN solutions are preintegrated and can be set up to be used with Teams streaming:

- **Hive Streaming** provides a simple and powerful solution for live and on-demand enterprise video distribution. Hive is a software-based solution that requires no extra hardware or bandwidth and provides a secure way to enable thousands of simultaneous video viewers without affecting to your network. For customers looking to understand the impact video is having on their network before purchasing an SDN/eCDN solution, Hive Streaming also provides a browser-based analytics solution for Microsoft customers. [Learn more](https://www.hivestreaming.com/partners/integration-partners/microsoft/).

- **Kollective** is a cloud-based, smart-peering distribution platform that uses your existing network infrastructure to deliver content in many forms (live streaming video, on-demand video, software updates, security patches, and more) faster, more reliably, and with less bandwidth. The world's largest financial institutions trust our secure platform and with no extra hardware, setup, and maintenance are easy. [Learn more](https://kollective.com/microsoft-pilot/).

- **Ramp OmniCache** provides next-generation network distribution and ensures seamless delivery of video content across global WANs, helping event producers optimize network bandwidth, and support successful live event broadcasts and on-demand streaming. The support for Ramp OmniCache for live events produced in Teams is coming soon. [Learn more](https://rampecdn.com).

- **Riverbed**, the industry standard in network optimization, is extending its acceleration solutions to Microsoft Teams. Now Microsoft 365 customers can confidently accelerate 365 traffic including Teams along with a wealth of other leading enterprise SaaS services to increase workforce productivity from anywhere. Teams acceleration can be enabled through an effortless setup that comes with all the assurance of Riverbed’s world-class support and ongoing investment.

> [!NOTE]
> If you choose a 3rd-party SDN or eCDN solution, it is subject to the selected **3rd party provider's terms of service and privacy policy**, which governs your use of the provider's solution. Your use of the provider's solution isn't subject to the Microsoft volume licensing terms or Online Services Terms. If you don't agree to the **3rd party provider's terms**, then don't turn on the solution in Teams.

After you set up the SDN or eCDN solution, you're ready to configure the provider for live events in Teams.

## Next steps

Go to [Configure live events settings in Teams](configure-teams-live-events.md).

### Related topics

- [What is Teams live events?](what-are-teams-live-events.md)
- [Plan for Teams live events](plan-for-teams-live-events.md)
- [Configure live events settings in Teams](configure-teams-live-events.md)
