---
title: "Setting up Bookable Desks in Microsoft Teams "  
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: eviegrimshaw
ms.date: 07/01/2024  
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
description: Helps admins set up Bookable Desks for their Microsoft Teams organization.
---

# Setting up Bookable Desks in Microsoft Teams

This article helps guide you through the process of setting up Bookable Desks in Microsoft Teams. This includes creating desk pool accounts, searching for and identifying the devices you want included, and then linking those devices with desk pool accounts.

Bookable Desks is the name of this feature on Microsoft Teams that utilizes Exchange Desk Pool accounts to provide users the ability to book or reserve an individual desk that is a part of a desk pool when they plug in to devices at that desk.

## Bookable Desks in Microsoft Teams

When end users are working in a hybrid work environment or need a landing place in a building to work for the day, they'll need to be able to book or reserve a space to get work done. Bookable Desks is the feature that can be used to make this easy. After you set up Bookable Desks in Teams, an end user can use the new Teams desktop app on Windows or a Mac to reserve a workspace.

The Bookable Desk feature lets end users walk up to shared desks to reserve them when they plug in or book in advance and get notified when they get there about an existing booking if they have Teams app running on their Windows or Mac PC. 

For admins, the Microsoft Teams Rooms Pro Management portal provides the manageability including the ability to discover devices, and make them visible in the inventory.

## Overview of steps  

To set up and use Bookable Desks in your organization, you must perform these tasks:

- Step 1: Verify the prerequisites are met.
- Step 2: Create desk pool accounts.
- Step 3: Collect information on peripheral devices on individual desks.
- Step 4: Test end-user experience.

## Step 1 - Verify the prerequisites are met

- Verify you have access to the Microsoft Teams Pro Management portal.
- Verify you have a minimum of one Teams Shared license or one Teams Rooms Pro license per organization.
- Create and set up the required resource accounts found in Step 2.
- Use the new version of Microsoft Teams desktop app on Windows or on a Mac.

## Step 2 - Create Desk Pool Accounts

Desk pool accounts are slightly different from room accounts but are based on the workspace resource mailbox architecture. A desk pool can be reserved multiple times by different users at the same time, up to a defined capacity. However, rooms can only be reserved once at a specific time. Refer to the FAQ section below for more clarity. Since this experience is only supported for a group of desks, you need to create desk pool accounts. Creating a desk pool is like configuring a room.

**To create a desk pool account**

- Step 1: Set up new workspaces or desk pools in Exchange. To do this, see [Create and book a workspace in Outlook](/exchange/troubleshoot/outlook-issues/create-book-workspace-outlook).
- Step 2: Configure metadata for the Bookable Desks. To do this, see the [Set-Place](/powershell/module/exchange/set-place) cmdlet.

After you create the workspaces and setting the metadata, the Bookable Desks are found when using Places Finder on Outlook or while booking a desk pool on Teams.  

## Step 3 - Collect information on peripheral devices on individual desks

There are two ways that you can collect device and peripheral information - using a downloadable PowerShell script, or manually.

### Using the PowerShell script to collect device and peripheral information

To ensure seamless end-to-end user experience, devices and peripherals such as monitors attached to the physical desks need to be associated or linked to a desk pool account you created earlier. To do this, you need to identify devices based on unique information such as product ID, vendor ID, serial number, model, and the manufacturer.

You can use a custom script to get device details from desks to locate devices correctly and ensure they're mapped to the corresponding desk pool accounts. The PowerShell script located [here](https://www.microsoft.com/en-us/download/details.aspx?id=106063) must be ran with administrator permissions.

For detailed step-by-step instructions, see [Get information for connected peripherals](../rooms/get-peripheral-information.md). After uploading information on the devices and peripherals, you then use the Teams Pro Management portal to confirm if the devices are correctly associated with the desk pools.

### Collecting device and peripheral information through auto discovery

You can use the auto discovery feature to get the device information and then associate it to a correspond desk pool account using the Microsoft Teams Pro Management portal.

1. Sign in and open the [Microsoft Teams Pro Management portal](https://portal.rooms.microsoft.com/) > **Inventory** in the left navigation.

   Devices are automatically discovered using your users' Teams app to send device data to the Teams Pro Management Portal. When five users plug in to device on a desk any connected displays and USB audio/video peripherals are scanned and transmitted to the cloud. These devices populate the **Devices** tab within the **Inventory** section.

2. Go to **Planning** > **Inventory** > **Devices** page.
3. Select the specific device you want to associate to a desk pool. You see a **Needs action** banner.
4. Verify that a new panel displays device information and a call-to-action button labeled **Add device to a room or desk**.
5. Select **Add device to a room or desk**.
6. The list of desk pools is displayed that allows you to select the desired desk pool from the list where the device is located. 

   > [!NOTE]
   > If you want to look for a specific desk pool use the **PlaceType:** desks filter in the search bar to see only Desk Pool accounts in the organization.

7. Once you select the desk pool, select **Save**.

   The device is now associated with the Desk Pool account.

8. Go to **Inventory** > **Desks** page and make sure the device has the specific associated desk pool under the location.

   > [!NOTE]
   > The Desk pool is named **Desk** in the Microsoft Teams Pro Management portal.  

## Step 4 - Test the end user experience

1. Take the laptop or tablet and sign in to Teams.

2. Physically plug in the laptop. When you plug in to this associated device, you receive a desk reservation notification with a booking appearing on Teams calendar. You can also reserve a desk using the Teams app or Places Finder on Outlook. If you reserve a Bookable Desk, you see an arrival notification for an existing reservation.  

## Frequently asked questions

**Question:** What are Desk Pools?  

**Answer:** Desk Pools are a group of individual desks close to each other setup with the same equipment and experience. Desk Pools empower employees to book a desk while simultaneously reducing the overhead for administrators to manage thousands of individual desks in the system. When an employee books a desk in the desk pool, they're guaranteed a desk in the desk pool and can select which exact desk to sit at once they arrive at the space.

**Question:** are bookable desks feature available on Classic (old Teams) and new Teams?  

**Answer:** No, the bookable desk experience is only available on the new Teams client. To download and switch to the latest Teams client see, [Switch to the new Microsoft Teams](https://adoption.microsoft.com/new-microsoft-teams/).

**Question:** Will the bookable desk feature work if the Teams app isn't running actively on the laptop?  

**Answer:** No, for the bookable desk feature to work, meaning to let end users reserve a desk upon plug-in Teams app must be already running on your laptop before plugging in.  

**Question:** What is the difference between individual desks, desk pools and Bookable Desks in this article?

**Answer:** Individual desks that are part of a desk pool have the same User Principal Name (UPN) or resource email address, often identical and close to each other in an office. Desk pools are a cluster of individual desks that have a dedicated resource account. The resource account is on Exchange supported by workspace mailbox architecture. The capacity of a desk pool along with metadata such as location can be set using [Set-Place](/powershell/module/exchange/set-place) cmdlet. All devices need to be associated to desk pool accounts on the Teams Pro Management Portal for the end-to-end functionality to work.

## Related links

- [First things to know about bookable desks for end users](https://support.microsoft.com/office/first-things-to-know-about-bookable-desks-5d10c217-1205-48a1-a883-ff4533f4ae71)

