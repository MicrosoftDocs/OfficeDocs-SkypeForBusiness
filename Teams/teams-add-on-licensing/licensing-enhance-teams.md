---
title: Microsoft Teams Premium licensing
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.reviewer: jogruszc
ms.date: 11/09/2022
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
- [Are there current Teams features that will move to Teams Premium?](#are-there-current-teams-features-that-will-move-to-teams-premium)
- [What are the requirements to purchase Teams Premium?](#what-are-the-requirements-to-purchase-teams-premium)
- [Which users should be assigned Teams Premium licenses?](#which-users-should-be-assigned-teams-premium-licenses)
- [How does Teams Premium differ from Teams Rooms Pro?](#how-does-teams-premium-differ-from-teams-rooms-pro)
- [Can I experience Teams Premium before buying licenses?](#can-i-experience-teams-premium-before-buying-licenses)
- [How do I purchase Teams Premium licenses?](#how-do-i-purchase-teams-premium-licenses)
- [Is admin configuration required after assigning users licenses?](#is-admin-configuration-required-after-assigning-users-licenses)

To learn how to set up and configure Teams Premium features, see [Microsoft Teams Premium - Overview for administrators](/microsoftteams/enhanced-teams-experience), which will also include links to end-user documentation as it becomes available.

## How does Teams Premium compare to Teams?

Customers who purchase a Microsoft 365 subscription also receive Teams licenses for their users. Purchasing the Teams Premium add-on license provides admins and end users with extra features on top Teams with their Microsoft 365 subscription.

The following table compares key features between Teams and Teams Premium.

### Meetings

| Feature | Teams | Teams Premium |
|---------|:-----:|:-------------:|
| Host and attend Teams Meetings | x | x |
| Experience Teams’ standard look and feel | x | x |
| Use standard and custom meeting backgrounds at the user level| x | x |
| Read live captions during meetings and live events | x | x |
| Customize meeting templates for your organization |  | x |
| Add organization branding to meeting lobbies |  | x |
| Customize meeting backgrounds for your organization | | x |
| Customize Together mode scenes for your organization |  | x |
| Read live translated captions during meetings |  | x |
| Translate post-meeting transcriptions (*coming soon*) |  | x |
| Turn on eCDN for Live Events\* |  | x |

\* *eCDN can be acquired as a standalone license, and more licenses can be purchased outside of Teams Premium, if needed. To learn about eCDN standalone licensing, see [Microsoft eCDN](https://www.microsoft.com/en-us/microsoft-teams/ecdn).*

### Webinars

| Feature | Teams | Teams Premium |
|---------|:-----:|:-------------:|
| Require attendees to register | x | x |
| Assign a co-organizer | x | x |
| Limit the number of people who can register | x | x |
| Turn on Q&A for webinars with up to 1000 attendees | x | x |
| View attendance reports | x | x |
| Integrate with Dynamics 365 | x | x |
| Set up a green room for webinar presenters |  | x |
| Manage attendees’ view |  | x |
| Send reminder emails to registrants |  | x |
| Create a webinar wait list |  | x |
| Manually approve registrants |  | x |
| Limit the day and time when people can register |  | x |
| Allow registered users to bypass the lobby |  | x |
| Use RTMP-In for Webinars (*coming soon*) |  | x |

### Meetings protection

| Feature | Teams | Teams Premium |
|---------|:-----:|:-------------:|
| Manage meeting lobbies | x | x |
| End-to-end encryption for one-to-one calls | x | x |
| Moderate meeting chats | x | x |
| Control who can present | x | x |
| Add watermarks to meetings |  | x |
| End-to-end encryption for meetings with up to 50 attendees |  | x |
| Control who can record |  | x |
| Prevent copy/paste in meeting chats |  | x |
| Assign Microsoft Purview Information Protection sensitivity labels for meetings\*  |  | x |
| Custom user policy packages |  | x |
| Turn on advanced meeting monitoring and alerting |  | x |

\* *This feature is only available to Teams Premium users with a Microsoft 365 E5 subscription or Microsoft E3 subscription plus the Advanced Compliance license. For more information on licensing requirements, see [What are the requirements to purchase Teams Premium?](#what-are-the-requirements-to-purchase-teams-premium)*

### Meetings reporting

| Feature | Teams | Teams Premium |
|---------|:-----:|:-------------:|
| View recordings of meetings | x | x |
| View meeting transcripts | x | x |
| View and use files added to meetings | x | x |
| View and use apps added to meetings | x | x |
| Navigate meeting recordings with autogenerated chapters (*coming soon*) |  | x |
| Navigate meeting recordings with PPT live chapters |  | x |
| View time markers in meeting recordings when you joined or left a meeting |  | x |
| Search meeting transcripts with speaker suggestions (*coming soon*) |  | x |
| View and act on autogenerated tasks from meetings (*coming soon*) |  | x |
| View when you were @mentioned (*coming soon*) |  | x |

### Virtual Appointments

| Feature | Teams | Teams Premium |
|---------|:-----:|:-------------:|
| Access Virtual Appointments with the Bookings app for scheduling, appointment management, and email notifications | x | x |
| Integrate Virtual Appointments using APIs | x | x |
| Join appointments from a browser | x | x |
| Join appointments in Teams | x | x |
| Allow users to join a virtual lobby waiting room | x | x |
| Integrate with Microsoft Forms | x | x |
| Customize the lobby waiting room with themes and logos |  | x |
| Send SMS notifications |  | x |
| Chat back and forth with attendees in the lobby waiting room (*coming soon*) |  | x |
| Organizational and departmental analytics |  | x |
| View and manage scheduled appointments in the queue |  | x |
| View and manage on-demand appointments in the queue |  | x |
| Send post-appointment follow-ups (*coming soon*) |  | x |

## Are there current Teams features that will move to Teams Premium?

With the general release of Teams Premium, some Teams features will move from Teams licenses to Teams Premium licenses. Each of these features has a grace period of 30 or 60 days after general availability. When the grace period expires, users will lose access to that feature.

To allow your users to keep using these features, you'll need to purchase and assign Teams Premium licenses.

The features that are moving to Teams Premium are:

- Live translated captions.
  - Available to all Teams subscribers for a 60-day grace period after Teams Premium general availability.
- PPT live chapters.
  - Available to all Teams subscribers for a 60-day grace period after Teams Premium general availability.
- Timeline markers in Teams meeting recordings for when a user left or joined meetings.
  - Available to all Teams subscribers for a 60-day grace period after Teams Premium general availability.
- Custom organization Together mode scenes.
  - Available to all Teams subscribers for a 30-day grace period after Teams Premium general availability.
- Virtual Appointments: SMS notifications.
  - Available to all Teams subscribers for a 30-day grace period after Teams Premium general availability.
- Virtual Appointments: Organizational analytics in the Teams admin center.
  - Available to all Teams subscribers for a 30-day grace period after Teams Premium general availability.
- Virtual Appointments: Scheduled queue view.
  - Available to all Teams subscribers for a 30-day grace period after Teams Premium general availability.

## What are the requirements to purchase Teams Premium?

At release, Teams Premium will be available to purchase worldwide through all Microsoft purchasing channels, including EA, EAS, CSP, Web Direct, NCE – Customer led, and NCE – Partner led.

Before you can purchase Teams Premium licenses for your users, ensure your tenant and users meet the requirements.

The **tenant requirement** is:

- Must be a commercial, worldwide public sector, EDU, or non-profit tenant.
  - At general release, Microsoft won’t offer an EDU-specific license or EDU discounts for Teams Premium.
  - GCC, GCC High, and DoD licenses will become available sometime after the general release.

The **user requirement** is:

- An Office 365 or Microsoft 365 subscription with Teams.

### Can I acquire Teams Premium features without the Teams Premium license?

Teams Premium bundles a large set of Teams features under a single license. There are instances where a single Teams Premium feature could be acquired through other licensing scenarios. However, the Teams Premium license is designed to be the most holistic and simplest avenue to enhance your organization's and users' Teams experience.

## Which users should be assigned Teams Premium licenses?

Teams Premium is per-user, per-month license where each user who needs access to Teams Premium functionality needs to have a license assigned. The only way to ensure users have access to Teams Premium features is to assign them a license.

There are some specific meeting and event features that will provide the feature benefit to all meeting attendees, including guests and external participants. Here's some guidance to help you decide who to acquire Teams Premium licenses for:

- External participants in Virtual Appointments don't require a Teams Premium license to benefit from Teams Premium advanced Virtual Appointments.

- For intelligent recap, all meeting participants need a Teams Premium license to benefit from this feature.

- For live translation (for captions), advanced meeting protection, and advanced webinars, if the meeting organizer is licensed with Teams Premium, meeting participants (including guests and external participants) don't need the Teams Premium license to benefit from these premium features. If an attendee is licensed with Teams Premium but the meeting organizer isn't, that attendee will still be able to access live translations.

- For advanced meeting protection, and advanced webinars, if the meeting organizer is licensed with Teams Premium, meeting participants (including guests and external participants) don't need the Teams Premium license to benefit from these premium features.

If a user needs access to a Teams Premium feature, license them to ensure consistent access and experiences to Teams Premium capabilities. The scenarios above can't be used against our [Online Services license terms](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all), and these scenarios are subject to change.

## How does Teams Premium differ from Teams Rooms Pro?

Teams Premium licenses are assigned to your organization’s users, and Teams Rooms Pro licenses should only be assigned to Microsoft Teams Rooms devices. These two licenses aren’t dependent on one another, don’t overlap features, and won’t cause license enforcement conflicts.

Before the release of Teams Rooms Pro, Microsoft offered a Teams Rooms license called Teams Rooms Premium. Teams Rooms Premium has been retired and isn’t related to Teams Premium.

## Can I experience Teams Premium before buying licenses?

Starting in December 2022, organizations can try Teams Premium by purchasing the zero-cost Teams Premium 30-day trial license available in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=868433).

Organizations with a Teams Premium trial license will have 25 licenses to assign to users. Those 25 users can experience and test Teams Premium features as they become available. Also, the admin can manage Teams Premium features for the 25 licensed users.

Most organization segments can purchase and use the Teams Premium trial license, excluding GCC High and DoD tenants.

### What will happen if my users’ trial licenses expire?

After the 30-day trial licenses expire, the 25 licensed users will lose all Teams Premium functionality. There’s currently no grace period between the expiration of the trial license and the loss of functionality.

For this reason, we recommend organizations plan their Teams Premium trial period, ensuring all necessary test scenarios are thoroughly vetted before the trial period expires.

When the trial licenses expire, the tenant's uploaded Teams Premium assets like custom templates and meeting backgrounds will remain in the tenant but will be grayed out and unusable.

If your organization wishes to keep Teams Premium features after the trial period, you'll need to purchase Teams Premium licenses when they become available and reassign the licenses to your users.

## How do I purchase Teams Premium licenses?

If your tenant and users meet [the requirements for Teams Premium](#what-are-the-requirements-to-purchase-teams-premium), you can purchase Teams Premium add-on licenses through your preferred purchasing channel once Teams Premium becomes generally available.

After you purchase your Teams Premium licenses, you’ll assign the licenses to your users in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=834822).

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
