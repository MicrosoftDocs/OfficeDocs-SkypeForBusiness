---
title: Microsoft Teams Premium licensing
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.reviewer: jogruszc
ms.date: 08/30/2023
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - tier1
audience: Admin
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom:
  - Licensing
  - admindeeplinkTEAMS
  - admindeeplinkMAC
description: Learn how to enhance your Microsoft Teams experience with the Microsoft Teams Premium add-on license
---

# Microsoft Teams Premium licensing

Microsoft Teams Premium is a Teams add-on license that allows organizations with Microsoft 365 subscriptions to enhance their Teams experience with benefits like:

- More personalized and intelligent meetings and webinars.
- Enhanced protection for meetings.
- Advanced management and reporting capabilities for IT.
- Advanced Virtual Appointments.

This article is for IT admins who wish to understand Teams Premium licensing and purchase Teams Premium licenses for their users. This article will provide answers to questions like:

- [How does Teams Premium compare to Teams?](#how-does-teams-premium-compare-to-teams)
- [Are there previous Teams features that moved to Teams Premium?](#are-there-previous-teams-features-that-moved-to-teams-premium)
- [What are the requirements to purchase Teams Premium?](#what-are-the-requirements-to-purchase-teams-premium)
- [Which users should be assigned Teams Premium licenses?](#which-users-should-be-assigned-teams-premium-licenses)
- [How does Teams Premium differ from Teams Rooms Pro?](#how-does-teams-premium-differ-from-teams-rooms-pro)
- [Can I experience Teams Premium before buying licenses?](#can-i-experience-teams-premium-before-buying-licenses)
- [How do I purchase Teams Premium licenses?](#how-do-i-purchase-teams-premium-licenses)
- [Is admin configuration required after assigning users licenses?](#is-admin-configuration-required-after-assigning-users-licenses)

To learn how to set up and configure Teams Premium features, see [Microsoft Teams Premium - Overview for administrators](/microsoftteams/enhanced-teams-experience), which will also include links to end-user documentation as it becomes available.

> [!IMPORTANT]
> For admins to be able to manage Teams Premium features, their tenant needs at least one user with an active Teams Premium license.

## How does Teams Premium compare to Teams?

Customers who purchase a Microsoft 365 subscription also receive Teams licenses for their users. Purchasing the Teams Premium add-on license provides admins and end users with extra features on top Teams with their Microsoft 365 subscription.

The following table compares key features between Teams and Teams Premium.

### Meetings

| Feature | Teams | Teams Premium |
|---------|:-----:|:-------------:|
| Host and attend Teams Meetings | ✔️ |  |
| Experience Teams' standard look and feel | ✔️ |  |
| Use standard and custom meeting backgrounds at the user level| ✔️ |  |
| Read live captions during meetings and live events | ✔️ |  |
| Set up a green room for meeting presenters and organizers| ✔️ |  |
| Customize meeting templates for your organization |  | ✔️ |
| Add organization branding to meeting lobbies |  | ✔️ |
| Customize meeting backgrounds for your organization | | ✔️ |
| Customize Together mode scenes for your organization |  | ✔️ |
| Read live translated captions during meetings |  | ✔️ |
| Manage what attendees see |  | ✔️ |
| Use RTMP-In for meetings |  | ✔️ |
| Translate post-meeting transcriptions (*coming soon*) |  | ✔️ |
| Turn on eCDN for Live Events\* |  | ✔️ |

\* *eCDN can be acquired as a standalone license, and more licenses can be purchased outside of Teams Premium, if needed. To learn about eCDN standalone licensing, see [Microsoft eCDN](https://www.microsoft.com/en-us/microsoft-teams/ecdn).*

### Webinars

| Feature | Teams | Teams Premium |
|---------|:-----:|:-------------:|
| Require attendees to register | ✔️ |  |
| Assign a co-organizer | ✔️ |  |
| Limit the number of people who can register | ✔️ |  |
| Allow registered users to bypass the lobby | ✔️ |  |
| Turn on Q&A for webinars with up to 1000 attendees | ✔️ |  |
| View attendance reports | ✔️ |  |
| Set up a green room for webinar presenters and organizers| ✔️ |  |
| Manage what attendees see |  | ✔️ |
| Send custom and reminder emails to registrants |  | ✔️ |
| Create a webinar wait list |  | ✔️ |
| Manually approve registrants |  | ✔️ |
| Limit the day and time when people can register |  | ✔️ |
| Use RTMP-In for webinars |  | ✔️ |

### Analytics

| Feature | Teams | Teams Premium |
|---------|:-----:|:-------------:|
| View insights on inactive external domains |  | ✔️ |
| View insights on inactive teams |  | ✔️ |
| View insights on external collaboration by user |  | ✔️ |
| View insights on external collaboration by team |  | ✔️ |
| View insights on external collaboration by guest |  | ✔️ |

Customers must acquire and assign Teams Premium licenses to each user in their tenant for its use of ACT Advanced Collaboration Analytics.

### Meetings protection

| Feature | Teams | Teams Premium |
|---------|:-----:|:-------------:|
| Manage meeting lobbies | ✔️ |  |
| End-to-end encryption for one-to-one calls | ✔️ |  |
| Moderate meeting chats | ✔️ |  |
| Control who can present | ✔️ |  |
| Add watermarks to meetings |  | ✔️ |
| End-to-end encryption for meetings with up to 50 attendees |  | ✔️ |
| Control who can record |  | ✔️ |
| Prevent copy/paste in meeting chats |  | ✔️ |
| Assign Microsoft Purview Information Protection sensitivity labels for meetings\* |  | ✔️ |
| Custom user policy packages |  | ✔️ |

\* *This feature is only available to Teams Premium users with a Microsoft 365 E5, E5 Compliance, F5 Compliance, or F5 Security + Compliance subscription. For more information on licensing requirements, see [What are the requirements to purchase Teams Premium?](#what-are-the-requirements-to-purchase-teams-premium)*

### Meeting recap and intelligent recap

| Feature | Teams | Teams Premium |
|---------|:-----:|:-------------:|
| View recordings of meetings | ✔️ |  |
| View meeting transcripts | ✔️ |  |
| View and use files added to meetings | ✔️ |  |
| View and use apps added to meetings | ✔️ |  |
| Navigate meeting recordings with autogenerated chapters (*coming soon*) |  | ✔️ |
| View when a screen was shared in the meeting transcript |  | ✔️ |
| View time markers in meeting recordings when you joined or left a meeting |  | ✔️ |
| Jump to different speakers with speaker timeline markers |  | ✔️ |
| View AI-generated notes and tasks from meetings |  | ✔️ |
| View when you were mentioned in a meeting\* |  | ✔️ |

\* *Mentions of a user's name is pulled from the meeting transcript, not from an @mention tag in the meeting chat.*

### Virtual Appointments

| Feature | Teams | Teams Premium |
|---------|:-----:|:-------------:|
| Access Virtual Appointments with the Bookings app for scheduling, appointment management, and email notifications | ✔️ |  |
| Integrate Virtual Appointments using APIs | ✔️ |  |
| Join appointments from a browser | ✔️ |  |
| Join appointments in Teams | ✔️ |  |
| Allow users to join a virtual lobby waiting room | ✔️ |  |
| Integrate with Microsoft Forms | ✔️ |  |
| Customize the lobby waiting room with themes and logos |  | ✔️ |
| Send SMS notifications\* |  | ✔️ |
| Organizational and departmental analytics |  | ✔️ |
| View and manage scheduled appointments in the queue |  | ✔️ |
| View and manage on-demand appointments in the queue |  | ✔️ |
| Send post-appointment follow-ups (*coming soon*) |  | ✔️ |

\* *SMS notifications for Virtual Appointments is currently available in the US, Canada, and UK.*

### Meet app

| Feature | Teams | Teams Premium |
|---------|:-----:|:-------------:|
| View and prepare upcoming meetings | ✔️ |  |
| Join ongoing meetings | ✔️ |  |
| View and recap meetings you attended | ✔️ |  |
| Filter meetings by All, with Content, and Recorded | ✔️ |  |
| View and recap meetings that you missed |  | ✔️ |
| View and recap meetings that mention you\* |  | ✔️ |
| View when you were mentioned in a meeting\* |  | ✔️ |
| View AI-generated tasks from meetings |  | ✔️ |

\* *Mentions of a user's name is pulled from the meeting transcript, not from an @mention tag in the meeting chat.*

## Are there previous Teams features that moved to Teams Premium?

With the general release of Teams Premium on February 1, 2023, the following Teams features moved from Teams to Teams Premium.

- Live translation of meeting captions.
- PPT live chapters.
- Timeline markers in Teams meeting recordings for when a user left or joined meetings.
- Custom organization Together mode scenes.
- Virtual Appointments: SMS notifications.
- Virtual Appointments: Organizational analytics in the Teams admin center.
- Virtual Appointments: Scheduled queue view.

## What are the requirements to purchase Teams Premium?

At release, Teams Premium will be available to purchase worldwide through all Microsoft purchasing channels, including EA, EAS, CSP, Web Direct, NCE - Customer led, and NCE - Partner led.

Before you can purchase Teams Premium licenses for your users, ensure your tenant and users meet the requirements.

The **tenant requirement** is:

- Must be a commercial, worldwide public sector, EDU, GCC, or non-profit tenant at general release.
  - Teams Premium for GCC became available on March 1, 2023.
  - At general release, Microsoft won't offer an EDU-specific license or EDU discounts for Teams Premium.
  - GCC High and DoD licenses will become available sometime after the general release.

The **user requirement** is:

- An Office 365 or Microsoft 365 subscription with Teams.

### Can I acquire Teams Premium features without the Teams Premium license?

Teams Premium bundles a large set of Teams features under a single license. There are instances where a single Teams Premium feature could be acquired through other licensing scenarios. However, the Teams Premium license is designed to be the most holistic and simplest avenue to enhance your organization's and users' Teams experience.

## Which users should be assigned Teams Premium licenses?

Teams Premium is licensed on a per-user subscription basis and is subject to the [Universal Terms for Online Services](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all). You should plan to assign a Teams Premium user subscription license to every user you want to provide Teams Premium features for.

> [!NOTE]
> When the organizer of a Teams meeting or live event is licensed for Teams Premium, the *Live translation (for captions)*, *advanced Meetings protection*, and *advanced Webinars* features are extended to all meeting participants, including external and guest users.
>
> External participants in Virtual Appointments don't require a Teams Premium license to benefit from Teams Premium advanced Virtual Appointments.
>
> All meeting participants must be licensed for Teams Premium to benefit from the *Intelligent recap* feature.

## How does Teams Premium differ from Teams Rooms Pro?

Teams Premium licenses are assigned to your organization's users, and Teams Rooms Pro licenses should only be assigned to Microsoft Teams Rooms devices. These two licenses aren't dependent on one another, don't overlap features, and won't cause license enforcement conflicts.

Before the release of Teams Rooms Pro, Microsoft offered a Teams Rooms license called Teams Rooms Premium. Teams Rooms Premium has been retired and isn't related to Teams Premium.

## Can I experience Teams Premium before buying licenses?

Starting in December 2022, organizations can try Teams Premium by purchasing the zero-cost Teams Premium 30-day trial license available in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=868433).

Organizations with a Teams Premium trial license will have 25 licenses to assign to users. Those 25 users can experience and test Teams Premium features as they become available. Also, the admin can manage Teams Premium features for the 25 licensed users.

Most organization segments can purchase and use the Teams Premium trial license, excluding GCC High and DoD tenants.

### What will happen if my users' trial licenses expire?

After the 30-day trial licenses expire, the 25 licensed users will lose all Teams Premium functionality. There's currently no grace period between the expiration of the trial license and the loss of functionality.

For this reason, we recommend organizations plan their Teams Premium trial period, ensuring all necessary test scenarios are thoroughly vetted before the trial period expires.

When the trial licenses expire, the tenant's uploaded Teams Premium assets like custom templates and meeting backgrounds will remain in the tenant but will be grayed out and unusable.

If your organization wishes to keep Teams Premium features after the trial period, you'll need to purchase Teams Premium licenses when they become available and reassign the licenses to your users.

## How do I purchase Teams Premium licenses?

If your tenant and users meet [the requirements for Teams Premium](#what-are-the-requirements-to-purchase-teams-premium), you can purchase Teams Premium add-on licenses through your preferred purchasing channel once Teams Premium becomes generally available.

After you purchase your Teams Premium licenses, you'll assign the licenses to your users in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=834822). It can take up to 24 hours before the assignment takes effect.

For instructions on assigning licenses in the Microsoft 365 admin center, see [Assign Microsoft 365 licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users).

## Is admin configuration required after assigning users licenses?

Many Teams Premium features require an IT admin to configure the feature before users can access the feature.

The following list indicates Teams Premium features that require admin configuration in the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851) before users can access the feature:

- Using end-to-end encryption on meetings up to 50 participants.
- Adding watermarks to meetings.
- Adding sensitivity labels.
- Preventing copy and paste in meeting chats.
- Using organization customized backgrounds.
- Using organization customized Together mode scenes.
  - Admin must create the custom Together mode scene.
- Being assigned a custom policy package.
- Using organization customized meeting templates.
- Seeing organization customized branding.
- Using eCDN for Live Events.
- Using RTMP-In.
- Customizing Virtual Appointment lobby rooms with branding.

For links to instructions, see [Microsoft Teams Premium - Overview for administrators](/microsoftteams/enhanced-teams-experience).
