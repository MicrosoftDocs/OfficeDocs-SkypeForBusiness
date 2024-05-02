---  
title: "Support article for Bookable Desks "  
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: prashibadkur
ms.date: 05/02/2024  
ms.topic: article
audience: Admin
appliesto: 
  - Microsoft Teams
ms.service: msteams  
ms.subservice: itpro-rooms
ms.localizationpriority: medium
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Rooms
  - Tier1
ms.custom: QuickDraft 
search.appverid: MET150  
f1.keywords:
  - NOCSH  
description: Helps admins set up Bookable Desks in their Microsoft Teams organization.
---  

# Bookable Desks in Microsoft Teams

This article will help guide you through the process of setting up Bookable Desks in Microsoft Teams. This includes creating desk pool accounts, identifying devices, and associating devices with desk pool accounts.

## 1. Create Desk Pool Accounts

Desk pool accounts are slightly different from room accounts. A desk pool can be reserved multiple times by different users at the same time, up to a defined capacity. However, rooms can only be reserved once at a specific time. Since this experience is only supported for groups of desks, you will need to create desk pool accounts. Creating a desk pool is similar to configuring a room. For detailed step-by-step instructions, refer to [How to create and book a desk pool - Exchange \| Microsoft Learn](/learn/modules/create-book-desk-pool-exchange/).

## 2. Get device details

To ensure a seamless end-to-end user experience, devices on the desk pools need to be associated with the desk pool accounts you created earlier. To do this, you will need to identify devices based on unique information such as product ID, vendor ID, serial number, model, and manufacturer. Once five unique users plug their devices into the desk pool, the unique device information will be sent to PMP under the **Devices** tab in **Inventory**. To locate monitors correctly and ensure they are mapped to the corresponding desk pool accounts, use the [Teams BYOD Room Manual Device Discovery Script - GitHub](https://github.com/Microsoft/Teams-Byod-Room-Manual-Device-Discovery-Script).

## 3. Device and Desk Association

After identifying the devices, you will need to associate them with the desk pool accounts created earlier. Follow the steps below to do this:

1. Click on a specific device with the **Needs action** banner.
2. Verify that a new panel displays device information and a call-to-action button labeled **Add device to a room or desk**.
3. Click on **Add device to a room or desk**.
4. Check that a list of desk pools is displayed, allowing you to select the desired desk from the list where the device is located.
5. Once you have selected the desk, click on the **Save** button.
6. The device is now associated with the desk.
7. Go back to the device page and make sure the device has the specific associated desk under location.

Recommendations: