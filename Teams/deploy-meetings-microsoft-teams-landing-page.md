---
title: Meetings and conferencing in Microsoft Teams
ms.reviewer: 
ms.date: 07/01/2023
ms.topic: article
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.service: msteams
ms.subservice: meetings
audience: admin
f1.keywords: 
  - NOCSH
ms.collection: 
  - M365-collaboration
  - remotework
  - m365initiative-meetings
  - highpri
ms.localizationpriority: medium
search.appverid: MET150
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020; intro-get-started
description: Use these deployment resources to help you roll out meetings and audio conferencing in Microsoft Teams.
---

# Meetings and conferencing in Microsoft Teams

This article walks you through the rollout of meetings and audio conferencing.

This article helps you decide whether to change any of the default settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups, starting with the core set of [changes you're more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, based on your organization's needs.

## Meetings and conferencing prerequisites

Before scaling your meetings deployment across your organization, take time to review and confirm that your environment is ready to provide users with the best possible experience. Review the following information and make any required changes to your environment as needed.

To get the best experience on Teams, your organization must have deployed Exchange Online and [SharePoint](/sharepoint/plan-for-sharepoint-onedrive), and you must have a verified domain for Microsoft 365 such as *contoso.com*.

Make sure that the following common ports are open to the internet from your users' locations:

- TCP ports 80 and 443 outgoing from clients that will use Teams
- UDP ports 3478 through 3481 outgoing from clients that will use Teams

To verify that your network is ready, see:

- [Prepare your organization's network for Microsoft Teams](prepare-network.md)
- [URLs and IP address ranges](office-365-urls-ip-address-ranges.md)

## Core deployment decisions

These are the settings that many organizations change to reflect their business needs.

### Teams administrators

Teams provides a set of custom administrator roles that can be used to manage Teams for your organization. The roles provide various capabilities to administrators. To learn more about Teams administrator roles see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md). To assign admin roles, see [Assign admin roles in the Microsoft 365 admin center](/microsoft-365/admin/add-users/assign-admin-roles).

### Meetings settings

Meetings settings are used to set up meeting invitations, and if you want to turn on Quality of Service (QoS), set the ports for real-time traffic. These settings will be used for all of the Teams meetings that users schedule in your organization.

To learn about meeting settings, see:

- [Customize meeting invitations](customize-meeting-invitations.md)
- [Implement Quality of Service (QoS) in Microsoft Teams](qos-in-teams.md)

### Meeting policies

Meeting policies are used to control what features are available to users when they join Teams meetings. You can use the default policy or create one or more custom meeting policies for people that host meetings in your organization. Some meeting policies also affect webinars and town halls. For more information, see [Plan for Teams meetings](plan-meetings.md).

### Events policies

Events policies are used to control what features are available to users when they join Teams webinars and town halls. You can use the default policy or create one or more custom events policies for people that host webinars and town halls in your organization. For more information, see [Plan for Teams webinars](plan-webinars.md) and [Plan for Teams town halls](plan-town-halls.md).

### Audio Conferencing

Audio Conferencing provides organizations with additional entry points to any meeting (ad hoc or scheduled) by allowing meeting participants to join via public switched telephone network (PSTN) by dialing in using a traditional land line, private branch exchange (PBX), or mobile phone.

When you're ready to roll out Audio Conferencing, see the in-depth [Audio Conferencing rollout](deploy-audio-conferencing-teams-landing-page.md) guidance.

### Meeting room and personal devices

For an optimal meeting experience in Teams, consider using Teams devices such as Teams Rooms systems, phones, headsets, and cameras. To learn more, see:

- [Teams devices for intelligent communications](https://products.office.com/microsoft-teams/across-devices).
- [Manage your devices in Teams](devices/device-management.md)
- [Teams Rooms certified systems and peripherals](rooms/certified-hardware.md).|

### Reporting

Use activity reports to see how users in your organization are using Teams. For example, if some don't use Teams yet, they might not know how to get started or understand how they can use Teams to be more productive and collaborative. Your organization can use the activity reports to decide where to prioritize training and communication efforts. For more information, see [Use activity reports for Teams](teams-activity-reports.md) and [Monitor usage and feedback in Teams](get-started-with-teams-monitor-usage-and-feedback.md).

## Additional deployment decisions

You may want to change these settings, based on your organization's needs and configuration.

### Bandwidth planning

Bandwidth planning lets organizations estimate the bandwidth that will be required to support meetings across their wide area networks and internet links so they can confirm that the network is correctly provisioned to support a scaled out meeting service. Teams won't let users schedule meetings when they're offline or running with limited bandwidth.

See [Network Readiness](3-envision-evaluate-my-environment.md#network-readiness) for more information and links to tools to simplify your planning process.

### Meeting recording and archiving

Users can record their meetings and group calls to capture audio, video, and screen sharing activity. Organizers can record webinars and town halls. There is also an option for recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and search for important discussion items in the transcript. The recording is saved in OneDrive or SharePoint, so users can share it securely across their organization.

To learn more, see [Teams meeting recording](meeting-recording.md) and [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md).

### Cloud video interop

Cloud video interop makes it possible for third-party meeting room devices to join Teams meetings. Cloud video interop for Teams works with third-party systems and delivers a native meeting experience for all participants – in meeting rooms or inside Teams clients. Read [Cloud Video Interop for Teams](cloud-video-interop.md) for more information.

### Troubleshoot meeting and call quality

The [Call Analytics and Call Quality Dashboard](monitor-call-quality-qos.md) shows detailed information about the devices, networks, and connectivity related to the specific calls and meetings for each user. It is designed to help admins and network engineers optimize a network

Call Analytics is designed to help admins and help desk agents troubleshoot call quality problems with specific calls. Read [Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md) for information about permission levels required to troubleshoot call quality issues.

### Operate your meetings service

It's important that you understand the overall health of the Teams service so that you can proactively alert others in your organization of any event that affects the service.

Decide who in your organization will be responsible for managing the meetings service. Make sure this person has the Teams admin permissions they need in order to manage your meetings service. To learn more about Teams administrator roles see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md).

## Next steps

- [Drive adoption](adopt-microsoft-teams-landing-page.md) of meetings & conferencing throughout your organization.
- [Add audio conferencing](deploy-audio-conferencing-teams-landing-page.md)
- [Roll out cloud voice](cloud-voice-landing-page.md)

## Related topics

[Meetings and calls](https://support.office.com/article/d92432d5-dd0f-4d17-8f69-06096b6b48a8)

[Teams features by platform](https://support.microsoft.com/office/debe7ff4-7db4-4138-b7d0-fcc276f392d3)