---
title: Teams Progressive Web Apps (PWAs)
description: Progressive Web Apps (PWAs) allow sites like Teams on the web to offer more desktop capabilities that are typically unavailable to websites.
author: MicrosoftHeidi
ms.author: heidip
manager: jacktremper
audience: admin
displayType: one-column
ms.date: 10/18/2024
ms.reviewer: 
ms.service: msteams
ms.topic: tutorial
ms.localizationpriority: medium
search.appverid: MET150
ms.collection:
  - M365-collaboration
  - tier2
f1.keywords:
  - CSH
ms.custom:
  - NewAdminCenter_Update
  - seo-marvel-mar2020
appliesto: 
  - Microsoft Teams
---

# What is a Progressive Web App (PWA)?

A Progressive Web App (PWA) is a type of web application that can be installed on a device and provides a user experience similar to a native desktop app. PWAs allow sites like Teams on the web to offer more desktop capabilities that are typically unavailable to websites.

PWAs are hosted by Microsoft Edge and Chrome browsers but look and feel like a native app. At their core, PWAs are still websites and operate within the same browser sandbox environment, offering the security and control many administrators require for their users.

## Microsoft Teams on the web as a PWA

Microsoft Teams on the web can be installed as a PWA on Edge or Chrome browsers. This allows users who can't install the Microsoft Teams desktop client or prefer using web apps to still have a seamless Teams desktop experience.

## Benefits of using Teams PWA

- **Automatic start**: Can automatically start on login for quick access.
- **Easy access**: Can be pinned to the taskbar or dock for easy access.
- **Consistent experience**: Provides a more consistent experience for web users who also use Teams desktop clients on other devices.

## Deploying Teams PWA using group policies

Administrators can deploy Microsoft Teams on the web PWA using group policies in Edge and Chrome browsers. There are two relevant policies:

- **WebAppInstallForceList**: This policy allows administrators to force-install specific web apps, including PWAs. Users are unable to uninstall PWAs in this policy, and removing the policy causes the PWA to be uninstalled.
- **WebAppSettings**: This policy provides more settings for managing web apps.

For detailed instructions on configuring these policies, see the following documentation:

- [Edge group policy documentation](/deployedge/microsoft-edge-policies)
- [Chrome group policy documentation](https://support.google.com/chrome/a/answer/187202)

## Recommended group policies for PWA users

To ensure a smooth experience for PWA users and to avoid common permission issues, it's also recommended that administrators set the following group policies:

- **SleepingTabsBlockedForUrls**: Prevents tabs with Teams on the web from going to sleep.
- **NotificationsAllowedForURLs**: Automatically allows notifications for Teams on the web.
- **ScreenCaptureAllowedByOrigins**: Allows screen capture for Teams on the web.
- **AudioCaptureAllowedUrls**: Allows audio capture for Teams on the web.
- **VideoCaptureAllowedUrls**: Allows video capture for specified URLs.
- **CookiesAllowedForUrls**: Unblocks specific cookies for Teams on the web, including third-party cookies used in line-of-business (LOB) apps.

Setting these policies helps users avoid repeatedly approving common permissions or accidentally blocking functionalities needed for Teams on the web.
