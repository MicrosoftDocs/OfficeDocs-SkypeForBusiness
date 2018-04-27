---
title: "Deploying Skype for Business Online phones"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: wasseemh
ms.date: 01/22/2018
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
ms.audience: Admin
appliesto:
- Skype for Business 
localization_priority: Normal
f1keywords: None
ms.custom:
- Phone System
- Strat_SB_PSTN
description: "Learn the deployment steps to get the correct firmware, update it if needed, assign licenses, and configure settings for Common Area Phones."
---


## Common Area Phones
A common area phone, or CAP, is typically placed in a shared area and not associated with an individual user. For example, a reception area phone, door phone or meeting room phone, CAPs are set up as devices rather than users and automatically  sign in to the network. In the steps below, we’ll help you set up an account for Microsoft Phone System with Calling Plans and then deploy a CAP.

## Prerequisites for Common Area Phones
	- **Purchased Common Area Phone SKU 
	- **Updated firmware (See Supported Firmware in topichttps://docs.microsoft.com/en-us/SkypeForBusiness/what-is-phone-system-in-office-365/getting-phones-for-skype-for-business-online/getting-phones-for-skype-for-business-online)
	- **Approved  phones (see this for https://docs.microsoft.com/en-us/SkypeForBusiness/what-is-phone-system-in-office-365/getting-phones-for-skype-for-business-online/deploying-skype-for-business-online-phones 


## Check the firmware for your phone
- **Polycom VVX phones**, go to **Settings** > **Status** > **Platform** > **Application** > **Main**.
- **Yealink phones**, go to **Status** on the main phone screen.
- **AudioCodes phones**, go to **Menu** > **Device Status** > **Firmware version** from the start screen. 
- **Lync Phone Edition (LPE) phones**, go to **Menu** > **System Information** from the start screen.

Firmware updates are managed by the Skype for Business Service. Every Skype for Business certified phone's firmware is uploaded to the Skype for Business Update server, and device update is enabled on all phones by default. Depending on the inactivity time on the phone and polling intervals, phones will automatically download and install the latest certified builds. You can disable the device update settings by using the [Set-CsIPPhonePolicy](https://technet.microsoft.com/en-us/library/mt629497.aspx) cmdlet and setting the _EnableDeviceUpdate_ parameter to `false`.

## Configure settings

Create user and assign calling plans
To set up a common area phones, you’ll need to do these in order:

	1.	Make sure you have purchased the Common Area Phone SKU
	
		  In the Office 365 admin center, go to Billing > Purchase Services, and add Common Area Phone
 	
	2.	Create new user for the Common Area Phone 
	
	3.	Assign Common Area Phone SKU
	
	4.	Assign Calling Plan (If using Microsoft Phone System with Calling Plans). 
	
	5.	In SfB Admin Center, assign a telephone number if you have one available or request a new telephone number 

Add two more sections
	
	
