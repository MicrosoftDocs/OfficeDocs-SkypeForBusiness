---
title: Microsoft Teams Premium - Overview for administrators
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.reviewer: 
ms.date: 10/05/2022
ms.topic: conceptual
ms.service: msteams
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

![Information icon](media/info.png) **Most of the features described in this article require Teams Premium.** A few features, for example, some webinar features, are available with other licenses as well. For details about feature availability and licensing, see [Teams Premium licensing](teams-add-on-licensing/licensing-enhance-teams.md).

This article is for IT Pros and administrators who will be deploying and configuring Teams Premium features. The article provides a brief description of the features, with links to more detailed documentation.

Teams Premium is an add-on license that provides the following enhancements to Teams:  

- Enhanced meeting experiences for your end users
- Enhanced security and protection for meetings
- Enhanced administrative and telemetry support

> [!IMPORTANT]
> Now that Teams Premium has reached general availability, some features formerly available with Teams will only be available with a Teams Premium license.
>
> For admins to be able to manage Teams Premium features, their tenant needs at least one user with an active [Teams Premium license](/MicrosoftTeams/teams-add-on-licensing/licensing-enhance-teams).

The following sections describe the Teams Premium enhancements for:

- [Protected meetings](#protected-meetings)
- [Custom meetings](#custom-meetings)
- [Premium events](#premium-events)
- [Virtual Appointments](#advanced-virtual-appointments)

>[!Note]
>We will continue to update this article. Check back often for links to new content.

## Protected meetings

Teams Premium provides additional ways to safeguard meetings with the following key features:

- **Sensitivity labels** - Extended capabilities for sensitivity labels to control meeting settings normally controlled by the meeting organizer. These capabilities include new settings to control lobby, chat, chat copy, presentation, and recording functions.

- **Watermarking** - Enforced through a sensitivity label. Watermarks display the email address of a meeting participant, which is useful for protecting confidential information shared in meetings.

- **End-to-end encryption** - Enforced through a sensitivity label. End-to-end encryption provides increased security for meetings that require a higher level of protection.

| Feature/Task  | Documentation for administrators | Documentation for your end users
| -------------------- | ----------- | ------------ |
| Sensitivity labels | [Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md) | |
| Watermarks | [Require a watermark for meetings](watermark-meeting-content-video.md) | [Watermarks for meetings](https://support.microsoft.com/office/watermark-for-teams-meetings-a9166432-f429-4a19-9a72-c9e8fdf4f589)|
| End-to-end encryption (E2EE) | [Encryption for sensitive meetings](end-to-end-encrypted-meetings.md) | [Use encryption](https://support.microsoft.com/office/use-end-to-end-encryption-for-teams-meetings-a8326d15-d187-49c4-ac99-14c17dbd617c)  |
| Templates, labels, and policies | [Templates, sensitivity labels, and policies](meeting-templates-sensitivity-labels-policies.md)  | [Use custom templates](https://support.microsoft.com/office/use-custom-templates-for-teams-meetings-78279be9-3283-4999-b24e-96fb0da2fb4f) |
| Restrict who can record | [Manage recordings for sensitive meetings](manage-meeting-recording-options.md) | [Record a meeting](https://support.microsoft.com/office/record-a-meeting-in-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24?storagetype=stage#bkmk_whocanstartorstoparecording) |

## Custom meetings

Teams Premium provides the following additional features for customizing meetings:

- **Meeting templates** - Used to control meeting settings that the meeting organizer normally controls. With templates, you can create consistent meeting experiences in your organization and help enforce compliance requirements and business rules.

- **Meeting themes** - Allows your organization to extend their visual identities across the meeting experience. You can set up and create meeting themes for a variety of business units and departments within a single tenant.

- **Custom meeting backgrounds for organizations** - You can create and define custom meeting backgrounds that are then available to your end users with a Teams Premium license.

- **Custom together mode scenes for organizations** -  You can create, customize, or accept custom together mode scenes for meetings that are then available to your end users with a Teams Premium license.

| Feature/Task | Documentation for administrators | Documentation for your end users
| -------------------- | ----------- | ------------ |
| Meeting templates | - [Overview](custom-meeting-templates-overview.md)<br>- [Create a custom meeting template](create-custom-meeting-template.md)| [Use custom templates](https://support.microsoft.com/office/use-custom-templates-for-teams-meetings-78279be9-3283-4999-b24e-96fb0da2fb4f)
| Meeting themes | [Themes for Teams meetings](meeting-themes.md) | [Use meeting themes](https://support.microsoft.com/office/use-meeting-themes-for-teams-meetings-fbfd826d-1112-4790-918a-5a82cac8250e) |
| Custom meeting backgrounds for organizations | [Meeting backgrounds](custom-meeting-backgrounds.md)| |
| Custom together mode scenes for organizations | [Content for you and your developers](/microsoftteams/platform/apps-in-teams-meetings/teams-together-mode)| |

## Premium events

Teams Premium provides an advanced webinar experience for your users with the new Teams Events policy. While continuing to support registration and tracking, the new policy will also provide functionality for meeting hosters and organizers, such as:

- **Terms and conditions custom question** - To present to attendees.
- **Presenter bio** - To include information about presenters.
- **Banner, logo, and predefined color** - To present a customized visual webinar experience.
- **Advanced registration capabilities** - Including manual approval, waitlist, registration date and time limit.
- **Registration overview and management** - For each event, a summary of registration status with lists of attendees in different registration states--depending on which registration features have been enabled.

| Feature/Task | Documentation for administrators | Documentation for your end users
| -------------------- | ----------- | ----------- |
| Understand meetings, webinars, and live events | [Quick start](quick-start-meetings-live-events.md) | |
| Set up webinars | [Set up webinars](set-up-webinars.md) | - [Manage webinar registration](https://support.microsoft.com/office/manage-webinar-registration-923f382a-0cca-433a-b38d-7461971192d1) <br> - [Manage what attendees see](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16)|
| Meeting policy for webinars | [Meeting policies](meeting-policies-in-teams-general.md) | |

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
- [Microsoft Teams Premium blog](https://www.microsoft.com/en-us/microsoft-365/blog/2023/02/01/microsoft-teams-premium-cut-costs-and-add-ai-powered-productivity)
