---
title: "Configure accounts for Skype Room Systems v2"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 5/10/2018
ms.audience: ITPro
ms.reviewer: davgroom
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Admin
ms.custom:
ms.assetid: 
description: "Read this topic to learn about configuring accounts for Skype Room Systems v2 in Exchange and Skype for Business."
---

# Configure accounts for Skype Room Systems v2
 
Read this topic to learn about Skype Room Systems v2 and how it integrates with Exchange and Skype for Business.
  
This topic introduces how to create accounts used by Skype Room Systems v2 in Microsoft Exchange and Skype for Business . Deployment instructions for Skype Room Systems v2 devices is covered in [Configure a Skype Room Systems v2 console](console.md). Your infrastructure will likely fall into one of the following configurations:
  
- Online deployment: Your organization's environment is deployed entirely on Office 365. For more information, see [Deploy Skype Room Systems v2 with Office 365](with-office-365.md).
    
- On-premises deployment: Your organization has servers that it controls, where Active Directory, Exchange, and Skype for Business Server are hosted. For more information, see [Deploy Skype Room Systems v2 with Skype for Business Server](with-skype-for-business-server-2015.md)
    
- Hybrid deployments: Your organization has a mix of services, with some hosted on premises and some hosted online through Office 365. With Skype Room Systems v2, the following hybrid scenarios are supported: 
    
  - Exchange Online with Skype for Business Server on premises. For more information, see [Deploy Skype Room Systems v2 with Exchange Online (Hybrid)](with-exchange-online.md).
    
  - Exchange on premises with Skype for Business Online. For more information, see [Deploy Skype Room Systems v2 with Exchange on premises (Hybrid)](with-exchange-on-premises.md).
    
Which configuration you have will affect how you prepare for device setup.
  
Skype Room Systems v2 needs to be assigned a "User account" in Active Directory, Exchange, and Skype for Business. The account is used to access its meeting calendar and establish Skype for Business connectivity. People can book this account by scheduling a meeting with it. Skype Room Systems v2 will be able to join that meeting and provide various features to the meeting attendees.
  
> [!IMPORTANT]
> Without a user account, none of these features will work. 
  
Every user account is unique to a single Skype Room Systems v2 device, and requires some setup:
  
- The user account must be configured correctly.
    
- Your infrastructure must be configured to allow Skype Room Systems v2 to validate the user account, and to reach the appropriate Microsoft services.
    
> [!IMPORTANT]
> It is highly recommended that account creation be done well in advance of actual hardware installation. Ideally, account preparation is started two to three weeks before installation. 
  
You can think of a user account as the resource account that people recognize as a conference room's or meeting space's account. When you want to schedule a meeting using that conference room, you invite the account to that meeting. In order to use Skype Room Systems v2 most effectively, you do the same with the user account that's assigned to each one.
  
If you already have a resource mailbox account set up for the meeting space where you're installing Skype Room Systems v2, you can change that resource account into a user account. Once that's done, all you need to do is add the user account to a Skype Room Systems v2 device. See user account setup examples provided below.
  
With additional configuration, remote management is possible using Microsoft Azure Monitor as described in [Plan Skype Room Systems v2 management with Azure Monitor](../../plan-your-deployment/clients-and-devices/azure-monitor.md), [Deploy Skype Room Systems v2 management with Azure Monitor](azure-monitor.md),  and [Manage Skype Room Systems v2 devices with Azure Monitor](../../manage/skype-room-systems-v2/azure-monitor.md). 
  
## Basic configuration

These properties represent the minimum configuration for a user account to work with Skype Room Systems v2. Your user account may require further setup.
  
|**Property**|**Purpose**|
|:-----|:-----|
|Exchange mailbox (Exchange 2013 SP1 or later, or Exchange Online)  <br/> |Enabling the account with an Exchange mailbox gives the user account the capability to receive and send both mail and meeting requests, and to display a meetings calendar on the Skype Room Systems v2 device. The Skype Room Systems v2 mailbox must be a room mailbox.  <br/> |
|Skype for Business is enabled  <br/> |Skype for Business must be enabled in order to use various conferencing features, like video calls, IM, and screen-sharing. Both Skype for Business Online and Skype for Business Server are supported.  <br/> |
|Password-enabled  <br/> |The user account must be enabled with a password, or it cannot authenticate with either Exchange or Skype for Business Server.  <br/> |
   
## Advanced configuration

While the properties for the basic configuration will allow the user account to be set up in a simple environment, it is possible your environment has other restrictions on directory accounts that must be met in order for Skype Room Systems v2 to successfully use the user account.
  
|**Property**|**Purpose**|
|:-----|:-----|
|Certificate-based authentication  <br/> |Certificates may be required for both Exchange and Skype for Business Server. To deploy certificates, you can load them when logged in as Admin.  <br/> |
   
The easiest way to set up user accounts is to configure them using remote Windows PowerShell. Microsoft provides [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105), a script that will help create new user accounts, or validate existing resource accounts you have in order to help you turn them into compatible Skype Room Systems v2 user accounts.
  
If you prefer to use the Office 365 UI over Windows PowerShell cmdlets, some steps can be performed manually. See [Creating a device account using Office 365](https://docs.microsoft.com/surface-hub/create-a-device-account-using-office-365).
  
## See also

[Plan for Skype Room Systems v2](../../plan-your-deployment/clients-and-devices/skype-room-systems-v2-0.md)
  
[Configure a Skype Room Systems v2 console](console.md)
  
[Manage Skype Room Systems v2](../../manage/skype-room-systems-v2/skype-room-systems-v2.md)

