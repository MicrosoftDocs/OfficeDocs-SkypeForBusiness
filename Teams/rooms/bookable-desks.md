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

Making a desk your own for a day in the office has never been easier! Simply use your Teams desktop app (T2.1) on Windows or a Mac laptop to reserve the perfect workspace in seconds. No more scrambling or frustration – just effortless booking and immediate access to your dedicated work zone. This means more time for what truly matters: focusing on your work and achieving peak productivity. 

The Bookable Desk feature will allow end users walking up to shared desks to book them upon plug-in or get notified upon arrival about an existing booking if they have an active Teams app running on their Windows or Mac laptops.  

On the back end, for the IT admins, Teams Rooms Pro Management will provide the ability to discover devices, make them visible in inventory, and track in the admin portal. 

This article helps guide you through the process of setting up Bookable Desks in Microsoft Teams. This includes creating desk pool accounts, identifying the devices you want included, and then linking those devices with desk pool accounts.

## Overview of steps  

To set up and use Bookable Desks in your organization, you must perform these tasks: 

Step 1: Verify that all prerequisites are met 

Step 2: Create desk pool accounts  

Step 3: Collect information on peripheral devices on individual desks  

Step 4: Test end-user experience  

## 1. Verify that all prerequisites are met 

- You must ensure that you have access to the Teams Pro Management Portal meeting minimum criteria of 1 Teams Shared license or 1 Teams Rooms Pro license per tenant. 

- You must create and set up the necessary resource accounts. See step 2 on “Create Desk Pool accounts”. 

- You must test the end-user experience using the latest versions of Microsoft Teams T2.1 Desktop client on Windows or Mac PC.  

## 2. Create Desk Pool Accounts

Desk pool accounts are slightly different from room accounts and are based on workspace resource mailbox architecture. A desk pool can be reserved multiple times by different users at the same time, up to a defined capacity. However, rooms can only be reserved once at a specific time. Refer to the FAQ section below for more clarity. Since this experience is only supported for a group of desks, you will need to create desk pool accounts.  Creating a desk pool is like configuring a room. Follow the steps below to create a desk pool account: 

- Step 1: For information on how to set up new workspaces/desk pools in exchange, see this article: https://learn.microsoft.com/en-us/exchange/troubleshoot/outlook-issues/create-book-workspace-outlook

- Step 2: Configure metadata for desks, using the details in this article:(https://learn.microsoft.com/en-us/powershell/module/exchange/set-place?view=exchange-ps)

- Step 3: After creating workspaces in exchange in step 1 and adding location metadata in step 2 desk pools should be searchable on Places Finder on Outlook or while booking a desk pool on Teams.  

## 3. Collect information on peripheral devices on individual desks

To ensure seamless end-to-end user experience, devices on the individual desks need to be associated with the desk pool accounts you created earlier. To do this, you will need to identify devices based on unique information such as product ID, vendor ID, serial number, model, and manufacturer. You can use a custom script to get device details from desks to locate devices correctly and ensure they are mapped to the corresponding desk pool accounts. The script is on GitHub and is recommended to be run on PowerShell with administrator access - Teams BYOD Room Manual Device Discovery Script · GitHub. For detailed step-by-step instructions to run this script check this article Get information for connected peripherals - Microsoft Teams | Microsoft Learn. After uploading information on the devices, confirm on Teams Pro Management Portal if the devices are correctly associated with the desk pools as you ran in the script. Follow Step 4 on Test end-user experience after this step. 

Other alternative methods for this step: 

In case you prefer alternative method of manually importing to fetch device information and associate to corresponding desk pool accounts, follow the steps below: 

- Open Pro Management Portal on https://portal.rooms.microsoft.com/ and navigate to Inventory. 

- Devices are automatically discovered using your users' Teams client to send device data to Pro Management Portal. When at least 5 users plug in to device on a desk any connected displays and USB audio/video peripherals are scanned and transmitted to the cloud. These devices populate your Devices tab within the Inventory navigation. 

- To check under Planning click Inventory. 

- Under Inventory navigate to Devices page. 

- Click on the specific device you want to associate to a desk pool with the Needs action banner. 

- Verify that a new panel displays device information and a call-to-action button labeled Add device to a room or desk. 

- Click on Add device to a room or desk. 

- Check that a list of desk pools is displayed, allowing you to select the desired desk pool from the list where the device is located. In case you want to look for a specific desk pool use the PlaceType: desks filter in the search bar to see only desk pools account in the tenant. 

- Once you have selected the desk pool, click on the Save button. 

- The device is now associated. 

- Go to the Desks page under Inventory and make sure the device has the specific associated desk pool under location. 

- Follow Step 4 on Test end-user experience after this step. 

Note: Desk pool is named as Desk on the Teams Pro Management Portal UI.  
 
## 4. Test end-user experience

Now upon plug-in to this associated device you will receive a desk reservation with a booking appearing on Teams calendar along with a notification. You can also pre-book a desk using Teams or Places Finder on Outlook (see pre-requisites in Step 1) and see an arrival notification for an existing reservation.  

## FAQ

1. What are Desk Pools?  

Everyone has heard of desk booking, but what is Desk Pool booking? Desk Pools are a group of individual desks close to each other set up with the same equipment and experience. Desk Pools empower employees to book a desk while simultaneously reducing the overhead for administrators to manage thousands of individual desks in the system. When an employee books a desk in the desk pool, they are guaranteed a desk in the desk pool and can select which exact desk to sit at once they arrive at the space. 


2. Is bookable desks feature available on Classic (old Teams) and new Teams?  

No, the bookable desk experience is only available on the new Teams client T2.1. To download/switch to the latest Teams client please visit - Switch to the new Microsoft Teams - Microsoft Support or Introducing the new Microsoft Teams | Microsoft 365 Blog.   

3. Will the bookable desk feature work if the Teams app is not running actively on the laptop?  

No, for the bookable desk feature to work, meaning to let end users auto-book upon plug-in Teams app must be already running on your laptop before plugging in.  

 
4. What is the difference between individual desks, desk pools and Bookable Desks in this article? 

Individual desks are part of a desk pool that have the same UPN or resource email address, often identical and close to each other in an office.Desk pools are a cluster of individual desks that have a dedicated resource account. The resource account is on Exchange supported by workspace mailbox architecture. The capacity of a desk pool along with metadata such as location can be set using the commands here. Set-Place (ExchangePowerShell) | Microsoft Learn. Bookable Desks is the name of this feature on Microsoft Teams that utilizes created desk pool accounts to provide users the ability to book an individual desk that are part of a desk pool upon plug-in to devices at that desk. As highlighted in the sections above, the devices need to be associated to desk pool accounts on the Teams Pro Management Portal for the end-to-end functionality to work. 