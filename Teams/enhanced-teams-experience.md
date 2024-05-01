---
title: Microsoft Teams Premium - Overview for administrators
author: wlibebe
ms.author: wlibebe
manager: pamgreen
ms.reviewer: spraveen, margidesai
ms.date: 11/27/2023
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

# Microsoft Teams Premium - Overview for administrators

![Information icon](media/info.png) **Most of the features described in this article require a Teams Premium license.** A few features, for example, some webinar features, are available with other licenses as well. 

![Information icon](media/info.png)
**Teams Premium licenses are not a replacement for Teams licenses.** Users must have both a Teams license and a Teams Premium license for Teams and Teams Premium features to work properly.  For details about feature availability and licensing, see [Teams Premium licensing](teams-add-on-licensing/licensing-enhance-teams.md).

![Information icon](media/info.png) Now that Teams Premium has reached general availability, some features formerly available with Teams will only be available with a Teams Premium license.

This article is for IT Pros and administrators who will be deploying and configuring Teams Premium features. The article provides a brief description of the features, with links to more detailed documentation.

Teams Premium is an add-on license that provides the following enhancements to Teams:  

- Enhanced meeting experiences for your end users
- Enhanced security and protection for meetings
- Enhanced administrative and telemetry support


The following sections describe the Teams Premium enhancements for:

- [Advanced protection](#advanced-protection)
- [Custom meetings](#custom-meetings)
- [Premium events](#premium-events)
- [Virtual Appointments](#advanced-virtual-appointments)

For more information about Teams meetings and premium events in general, see the following articles:

- [Meetings, webinars, and townhalls](overview-meetings-webinars-town-halls.md)
- [Plan for Teams meetings](plan-meetings.md)
- [Plan for Teams webinars](plan-webinars.md)
- [Plan for Teams town halls](plan-town-halls.md)

> [!NOTE]
> We will continue to update this article. Check back often for links to new content.

## Advanced protection

Teams Premium provides additional ways to safeguard and monitor users' Teams experiences with the following key features:

- **Sensitivity labels** - Extended capabilities for sensitivity labels to control meeting settings normally controlled by the meeting organizer. These capabilities include new settings to control lobby, chat, chat copy, presentation, and recording functions.

- **Watermarking** - Enforced through a sensitivity label. Watermarks display the email address of a meeting participant, which is useful for protecting confidential information shared in meetings.

- **End-to-end encryption** - Enforced through a sensitivity label. End-to-end encryption provides increased security for meetings that require a higher level of protection.

- **Manage what attendees see** - Meeting organizers can decide whose avatars or video feeds to spotlight during a Teams meeting. Others will be hidden from view.

- **Hide attendee names** - Meeting and webinar organizers can hide the names of attendees from other attendees in the stage, roster, and chat.

- **Advanced collaboration analytics** - In the Teams admin center, Teams admins can view data on their users, teams, federated domains, channels, and guests concerning their external collaboration activity.

- **Real time telemetry and retention** - Real-time telemetry is gathered automatically for all users who have a Teams Premium license and retained for seven days.

| Feature/Task  | Documentation for administrators | Documentation for your end users |
| -------------------- | ----------- | ------------ |
| Sensitivity labels | [Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md) ||
| Watermarks | [Require a watermark for meetings](watermark-meeting-content-video.md) | [Watermarks for meetings](https://support.microsoft.com/office/watermark-for-teams-meetings-a9166432-f429-4a19-9a72-c9e8fdf4f589)|
| End-to-end encryption (E2EE) | [Encryption for sensitive meetings](end-to-end-encrypted-meetings.md) | [Use encryption](https://support.microsoft.com/office/use-end-to-end-encryption-for-teams-meetings-a8326d15-d187-49c4-ac99-14c17dbd617c)  |
| Templates, labels, and policies | [Templates, sensitivity labels, and policies](meeting-templates-sensitivity-labels-policies.md)  | [Use custom templates](https://support.microsoft.com/office/use-custom-templates-for-teams-meetings-78279be9-3283-4999-b24e-96fb0da2fb4f) |
| Restrict who can record | [Manage recordings for sensitive meetings](manage-meeting-recording-options.md) | [Record a meeting](https://support.microsoft.com/office/record-a-meeting-in-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24?storagetype=stage#bkmk_whocanstartorstoparecording) |
| Manage what attendees see | No admin control. | [Manage what attendees see in Teams meetings](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16)|
| Hide attendee names | [Allow meeting and webinar organizers to hide the names of attendees](hide-attendee-names.md) |[Hide attendee names in Teams meetings and webinars](https://support.microsoft.com/office/hide-attendee-names-in-teams-meetings-and-webinars-00389c74-ee61-48b5-bad8-8295600085ed) |
| Advanced collaboration analytics | [Advanced Collaboration Analytics for Microsoft Teams](advanced-collaboration-analytics.md) | No end-user controls. |
| Real time telemetry and retention| [Use real time telemetry to troubleshoot poor meeting quality](use-real-time-telemetry-to-troubleshoot-poor-meeting-quality.md) | No end-user controls. |

## Custom meetings

Teams Premium provides the following additional features for customizing meetings:

- **Meeting templates** - Used to control meeting settings that the meeting organizer normally controls. With templates, you can create consistent meeting experiences in your organization and help enforce compliance requirements and business rules.

- **Meeting themes** - Allows your organization to extend their visual identities across the meeting experience. You can set up and create meeting themes for a variety of business units and departments within a single tenant.

- **Custom meeting backgrounds for organizations** - You can create and define custom meeting backgrounds that are then available to your end users with a Teams Premium license.

- **Custom together mode scenes for organizations** -  You can create, customize, or accept custom together mode scenes for meetings that are then available to your end users with a Teams Premium license.

- **Real Time Messaging Protocol (RTMP)-In** - Organizers can produce their Teams meetings directly from an external hardware or software-based encoder.

| Feature/Task | Documentation for administrators | Documentation for your end users |
| -------------------- | ----------- | ------------ |
| Meeting templates | - [Overview](custom-meeting-templates-overview.md)<br>- [Create a custom meeting template](create-custom-meeting-template.md)| [Use custom templates](https://support.microsoft.com/office/use-custom-templates-for-teams-meetings-78279be9-3283-4999-b24e-96fb0da2fb4f) |
| Meeting themes | [Themes for Teams meetings](meeting-themes.md) | [Use meeting themes](https://support.microsoft.com/office/use-meeting-themes-for-teams-meetings-fbfd826d-1112-4790-918a-5a82cac8250e) |
| Custom meeting backgrounds for organizations | [Meeting backgrounds](custom-meeting-backgrounds.md)| |
| Custom together mode scenes for organizations | [Content for you and your developers](/microsoftteams/platform/apps-in-teams-meetings/teams-together-mode)| |
| RTMP-In | [Manage RTMP-In for Teams meetings](meetings-rtmp-in.md)|[Use RTMP-In in a Teams meeting](https://support.microsoft.com/office/use-rtmp-in-in-a-teams-meeting-789d6090-8511-4e2e-add6-52a9f551be7f) |

## Premium events

Premium events include town halls and webinars.

- **[Town halls](#town-halls)** bring interactive video streaming to a new level. Town halls are meant for one-to-many communications where the presenters, organizers, and co-organizers are leading the interactions. The audience participation is primarily to view and react to the content being shared.

- **[Webinars](#webinars)** provide a two-way interactive virtual event where the presenters deliver information to attendees. This format provides extra control for an organizer over the conversation and participants.

The following sections describe Teams Premium feature enhancements for town halls and webinars. For more information about planning for town halls, webinars, and meetings in general, see [Plan for town halls](plan-town-halls.md), [Plan for webinars](plan-webinars.md), and [Meetings, webinars, and town halls](overview-meetings-webinars-town-halls.md).

### Town halls

Teams Premium provides the following features for an enhanced town hall experience:

- **Custom emails** - Organizers and co-organizers can customize the town hall email templates sent to attendees.
- **Increased broadcast and Q&A capacity**- Organizers can broadcast their town halls to 20,000 attendees. All attendees can use Q&A to interact with presenters, organizers, and co-organizers.
- **Increased languages for live translations**- Attendees have 10 language options for  live translated captions in town halls. These languages include:

  - English (en-us)
  - Japanese (ja-jp)
  - Spanish (es-es)
  - Portuguese (pt-pt)
  - French (fr-fr)
  - Chinese (zh-cn)
  - German (de-de)
  - Italian (it-it)
  - Korean (ko-kr)
  - Russian (ru-ru)
- **Town hall insights** - Town hall organizers can troubleshoot town halls while they're live.
- **Real time monitoring of the attendee experience** - Admins can use the analytics dashboard to troubleshoot the attendee experience during live town halls.

| Feature/Task | Documentation for administrators | Documentation for your end users |
| -------------------- | ----------- | ----------- |
| Custom emails | [Manage email communications](manage-email-communications.md) |[Schedule a town hall in Microsoft Teams](https://support.microsoft.com/office/schedule-a-town-hall-in-microsoft-teams-d493b5cc-9f61-4dac-8027-d837dafb7a4c#bkmk_town_hall_invites) |
| Town hall insights | No admin control|[Town hall insights in Microsoft Teams](https://support.microsoft.com/office/town-hall-insights-in-microsoft-teams-def99575-61bf-4ea2-ad0e-c6e75dce7741) |
| Live translated captions | [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)|[Use live captions in Microsoft Teams meetings](https://support.microsoft.com/office/use-live-captions-in-microsoft-teams-meetings-4be2d304-f675-4b57-8347-cbd000a21260) |
| Real time monitoring of the attendee experience | [Analytics](/ecdn/technical-documentation/analytics)|No end user control |

### Webinars

Teams Premium provides the following features for an enhanced webinar experience:

- **Real Time Messaging Protocol (RTMP)-In** - Organizers can produce their Teams webinar directly from an external hardware or software-based encoder.
- **Custom emails** - Organizers and co-organizers can customize the webinar email templates sent to attendees.
- **Custom webinar reminder email send times** - Webinar reminder emails are automatically sent to registrants an hour before the event starts. With Teams Premium, organizers can edit the send time to notify attendees sooner.
- **Manage what attendees see** - Webinar organizers can decide whose avatars or video feeds to spotlight during a Teams webinar. Others will be hidden from view.
- **Manually approve registrants** - Organizers can approve or deny requests to register for their webinar.
- **Enable and manage the waitlist for webinars beyond capacity** - When the webinar's registration reaches capacity, organizers can manage overflow registration requests through a waitlist.
- **Limit registration start and end times** - Organizers can set a time window during which potential attendees can register for their webinar.
- **Hide attendee names** - Meeting and webinar organizers can hide the names of attendees from other attendees in the stage, roster, and chat.

| Feature/Task | Documentation for administrators | Documentation for your end users |
| -------------------- | ----------- | ----------- |
| Custom emails | [Manage email communications](manage-email-communications.md) |[Manage webinar emails in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-emails-in-microsoft-teams-d0006848-f707-494f-b0a4-eeebcbc723be) |
| RTMP-In | [Manage RTMP-In for Teams meetings](meetings-rtmp-in.md)|[Use RTMP-In in a Teams meeting](https://support.microsoft.com/office/use-rtmp-in-in-a-teams-meeting-789d6090-8511-4e2e-add6-52a9f551be7f) |
| Manage what attendees see | No admin control | [Manage what attendees see in Teams meetings](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16)|
| Manually approve registrants |No admin control |[Manage webinar registration in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-registration-in-microsoft-teams-923f382a-0cca-433a-b38d-7461971192d1) |
| Enable and manage the waitlist for webinars beyond capacity | No admin control|[Manage webinar registration in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-registration-in-microsoft-teams-923f382a-0cca-433a-b38d-7461971192d1) |
| Limit registration start and end times|No admin control|[Manage webinar registration in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-registration-in-microsoft-teams-923f382a-0cca-433a-b38d-7461971192d1) |
| Hide attendee names | [Allow meeting and webinar organizers to hide the names of attendees](hide-attendee-names.md) | [Hide attendee names in Teams meetings and webinars](https://support.microsoft.com/office/hide-attendee-names-in-teams-meetings-and-webinars-00389c74-ee61-48b5-bad8-8295600085ed)|

## Advanced Virtual Appointments

With any Microsoft 365 license, your end users can use basic Virtual Appointments capabilities to schedule and join business-to-customer meetings. For example, users can schedule appointments in the Bookings calendar and external attendees can join through a browser without having to download Teams.

Teams Premium provides advanced Virtual Appointment capabilities, such as:

- SMS notifications
- Custom waiting room
- A queue of scheduled and on-demand appointments
- Analytics

| Feature/Task  | Documentation for administrators |
| -------------------- | ----------- |
| SMS notifications  | [SMS text notifications](bookings-app-admin.md#sms-text-notifications) |
| Reporting | [Virtual Appointments usage report](/microsoft-365/frontline/virtual-appointments-usage-report?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json)<br>[Advanced Virtual Appointments activity report](/microsoft-365/frontline/advanced-virtual-appointments-activity-report?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json) |

## Additional resources

You can find additional resources here:

- [Microsoft Teams Premium product site](https://www.microsoft.com/microsoft-teams/premium)
- [Teams Premium deployment guide](https://aka.ms/TeamsPremiumDeployment)
- [Teams Premium user guide](https://adoption.microsoft.com/files/microsoft-teams/Microsoft-Teams-Premium-user-guide.pptx)
- [Microsoft Teams Premium blog](https://www.microsoft.com/en-us/microsoft-365/blog/2023/02/01/microsoft-teams-premium-cut-costs-and-add-ai-powered-productivity)

> [!TIP]
> As a companion to this article, we recommend using the [Teams Premium Advanced Deployment Guide](https://go.microsoft.com/fwlink/?linkid=2264339) when signed in to the Microsoft 365 admin center. This guide customizes your experience based on your environment. To review best practices without signing in and activating automated setup features, go to the [Microsoft 365 setup portal](https://go.microsoft.com/fwlink/?linkid=2263487).
