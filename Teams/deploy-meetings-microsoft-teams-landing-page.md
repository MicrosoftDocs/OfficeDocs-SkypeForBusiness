---
title: Deploy Meetings in Microsoft Teams
description: Use these deployment resources to help you roll out meetings in Microsoft Teams.
ms.topic: article
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 01/07/2019
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
search.appverid: MET150
appliesto: 
- Microsoft Teams
---


# Deploy Meetings in Microsoft Teams

You've completed [Quick start](get-started-with-teams-quick-start.md). You've rolled out Teams with [chat, teams, channels, & apps](deploy-chat-teams-channels-microsoft-teams-landing-page.md) across your organization. Now you're ready to add the meetings workload, including [audio conferencing](deploy-audio-conferencing-teams-landing-page.md). Here's how.

## Meetings service decisions

Teams is designed to provide a great out-of-the-box collaboration experience for your organization, and most organizations find that the default settings work for them. This article helps you decide whether you need to change any of the default settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups starting with the core set of [changes you are more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, again based on your organization's needs.

## Meetings prerequisites 

Before scaling your meetings deployment across your organization, take time to review and confirm that your environment is ready to provide users with the best
possible experience. Review the following information and make any required changes to your environment as needed.

To get the best experience on Teams, your organization must have deployed Exchange Online and SharePoint Online, and you must have a verified domain for O365
such as *contoso.com*.

To scale meetings across your organization you should ensure that all user locations have internet access to connect to the Office 365 Services. At a minimum you should make sure that the following common ports are open to the internet from your user’s locations:-

- TCP ports 80 and 443 outgoing from clients that will use Teams
- UDP ports 3478 through 3481 outgoing from clients that will use Teams

You can use the [Network Testing Companion](https://www.powershellgallery.com/packages/NetworkTestingCompanion/1.5.2) to confirm that your network locations are ready for the voice and video traffic that will support your meetings experience.

| Ask yourself | Action |
|--------------|--------|
|Is my network ready for Teams meetings deployment? | To verify that your network is ready, see:<ul><li>[Prepare your organization's network for Microsoft Teams](https://docs.microsoft.com/en-us/MicrosoftTeams/prepare-network)</li><li>[Office 365 URLs and IP address ranges](https://docs.microsoft.com/en-us/MicrosoftTeams/office-365-urls-ip-address-ranges)</li></ul> |
|||

## Core deployment decisions

These are the settings that most organizations want to change (if the Teams default settings don't work for the organization).

### Teams administrators

Teams provides a set of custom administrator roles that can be used to manage Teams for your organization. The roles provide various capabilities to administrators. 

| Ask yourself | Action |
|--------------|--------|
|<ul><li>Who will be assigned the Teams Communications Administrator role?</li><li>Who will be assigned the Teams Communications Support Engineer role?</li><li>Who will be assigned the Teams Communications Support Specialist role?</li></ul> |<ul><li> To learn more about Teams administrator roles see [Use Microsoft Teams admin roles to manage Teams](https://docs.microsoft.com/en-us/MicrosoftTeams/using-admin-roles).</li><li> To assign admin roles, see [Assign administrator and non-administrator roles to users with Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).</li></ul> |
|||

### Meetings settings 

Meetings settings are used to control whether anonymous users can join Teams meetings, set up meeting invitations, and if you want to turn on Quality of Service (QoS), set the ports for real-time traffic. These settings will be used for all of the Teams meetings that users schedule in your organization. 

| Ask yourself | Action |
|--------------|--------|
|<ul><li>Will I customize the initial meeting settings?</li><li>Will I implement QoS?</li></ul> |<ul><li> See the [Meetings in Microsoft Team tutorial](https://docs.microsoft.com/en-US/MicrosoftTeams/tutorial-meetings-in-teams?WT.mc_id=TeamsAdminCenterCSH) for more information about meetings settings.</li><li>See [Quality of Service in Microsoft Teams](qos-in-teams.md) for information about QoS concepts. scenarios, and implementation.</li></ul>|
|||

### Meeting policies

Meeting policies are used to control what features are available to users when they join Microsoft Teams meetings. You can use the default policy or create one or more custom meeting policies for people that host meetings in your organization. 

See the [Meetings in Microsoft Team tutorial](https://docs.microsoft.com/en-US/MicrosoftTeams/tutorial-meetings-in-teams?WT.mc_id=TeamsAdminCenterCSH) for more information.

| Ask yourself | Action |
|--------------|--------|
|<ul><li>Will I customize the initial meeting policies?</li><li>Do I require multiple meeting policies?</li><li>How will I determine which groups of users get which meetings policy applied?</li></ul>| <need links>|
|||

### Conference bridges

Conference bridges let people dial into meetings using a phone. You can use the default settings for a conference bridge or change the phone numbers (toll and toll-free) and other settings, such as the PIN or the languages that are used. 

See [Audio Conferencing in Office 365](https://docs.microsoft.com/en-US/microsoftteams/audio-conferencing-in-office-365?WT.mc_id=TeamsAdminCenterCSH) for more information.

| Ask yourself | Action |
|--------------|--------|
|<ul><li>Will I add new bridge numbers?</li><li>Will I modify the bridge settings?</li></ul>|<need links> |
|||

### Live events policies

Teams live events policies are used to manage event settings for groups of users. You can use the default policy or create additional policies that can be assigned to users who hold live events within your organization. 

See [the live events articles](https://docs.microsoft.com/en-US/microsoftteams/teams-live-events/what-are-teams-live-events?WT.mc_id=TeamsAdminCenterCSH) for more information about planning for, setting up, and configuring Teams live events.

| Ask yourself | Action |
|--------------|--------|
|<ul><li>Will I customize the initial live events policies? </li><li>Do I require multiple policies?</li><li>How will I determine which groups of users get which policy applied?</li></ul>| <need links>|
|||

### Meeting room and personal devices

Meetings bring together content, chat, sharing, audio, and video. When taking part in meetings, your users will benefit from using devices such as room systems, phones, headsets, and cameras that have been designed to give a great experience with Microsoft Teams. 

See [Intelligent Communications for devices](https://products.office.com/en-gb/microsoft-teams/across-devices?ms.url=officecomteamsdevices&rtc=1) for more information about the types of personal and room devices available.

| Ask yourself | Action |
|--------------|--------|
|<ul><li>Will I purchase and deploy personal devices for my users? </li><li>Will I purchase and deploy room system devices for my conference rooms?</li></ul> | <need links> |
|||

### Reporting

You can use activity reports to see how users in your organization are using Microsoft Teams. For example, if some don’t use Teams yet, they might not know how to get started or understand how they can use Teams to be more productive and collaborative. Your organization can use the activity reports to decide where to prioritize training and communication efforts. 

See [Use activity reports for Microsoft Teams(https://docs.microsoft.com/en-gb/MicrosoftTeams/teams-activity-reports) for more information.

| Ask yourself | Action |
|--------------|--------|
|<ul><li>Who will be responsible for reporting?</li><li>Who will be responsible for monitoring usage? </li></ul>|<Need links> |
|||

## Additional deployment decisions

You may want to change these settings, based on your organization's needs and configuration.

### Bandwidth planning 

Bandwidth planning lets organizations estimate the bandwidth that will be required to support meetings across their wide area networks and internet links so they can confirm that the network is correctly provisioned to support a scaled out meeting service. 

| Ask yourself | Action |
|--------------|--------|
| Will I undertake bandwidth planning prior to and during my rollout of Meetings? |See [Network Readiness](https://docs.microsoft.com/en-gb/MicrosoftTeams/3-envision-evaluate-my-environment#network-readiness) for more information and links to tools to make the planning process simpler.|
|||

### Meeting recording and archiving | 

Users can record their meetings and group calls to capture audio, video, and screen sharing activity. There is also an option for recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and search for important discussion items in the transcript. The recording happens in the cloud and is saved in Microsoft Stream, so users can share it securely across their organization. 

See [Teams cloud meeting recording](https://docs.microsoft.com/en-gb/MicrosoftTeams/cloud-recording) for more information 

| Ask yourself | Action |
|--------------|--------|
| Will I turn on the meeting transcription service?|<need link>|
|||

### Conference room systems rollout

Organizations with many conference rooms may want to consider a structured approach to inventorying their rooms, identifying the appropriate devices, and then rolling them out. 

The [Plan Skype Room Systems v2](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/clients-and-devices/skype-room-systems-v2-0) articles introduce these concepts and provide more information.

| Ask yourself | Action |
|--------------|--------|
| Will I plan my room systems deployment?|<need link>|
|||

### Cloud video interop

Cloud video interop makes it possible for third-party meeting room devices to join Teams meetings. 

Video teleconferencing with content collaboration helps you make the most out of meetings. However, meeting room systems and devices are expensive to upgrade. Cloud video interop for Microsoft Teams works with third-party systems and delivers a native meeting experience for all participants – in meeting rooms or inside Teams clients. 

| Ask yourself | Action |
|--------------|--------|
| Will I use a cloud video interop solution as part of my room systems deployment? | See [Cloud Video Interop for Microsoft Teams](https://docs.microsoft.com/en-gb/MicrosoftTeams/cloud-video-interop) for more information.|
|||

### Personal device rollout

When planning a larger rollout of personal devices to support meetings or voice deployments, you might want to consider using a repeatable site-by-site rollout process that delivers repeatable quality. The [Site enablement playbook for Microsoft Teams](https://docs.microsoft.com/en-gb/MicrosoftTeams/3-onboard-deploy-my-service#site-enablement-playbook-for-microsoft-teams-voice-workloads) provides a good foundation that you can use for your own deployments. The guide is focused on voice, but the general principles of device delivery, account readiness, adoption, and training apply to a large meeting deployment.

| Ask yourself | Action |
|--------------|--------|
|Will I use a site-by-site approach to deploy meetings? | <need link> |
|||

### Meeting quality and troubleshooting

Microsoft Teams gives you two ways to monitor and troubleshoot call quality problems: Call Analytics and Call Quality Dashboard. Call Analytics shows detailed information about the devices, networks, and connectivity related to the specific calls and meetings for each user. Where Call Analytics is designed to help admins and helpdesk agents troubleshoot call quality problems with specific calls, the Call Quality Dashboard is designed to help admins and network engineers optimize a network. Call Quality Dashboard shifts focus from specific users and instead looks at aggregate information for an entire Teams organization. | See [Call Analytics and Call Quality Dashboard](https://docs.microsoft.com/en-gb/MicrosoftTeams/difference-between-call-analytics-and-call-quality-dashboard) for more information.

|Ask yourself|Action |
|------------|-------|
| Who will be responsible for monitoring and troubleshooting call quality issues? | See [Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md) for information about permission levels required to troubleshoot call quality issues.|
|||

### Operating your meetings service

It’s important that you understand the overall health of the Microsoft Teams service so that you can proactively alert others in your organization of any event that affects the service. The [Operate my service](https://docs.microsoft.com/en-gb/MicrosoftTeams/1-drive-value-operate-my-service) articles provide in-depth guidance for service operations.

|Ask yourself|Action |
|------------|-------|
|Who in my organization will be responsible for managing the meetings service? | <need link>|
|||



