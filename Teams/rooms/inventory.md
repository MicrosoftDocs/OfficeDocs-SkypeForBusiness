---
title: "Inventory management in Teams Rooms Pro Management portal"
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: srpall
ms.date: 08/21/2024
ms.topic: article
audience: admin
appliesto:
- Microsoft Teams
ms.service: msteams
ms.subservice: itpro-rooms
ms.collection: 
  - teams-rooms-devices
  - teams-rooms-consoles
  - Tier1
f1.keywords: 
  - NOCSH                           
search.appverid: MET150
ms.localizationpriority: medium
description: Learn how to manage your Teams Rooms devices in the Teams Room Pro Management portal.
ai-usage:  
- ai-assisted
ms.custom: QuickDraft
---

# Manage your device and console inventory

Manage your organization's meeting rooms and device inventory using the inventory management features in Microsoft Teams Rooms. This guide covers how to onboard your organization, manage your location directory, search for meeting rooms, and update meeting room information.

## Onboard your organization

To set up your organization with meeting room location information:

1. Sign in to the Teams Rooms Pro Management portal.
2. Select on the **Inventory** tab in the left navigation pane.
3. Select **Get data** to retrieve the location details and inventory of Microsoft Teams Rooms devices deployed in your organization.

>[!NOTE]
> This process may take some time, depending on the number of meeting rooms. For example, a large organization with over 20,000 meeting rooms might experience a wait of up to 20 minutes.

4. Newly created room resource accounts may take up to 48 hours to appear in the portal.

>[!NOTE]
> Alternatively, you can perform an on-demand sync from the inventory command bar by selecting the **Sync** option. However, this on-demand sync will take 15 minutes.

## Manage Your location directory and view meeting rooms

Once the setup is complete, your organization's location directory appears in the left pane. Meeting rooms are organized hierarchically by location details, such as country, state, city, campus, building, floor, and room. You can also view a comprehensive list of all meeting rooms within your organization.

At the top, you find a summary that includes a breakdown of meeting rooms, including the number of unlicensed rooms. Additionally, there's a quick overview of meeting rooms categorized by type, such as Small, Medium, and Large.

## Search for specific meeting rooms

To filter your meeting rooms, use the search feature. You can search for rooms in your organization by address details such as country, state, and city, or by meeting room name and other attributes, such as the device manufacturer, capacity, place type, and device type.

## Manage Your inventory of devices

You can view and manage your inventory of Teams Room systems and other assets from the inventory pane:

- If a Microsoft Teams Room console is deployed in a meeting room, it is automatically detected and added to the room's inventory.
- To remove a device, select it and select the **Remove** button.
- To add a new device, select **Add** and choose from the available Teams Room system devices in your organization.

Microsoft Teams Room systems, Surface Hubs, Collab Bars, Teams Displays, and Teams IP Phones are automatically detected. For all other hardware types, you can manually add them to the room inventory under the **Meeting Room assets** section. You can also manage additional meeting room assets, such as projectors, docking stations, routers, motion sensors, or tables, using the **Add, Edit, or Remove** functions in the **Manage Room assets** section.

## Update your meeting room information

Select a room from your inventory and go to the **General** tab to update details such as address, building, and floor. The changes are immediately reflected in your location directory. Updated location information will also be saved in Microsoft Entra.

## Access control

To create, edit, or remove resource accounts in a Microsoft 365 tenant, high-level privileges are required. Specifically, the IT administrator must be assigned to either the Exchange Admin or Global Admin role to perform these actions.

>[!IMPORTANT]
> Microsoft recommends using roles with the fewest permissions. Using lower-permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.
