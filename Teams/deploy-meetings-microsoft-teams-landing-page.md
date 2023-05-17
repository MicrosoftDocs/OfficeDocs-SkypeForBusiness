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

To scale meetings across your organization you should ensure that all user locations have internet access to connect to Microsoft 365. At a minimum you should make sure that the following common ports are open to the internet from your users' locations:

- TCP ports 80 and 443 outgoing from clients that will use Teams
- UDP ports 3478 through 3481 outgoing from clients that will use Teams

To verify that your network is ready, see:
- [Prepare your organization's network for Microsoft Teams](prepare-network.md)
- [URLs and IP address ranges](office-365-urls-ip-address-ranges.md)

## Core deployment decisions

These are the settings that most organizations want to change (if the Teams default settings don't work for the organization).

### Teams administrators

Teams provides a set of custom administrator roles that can be used to manage Teams for your organization. The roles provide various capabilities to administrators.

| Ask yourself | Action |
|--------------|--------|
|Who will be assigned the Teams Communications Administrator role?|To learn more about Teams administrator roles see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md).|
|Who will be assigned the Teams Communications Support Engineer role?|To assign admin roles, see [Assign administrator and non-administrator roles to users with Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).|

### Meetings settings

Meetings settings are used to set up meeting invitations, and if you want to turn on Quality of Service (QoS), set the ports for real-time traffic. These settings will be used for all of the Teams meetings that users schedule in your organization.

| Ask yourself | Action |
|--------------|--------|
|Will I customize meeting invitations? |See the [Customize meeting invitations](customize-meeting-invitations.yml) to learn more about meetings settings.|
|Will I implement QoS?|See [Quality of Service in Microsoft Teams](qos-in-teams.md) for information about QoS concepts. scenarios, and implementation.|

### Meeting policies

Meeting policies are used to control what features are available to users when they join Teams meetings. You can use the default policy or create one or more custom meeting policies for people that host meetings in your organization.

| Ask yourself | Action |
|--------------|--------|
|<ul><li>Will I customize the initial meeting policies?</li><li>Do I require multiple meeting policies?</li><li>How will I determine which groups of users get which meetings policy applied?</li></ul>|<br>Read [Manage meeting policies in Teams](meeting-policies-overview.md).|

### Audio Conferencing

Audio Conferencing provides organizations with additional entry points to any meeting (ad hoc or scheduled) by allowing meeting participants to join via public switched telephone network (PSTN) by dialing in using a traditional land line, private branch exchange (PBX), or mobile phone.

When you're ready to roll out Audio Conferencing, see the in-depth [Audio Conferencing rollout](deploy-audio-conferencing-teams-landing-page.md) guidance.

### Meeting room and personal devices

For an optimal meeting experience in Teams, consider using Teams devices such as room systems, phones, headsets, and cameras. To learn more, see [Teams devices for intelligent communications](https://products.office.com/microsoft-teams/across-devices).

| Ask yourself | Action |
|--------------|--------|
|Will I purchase personal devices for my users? |Read [Manage your devices in Teams](devices/device-management.md). |
|Will I purchase and deploy room system devices for my conference rooms?|Read [Meeting room devices and solutions](/skypeforbusiness/certification/devices-meeting-rooms?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fMicrosoftTeams%2ftoc.json).|

### Reporting

Use activity reports to see how users in your organization are using Teams. For example, if some don't use Teams yet, they might not know how to get started or understand how they can use Teams to be more productive and collaborative. Your organization can use the activity reports to decide where to prioritize training and communication efforts.

| Ask yourself | Action |
|--------------|--------|
|Who will be responsible for reporting?|Read [Use activity reports for Teams](teams-activity-reports.md).  |
|Who will be responsible for monitoring usage?|Read [Monitor usage and feedback in Teams](get-started-with-teams-monitor-usage-and-feedback.md).|

## Additional deployment decisions

You may want to change these settings, based on your organization's needs and configuration.

### Bandwidth planning

Bandwidth planning lets organizations estimate the bandwidth that will be required to support meetings across their wide area networks and internet links so they can confirm that the network is correctly provisioned to support a scaled out meeting service.

> [!IMPORTANT]
> Teams won't let users schedule meetings when they're offline or running with limited bandwidth.

| Ask yourself | Action |
|--------------|--------|
| Do I need to do bandwidth planning prior to and during my Meetings rollout? |See [Network Readiness](3-envision-evaluate-my-environment.md#network-readiness) for more information and links to tools to simplify your planning process.|

### Meeting recording and archiving

Users can record their meetings and group calls to capture audio, video, and screen sharing activity. There is also an option for recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and search for important discussion items in the transcript. The recording is saved in OneDrive or SharePoint, so users can share it securely across their organization.

To learn more, see [Teams meeting recording](meeting-recording.md) and [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md).

| Ask yourself | Action |
|--------------|--------|
| Will I turn on the meeting transcription service?|See [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)|

### Conference room systems rollout

Organizations with many conference rooms may want to consider a structured approach to inventorying their rooms, identifying the appropriate devices, and then rolling them out.

| Ask yourself | Action |
|--------------|--------|
| What do I need to do to roll out conference room systems?|Check out [Plan Microsoft Teams Rooms](/microsoftteams/rooms/rooms-plan).|

### Cloud video interop

Cloud video interop makes it possible for third-party meeting room devices to join Teams meetings.

Video teleconferencing with content collaboration helps you make the most out of meetings. However, meeting room systems and devices are expensive to upgrade. Cloud video interop for Teams works with third-party systems and delivers a native meeting experience for all participants – in meeting rooms or inside Teams clients.

| Ask yourself | Action |
|--------------|--------|
| Will I use a cloud video interop solution as part of my room systems deployment? | Read [Cloud Video Interop for Teams](cloud-video-interop.md).|

### Troubleshoot meeting and call quality

The [Call Analytics and Call Quality Dashboard](monitor-call-quality-qos.md) shows detailed information about the devices, networks, and connectivity related to the specific calls and meetings for each user. It is designed to help admins and network engineers optimize a network

Call Analytics is designed to help admins and help desk agents troubleshoot call quality problems with specific calls.

|Ask yourself|Action |
|------------|-------|
| Who will be responsible for monitoring and troubleshooting call quality issues? | Read [Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md) for information about permission levels required to troubleshoot call quality issues.|

### Operate your meetings service

It's important that you understand the overall health of the Teams service so that you can proactively alert others in your organization of any event that affects the service.

|Ask yourself|Action |
|------------|-------|
|Who in my organization will be responsible for managing the meetings service? | Make sure this person has the Teams admin permissions they need in order to manage your meetings service. To learn more about Teams administrator roles see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md).|

## Next steps

- [Drive adoption](adopt-microsoft-teams-landing-page.md) of meetings & conferencing throughout your organization.
- [Add audio conferencing](deploy-audio-conferencing-teams-landing-page.md)
- [Roll out cloud voice](cloud-voice-landing-page.md)

## Related topics

[Meetings and calls](https://support.office.com/article/d92432d5-dd0f-4d17-8f69-06096b6b48a8)

[Teams features by platform](https://support.microsoft.com/office/debe7ff4-7db4-4138-b7d0-fcc276f392d3)