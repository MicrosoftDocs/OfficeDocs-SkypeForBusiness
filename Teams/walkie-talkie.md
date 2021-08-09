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

The Walkie Talkie app in Teams provides instant push-to-talk (PTT) communication for your team and is now available on Android. Walkie Talkie allows users to connect with their team using the same underlying channels they're members of. Only users who connect to Walkie Talkie in a channel become participants and can communicate with each other using push-to-talk, one at a time.

With Walkie Talkie in Teams, frontline workers can now securely communicate with a familiar PTT experience without needing to carry bulky radios, and Walkie Talkie works anywhere with WiFi or cellular internet connectivity.

## Getting started

### Deploying Walkie Talkie

Currently, Walkie Talkie is available for Android devices with Google Mobile Services (GMS) and is not pre-installed. To enable this feature for users in your organization, you need to add Walkie Talkie to the [App Setup Policy](teams-app-setup-policies.md) assigned to users from the [Teams Admin Center](https://admin.teams.microsoft.com/). Once enabled, Walkie Talkie will become available on the Android app within 48 hours.

### Adding Walkie Talkie to your app list

In the Microsoft Teams admin center, under **Teams app** > **Setup policies**, you should have **Allow user pinning** set to **On**. Then, under the Pinned Apps section, click **+Add Apps**.

:::image type="content" source="media/deploy-walkie-talkie-1.png" alt-text="Shows the Pinned apps section and the Add Apps button to be selected.":::

On the **Add pinned apps** panel that appears on the right, use the **Search** textbox to look for Walkie Talkie. When you have it as a search result, select the **Add** button to the right of the name to add it to your list.

:::image type="content" source="media/deploy-walkie-talkie-2.png" alt-text="Shows the Add pinned apps sidebar with Walkie entered into the search pane and the Walkie Talkie app in the search results, with the Add button next to it.":::

The Walkie Talkie app should now appear on the Pinned Apps list, and be available for use once you click the **Save** button.

:::image type="content" source="media/deploy-walkie-talkie-3.png" alt-text="Shows the Pinned apps list with the Walkie Talkie app added, and the Save button underneath the list.":::

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
  - Wireless headsets 
    - [BlueParrott](https://www.blueparrott.com/microsoft-teams-walkie-talkie)
  - Wired headsets 
    - [Klein Electronics](https://www.kleinelectronics.com/poc-accessories/mtwt/)
- **Rugged phones**
  - Samsung [Galaxy XCover Pro](https://www.samsung.com/us/business/products/mobile/phones/galaxy-xcover-pro/), [Galaxy XCover 5](https://www.samsung.com/de/smartphones/others/galaxy-xcover-5-black-64gb-sm-g525fzkdeeb/buy), [Galaxy Tab Active 3](https://www.samsung.com/us/business/tablets/galaxy-tab-active/buy/)
    -  Manual setup - With Teams installed, navigate to Settings > Advanced Features > XCover/Active key. Turn on 'Control XCover key with app' and select 'Teams'
    -  [MDM setup](https://docs.samsungknox.com/admin/knox-service-plugin/intune-teams.htm)

> [!NOTE]
> These devices are not Teams certified. They have been validated to work with Teams Walkie Talkie.

### License requirements

Walkie Talkie app is included in all paid licenses of Teams in [Office 365 subscriptions](/office365/servicedescriptions/teams-service-description). For more information about getting Teams, check out [How do I get access to Microsoft Teams](https://support.office.com/article/fc7f1634-abd3-4f26-a597-9df16e4ca65b)?

> [!NOTE]
> Certain advanced features may require additional licensing. For example, integration with Samsung Galaxy XCover Pro requires a Knox license.

## Further information

- ITAdmins can maintain control over who is using Walkie Talkie through App Policies.
- If your frontline worker is using mobile data to communicate via Teams, Walkie Talkie will use the same method.
- Walkie Talkie should work well in low bandwidth situations, or situations where your smartphone is connected and working. Walkie Talkie will not work when there is no connectivity at all.

For further reading on the end-user experience, see:

- [Get started with Teams Walkie Talkie](https://support.microsoft.com/office/get-started-with-teams-walkie-talkie-25bdc3d5-bbb2-41b7-89bf-650fae0c8e0c)
- [Communicate with your team with Walkie Talkie](https://support.microsoft.com/office/communicate-with-your-team-in-walkie-talkie-e4342550-5516-4451-b9ec-93166b60f8a4)
