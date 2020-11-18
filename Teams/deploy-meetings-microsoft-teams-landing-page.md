---
title: Meetings and conferencing in Microsoft Teams
ms.reviewer: 
description: Use these deployment resources to help you roll out meetings and audio conferencing in Microsoft Teams.
ms.topic: article
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.service: msteams
audience: admin
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_RemoteWorkers
  - remotework
  - m365initiative-meetings
localization_priority: Priority
search.appverid: MET150
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---


# Meetings and conferencing in Microsoft Teams

> [!NOTE]
> - For an overview of making the transition to remote learning and resources to help you get started, see our [**remote learning home page**](https://www.microsoft.com/education/remote-learning).
> - Resources to assist educators and students with remote learning are available in [**Remote teaching and learning in Office 365 Education**](https://support.office.com/article/remote-teaching-and-learning-in-office-365-education-f651ccae-7b65-478b-8366-51bb884025c4).


You've completed [Get started](get-started-with-teams-quick-start.md). You've rolled out Teams with [chat, teams, channels, & apps](deploy-chat-teams-channels-microsoft-teams-landing-page.md) across your organization. Now you're ready to add the meetings workload, including [audio conferencing](deploy-audio-conferencing-teams-landing-page.md), video, and sharing. This article walks you through the rollout of meetings and audio conferencing. Start by watching our Teams meetings, conferencing, and devices video (3:28 minutes):

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE46ZdQ]

To learn more about the meetings experience for your users, see [Meetings and calls](https://support.office.com/article/meetings-and-calls-d92432d5-dd0f-4d17-8f69-06096b6b48a8). 


*New in April 2020*: Meeting organizers can end a meeting for all meeting participants in Teams by clicking **End meeting** in the meeting controls within the meeting.  

*New in November 2019*: You can now [use Advisor for Teams (preview) to help you roll out Microsoft Teams](use-advisor-teams-roll-out.md). Advisor for Teams (preview) walks you through your Teams rollout, including meetings and conferencing. It assesses your Office 365 environment and identifies the most common configurations that you may need to update or modify before you can successfully roll out meetings and conferencing in Teams.

 > [!Note]
> For details about Teams meetings and conferencing on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

## Meetings and conferencing deployment decisions

Teams provides a great out-of-the-box experience for your organization, and most organizations find that the default settings work for them. This article helps you decide whether to change any of the default settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups, starting with the core set of [changes you're more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, based on your organization's needs.

> [!Tip]
> Watch the following session to learn more about Meetings: [Introduction to Meetings in Microsoft Teams for IT Pros](https://aka.ms/teams-meetings-intro)


## Meetings and conferencing prerequisites 

Before scaling your meetings deployment across your organization, take time to review and confirm that your environment is ready to provide users with the best
possible experience. Review the following information and make any required changes to your environment as needed.

To get the best experience on Teams, your organization must have deployed Exchange Online and SharePoint Online, and you must have a verified domain for O365
such as *contoso.com*.

To scale meetings across your organization you should ensure that all user locations have internet access to connect to the Office 365 Services. At a minimum you should make sure that the following common ports are open to the internet from your user's locations:-

- TCP ports 80 and 443 outgoing from clients that will use Teams
- UDP ports 3478 through 3481 outgoing from clients that will use Teams

| Ask yourself | Action |
|--------------|--------|
|Is my network ready for Teams meetings deployment? | To verify that your network is ready, see:<ul><li>[Prepare your organization's network for Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/prepare-network)</li><li>[URLs and IP address ranges](https://docs.microsoft.com/MicrosoftTeams/office-365-urls-ip-address-ranges)</li></ul> |
|||

## Core deployment decisions

These are the settings that most organizations want to change (if the Teams default settings don't work for the organization).

### Teams administrators

Teams provides a set of custom administrator roles that can be used to manage Teams for your organization. The roles provide various capabilities to administrators. 

| Ask yourself | Action |
|--------------|--------|
|Who will be assigned the Teams Communications Administrator role?|To learn more about Teams administrator roles see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md).|
|Who will be assigned the Teams Communications Support Engineer role?|To assign admin roles, see [Assign administrator and non-administrator roles to users with Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).|
|Who will be assigned the Teams Communications Support Specialist role?||
|||

### Meetings settings 

Meetings settings are used to control whether anonymous users can join Teams meetings, set up meeting invitations, and if you want to turn on Quality of Service (QoS), set the ports for real-time traffic. These settings will be used for all of the Teams meetings that users schedule in your organization. 

| Ask yourself | Action |
|--------------|--------|
|Will I customize the initial meeting settings? |See the [Meetings in Teams tutorial](tutorial-meetings-in-teams.yml) to learn more about meetings settings.|
|Will I implement QoS?|See [Quality of Service in Microsoft Teams](qos-in-teams.md) for information about QoS concepts. scenarios, and implementation.|
|||

### Meeting policies

Meeting policies are used to control what features are available to users when they join Teams meetings. You can use the default policy or create one or more custom meeting policies for people that host meetings in your organization. To learn more, see the [Meetings in Microsoft Team tutorial](tutorial-meetings-in-teams.yml).

| Ask yourself | Action |
|--------------|--------|
|<ul><li>Will I customize the initial meeting policies?</li><li>Do I require multiple meeting policies?</li><li>How will I determine which groups of users get which meetings policy applied?</li></ul>|<br>Read [Manage meeting policies in Teams](meeting-policies-in-teams.md).|
|||

### Audio Conferencing

Audio Conferencing provides organizations with additional entry points to any meeting (ad hoc or scheduled) by allowing meeting participants to join via public switched telephone network (PSTN) by dialing in using a traditional land line, private branch exchange (PBX), or mobile phone. 

When you're ready to roll out Audio Conferencing, see the in-depth [Audio Conferencing rollout](deploy-audio-conferencing-teams-landing-page.md) guidance.

### Meeting room and personal devices

For an optimal meeting experience in Teams, consider using Teams devices such as room systems, phones, headsets, and cameras. To learn more, see [Teams devices for intelligent communications](https://products.office.com/microsoft-teams/across-devices).

| Ask yourself | Action |
|--------------|--------|
|Will I purchase personal devices for my users? |Read [Manage your devices in Teams](devices/device-management.md). |
|Will I purchase and deploy room system devices for my conference rooms?|Read [Meeting room devices and solutions](https://docs.microsoft.com/skypeforbusiness/certification/devices-meeting-rooms?toc=/MicrosoftTeams/toc.json&bc=/microsoftteams/breadcrumb/toc.json).|
|||

### Reporting

Use activity reports to see how users in your organization are using Teams. For example, if some don't use Teams yet, they might not know how to get started or understand how they can use Teams to be more productive and collaborative. Your organization can use the activity reports to decide where to prioritize training and communication efforts. 


| Ask yourself | Action |
|--------------|--------|
|Who will be responsible for reporting?|Read [Use activity reports for Teams](teams-activity-reports.md).  |
|Who will be responsible for monitoring usage?|Read [Monitor usage and feedback in Teams](get-started-with-teams-monitor-usage-and-feedback.md).|
|||

## Additional deployment decisions

You may want to change these settings, based on your organization's needs and configuration.

### Bandwidth planning 

Bandwidth planning lets organizations estimate the bandwidth that will be required to support meetings across their wide area networks and internet links so they can confirm that the network is correctly provisioned to support a scaled out meeting service. 

| Ask yourself | Action |
|--------------|--------|
| Do I need to do bandwidth planning prior to and during my Meetings rollout? |See [Network Readiness](3-envision-evaluate-my-environment.md#network-readiness) for more information and links to tools to simplify your planning process.|
|||

### Meeting recording and archiving

Users can record their meetings and group calls to capture audio, video, and screen sharing activity. There is also an option for recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and search for important discussion items in the transcript. The recording happens in the cloud and is saved in Microsoft Stream, so users can share it securely across their organization. To find the recording for a meeting, go to the meeting conversation.

>[!Note]
> The change from using Microsoft Stream to [OneDrive for Business and SharePoint for meeting recordings](tmr-meeting-recording-change.md) will be a phased approach. At launch you'll be able to opt-in to this experience, in November you'll have to opt-out if you want to continue using Stream, and some time in early 2021 we'll require all customers to use OneDrive for Business and SharePoint for new meeting recordings.

To learn more, see [Teams cloud meeting recording](cloud-recording.md).

| Ask yourself | Action |
|--------------|--------|
| Will I turn on the meeting transcription service?|See [Turn on or turn off recording transcription](cloud-recording.md#turn-on-or-turn-off-recording-transcription)|
|||


### Live events policies

Teams live events policies are used to manage event settings for groups of users. You can use the default policy or create additional policies that can be assigned to users who hold live events within your organization. 

| Ask yourself | Action |
|--------------|--------|
| Will my organization use Teams live events?| See the [live events articles](teams-live-events/what-are-teams-live-events.md) for more information about planning for, setting up, and configuring Teams live events.|
|||

### Conference room systems rollout

Organizations with many conference rooms may want to consider a structured approach to inventorying their rooms, identifying the appropriate devices, and then rolling them out. 



| Ask yourself | Action |
|--------------|--------|
| What do I need to do to roll out conference room systems?|Check out the [Plan Microsoft Teams Rooms](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/clients-and-devices/skype-room-systems-v2-0?toc=/MicrosoftTeams/toc.json&bc=/microsoftteams/breadcrumb/toc.json) articles.|
|||

### Cloud video interop

Cloud video interop makes it possible for third-party meeting room devices to join Teams meetings. 

Video teleconferencing with content collaboration helps you make the most out of meetings. However, meeting room systems and devices are expensive to upgrade. Cloud video interop for Teams works with third-party systems and delivers a native meeting experience for all participants – in meeting rooms or inside Teams clients. 

| Ask yourself | Action |
|--------------|--------|
| Will I use a cloud video interop solution as part of my room systems deployment? | Read [Cloud Video Interop for Teams](cloud-video-interop.md).|
|||


### Personal device rollout

When planning a larger rollout of personal devices to support meetings or voice deployments, consider using a repeatable site-by-site rollout process that delivers repeatable quality.

| Ask yourself | Action |
|--------------|--------|
|Will I use a site-by-site approach to roll out Meetings? |  The [Site enablement playbook for Teams](3-onboard-deploy-my-service.md#site-enablement-playbook-for-microsoft-teams-voice-workloads) provides a good foundation that you can use for your own deployments. The guide is focused on voice, but the general principles of device delivery, account readiness, adoption, and training apply to a large meeting deployment. |
|||

### Troubleshoot meeting and call quality 

Teams gives you two ways to monitor and troubleshoot call quality problems: [Call Analytics and Call Quality Dashboard](monitor-call-quality-qos.md). Call Analytics shows detailed information about the devices, networks, and connectivity related to the specific calls and meetings for each user. Call Analytics is designed to help admins and helpdesk agents troubleshoot call quality problems with specific calls, whereas the Call Quality Dashboard is designed to help admins and network engineers optimize a network. Call Quality Dashboard shifts focus from specific users and instead looks at aggregate information for an entire Teams organization. 

|Ask yourself|Action |
|------------|-------|
| Who will be responsible for monitoring and troubleshooting call quality issues? | Read [Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md) for information about permission levels required to troubleshoot call quality issues.|
|||

### Operate your meetings service

It's important that you understand the overall health of the Teams service so that you can proactively alert others in your organization of any event that affects the service. The [Operate my service](1-drive-value-operate-my-service.md) articles provide in-depth guidance for service operations.

|Ask yourself|Action |
|------------|-------|
|Who in my organization will be responsible for managing the meetings service? | Make sure this person has the Teams admin permissions they need in order to manage your meetings service. To learn more about Teams administrator roles see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md).|
|||


## Next steps
- [Drive adoption](adopt-microsoft-teams-landing-page.md) of meetings & conferencing throughout your organization.
- [Add audio conferencing](deploy-audio-conferencing-teams-landing-page.md)
- [Roll out cloud voice](cloud-voice-landing-page.md)
- Include featured apps - such as Planner - in your initial Teams rollout. Add other [apps, bots, & connectors](deploy-apps-microsoft-teams-landing-page.md) as you drive Teams adoption.
