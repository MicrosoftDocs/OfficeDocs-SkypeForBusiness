---
title: "Set up Common Area Phones"
description: Learn the deployment steps to get the correct firmware, update it if needed, assign licenses, and configure settings for Common Area Phones. 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: wasseemh
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
---


# Set up Common Area Phones

A common area phone, or CAP, is typically placed in a shared area and not associated with an individual user. For example, a reception area phone, door phone or meeting room phone, CAPs are set up as devices rather than users and automatically  sign in to the network. In the steps below, we’ll help you set up an account for Microsoft Phone System with Calling Plans and then deploy a CAP.

## Prerequisites for Common Area Phones

Confirm that you have the following:

- 	- Purchased Common Area Phone SKU 
- 	- Updated firmware (See Supported Firmware in this topic:
        https://docs.microsoft.com/en-us/SkypeForBusiness/what-is-phone-system-in-office-365/getting-phones-for-skype-for-business-online/getting-phones-for-skype-for-business-online)
- 	- Approved  phones (view the list at:            
        https://docs.microsoft.com/en-us/SkypeForBusiness/what-is-phone-system-in-office-365/getting-phones-for-skype-for-business-online/deploying-skype-for-business-online-phones)

## Check the firmware for your phone
- **Polycom VVX phones**, go to **Settings** > **Status** > **Platform** > **Application** > **Main**.
- **Yealink phones**, go to **Status** on the main phone screen.
- **AudioCodes phones**, go to **Menu** > **Device Status** > **Firmware version** from the start screen. 
- **Lync Phone Edition (LPE) phones**, go to **Menu** > **System Information** from the start screen.

Firmware updates are managed by the Skype for Business Service. Every Skype for Business certified phone's firmware is uploaded to the Skype for Business Update server, and device update is enabled on all phones by default. 

Depending on the inactivity time on the phone and polling intervals, phones will automatically download and install the latest certified builds. You can disable the device update settings by using the [Set-CsIPPhonePolicy](https://technet.microsoft.com/en-us/library/mt629497.aspx) cmdlet and setting the _EnableDeviceUpdate_ parameter to `false`.

## Create CAP
You create the CAP by configuring the settings before you set up the physical phone.

#### Purchase the Common Area Phone SKU. 
    In the Office 365 admin center, go to **Billing > Purchase Services**, and add **Common Area Phone**.

#### Set up the common area phone  <!-- this section could use a screen shot-->

**Create user** 
1. Assign Common Area Phone SKU
2. Assign Calling Plan (if using Microsoft Phone System with Calling Plans). 
3. Assign an available telephone number in the Skype for Business Admin Center, or request a new telephone number.

**Create New User**

1. In the provisioning pane, you have an option to enter a first and last name (for example, Reception Main).
2. Enter a display name (required), for example, "Main Reception."
3. Enter a username (required), for example “MainReception” @” domain” (company or enterprise name)
4. Enter Location (country).

**Assign Common Area Phone SKU**
    In the Office 365 admin center, go to **Billing > Purchase Services** and add **Common Area Phone**

**Assign Calling Plan in CAP SKU**

1. Select a Calling Plan to enable the phone. 
2. Add the CAP to enable the Phone System and Skype for Business Online Plan 2 in the CAP SKU. <!-- odd order for step -->

**Assign a telephone number**
1. Check for available phone numbers under **Voice > Phone Numbers**.
2. Select a number from the available list of phone numbers number.
3. Confirm your selection by selecting **Voice** and **Phone Numbers**.

    >[Note]
    Voice users only show if they have the Phone System licence applied, although even after applying, it can take time to refresh. Sometime reopening Skype for Business Admin center helps.
	
## Configure Phone

**Prepare the physical phones**

Your chosen phone needs to have the Common Area Phone mode. 

***Example Polycom VVX phone***

Enable Common Area Phone Mode for the Polycom VVX by following these steps:
1. In your browser, use the web interface to enable CAP mode on the VVX
2. Go to **Setting**  and in the Skype for Business Setting option, select **Common Area Phone**.
3. Click **Yes** to save your configuration settings.

Now that the CAP phone mode is enabled, set up the phone using the phone's display. The display should show "CaAP is enabled."

1. Click **Settings**.
2. Select **Advanced**.
3. Enter the password.
4. In Administration settings, select **Common Area Phone Settings**.
5. Enable **CAP** and **CAP Admin Mode**.
6. Click **Save Config**.

Your phone is ready to be provisioned, which you'll do when you sign in on the home screen.

1. Sign in by selecting **Settings** > **Features** > **Skype for Business.**
2. Select **User Credentials**, and select **web sign-in (CAP)** to generate a code..
3. Go to the provisioning portal at http://aka.ms/skypecap, and sign in as **admin**.
4. Enter display name (for example, Main Reception) to view your CAP.

>[Note]
If “Search for Common Area Phones only” is checked, clear the checkbox and search again.

5. In the pairing code window, enter the code displayed on the phone and click **Provision**.

Following this last step, the phone should sign in automatically.

Learn more about available phones at [Deploying Skype for Business Online phones](https://docs.microsoft.com/en-us/SkypeForBusiness/what-is-phone-system-in-office-365/getting-phones-for-skype-for-business-online/deploying-skype-for-business-online-phones).


