---
title: Microsoft Teams displays
ms.author: dstrome
author: dstrome
manager: serdars
ms.reviewer: weizxue
ms.topic: reference
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords: 
  - NOCSH
ms.collection: 
  - M365-voice
  - Teams_ITAdmin_Devices
search.appverid: MET150
ms.localizationpriority: medium
description: This article provides an overview of and features supported by Microsoft Teams displays.
---

# Microsoft Teams displays

Microsoft Teams displays are a category of all-in-one dedicated Teams devices that feature an ambient touchscreen and a hands-free experience powered by Cortana. This article provides an overview of Teams displays and can help you plan, deliver, and manage Teams displays in your organization.

Teams displays brings together your favorite Teams features&ndash;chat, meetings, calls, calendar, and files&ndash;into a single device. With Teams displays, users can use a microphone, camera, and speakers (or Bluetooth headset) for a reliable calling and meeting experience. Teams displays integrates with users' Windows PCs to bring a companion experience that allows for seamless cross-device interaction.

To learn more, check out [Get started with Teams displays](https://support.microsoft.com/office/get-started-with-teams-displays-ff299825-7f13-4528-96c2-1d3437e6d4e6).

## Features supported by Teams displays

In addition to the [features supported by Teams phones](phones-for-teams.md#features-supported-by-teams-phones), the following features are unique to Teams displays:

- **Dedicated displays for Teams** Users can access all core Teams features including chat, meetings, calls, teams and channels, files and more.
- **Ambient experience** Users can easily stay on top of their work with always-on and glanceable displays to see important activities and notifications without context-switching on their primary work device. Users can also personalize Teams displays by customizing the background through settings.
- **Hands-free with Cortana** Users can interact with Teams displays using their voice to effortlessly join and present in meetings, dictate replies to a Teams chat, check what’s on the calendar, and more.
- **Leave a note on lock screen** Guests can choose to leave audio, video, and text notes, and users can check the notes left by guests and see who’s stopped by.  

## Required licenses

Teams licenses can be purchased as part of [Microsoft 365 and Office 365 subscriptions](/office365/servicedescriptions/teams-service-description). To learn more about the required licenses to use Teams displays, see [Voice and video calling with Microsoft Teams](https://products.office.com/microsoft-teams/voice-calling).

For more information about how to get Teams, check out [How do I get access to Microsoft Teams?](https://support.office.com/article/fc7f1634-abd3-4f26-a597-9df16e4ca65b)

## Deploy Teams displays using Intune

To learn more about how to deploy Teams displays using Intune, see [Deploy Teams phones and Teams displays](phones-displays-deploy.md).

## Manage Teams displays in your organization

To manage your Teams display devices, in the left navigation of the Microsoft Teams admin center, go to **Teams displays**. From here, you can change the device configuration profile, manage updates, restart devices, add and remove device tags, and more. For more information, see [Manage your devices in Teams](device-management.md).

## Set up hot desking on Teams displays

Hot desking allows people in your organization to reserve temporary workspaces in advance through Teams and Outlook, or from the device itself. When hot desking is enabled, users sign into Teams displays with their Microsoft 365 credentials to access their meetings, chats, and files. When they sign out, all their personal information is removed from the device.

To get started, you'll need to acquire [Microsoft Teams Rooms licenses](../rooms/rooms-licensing.md) and create resource accounts for each Teams display. See [Create resource accounts for rooms and shared Teams devices](../rooms/with-office-365.md) to create resource accounts.

After you create resource accounts, you can create and assign a policy to enable hot desking. See [New-CsTeamsIPPhonePolicy](/powershell/module/skype/new-csteamsipphonepolicy?view=skype-ps) to learn more.

> [!IMPORTANT]
> Because Teams displays with hot desking are used in shared workspaces by multiple people, Conditional Access rules and other identity configurations in your environment, like Multi-Factor Authentication, can impact these devices and cause sign-in issues. For guidance on securing shared devices, see [Authentication best practices for shared Teams Android devices](authentication-best-practices-for-android-devices.md).

## Upgrade Teams phones to Teams displays

Teams displays is the evolution of Teams phones. You can upgrade Teams phones in your organization to Teams displays using the Microsoft Teams admin center. This option is available only to phones that support upgrading to Teams displays. To learn more, see [Upgrade Teams phones to Teams displays](upgrade-phones-to-displays.md).

## See also

[Introducing Microsoft Teams displays](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/introducing-microsoft-teams-displays/ba-p/1505437)

[Teams Marketplace](https://office.com/teamsdevices)

[Phones for Teams](phones-for-teams.md)

[IP Phones certified for Microsoft Teams](teams-ip-phones.md)

[Upgrade IP phones to Teams displays](upgrade-phones-to-displays.md)

[Cortana voice assistance in Teams](../cortana-in-teams.md)