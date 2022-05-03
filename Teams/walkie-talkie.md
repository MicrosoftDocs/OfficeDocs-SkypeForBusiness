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
ms.localizationpriority: medium
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

The Walkie Talkie app in Teams provides instant push-to-talk (PTT) communication for your team and is now available on Android & iOS. Walkie Talkie allows users to connect with their team using the same underlying channels they're members of. Only users who connect to Walkie Talkie in a channel become participants and can communicate with each other using push-to-talk, one at a time.

With Walkie Talkie in Teams, frontline workers can now securely communicate with a familiar PTT experience without needing to carry bulky radios, and Walkie Talkie works anywhere with WiFi or cellular internet connectivity.

## Getting started

### Deploying Walkie Talkie

Walkie Talkie is supported on Android devices with Google Mobile Services (GMS) and iOS devices.

### Use the Tailored frontline app experience to pin Walkie Talkie and other apps to Teams

The tailored frontline app experience in Teams pins the most relevant apps in Teams for users who have an [F license](https://www.microsoft.com/microsoft-365/enterprise/frontline#office-SKUChooser-0dbn8nt). Pinned apps include Walkie Talkie, Shifts, Tasks, and Approvals. By default, this feature is on, giving your frontline workers an out-of-the-box experience that’s tailored to their needs.

The apps are pinned to the app bar—the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients—where users can quickly and easily access them.

To learn more, including how the experience works with app policies that you set, see [Tailor Teams apps for your frontline workers](pin-teams-apps-based-on-license.md).

### Use an app setup policy to pin Walkie Talkie to Teams

App setup policies let you customize Teams to pin apps that are most important for your users in your users.

To pin the Walkie Talkie app for your users, you can edit the global (Org-wide default) policy or create and assign a custom app setup policy. To learn more, see [Manage app setup policies in Teams](teams-app-setup-policies.md).

:::image type="content" source="media/deploy-walkie-talkie-2.png" alt-text="Screenshot showing adding Walkie Talkie to the pinned apps list in the Add pinned apps pane." lightbox="media/deploy-walkie-talkie-2.png":::

### Network documentation

Walkie Talkie in Teams requires Internet connectivity and below the network conditions are required for optimal experience.

|Metric | Required |
|---|---|
|Latency (RTT) | < 300ms |
|Jitter |< 30ms |
|Packet Loss |< 1% |

As noted above, the quality of real-time media over an IP network is greatly impacted by the quality of the network connectivity, but especially by the amount of:

- **Latency** - This is the time it takes to get an IP packet from point A to point B on the network. This network propagation delay is essentially tied to physical distance between the two points and the speed of light, including more overhead taken by the various routers in between. Latency is measured as Round-trip Time (RTT).
- **Inter-Arrival Jitter** - This is the average change in delay between successive packets.
- **Packet Loss** - This is often defined as a percentage of packets that are lost in a given window of time. Packet loss directly affects audio quality—from small, individual lost packets having almost no impact, to back-to-back burst losses that cause complete audio cut-out.

Expected data usage from Walkie Talkie is around 20 Kb/s when sending or receiving audio. When idle, expected data usage from Walkie Talkie is negligible.

### Walkie Talkie devices

Frontline workers often need to speak and receive Walkie Talkie calls even when their phones are locked. This experience is possible through specialized devices with a dedicated PTT button.

- **Headsets**
  - Wireless headsets (iOS & Android)
    - [BlueParrott](https://www.blueparrott.com/microsoft-teams-walkie-talkie)
  - Wired headsets (Android only)
    - [Klein Electronics](https://www.kleinelectronics.com/poc-accessories/mtwt/)
- **Rugged Android phones**
  - Samsung [Galaxy XCover Pro](https://www.samsung.com/us/business/products/mobile/phones/galaxy-xcover-pro/), [Galaxy XCover 5](https://www.samsung.com/de/smartphones/others/galaxy-xcover-5-black-64gb-sm-g525fzkdeeb/buy), [Galaxy Tab Active 3](https://www.samsung.com/us/business/tablets/galaxy-tab-active/buy/)
    - Manual setup - With Teams installed, navigate to Settings > Advanced Features > XCover/Active key. Turn on 'Control XCover key with app' and select 'Teams'
    - [MDM setup](https://docs.samsungknox.com/admin/knox-service-plugin/intune-teams.htm)
  - Zebra [TC5x](https://www.zebra.com/us/en/products/mobile-computers/handheld/tc52-tc57-series-touch-computer.html), [TC7x](https://www.zebra.com/us/en/products/mobile-computers/handheld/tc72-tc77-series-touch-computer.html), [TC2x](https://www.zebra.com/us/en/products/mobile-computers/handheld/tc21-tc26.html), [EC5x](https://www.zebra.com/us/en/products/mobile-computers/handheld/ec50-ec55.html), [EC30](https://www.zebra.com/us/en/products/mobile-computers/handheld/ec30.html), [MC3300](https://www.zebra.com/us/en/products/mobile-computers/handheld/mc3300.html), [MC9300](https://www.zebra.com/us/en/products/mobile-computers/handheld/mc9300.html) 
    - Manual setup - With Teams installed, the dedicated PTT button (LEFT_TRIGGER_2) works with Walkie Talkie by default
    
> [!NOTE]
> These devices are not Teams certified. They have been validated to work with Teams Walkie Talkie.

### License requirements

Walkie Talkie app is included in all paid licenses of Teams in [Office 365 subscriptions](/office365/servicedescriptions/teams-service-description). For more information about getting Teams, check out [How do I get access to Microsoft Teams](https://support.office.com/article/fc7f1634-abd3-4f26-a597-9df16e4ca65b)?

## Further information

- ITAdmins can maintain control over who is using Walkie Talkie through App Policies.
- If your frontline worker is using mobile data to communicate via Teams, Walkie Talkie will use the same method.
- Walkie Talkie should work well in low bandwidth situations, or situations where your smartphone is connected and working. Walkie Talkie will not work when there is no connectivity at all.

For further reading on the end-user experience, see:

- [Get started with Teams Walkie Talkie](https://support.microsoft.com/office/get-started-with-teams-walkie-talkie-25bdc3d5-bbb2-41b7-89bf-650fae0c8e0c)
- [Communicate with your team with Walkie Talkie](https://support.microsoft.com/office/communicate-with-your-team-in-walkie-talkie-e4342550-5516-4451-b9ec-93166b60f8a4)
