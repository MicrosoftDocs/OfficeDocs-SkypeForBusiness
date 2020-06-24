---
title: "Walkie Talkie application in Microsoft Teams"
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer:
description: How to configure the Walkie Talkie app in Microsoft Teams, from an ITAdmin perspective.
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
ms.custom: 
- Security
appliesto: 
  - Microsoft Teams
---

# Walkie Talkie app in Microsoft Teams

The Walkie Talkie app in Teams provides instant push-to-talk (PTT) communication for your team and will soon be available in Public Preview on Android. Walkie Talkie allows users to connect with their team using the same underlying channels they're members of. Only users who connect to Walkie Talkie in a channel become participants and can communicate with each other using push-to-talk, one at a time.

With Walkie Talkie in Teams, Firstline Workers can now securely communicate with a familiar PTT experience without needing to carry bulky radios, and Walkie Talkie works anywhere with WiFi or cellular internet connectivity.

## Getting started

### Deploying Walkie Talkie

During the Public Preview, Walkie Talkie is not pre-installed. To enable this feature for users in your organization, you need to add Walkie Talkie to the [App Setup Policy](teams-app-setup-policies.md) assigned to users from the [Teams Admin Center](https://admin.teams.microsoft.com/).

Once enabled, Walkie Talkie will become available on the Android app within 48 hours.

### Network documentation

Walkie Talkie in Teams requires Internet connectivity and below network conditions are required for optimal experience.

Latency (RTT) < 300ms | Jitter < 30ms | Packet Loss < 1%

Expected data usage from Walkie Talkie is around 20KB/s when sending or receiving audio. When idle, expected data usage from Walkie Talkie is negligible.

### Walkie Talkie devices

FirstLine Workers often need to speak and receive Walkie Talkie calls even when their phones are locked. This experience is possible through specialized devices with a dedicated PTT button.

- Existing phones
  - Wired headsets (Klein) ??? link needed
  - Wireless headsets (Jabra BlueParrott) >>> link needed
- Rugged phones
  - Samsung Galaxy XCover Pro
    - More info. ??? link needed
    - [Setup guide](https://docs.samsungknox.com/admin/knox-service-plugin/intune-teams.htm).

> [!NOTE]
> These devices are not Teams certified. They have been validated to work with Teams Walkie Talkie.

### License requirements

Walkie Talkie app is included in all paid licenses of Teams in [Office 365 subscriptions](https://docs.microsoft.com/MicrosoftTeams/office-365-licensing). For more information about getting Teams, check out [How do I get access to Microsoft Teams](https://support.office.com/article/fc7f1634-abd3-4f26-a597-9df16e4ca65b)?

> [!NOTE]
> Certain advanced features may require additional licensing. For example, integration with Samsung Galaxy XCover Pro requires a Knox license.

## Further information

- ITAdmins can maintain control over who is using Walkie Talkie through App Policies.
- If your Firstline Worker is using mobile data to communicate via Teams, Walkie Talkie will use the same method.
- Walkie Talkie should work well in low bandwidth situations, or situations where your smartphone is connected and working. Walkie Talkie will not work when there is no connectivity at all.

For further reading on the end-user experience, see END USER CONTENT LINK HERE. ???
