---
title: "Microsoft Teams displays"
ms.author: v-lanac
author: lanachin
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
search.appverid: MET150
localization_priority: Normal
description: "This article provides an overview of and features suppprted by Microsoft Teams displays."
---

# Microsoft Teams displays

Microsoft Teams displays are a category of all-in-one dedicated Teams devices that feature an ambient touchscreen and a hands-free experience powered by Cortana. This article provides an overview of Teams displays and can help you plan, deliver, and manage Teams displays in your organization.

Teams displays brings together your favorite Teams features&ndash;chat, meetings, calls, calendar, and files&ndash;into a single device. With Teams displays, users can use a microphone, camera, and speakers (or Bluetooth headset) for a reliable calling and meeting experience. Teams displays integrates with users' Windows PCs to bring a companion experience that allows for seamless cross-device interaction.

For the latest information on Teams devices, check out [Teams Marketplace](https://office.com/teamsdevices).

## Features supported by Teams displays

In addition to the [features supported by Teams phones](phones-for-teams.md#features-supported-by-teams-phones), the following features are unique to Teams displays:

- **Dedicated displays for Teams** Users can access all core Teams features including chat, meetings, calls, teams and channels, files and more.
- **Ambient experience** Users can easily stay on top of their busy work with always-on and glanceable displays to see important activities and notifications without context-switching on their primary work device. Users can also personalize Teams displays by customizing the background through settings.
- **Hands-free with Cortana** Users can interact with Teams displays using their voice to effortlessly join and present in meetings, dictate replies to a Teams chat, check what’s on the calendar, and more.
- **Leave a note on lock screen** Guests can choose to leave audio,video, and text notes, and users can check the notes left by guests and see who’s stopped by.  

## Required licenses

Teams licenses can be purchased as part of [Microsoft 365 and Office 365 subscriptions](https://docs.microsoft.com/office365/servicedescriptions/teams-service-description). To learn more about the required licenses to use Teams displays, see [Voice and video calling with Microsoft Teams](https://products.office.com/microsoft-teams/voice-calling).

For more information about how to get Teams, check out [How do I get access to Microsoft Teams?](https://support.office.com/article/fc7f1634-abd3-4f26-a597-9df16e4ca65b)

## Deploy Teams displays via Intune

### Conditional Access

Conditional Access is an Azure Active Directory feature that helps you to ensure devices accessing your Office 365 resources are properly managed and are secure.  If you apply Conditional Access policies to the Teams service, Android devices (including Teams displays) that access Teams need to be enrolled into Intune and their settings need to comply with your policies.  If the device isn't enrolled into Intune, or if it's enrolled but its settings don't comply with your policies, Conditional Access will prevent a user from signing into or using the Teams app on the device.

Typically, compliance policies defined within Intune are assigned to groups of users.  This means that if you assign an Android compliance policy to user@contoso.com, that policy will apply equally to their Android smartphone and to any Android-based Teams device that user@contoso.com signs into.

If you use Conditional Access, which requires Intune enrollment to be enforced, in your organization, there are a couple things you need to set up to allow for a successful Intune enrollment:

- **Intune license** The user signing into the Microsoft Teams phone must be licensed for Intune.  As long as the Teams displays are signed into a user account that has a valid Intune license, the device will automatically be enrolled in Microsoft Intune as part of the sign-in process.
- **Configure Intune** You must have a properly configured Intune tenant set up for Android Device Administrator enrollment.

### Configure Intune to enroll Teams Android-based devices

Teams Android-based devices are managed by in Intune via Android Device Administrator (DA) management. Before devices can be enrolled into Intune, there are a few basic steps to perform.  If you are already managing devices with Intune today, you probably have already done all these things.  If not, here’s what to do:

1. Set Intune MDM (mobile device management) Authority.  If you’re never used Intune before, you need to set the MDM authority before you can enroll devices. For more information, see [Set the mobile device management authority](https://docs.microsoft.com/intune/fundamentals/mdm-authority-set).  This is a one-time step that has to be done upon creating a new Intune tenant.
2. Enable Android device administrator enrollment. Android-based Teams device are managed as device administrator devices with Intune.  Device administrator enrollment is off by default for newly created tenants.  For more information, see [Android device administrator enrollment](https://docs.microsoft.com/intune/enrollment/android-enroll-device-administrator).
3. Assign licenses to users. Users of Teams devices enrolling to Intune must be assigned a valid Intune license. For more information, see [Assign licenses to users so they can enroll devices in Intune](https://docs.microsoft.com/intune/fundamentals/licenses-assign).
4. Assign Device Administrator compliance policies.  Create an Android Device Administrator compliance policy and assign it to the Azure Active Directory group that contains the users that will be signing into the Teams devices. For more information, see [Use compliance policies to set rules for devices you manage with Intune](https://docs.microsoft.com/mem/intune/protect/device-compliance-get-started).

## Manage Teams displays in your organization

Admins can manage and keep all your Teams devices up-to-date using the Microsoft Teams admin center. For more information, see [Manage your devices in Teams](device-management.md).

## See also

[Introducing Microsoft Teams displays](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/introducing-microsoft-teams-displays/ba-p/1505437)

[Teams Marketplace](https://office.com/teamsdevices)

[Phones for Teams](phones-for-teams.md)

[IP Phones certified for Microsoft Teams](teams-ip-phones.md)

[Cortana voice assistance in Teams](https://docs.microsoft.com/MicrosoftTeams/cortana-in-teams)
