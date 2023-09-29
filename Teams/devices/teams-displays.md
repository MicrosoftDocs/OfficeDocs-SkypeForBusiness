---
title: Microsoft Teams displays
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: weizxue
ms.date: 08/24/2020
ms.topic: reference
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords: 
  - NOCSH
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
search.appverid: MET150
ms.localizationpriority: medium
description: This article provides an overview of and features supported by Microsoft Teams displays.
---

# Microsoft Teams displays

Microsoft Teams displays are a category of all-in-one dedicated Teams devices that feature an ambient touchscreen. This article provides an overview of Teams displays and can help you plan, deliver, and manage Teams displays in your organization.

Teams displays brings together your favorite Teams features&ndash;chat, meetings, calls, calendar, and files&ndash;into a single device. With Teams displays, users can use a microphone, camera, and speakers (or Bluetooth headset) for a reliable calling and meeting experience. Teams displays integrates with users' Windows PCs to bring a companion experience that allows for seamless cross-device interaction.

To learn more, check out [Get started with Teams displays](https://support.microsoft.com/office/get-started-with-teams-displays-ff299825-7f13-4528-96c2-1d3437e6d4e6).

## Features supported by Teams displays

In addition to the [features supported by Teams phones](phones-for-teams.md#features-supported-by-teams-phones), the following features are unique to Teams displays:

- **Dedicated displays for Teams** Users can access all core Teams features including chat, meetings, calls, teams and channels, files and more.
- **Ambient experience** Users can easily stay on top of their work with always-on and glanceable displays to see important activities and notifications without context-switching on their primary work device. Users can also personalize Teams displays by customizing the background through settings.
- **Leave a note on lock screen** Guests can choose to leave audio, video, and text notes, and users can check the notes left by guests and see who’s stopped by.  
- **Virtual front desk experience on Teams-certified displays** Enables staff to greet and serve visitors or employees via video call on a Teams display. It can be used for virtual reception, helpdesk, and a variety of use cases across industries.
  
## Required licenses

Teams licenses can be purchased as part of [Microsoft 365 and Office 365 subscriptions](/office365/servicedescriptions/teams-service-description). To learn more about the required licenses to use Teams displays, see [Voice and video calling with Microsoft Teams](https://products.office.com/microsoft-teams/voice-calling).

For more information about how to get Teams, check out [How do I get access to Microsoft Teams?](https://support.office.com/article/fc7f1634-abd3-4f26-a597-9df16e4ca65b)

## Deploy Teams displays using Intune

To learn more about how to deploy Teams displays using Intune, see [Deploy Teams phones and Teams displays](phones-displays-deploy.md).

## Manage Teams displays in your organization

To manage your Teams display devices, in the left navigation of the Microsoft Teams admin center, go to **Teams displays**. From here, you can change the device configuration profile, manage updates, restart devices, add and remove device tags, and more. For more information, see [Manage your devices in Teams](device-management.md).

## Set up hot-desking on Teams displays

Hot desking allows people in your organization to reserve temporary workspaces in advance through Teams and Outlook, or from the device itself. When hot-desking is enabled, users sign into Teams displays with their Microsoft 365 credentials to access their meetings, chats, and files. When they sign out, all their personal information is removed from the device.

To get started, you'll need to acquire [Microsoft Teams Shared Device licenses](../teams-add-on-licensing/teams-shared-device-license.md) and create resource accounts for each Teams display. See [Create resource accounts for rooms and shared Teams devices](../rooms/create-resource-account.md) to create resource accounts.

After you create resource accounts, you can create and assign a policy to enable hot-desking. See [New-CsTeamsIPPhonePolicy](/powershell/module/skype/new-csteamsipphonepolicy) to learn more.

> [!IMPORTANT]
> Because Teams displays with hot-desking are used in shared workspaces by multiple people, Conditional Access rules and other identity configurations in your environment, like Multi-Factor Authentication, can impact these devices and cause sign-in issues. For guidance on securing shared devices, see [Authentication best practices for shared Teams Android devices](authentication-best-practices-for-android-devices.md).

## See also

[Introducing Microsoft Teams displays](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/introducing-microsoft-teams-displays/ba-p/1505437)

[Teams Marketplace](https://office.com/teamsdevices)

[Phones for Teams](phones-for-teams.md)

[IP Phones certified for Microsoft Teams](teams-ip-phones.md)


