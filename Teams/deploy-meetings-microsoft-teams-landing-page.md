---
title: Deploy meetings in Microsoft Teams
description: Use these deployment resources to help you roll out meetings in Microsoft Teams.
layout: LandingPage
ms.topic: article
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 10/31/2018
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
search.appverid: MET150
appliesto: 
- Microsoft Teams
---
# Deploy meetings in Microsoft Teams


You've completed [Quick start](get-started-with-teams-quick-start.md). You've rolled out Teams with [chat, teams, & channels](deploy-chat-teams-channels-microsoft-teams-landing-page.md) across your organization. Now you're ready to add the Meetings workload, including audio conferencing. Here's how:

## Meetings service decisions


Teams has been designed to provide a great out of the box collaboration experience for your organization, depending on your organization’s complexity and business requirements you many want to adjust the initial configuration. 

This section walks you through the main service decisions that you may need to make as part of the technical implementation to define your configuration, in this section these decisions relate to the key collaboration components of chat, teams, channels, apps and tabs.

We recommend that all organizations work through the core decisions and then if your organization has additional requirements to review the following material.

# Meetings Service Decisions 

Teams has been designed to provide a great out of the box collaboration
experience for your organization, depending on your organisation’s complexity
and business requirements you many want to adjust the initial configuration.

This section walks you through the main service decisions that you may need to
make as part of the technical implementation to define your configuration, in
this section these decisions relate to the key meeting components of meetings,
personal devices, room systems and audio conferencing.

We recommend that all organisations work through the core decisions and then if
your organisation has additional requirements to review the following material.

## Meeting Prerequisites 

Prior to scaling your meetings deployment across your organization, take time to
review and confirm your environment is ready to provide users with the best
possible experience. Review the following information and make any required
changes to your environment as needed.

To get the best experience on Teams, your organization must have deployed
Exchange Online and SharePoint Online and you have a verified domain for O365
such as contoso.com.

To scale meetings across your organisation you should ensure that all user
locations have Internet access to connect to the Office 365 Services, at a
minimum you should ensure that the following common ports are open to the
Internet from your user’s locations:-

• Open TCP ports 80 and 443 outgoing from clients that will use Teams.

• Open UDP ports 3478 through 3481 outgoing from clients that will use Teams

You can leverage the [Network Testing
Companion](https://www.powershellgallery.com/packages/NetworkTestingCompanion/1.5.2)
to confirm that your network locations are ready for the voice and video traffic
that will support your meetings experience.

|<img src="audio-conferencing-image7.png" />| Is my network ready for Teams meetings deployment? |
|------------------------------------------|----------------------------------------------------|


The following articles provide further reading related to network readiness.

### Network Readiness

<https://docs.microsoft.com/en-us/MicrosoftTeams/prepare-network>

### Office 365 URLs and IPs

<https://docs.microsoft.com/en-us/MicrosoftTeams/office-365-urls-ip-address-ranges>

## Core service decisions

### Teams administrators

Teams provides a set of custom administrator roles that can be used to manage
Teams for your organization. The roles provide various capabilities to
administrators. To learn more about Teams administrator roles see [Use Microsoft
Teams admin roles to manage
Teams](https://docs.microsoft.com/en-us/MicrosoftTeams/using-admin-roles).

|<img src="media/audio_conferencing_image7.png" />| Who will be assigned Teams Communications Administrator role? |
|------------------------------------------|---------------------------------------------------------------|


-   Who will be assigned Teams Communications Support Engineer role?

-   Who will be assigned Teams Communications Support Specialist role?

### Meetings Settings 

Meeting settings are used to control whether anonymous users can join Teams
meetings, to set up your meeting invitations and if you want to enable Quality
of Service (QoS), you can set the ports for real-time traffic. These settings
will be used for all of the Teams meetings that users schedule in your
organization.

The [Meetings in Microsoft Team
tutorial](https://docs.microsoft.com/en-US/MicrosoftTeams/tutorial-meetings-in-teams?WT.mc_id=TeamsAdminCenterCSH)
provides more information.

|<img src="media/audio_conferencing_image7.png" />| Will you customize the initial meeting settings? |
|------------------------------------------|--------------------------------------------------|


### Meetings Policies 

Meeting policies are used to control what features are available to users when
they join Microsoft Teams meetings. You can use the default policy or create one
or more custom meeting policies for people that host meetings in your
organization.

The [Meetings in Microsoft Team
tutorial](https://docs.microsoft.com/en-US/MicrosoftTeams/tutorial-meetings-in-teams?WT.mc_id=TeamsAdminCenterCSH)
provides more information.

|<img src="media/audio_conferencing_image7.png" />| Will you customize the initial meeting policies? |
|------------------------------------------|--------------------------------------------------|


-   Do you require multiple meeting policies?

-   How will you determine which groups of users get which meetings policy
    applied?

### Conference bridges

Conference bridges let people dial into meetings using a phone. You can use the
default settings for a conference bridge or change the phone numbers (toll and
toll-free) and other settings such as the PIN or the languages that are used.

The [Audio Conferencing in Office
365](https://docs.microsoft.com/en-US/microsoftteams/audio-conferencing-in-office-365?WT.mc_id=TeamsAdminCenterCSH)
article provides more information.

|<img src="media/audio_conferencing_image7.png" />| Will you add new Bridge numbers? |
|------------------------------------------|----------------------------------|


-   Will you modify the Bridge settings?

### Live events policies

Teams live events policies are used to manage event settings for groups of
users. You can use the default policy or create additional policies that can be
assigned to users that hold live events within your organization.

The [What are Microsoft Teams live
events](https://docs.microsoft.com/en-US/microsoftteams/teams-live-events/what-are-teams-live-events?WT.mc_id=TeamsAdminCenterCSH)
article provides more information.

|<img src="media/audio_conferencing_image7.png" />| Will you customize the initial Live Events policies? |
|------------------------------------------|------------------------------------------------------|


-   Do you require multiple policies?

-   How will you determine which groups of users get which policy applied?

### Meeting Room and Personal Devices 

Meetings bring together content, chat, sharing, audio and video, when taking
part in meetings your users will benefit from using devices such as room
systems, phones, headsets and cameras that have been designed to give a great
experience with Microsoft Teams.

The [Intelligent Communications for
devices](https://products.office.com/en-gb/microsoft-teams/across-devices?ms.url=officecomteamsdevices&rtc=1)
page provides more information about the types of personal and room devices
available.

|<img src="media/audio_conferencing_image7.png" />| Will you purchase and deploy personal devices for your users? |
|------------------------------------------|---------------------------------------------------------------|


-   Will you purchase and deploy room system devices for your conference rooms?

### Reporting 

You can use activity reports to see how users in your organization are using
Microsoft Teams. For example, if some don’t use Teams yet, they might not know
how to get started or understand how they can use Teams to be more productive
and collaborative. Your organization can use the activity reports to decide
where to prioritize training and communication efforts.

The [Use activity reports for Microsoft
Teams](https://docs.microsoft.com/en-gb/MicrosoftTeams/teams-activity-reports)
article provides more information.

|<img src="media/audio_conferencing_image7.png" />| Who will be responsible for reporting? |
|------------------------------------------|----------------------------------------|


-   Who will be responsible for monitoring usage?

## Additional service decisions that may apply based on organizational profile

Customers with additional complexity or compliance requirements may also want to
consider the following in addition to the Core service decisions outlined above.

### Bandwidth Planning 

Bandwidth planning enables organizations to estimate the bandwidth that will be
required to support meeting across their wide area networks and internet links
to confirm that the network is correctly provisioned to support a scaled out
meeting service.

The [Network
Readiness](https://docs.microsoft.com/en-gb/MicrosoftTeams/3-envision-evaluate-my-environment#network-readiness)
article provides more information and links to tools to make the planning
process simple to undertake.

|<img src="media/audio_conferencing_image7.png" />| Will you undertake bandwidth planning prior to and during your rollout of meetings? |
|------------------------------------------|-------------------------------------------------------------------------------------|


### Meeting Recording / Archiving 

Users can record their meetings and group calls to capture audio, video, and
screen sharing activity. There is also an option for recordings to have
automatic transcription, so that users can play back meeting recordings with
closed captions and search for important discussion items in the transcript. The
recording happens in the cloud and is saved to Microsoft Stream, so users can
share it securely across their organization.

The [Teams cloud meeting
recording](https://docs.microsoft.com/en-gb/MicrosoftTeams/cloud-recording)
article provides more information

|<img src="media/audio_conferencing_image7.png" />| Will you enable the meeting transcription service? |
|------------------------------------------|----------------------------------------------------|


### Conference Room Systems Rollout Approach 

Organisations with many conference rooms may want to consider a structured
approach to inventorying their rooms, identifying the appropriate devices and
then rolling them out.

The Plan Skype Room Systems v2 articles introduces these concepts and provides
more information

|<img src="media/audio_conferencing_image7.png" />| Will you plan your room systems deployment? |
|------------------------------------------|---------------------------------------------|


### Cloud Video Interop

Cloud Video Interop enables third-party meeting room devices to join Microsoft
Teams meetings.

Video teleconferencing with content collaboration helps you make the most out of
meetings. However, meeting room systems and devices are expensive to upgrade.
Cloud Video Interop for Microsoft Teams works with 3rd party systems and
delivers a native meeting experience for all participants – in meeting rooms or
inside of Teams clients.

The [Cloud Video Interop for Microsoft
Teams](https://docs.microsoft.com/en-gb/MicrosoftTeams/cloud-video-interop)
article provides more information.

|<img src="media/audio_conferencing_image7.png" />| Will you use a Cloud Video interop solution as part of your room systems deployment? |
|------------------------------------------|--------------------------------------------------------------------------------------|


### Personal Device Rollout 

When planning a larger rollout of personal devices to support meetings or voice
deployments it is often useful to consider leveraging a repeatable site by site
rollout process that delivers repeatable quality.

The [Site enablement playbook for Microsoft
Teams](https://docs.microsoft.com/en-gb/MicrosoftTeams/3-onboard-deploy-my-service#site-enablement-playbook-for-microsoft-teams-voice-workloads)
provides a good foundation that you can leverage for your own deployments, the
guide was written focussing on voice however the general principles of device
delivery, account readiness, adoption and training apply to a large meeting
deployment.

|<img src="media/audio_conferencing_image7.png" />| Will you leverage a site by site approach to deploying meetings? |
|------------------------------------------|------------------------------------------------------------------|


### Meeting Quality 

Microsoft Teams gives you two ways to monitor and troubleshoot call-quality
problems: Call Analytics and Call Quality Dashboard. This article describes both
and tells you when to use each one.

The [Call Analytics and Call Quality
Dashboard](https://docs.microsoft.com/en-gb/MicrosoftTeams/difference-between-call-analytics-and-call-quality-dashboard)
article provides more information.

|<img src="media/audio_conferencing_image7.png" />| Who will be responsible for monitoring and troubleshooting call quality issues? |
|------------------------------------------|---------------------------------------------------------------------------------|


### Operating your meetings service 

It’s important that you understand the overall health of the Microsoft Teams
service so that you can proactively alert others in your organization of any
event that affects the service.

The [Operate my
service](https://docs.microsoft.com/en-gb/MicrosoftTeams/1-drive-value-operate-my-service)
articles provides in-depth guidance for service operations.

|<img src="media/audio_conferencing_image7.png" />| Who in your organisation will be responsible for managing the meetings service? |
|------------------------------------------|---------------------------------------------------------------------------------|



