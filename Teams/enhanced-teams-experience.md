---
title: Microsoft Teams Premium - Overview for admins
author: wlibebe
ms.author: wlibebe
manager: pamgreen
ms.reviewer: spraveen, margidesai
ms.date: 7/11/2024
ms.topic: conceptual
ms.service: msteams
ms.subservice: teams-premium
search.appverid: MET150
ms.collection:
  - M365-collaboration
  - m365initiative-meetings
  - highpri
audience: Admin
appliesto:
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.custom:
  - Licensing
description: Learn about Microsoft Teams Premium for administrators and IT Professionals.
---

# Microsoft Teams Premium - Overview for admins

![Information icon](media/info.png) **The features described in this article require Teams Premium.** Teams Premium licenses aren't a replacement for Teams licenses. Users must have both a Teams license and a Teams Premium license for Teams and Teams Premium features to work properly. For more information about feature availability and licensing, see [Teams Premium licensing](teams-add-on-licensing/licensing-enhance-teams.md).

Teams Premium is an add-on license that provides the following enhancements to Teams:  

- Enhanced meeting experiences for your end users
- Enhanced security and protection for meetings
- Enhanced administrative and telemetry support

This article, written for IT Pros and admins who are deploying and configuring Teams Premium, describes the available features and provides links to more detailed documentation.

> [!IMPORTANT]
> Now that Teams Premium has reached general availability, some features that were previously accessible with Teams now require a Teams Premium license for access.
>
> For admins to manage Teams Premium features, their tenant needs at least one user with an active [Teams Premium license](/MicrosoftTeams/teams-add-on-licensing/licensing-enhance-teams).

The following sections in this article describe the Teams Premium enhancements for:

- [Protection and advanced management for meetings](#protection-and-advanced-management-for-meetings)
- [Personalized meetings](#personalized-meetings)
- [Premium events](#premium-events)
- [Virtual Appointments](#advanced-virtual-appointments)
- [Intelligent meeting features](#intelligent-meeting-features)
- [Custom 3D Immersive Mesh Experiences](#custom-3d-immersive-mesh-experiences)
- [Advanced Places Workplace Collaboration](#advanced-places-workplace-collaboration)
- [Intelligent call recap](#intelligent-call-recap)

For more general information about Teams meetings and premium events, see the following articles:

- [Meetings, webinars, and town halls](overview-meetings-webinars-town-halls.md)
- [Plan for Teams meetings](plan-meetings.md)
- [Plan for Teams webinars](plan-webinars.md)
- [Plan for Teams town halls](plan-town-halls.md)

> [!NOTE]
> We'll continue to update this article. Check back often for links to new content.

## Protection and advanced management for meetings

Teams Premium provides more ways to safeguard and monitor users' Teams experiences with the following key features:

- **Advanced collaboration analytics** - View external collaboration activity data on your users, teams, federated domains, channels, and guests.

- **Audio quality alerts** - Set up alerts for in-progress meeting audio issues and get notified immediately when your specified users experience issues.

- **Custom user policy packages** - Create policy packages to simplify, streamline, and help provide consistency when managing policies for groups of users across your organization.

- **End-to-end encryption** - Enforced through a sensitivity label, end-to-end encryption provides increased security for meetings that require a higher level of protection.

- **Hide attendee names** - Meeting and webinar organizers can hide the names of attendees from other attendees in the stage, roster, and chat.

- **Manage what attendees see** - Meeting organizers can decide whose avatars or video feeds to spotlight during a Teams meeting while others are hidden from view.

- **Prevent users from sharing content in external Teams meetings** - Control whether users in your org with a Teams Premium license can share content when attending external Teams meetings.

- **Screen sharing quality alerts** - Set up alerts for in-progress meeting screen sharing issues and get notified immediately when your specified users experience issues.

- **Sensitivity labels** - Extended capabilities for sensitivity labels to control meeting settings normally controlled by the meeting organizer. These capabilities include new settings to control lobby, chat, chat copy, presentation, and recording functions.

- **Real time telemetry and retention** - Real-time telemetry is gathered automatically for all users who have a Teams Premium license and retained for seven days.

- **Teams Premium feature usage report** - View aggregated usage of Teams Premium features by users in your org.

- **Video quality alerts** - Set up alerts for in-progress meeting video issues and get notified immediately when your specified users experience issues.

- **Watermarking** - Enforced through a sensitivity label, watermarks display the email address of a meeting participant. Watermarks are useful for protecting confidential information shared in meetings.

| Feature/Task  | Can admins turn this feature on/off? | Documentation for admins | Documentation for your end users |
| --------- | -----------| ----------- | ------------ |
| Advanced collaboration analytics |No, contact support for assistance.| [Advanced Collaboration Analytics for Microsoft Teams](advanced-collaboration-analytics.md) | No end-user control |
| Audio quality alerts |Yes, you can add or remove users.| [Alerts for in-progress meeting audio quality issues](/MicrosoftTeams/alerts/alerts-in-progress-meeting-audio) | No end-user control |
| Custom user policy packages |Yes| [Managing policy packages in Teams](manage-policy-packages.md) | No end-user control |
| End-to-end encryption (E2EE) | Yes |[Encryption for sensitive meetings](end-to-end-encrypted-meetings.md) | [Use encryption](https://support.microsoft.com/office/use-end-to-end-encryption-for-teams-meetings-a8326d15-d187-49c4-ac99-14c17dbd617c)  |
| Hide attendee names | Yes |[Allow meeting and webinar organizers to hide the names of attendees](hide-attendee-names.md) | [Hide attendee names in Teams meetings and webinars](https://support.microsoft.com/office/hide-attendee-names-in-teams-meetings-and-webinars-00389c74-ee61-48b5-bad8-8295600085ed) |
| Manage what attendees see | No, contact support for assistance.| No admin control | [Manage what attendees see in Teams meetings](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16)|
| Prevent copying chat content to clipboard |Yes, use the Teams admin center to add or delete chat content copying restrictions in your meeting templates. Use the Microsoft Purview compliance portal to turn labels with chat content copying restrictions on or off.| [Manage chat for sensitive Teams meetings](manage-chat-sensitive-meetings.md) | No end-user control |
| Prevent users from sharing content in external meetings|Yes| [Prevent users from sharing content in external meetings](block-external-content-share.md) | No end-user control |
| Real-time telemetry and retention|No, contact support for assistance.| [Use real-time telemetry to troubleshoot poor meeting quality](use-real-time-telemetry-to-troubleshoot-poor-meeting-quality.md#where-to-find-per-user-real-time-troubleshooting-telemetry) | No end-user control |
| Restrict who can record | Yes, use the Teams admin center to add or delete recording restrictions in your meeting templates. Use the Microsoft Purview compliance portal to turn labels with recording restrictions on or off.|[Manage recordings for sensitive meetings](manage-meeting-recording-options.md) | [Record a meeting](https://support.microsoft.com/office/record-a-meeting-in-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24?storagetype=stage#bkmk_whocanstartorstoparecording) |
| Screen sharing quality alerts|Yes, you can add or remove users.| [Alerts for in-progress meeting screen sharing issues](/MicrosoftTeams/alerts/alerts-in-progress-meeting-screen-sharing) | No end-user control |
| Sensitivity labels | Yes, use the Microsoft Purview compliance portal to turn labels on or off.|[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md) | [Sensitivity labels for Teams meetings](https://support.microsoft.com/office/sensitivity-labels-for-teams-meetings-2b244d1d-72d0-471e-8e58-c41079e190fb)|
| Teams Premium feature usage report|No, contact support for assistance.| [Teams Premium feature usage report](/microsoftteams/teams-analytics-and-reports/teams-premium-usage-report) | No end-user control |
| Templates, labels, and policies |Yes, use the Teams admin center to add or delete meeting templates. Use the Microsoft Purview compliance portal to turn labels on or off.| [Templates, sensitivity labels, and policies](meeting-templates-sensitivity-labels-policies.md)  | [Use custom templates](https://support.microsoft.com/office/use-custom-templates-for-teams-meetings-78279be9-3283-4999-b24e-96fb0da2fb4f) |
| Video quality alerts|Yes, you can add or remove users.| [Alerts for in-progress meeting video quality issues](/MicrosoftTeams/alerts/alerts-in-progress-meeting-video) | No end-user control |
| Watermarks | Yes | [Require a watermark for meetings](watermark-meeting-content-video.md) | [Watermarks for meetings](https://support.microsoft.com/office/watermark-for-teams-meetings-a9166432-f429-4a19-9a72-c9e8fdf4f589)|

## Personalized meetings

Teams Premium provides more ways to personalize your Teams meeting experiences with the following key features:

- **Custom meeting backgrounds for organizations** - Create and define custom meeting backgrounds that your users can use during meetings and events.

- **Custom together mode scenes for organizations** -Customize, create, or accept together mode scenes to digitally combine participants into a single virtual scene.

- **Meeting templates** - Control meeting settings that the meeting organizer normally controls. With templates, you can create consistent meeting experiences in your organization and help enforce compliance requirements and business rules.

- **Meeting themes** - Set up and create meeting themes for various business units and departments within a single tenant.

- **Real Time Messaging Protocol (RTMP)-In** - Organizers can produce their Teams meetings directly from an external hardware or software-based encoder.

| Feature/Task |  Can admins turn this feature on/off? | Documentation for admins | Documentation for your end users |
| -------------------- | ----------- | ----------- | ------------ |
| Custom meeting backgrounds for organizations | Yes| [Meeting backgrounds](custom-meeting-backgrounds.md)| [Use meeting themes](https://support.microsoft.com/office/use-meeting-themes-for-teams-meetings-fbfd826d-1112-4790-918a-5a82cac8250e) |
| Custom together mode scenes for organizations | No, contact support for assistance.|[Content for you and your developers](/microsoftteams/platform/apps-in-teams-meetings/teams-together-mode)| |
| Meeting templates | Yes| - [Overview](custom-meeting-templates-overview.md)<br>- [Create a custom meeting template](create-custom-meeting-template.md)| [Use custom templates](https://support.microsoft.com/office/use-custom-templates-for-teams-meetings-78279be9-3283-4999-b24e-96fb0da2fb4f) |
| Meeting themes | Yes| [Themes for Teams meetings](meeting-themes.md) | [Use meeting themes](https://support.microsoft.com/office/use-meeting-themes-for-teams-meetings-fbfd826d-1112-4790-918a-5a82cac8250e) |
| RTMP-In | Yes| [Manage RTMP-In for Teams meetings](meetings-rtmp-in.md)|[Use RTMP-In in a Teams meeting](https://support.microsoft.com/office/use-rtmp-in-in-a-teams-meeting-789d6090-8511-4e2e-add6-52a9f551be7f) |

## Premium events

Teams Premium offers advanced features to enhance your town halls and webinars.

- **[Town halls](#town-halls)** bring interactive video streaming to a new level. Town halls are meant for one-to-many communications where the presenters, organizers, and co-organizers are leading the interactions. The audience participation is primarily to view and react to the content being shared.

- **[Webinars](#webinars)** provide a two-way interactive virtual event where the presenters deliver information to attendees. This format provides extra control for an organizer over the conversation and participants.

The following sections describe Teams Premium feature enhancements for town halls and webinars. For more information about planning for town halls, webinars, and meetings in general, see [Plan for town halls](plan-town-halls.md), [Plan for webinars](plan-webinars.md), and [Meetings, webinars, and town halls](overview-meetings-webinars-town-halls.md).

### Town halls

Teams Premium provides more ways to elevate Teams town halls in your org with the following key features:

- **Custom emails for town halls** - Organizers and co-organizers can customize the town hall email templates sent to attendees.
- **Increased broadcast and Q&A capacity**- Organizers can broadcast their town halls to 20,000 attendees. All attendees can use Q&A to interact with presenters, organizers, and co-organizers.
- **Live translated captions**- The organizer can choose up to 10 languages for attendees to use when translating captions during the town hall.
- **Microsoft eCDN** - Optimize network performance for video streaming within an enterprise network. Microsoft eCDN allows millions of enterprise users around the world to communicate face-to-face efficiently and reliably. You can use the Microsoft eCDN or select one of our partner providers for Premium town halls.
- **Real time monitoring of the attendee experience** - Admins can use the eCDN analytics dashboard to troubleshoot the attendee experience during live town halls.
- **Town hall insights** - Town hall organizers can troubleshoot town halls while they're live.

| Feature/Task | Can admins turn this feature on/off? |Documentation for admins| Documentation for your end users |
| -------------------- |  ----------- | ----------- | ----------- |
| Custom emails for town halls | Yes | [Manage email communications](manage-email-communications.md) |[Schedule a town hall in Microsoft Teams](https://support.microsoft.com/office/schedule-a-town-hall-in-microsoft-teams-d493b5cc-9f61-4dac-8027-d837dafb7a4c#bkmk_town_hall_invites) |
| Live translated captions | Yes |[Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)|[Use live captions in Microsoft Teams meetings](https://support.microsoft.com/office/use-live-captions-in-microsoft-teams-meetings-4be2d304-f675-4b57-8347-cbd000a21260) |
| Microsoft eCDN |Yes |[How to enable Microsoft eCDN](/ecdn/how-to/enable-microsoft-ecdn-for-your-tenant)|No end user control |
| Manage which eCDN provider Premium town halls use |Yes |[Enterprise content delivery networks for streaming Microsoft Teams events](streaming-ecdn-enterprise-content-delivery-network.md#manage-the-ecdn-solution-for-premium-town-halls)|No end user control |
| Real time monitoring of the attendee experience | No, contact support for assistance. |[eCDN Analytics](/ecdn/technical-documentation/analytics)|No end user control |
| Town hall insights | No, contact support for assistance. | No admin control|[Town hall insights in Microsoft Teams](https://support.microsoft.com/office/town-hall-insights-in-microsoft-teams-def99575-61bf-4ea2-ad0e-c6e75dce7741) |

### Webinars

Teams Premium provides more ways to elevate Teams webinars in your org with the following key features:

- **Custom emails for webinars** - Organizers and co-organizers can customize the webinar email templates sent to attendees.
- **Custom webinar reminder email send times** - Webinar reminder emails are automatically sent to registrants an hour before the event starts. With Teams Premium, organizers can edit the send time to notify attendees sooner.
- **Enable and manage the waitlist for webinars beyond capacity** - When the webinar's registration reaches capacity, organizers can manage overflow registration requests through a waitlist.
- **Hide attendee names** - Meeting and webinar organizers can hide the names of attendees from other attendees in the stage, roster, and chat.
- **Limit registration start and end times** - Organizers can set a time window during which potential attendees can register for their webinar.
- **Manage what attendees see** - Webinar organizers can decide whose avatars or video feeds to spotlight during a Teams webinar while others are hidden from view.
- **Manually approve registrants** - Organizers can approve or deny requests to register for their webinar.
- **Real Time Messaging Protocol (RTMP)-In** - Organizers can produce their Teams webinar directly from an external hardware or software-based encoder.

| Feature/Task | Can admins turn this feature on/off? | Documentation for admins | Documentation for your end users |
| -------------------- | ----------- | ----------- | ----------- |
| Custom emails for webinars| Yes| [Manage email communications](manage-email-communications.md) |[Manage webinar emails in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-emails-in-microsoft-teams-d0006848-f707-494f-b0a4-eeebcbc723be) |
| Enable and manage the waitlist for webinars beyond capacity| No, contact support for assistance.| No admin control|[Manage webinar registration in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-registration-in-microsoft-teams-923f382a-0cca-433a-b38d-7461971192d1) |
| Hide attendee names | Yes | [Allow meeting and webinar organizers to hide the names of attendees](hide-attendee-names.md) | [Hide attendee names in Teams meetings and webinars](https://support.microsoft.com/office/hide-attendee-names-in-teams-meetings-and-webinars-00389c74-ee61-48b5-bad8-8295600085ed)|
| Limit registration start and end times | No, contact support for assistance.| No admin control|[Manage webinar registration in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-registration-in-microsoft-teams-923f382a-0cca-433a-b38d-7461971192d1) |
| Manage what attendees see | No, contact support for assistance.| No admin control | [Manage what attendees see in Teams meetings](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16)|
| Manually approve registrants |No, contact support for assistance.| No admin control |[Manage webinar registration in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-registration-in-microsoft-teams-923f382a-0cca-433a-b38d-7461971192d1) |
| RTMP-In | Yes| [Manage RTMP-In for Teams meetings](meetings-rtmp-in.md)|[Use RTMP-In in a Teams meeting](https://support.microsoft.com/office/use-rtmp-in-in-a-teams-meeting-789d6090-8511-4e2e-add6-52a9f551be7f) |

## Advanced Virtual Appointments

With any Microsoft 365 license, your end users can use basic Virtual Appointments capabilities to schedule and join business-to-customer meetings. For example, users can schedule appointments in the Bookings calendar and external attendees can join through a browser without having to download Teams.

To learn more about Virtual Appointments, see [Manage the Virtual Appointments app for your organization in Microsoft Teams](manage-virtual-appointments-app.md).

Teams Premium provides advanced Virtual Appointment capabilities, such as:

- Analytics at departmental and organizational levels
- Consumption and usage analytics for admins in the Teams admin center
- Custom lobby room with branding and logos​
- Queue of scheduled and on-demand appointments
- Short Message Service (SMS) notifications

| Feature/Task  | Can admins turn this feature on/off? | Documentation for admins |
| -------------------- | ----------- | ----------- |
| Reporting | No, contact support for assistance.| [Virtual Appointments usage report](/microsoft-365/frontline/virtual-appointments-usage-report?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json)<br>[Advanced Virtual Appointments activity report](/microsoft-365/frontline/advanced-virtual-appointments-activity-report?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json) |
| SMS notifications  | Yes| [SMS text notifications](bookings-app-admin.md#sms-text-notifications) |

## Intelligent meeting features

Teams Premium provides the following key AI-powered meetings features:

- **Decorate my background** - Your users can use AI to decorate their backgrounds.
- **Intelligent meeting recap** - Give your users a more personalized rundown of their meetings with intelligent meeting recap.
- **Live translated captions** -  Allow your users to see captions translated into the language they’re most comfortable with.
- **Live translated transcription** - Your users can understand each other better during a meeting or event by translating the meeting transcript into the language they're most comfortable with.

| Feature/Task  | Can admins turn this feature on/off? | Documentation for admins | Documentation for your end users |
| -------------------- | -----------| ----------- | ------------ |
| Decorate my background | No, contact support for assistance. | No admin control | [Decorate your background](https://adoption.microsoft.com/microsoft-teams-premium/decorate-your-background/)|
| Intelligent meeting recap| No, contact support for assistance.<sup>1</sup>|[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md) | [Meeting recap in Microsoft Teams](https://support.microsoft.com/office/meeting-recap-in-microsoft-teams-c2e3a0fe-504f-4b2c-bf85-504938f110ef#bkmk_intelligent_meeting_recap) |
| Live translated captions | Yes | [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)|[Use live captions in Microsoft Teams meetings](https://support.microsoft.com/office/use-live-captions-in-microsoft-teams-meetings-4be2d304-f675-4b57-8347-cbd000a21260) |
| Live translated transcription | Yes |  [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md) | [View live transcription in Microsoft Teams meetings](https://support.microsoft.com/office/view-live-transcription-in-microsoft-teams-meetings-dc1a8f23-2e20-4684-885e-2152e06a4a8b)|

<sup>1</sup>If you toggle the **Transcription** and **Recording** settings to **Off** in your **Meeting policies**, intelligent meeting recap isn't available for users with this policy.

## Custom 3D Immersive Mesh Experiences

With a Teams Premium license, users can explore immersive 3D experiences for the workplace. Host customized single or multi-room immersive events in the Mesh app for up to 200 attendees, available cross-platform on PC and Meta Quest VR devices.

Teams Premium provides custom Mesh experience capabilities for your users, such as:

- **Host immersive events tailored to your business needs** - Elevate team engagement during employee onboardings, trainings, product showcases, or any hybrid business scenarios by creating engaging and interactive experiences with the Mesh app.
- **Create custom 3D experiences** - Creators can easily use no-code tools to add videos, and images to pre-created and custom environments. Developers and technical artists can leverage scripting, physics, and embedded web content within the Mesh toolkit in Unity to build custom 3D environments with enhanced interactivity.
- **Create custom avatars, explore environments, and communicate virtually** - Customizable avatars can navigate around 3D environments to experience content and have multiple simultaneous discussions with colleagues using spatial audio built-in to the experience.
- **Integrated with Microsoft 365** - Mesh provides enterprise-grade security and privacy, built on trusted platforms.

| Feature/Task  | Can admins turn this feature on/off? | Documentation for admins |Documentation for end users |
| -------------------- | ----------- | ----------- |----------- |
| Set up Mesh | Yes, use [App centric management](app-centric-management.md) to allow or prevent users from using Mesh.| [Configure Microsoft Mesh](/mesh/setup/content/setup-m365-mesh)<br>[Preparing your organization for Mesh](/mesh/setup/content/preparing-your-organization) | No end user control.|
| Create your event | Yes| No admin control. |[Overview of Mesh events](/mesh/events-guide/events-overview) |
| Customize your avatar | Yes| No admin control. |[Personalize your avatar](/mesh/user-guide/avatars) |
| Develop a custom environment | Yes| No admin control. |[Mesh Development Overview](/mesh/develop/development-overview) |
| Download the Mesh app | Yes| No admin control. |[Getting started with events in Microsoft Mesh](/mesh/user-guide/getting-started) |

## Advanced Places Workplace Collaboration

Microsoft Places will be licensed as part of Microsoft Teams Premium, contributing to the Teams vision to build a smart workplace. With Places in Teams Premium, your users can experience upgraded features that support advanced booking, space analytics, and admin capabilities. To learn more about Places, see [Microsoft Places overview](/microsoft-365/places/places-overview).

## Intelligent call recap

**Intelligent call recap** provides AI-powered insights and recaps to Public Switched Telephone Network (PSTN) and 1:1 Teams calls.

- To use this feature for PSTN calls, you must assign a Teams Phone license and either Teams Premium license or a Copilot for Microsoft 365 license to users. For more information on Teams Phone licensing, see [Microsoft Teams add-on licenses](teams-add-on-licensing/microsoft-teams-add-on-licensing.md).
- To use this feature with 1:1 Teams calls, you must assign a Teams Premium license or Copilot for Microsoft 365 license to users.

## More resources

You can find more resources here:

- [Microsoft Teams Premium product site](https://www.microsoft.com/microsoft-teams/premium)
- [Teams Premium deployment guide](https://aka.ms/TeamsPremiumDeployment)
- [Teams Premium user guide](https://adoption.microsoft.com/files/microsoft-teams/Microsoft-Teams-Premium-user-guide.pptx)
- [Microsoft Teams Premium blog](https://www.microsoft.com/en-us/microsoft-365/blog/2023/02/01/microsoft-teams-premium-cut-costs-and-add-ai-powered-productivity)

> [!TIP]
> As a companion to this article, we recommend using the [Teams Premium Advanced Deployment Guide](https://go.microsoft.com/fwlink/?linkid=2264339) when signed in to the Microsoft 365 admin center. This guide customizes your experience based on your environment. To review best practices without signing in and activating automated setup features, go to the [Microsoft 365 setup portal](https://go.microsoft.com/fwlink/?linkid=2263487).
