---
title: Bring Your Own Device Rooms in Pro Management Portal
author: v-mathavale
ms.author: v-mathavale
manager: pamgreen
ms.date: 01/29/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: itpro-rooms
audience: Admin
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier3
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use Bring Your Own Device rooms feature in the Pro Management Portal
f1keywords: 
---

# Bring Your Own Device Rooms in Teams Pro Management portal

Bring Your Own Device rooms are identified as rooms with no Microsoft Teams Rooms. As an admin, you'll gain visibility of the Bring Your Own Device rooms and devices in the Teams Pro Management Portal upon logging in. To have access to the portal, you'll need at least one pro, premium, or Teams Shared Device (TSD) license.

1. Open Pro Management Portal on [https://portal.rooms.microsoft.com/](https://portal.rooms.microsoft.com/) and navigate to **Inventory**.
2. In the left navigation menu, select **Planning** and go to **Inventory**.

> [!NOTE]
> For the devices to be captured in Pro Management Portal as Bring Your Own Devices, user needs to plug in the device in the room and join a meeting. We will need at least five unique users to report the device.

## Inventory page

In the **Inventory** page, you'll find an overview of all the rooms within your organization. You can explore your organization's inventory and devices and you can find rooms based on specific groups (country, city, buildings) or by utilizing the search function.

There are two main tabs under **Inventory**: **Rooms** and **Devices**.

### Rooms view

:::image type="content" source="../media/byod/inventory-rooms-tab.png" alt-text="Screenshot of Inventory rooms tab." lightbox="../media/byod/inventory-rooms-tab.png"::: 
This page provides a comprehensive summary of your rooms, featuring the following key insights:

- The total number of rooms in your tenant categorized by type (Microsoft Teams Rooms, Bring Your Own Device).

> [!NOTE]
> The Devices and Rooms association needs to be done in order to view your **Bring Your Own Device** rooms under the **Rooms** page.

- Rooms by capacity: Distribution of rooms by capacity, with a breakdown into small, medium, and large rooms.

The following table describes the columns in the **Rooms** view of Inventory. 

| **Column** | **Description** |
| --- | --- |
| Display name | Name of the room |
| Capacity | Illustrate the room's capacity number |
| Room type | Type of the room either Teams Rooms or Bring Your Own Device |
| Licenses Type | Type of license assigned to the room (for example, pro, premium, basic, standard, shared licenses, or unlicensed) |

Below the headline, you'll find a table with specific information about each room:

#### Room detail view:

When you select a specific room, you'll see a new pane with two different pages, **General** and **Inventory** page.

- **The General page:** Provides the following room information:

| Name | The name of the room |
| --- | --- |
| Seating Capacity | The room's capacity |
| OEM name | The manufacturer name |
| Resource account | The account associated with the room |
| Room address | The physical address of the room (street, city, zip code, building, floor) |

- **The Inventory page** displays detailed information about the room's devices:

| **Column** | **Description** |
| --- | --- |
| Name | Name of the device |
| Type | Type of device (for example, Microsoft Teams Rooms, TeamsPanel, camera.) |
| Make | Manufacturer name |
| SerialNumber | The device's serial number |

### Device view

:::image type="content" source="../media/byod/inventory-devices-asso.png" alt-text="Screenshot of Device page." lightbox="../media/byod/inventory-devices-asso.png":::

The Device page offers a comprehensive overview of device and room insights.

The Devices tab displays a table with device information. Select the device to view more details.

| **Column** | **Description** |
| --- | --- |
| Device display name | Name of the device |
| Device type | The category of the device (for example, panel, speaker) |
| Associated account | The name of the room associated with the device. <br> Need action: Indicates if the device isn't yet associated with a room |
| SerialNumber | The device's serial number |

#### Device detailed view:

When you select a specific device associated with a room, a new page opens up displaying the following two tabs:

- **Configuration**: This page displays information about the device and room, including device serial number, product and vendor ID, manufacturer, and model. It also displays room details like name, capacity, city, state, building, and license type.
- **Usage details**: This page shows the room's usage report data for the selected period and can be accessible only with a Teams Shared Device license assigned to the room.

### To add a device to the room

To associate a device with a room, the following two methods are available:

- **Use Import/Export function:** You can use this function to export the inventory list via an Excel file and construct Bring Your Own Device rooms.

    1. In the **Devices** page, click **Export** to download the device inventory.
    2. Open the Excel file and verify that it contains all the devices and room information.
    3. In the Excel file, select the **PERIPHERALS** tab and fill out the Account or Display Name column for the devices listed.
    4. Save the file after associating the device with the specific room information.
    5. Go back to the Inventory Devices page and click **Import** to upload the modified file.
    6. Verify that the device-room association is updated successfully.

    > [!NOTE]
    > In cases where the devices were not discovered or reported by Pro Management portal, admins can add those new devices using the import function. Device information such as the Product ID, Vendor ID, Serial Number, and Account information are required for the association to be done.

- **Manually associate discovered devices using Pro Management UI:** 
    
    1. Go to the device table.
    1. Select the specific device with the **Need Action** banner. 
    1. Click **Add a room to this device**.
    1. Select the desired room from the list to associate the device with.
    1. Click **Save**.

:::image type="content" source="../media/byod/device-discovery.png" alt-text="Screenshot of device room association." lightbox="../media/byod/device-discovery.png":::


## Devices automatically discovered by the Pro Management Portal

Devices are automatically discovered using your users' Teams client to send device data to Pro Management Portal. When a user enters the prejoin screen of a meeting, any connected displays and USB audio/video peripherals are scanned and transmitted to the cloud. These devices populate your Devices tab within the Inventory navigation.

At launch, only displays are supported, but USB audio/video peripherals will follow within a few weeks. Display ingestion is supported on Windows and Mac, whereas USB audio/video will only be supported on Windows.

Be aware that Microsoft can't guarantee that devices provide unique data like serial numbers, and this may cause errors or overcounting of usage. We recommend working with your OEM partners to ensure that their devices are providing unique serial numbers to the operating system via the USB descriptor or EDID.

## Bring Your Own Device Usage Report 

> [!IMPORTANT]
> A Teams Shared Device license is required to unlock the Bring Your Own Device room usage report. For more information about the Teams Shared Device, see [Microsoft Teams Shared Devices licensing - Microsoft Teams | Microsoft Learn](../teams-add-on-licensing/teams-shared-device-license.md).

To view the Usage report for your Bring Your Own Device rooms:
1. In the left navigation menu, select **Reports**.
1. In the Reports page, select the **BYOD Usage** tab.  

:::image type="content" source="../media/byod/usage-report.png" alt-text="Screenshot of Usage Report." lightbox="../media/byod/usage-report.png":::
The headlines provide few rooms’ insights described in the following table: 

| Metrics | Description |
|---|---|
| **Total rooms** | Total number of Bring Your Own Device rooms |
| **Unused rooms** | Number of Bring Your Own Device rooms with no calls |
| **Used rooms** | Number of Bring Your Own Device rooms used based on calls made |
| **Utilization** | Percentage of utilization of all Bring Your Own Device rooms across the tenant. <br> Utilization = Total call duration (all rooms) / (Workdays * workday hour * Bring Your Own Device rooms) <br> For example: If the tenant has 15 Bring Your Own Device Rooms, total call duration for all rooms is 300 h, work days = 10, work day hour = 8 h; then Utilization = 300/(10\*8\*15)= 25% |
| **Audio and video calls** | Will generate the duration of the audio call and video camera |
| **Overall call performance** | Overall Percentage of calls rated as “Good” out of the total calls in the room. Each call is evaluated and receives a Good, poor, Unknown rating. |
| **Total calls** | Overall number of calls made in Bring Your Own Device rooms |

Below the headline metrics, there's a table that provides a granular breakdown of individual Bring Your Own Device rooms, accompanied by specific metrics that illuminate each room’s usage and performance during the period selected. 

| **Column** | **Description** |
|---|---|
| **Display room name** | The designated name of the Bring Your Own Device room |
| **Room Type** | Will show as “Bring Your Own Device Room” as room type |
| **Utilization** | The percentage of total call duration spent in a Bring Your Own Device room during business hours in the selected period. <br> For example, for a time period set to 10 Work days for room A, total call duration for room A is 12 h and Work Day Hour = 8 h; then room utilization = Total Call Duration in Room / (Work Days * Work Day Hour) = 12/(10\*8) =  15% |
| **Total calls** | Total count of calls conducted in the room during the specified timeframe |
| **Call performance** | Percentage of calls rated as “Good” out of the total calls in the room. Each call is evaluated and receives a Good, poor, Unknown rating. |

### Bring Your Own Device call utilization detailed view 

To see the call utilization view for each room, select the specific Bring Your Own Device room from the table. There will be a new pane, which gives a detailed view of devices call utilization based on selected period. 

> [!NOTE]
> Only rooms with Teams Shared Devices or Pro licenses and which are associated with their peripherals are shown in the Bring Your Own Device usage report. 
>
> Great news! for this first release, customers can utilize the Bring Your Own Device usage data without an additional Teams shared device license.  




