---
title: "Manage the Walkie Talkie app in Microsoft Teams"
author: lana-chin
ms.author: v-chinlana
manager: jtremper
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: yinchang
description: How to manage the Walkie Talkie app in Microsoft Teams, which provides push-to-talk communication for teams on Android and iOS devices.
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords: NOCSH
ms.collection: 
- M365-collaboration
- m365-frontline
- teams-1p-app-admin
- highpri
appliesto: 
  - Microsoft Teams
  - Microsoft 365 for frontline workers
ms.date: 02/27/2024
---

# Manage the Walkie Talkie app in Microsoft Teams

## Overview of Walkie Talkie

The Walkie Talkie app in Microsoft Teams provides a push-to-talk (PTT) experience that enables clear, instant, and secure voice communications – turning Android and iOS devices into a walkie talkie. Your users connect with their team through the same underlying Teams channels that they're already members of.

Team members can listen and talk to other team members who are connected through Walkie Talkie on the same channel. Users continue to receive transmissions until they tap **Stop listening**. Walkie Talkie supports communicating in standard and private channels in Teams. Shared channels aren't supported.

With Walkie Talkie, users can communicate through a familiar PTT experience without needing to carry bulky radios. And because Walkie Talkie works over Wi-Fi or cellular data, your users can stay connected to and instantly communicate with their team from anywhere they have an internet connection.

To learn more about the end-user experience, see [Get started with Teams Walkie Talkie](https://support.microsoft.com/office/get-started-with-teams-walkie-talkie-25bdc3d5-bbb2-41b7-89bf-650fae0c8e0c),
[Communicate with your team with Walkie Talkie](https://support.microsoft.com/office/communicate-with-your-team-in-walkie-talkie-e4342550-5516-4451-b9ec-93166b60f8a4), and [Set up and use a wired headset with Walkie Talkie](https://support.microsoft.com/office/set-up-and-use-a-wired-headset-with-walkie-talkie-in-teams-ee17b280-ad3c-4d5c-b78c-146a7b39c285).

> [!NOTE]
> Walkie Talkie currently is not available in China.

## Licensing

Walkie Talkie is included in all paid licenses of Teams.

## Prepare your network

Walkie Talkie requires connectivity to the internet. Use the following guidance to set up your organization's network for Walkie Talkie:

- Make sure that all endpoints listed for Teams in [Office 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams) are reachable by Teams users on your network.

- Prepare your network:

  - [Prepare your organization's network for Teams](prepare-network.md)
  - [Proxy servers for Teams](proxy-servers-for-skype-for-business-online.md)

- Download and run the [Microsoft Teams Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=103017) to test your network performance and connectivity to determine how well your network will perform with Walkie Talkie.

## Deploy Walkie Talkie

You deploy and manage Walkie Talkie from the Teams admin center. Walkie Talkie is supported on Android devices with Google Mobile Services (GMS) and iOS devices.

> [!IMPORTANT]
> Deployment is a three-step process. You'll need to complete all three steps for your users to have access to Walkie Talkie.

### Step 1: Make sure Walkie Talkie is enabled in your organization

You control whether the app is available at the organization level on the [Manage apps](manage-apps.md) page in the Microsoft Teams admin center. To confirm that the app is enabled in your organization:

1. In the left navigation of the Teams admin center, go to **Teams apps** > **Manage apps**.
2. In the list of apps, search for the Walkie Talkie app, select it, and then make sure the **Status** toggle is set to **Allowed**.

### Step 2: Create and assign an app permission policy

Control which users in your organization can use Walkie Talkie by assigning app permission policies in the Teams admin center. To learn more, see [Use app permission policies to control user access to apps](teams-app-permission-policies.md).

Make sure Walkie Talkie is an allowed app in the app permission policy, and you assign the policy to all users who need Walkie Talkie.

### Step 3: Pin Walkie Talkie for your users

Pin Walkie Talkie to Teams for easy access. This step depends on which license your users have.

- [If your users have E licenses](#e-license-use-an-app-setup-policy-to-pin-walkie-talkie-to-teams)
- [If your users have F licenses](#f-license-use-the-tailored-frontline-app-experience-to-pin-walkie-talkie-and-other-apps-to-teams)

#### E license: Use an app setup policy to pin Walkie Talkie to Teams

App setup policies let you customize Teams to pin apps that are most important for your users in your users.

To pin the Walkie Talkie app for your users, you can edit the global (Org-wide default) policy or create and assign a custom policy in app setup policy. To learn more, see [Use app setup policies to pin and auto-install apps for users](teams-app-setup-policies.md).

:::image type="content" source="media/deploy-walkie-talkie-2.png" alt-text="Screenshot showing adding Walkie Talkie to the pinned apps list in the Add pinned apps pane." lightbox="media/deploy-walkie-talkie-2.png":::

#### F license: Use the Tailored frontline app experience to pin Walkie Talkie and other apps to Teams

The tailored frontline app experience in Teams pins the most relevant apps in Teams for users who have an [F license](https://www.microsoft.com/microsoft-365/enterprise/frontline#office-SKUChooser-0dbn8nt). Pinned apps include Walkie Talkie, Shifts, Tasks, and Approvals. By default, this feature is on, giving your frontline workers an out-of-the-box experience tailored to their needs.

The apps are pinned to the app bar at the bottom of Teams mobile clients where users can quickly and easily access them.

To learn more, including how the experience works with app policies that you set, see [Tailor Teams apps for your frontline workers](/microsoft-365/frontline/pin-teams-apps-based-on-license?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json).

## Network considerations

The following network conditions are required for an optimal experience.

|Metric | Required |
|---|---|
|Latency (RTT) | < 300 ms |
|Jitter |< 30 ms |
|Packet Loss |< 1% |

As noted, the quality of real-time media over an IP network is greatly affected by the quality of the network connectivity, but especially by the amount of:

- **Latency** - The time it takes to get an IP packet from point A to point B on the network. This network propagation delay is tied to the physical distance between the two points and the speed of light, including more overhead taken by the various routers in between. Latency is measured as Round-trip Time (RTT).
- **Inter-arrival jitter** - The average change in delay between successive packets.
- **Packet loss** - Packet loss is often defined as a percentage of packets that are lost in a given window of time. Packet loss directly affects audio quality—from small, individual lost packets that have almost no impact, to back-to-back burst losses that cause complete audio cut-out.

Expected data usage from Walkie Talkie is around 20 Kb/s when sending or receiving audio. When idle, expected data usage from Walkie Talkie is negligible.

Also, keep in mind the following:

- Walkie Talkie should work well in low bandwidth situations, or situations where the user's phone is connected and working. Walkie Talkie doesn't work when there's no connectivity at all.
- If users are using mobile data to communicate in Teams, Walkie Talkie will use the same method.

## Devices and accessories

Heads-up and hands-free communication is key for real-time collaboration. Frontline workers often need to communicate with each other when their phones are locked. This experience is possible through the following devices and headsets:

- [Generic wired headsets](#generic-wired-headsets)
- [Specialized headsets and devices that have a dedicated PTT button](#specialized-headsets-and-devices-that-have-a-dedicated-ptt-button)

### Generic wired headsets

Walkie Talkie works with any generic wired (3.5 mm and USB-C) headset on Android. As long as the generic headset has a play/pause button or an answer/end call button, frontline workers can tap the button to start and end transmissions on Walkie Talkie in Toggle-to-Talk mode.

### Specialized headsets and devices that have a dedicated PTT button

Walkie Talkie is integrated with a range of specialized headsets and devices that have a dedicated PTT button. Press and hold the PTT button on the headset or device to instantly send transmissions. Here's a list of these headsets and devices from our partners.

**Headsets**

|Manufacturer  |Model  |Wired or wireless|Platform|
|---------|---------|---------|---------|
|[BlueParrott](https://www.blueparrott.com/microsoft-teams-walkie-talkie)|<ul><li>[B450-XT](https://www.blueparrott.ca/on-the-road-headsets/blueparrott-b450-xt), firmware version 1.07</li><li>[C300-XT](https://www.blueparrott.ca/on-the-road-headsets/blueparrott-c300-xt), firmware version 1.30</li></ul>|Wireless|Android, iOS|
|Jabra    |<ul><li>[Perform 45](https://www.jabra.ca/bluetooth-headsets/jabra-perform-45)</li></ul>|Wireless|Android, iOS|
|[Klein Electronics](https://www.kleinelectronics.com/poc-accessories/mtwt/)   |<ul><li>3.5 mm</li><li>USB-C</li></ul>|Wired|Android|

**Rugged Android phones**

|Manufacturer |Model|Setup |
|---------|---------|---------|
|Crosscall    |[Core-X4](https://www.crosscall.com/en_FR/core-x4-1001010801327.html), [Core-M5](https://www.crosscall.com/en_FR/core-m5-1001011101114.html), [Action-X5](https://www.crosscall.com/en_FR/action-x5-1001020701220.html), [Core-X5](https://www.crosscall.com/en_FR/core-x5-1001010701695.html), [Core-T5](https://www.crosscall.com/en_FR/core-t5-1003011401749.html)|Manual setup: With Teams installed, go to **Settings** > **Buttons**. On the Dedicated button (1 or 2), select **Long press**, and then choose **PTT App**. Select the blue wheel next to **Custom**, and select **Teams**. |
|Kyocera    |[DuraForce Ultra 5G](https://www.kyoceramobile.com/rugged-devices/duraforce-ultra-5g), [DuraSport 5G](https://kyoceramobile.com/durasport-5g/) |Manual setup: With Teams installed, go to **Settings** > **Programmable keys**. Choose **PTT key** or **Press and hold** (depending on the device), and select **Teams**.         |
|Honeywell    |[CT30 XP](https://sps.honeywell.com/us/en/products/productivity/mobile-computers/handheld-computers/ct30-xp-handheld-computer), [CT30 XP HC](https://sps.honeywell.com/us/en/products/productivity/mobile-computers/handheld-computers/ct30-xp-hc-mobile-computer), [EDA51](https://sps.honeywell.com/us/en/products/productivity/mobile-computers/handheld-computers/scanpal-eda51-handheld-computer), [EDA52](https://sps.honeywell.com/us/en/products/productivity/mobile-computers/handheld-computers/eda52-handheld-computer), [EDA52 HC](https://sps.honeywell.com/gb/en/products/productivity/mobile-computers/healthcare-computers/scanpal-eda52-healthcare-mobile-computer)          |Manual setup: With Teams installed, the dedicated PTT button works with Walkie Talkie by default.<br>**Important**: Customers using Honeywell CT30 should upgrade to Android version: **A11 HON4290 MR14**.         |
|Samsung    |[Galaxy XCover7](https://www.samsung.com/uk/smartphones/others/galaxy-xcover7-black-128gb-sm-g556bzkdeeb/) (not available in North America), [Galaxy XCover6 Pro](https://www.samsung.com/us/business/products/mobile/phones/galaxy-xcover-pro/), [Galaxy Tab Active5](https://www.samsung.com/us/business/mobile/tablets/galaxy-tab-active/explore/) |<ul><li>Manual setup: With Teams installed, go to **Settings** > **Advanced Features** > **XCover/Active key**. Turn on **Control XCover key with app**, and select **Teams**.</li><li>[MDM setup](https://docs.samsungknox.com/admin/knox-service-plugin/intune-teams.htm)</li></ul>         |
|Sonim |XP8        |Manual setup: With Teams installed, go to **Settings** > **Programmable Keys**. Choose **Select PTT Key app**, and select **Teams**.         |
|Zebra    |[TC5x](https://www.zebra.com/us/en/products/mobile-computers/handheld/tc5x-series.html), [TC15](https://www.zebra.com/gb/en/products/mobile-computers/handheld/tc15.html) (not available in North America), [TC5301](https://www.zebra.com/us/en/products/spec-sheets/mobile-computers/handheld/tc53-tc58.html) , [TC7x](https://www.zebra.com/us/en/products/mobile-computers/handheld/tc7x-series.html), [TC2x](https://www.zebra.com/us/en/products/mobile-computers/handheld/tc2x-series.html), [EC5x](https://www.zebra.com/us/en/products/mobile-computers/handheld/ec50-ec55.html), [MC3300](https://www.zebra.com/us/en/products/mobile-computers/handheld/mc3300.html), [MC9300](https://www.zebra.com/us/en/products/mobile-computers/handheld/mc9300.html), [ET40](https://www.zebra.com/us/en/products/spec-sheets/tablets/et40-et45.html)         |Manual setup: With Teams installed, the dedicated PTT button (LEFT_TRIGGER_2) works with Walkie Talkie by default.         |

> [!NOTE]
> These headsets and devices are not Teams certified. They have been validated to work with Walkie Talkie in Teams.

### Considerations when using Bluetooth devices

> [!NOTE]
> If your users are using Bluetooth accessories, make sure that your mobile device management (MDM) solution doesn't block Bluetooth devices.

On devices running Android OS version 12 or later, Bluetooth permissions are required and location permissions to connect using the BLE stack are no longer required. If "nearby permissions" aren't granted at the Teams level, a user receives a prompt for Bluetooth permissions. This prompt is displayed, whether or not a Bluetooth accessory, such as a headset, is connected to their device. If a Bluetooth accessory is connected, tapping **Allow** connects Walkie Talkie to the Bluetooth accessory.

## Get insight into Walkie Talkie usage and performance

The [Walkie Talkie usage and performance report](teams-analytics-and-reports/walkie-talkie-usage-report.md) in the Teams admin center gives you and overview of Walkie Talkie activity and performance in your organization. The report provides information such as the number of PTT transmissions made and received, channel activity, transmission duration, and device and participant details.

## Data residency

Walkie Talkie customer data for tenants in the European Union Data Boundary (EUDB) and in the United Kingdom is stored in data centers located in the EU. To be considered a tenant in the EUDB, the tenant must have a _default geography_ in a EUDB country/region or select a country/region in EUDB country/region as their residence during sign-up.

All other tenants have their Walkie Talkie customer data stored in data centers located in the United States. Tenants aren't provided with a choice for the specific deployment region for data storage.

### How can I determine customer data location?

See [Microsoft Entra ID and data residency](/azure/active-directory/fundamentals/data-residency).

## Give feedback or report an issue

To send feedback or report an issue, go to **Settings** > **Help & feedback**, and then choose **Send feedback**. Enter your feedback or details about the issue you're experiencing. Indicate at the beginning of your feedback report that you're sending feedback about Walkie Talkie so we can easily identify Walkie Talkie issues.

Users in your organization can attach logs while sharing feedback to Microsoft, if you enable the policy to [set whether users can send feedback about Teams to Microsoft](/microsoftteams/manage-feedback-policies-in-teams).
