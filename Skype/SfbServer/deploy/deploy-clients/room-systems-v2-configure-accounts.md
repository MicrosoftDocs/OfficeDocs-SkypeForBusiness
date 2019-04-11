---
title: "Configure accounts for Microsoft Teams Rooms"
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
- M365-voice
ms.custom:
ms.assetid: 
description: "Read this topic to learn about configuring accounts for Microsoft Teams Rooms in Exchange and Skype for Business."
---

# Configure accounts for Microsoft Teams Rooms
 
Read this topic to learn about Microsoft Teams Rooms and how it integrates with Exchange and Skype for Business.
  
This topic introduces how to create accounts used by Microsoft Teams Rooms in Microsoft Exchange and Skype for Business. Deployment instructions for Microsoft Teams Rooms devices is covered in [Configure a Microsoft Teams Rooms console](console.md). Your infrastructure will likely fall into one of the following configurations:
  
- Online deployment: Your organization's environment is deployed entirely on Office 365. For more information, see [Deploy Microsoft Teams Rooms with Office 365](with-office-365.md).
    
- On-premises deployment: Your organization has servers that it controls, where Active Directory, Exchange, and Skype for Business Server are hosted. For more information, see [Deploy Microsoft Teams Rooms with Skype for Business Server](with-skype-for-business-server-2015.md)
    
- Hybrid deployments: Your organization has a mix of services, with some hosted on premises and some hosted online through Office 365. With Microsoft Teams Rooms, the following hybrid scenarios are supported: 
    
  - Exchange Online with Skype for Business Server on premises. For more information, see [Deploy Microsoft Teams Rooms with Exchange Online (Hybrid)](with-exchange-online.md).
    
  - Exchange on premises with Skype for Business Online. For more information, see [Deploy Microsoft Teams Rooms with Exchange on premises (Hybrid)](with-exchange-on-premises.md).
    
Which configuration you have will affect how you prepare for device setup.
  
Microsoft Teams Rooms needs to be assigned a "device account" in Active Directory, Exchange, and Skype for Business. The account is used to access its meeting calendar and establish Skype for Business connectivity. People can book this account by scheduling a meeting with it. Microsoft Teams Rooms will be able to join that meeting and provide various features to the meeting attendees.
  
> [!IMPORTANT]
> Without a device account, none of these features will work. 
  
Every device account is unique to a single Microsoft Teams Rooms device, and requires some setup:
  
- The device account must be configured correctly.
    
- Your infrastructure must be configured to allow Microsoft Teams Rooms to validate the device account, and to reach the appropriate Microsoft services.
    
> [!IMPORTANT]
> It is highly recommended that account creation be done well in advance of actual hardware installation. Ideally, account preparation is started two to three weeks before installation. 
In hybrid environments the account used for SRS must have password sync enabled in ADDsync because SRS authentication requires 0365 authentication.
  
You can think of a device account as the resource account that people recognize as a conference room's or meeting space's account. When you want to schedule a meeting using that conference room, you invite the account to that meeting. In order to use Microsoft Teams Rooms most effectively, you do the same with the device account that's assigned to each one.
  
If you already have a resource mailbox account set up for the meeting space where you're installing Microsoft Teams Rooms, you can change that resource account into a device account. Once that's done, all you need to do is add the device account to a Microsoft Teams Rooms device. See device account setup examples provided below.
  
With additional configuration, remote management is possible using Microsoft Azure Monitor as described in [Plan Microsoft Teams Rooms management with Azure Monitor](../../plan-your-deployment/clients-and-devices/azure-monitor.md), [Deploy Microsoft Teams Rooms management with Azure Monitor](azure-monitor.md),  and [Manage Microsoft Teams Rooms devices with Azure Monitor](../../manage/skype-room-systems-v2/azure-monitor.md). 
  
## Basic configuration

These properties represent the minimum configuration for a device account to work with Microsoft Teams Rooms. Your device account may require further setup.
  
|**Property**|**Purpose**|
|:-----|:-----|
|Exchange mailbox (Exchange 2013 SP1 or later, or Exchange Online)  <br/> |Enabling the account with an Exchange mailbox gives the device account the capability to receive and send both mail and meeting requests, and to display a meetings calendar on the Microsoft Teams Rooms device. The Microsoft Teams Rooms mailbox must be a room mailbox.  <br/> |
|Skype for Business is enabled  <br/> |Skype for Business must be enabled in order to use various conferencing features, like video calls, IM, and screen-sharing. Both Skype for Business Online and Skype for Business Server are supported.  <br/> |
|Password-enabled  <br/> |The device account must be enabled with a password, or it cannot authenticate with either Exchange or Skype for Business Server.  <br/> |
   
## Advanced configuration

While the properties for the basic configuration will allow the device account to be set up in a simple environment, it is possible your environment has other restrictions on directory accounts that must be met in order for Microsoft Teams Rooms to successfully use the device account.
  
|**Property**|**Purpose**|
|:-----|:-----|
|Certificate-based authentication  <br/> |Certificates may be required for both Exchange and Skype for Business Server. To deploy certificates, you can load them when logged in as Admin.  <br/> |
   
The easiest way to set up device accounts is to configure them using remote Windows PowerShell. Microsoft provides [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105), a script that will help create new device accounts, or validate existing resource accounts you have in order to help you turn them into compatible Microsoft Teams Rooms device accounts.
  
If you prefer to use the Office 365 UI over Windows PowerShell cmdlets, some steps can be performed manually. See [Creating a device account using Office 365](https://docs.microsoft.com/surface-hub/create-a-device-account-using-office-365).
  
## See also

[Plan for Microsoft Teams Rooms](../../plan-your-deployment/clients-and-devices/skype-room-systems-v2-0.md)
  
[Configure a Microsoft Teams Rooms console](console.md)
  
[Manage Microsoft Teams Rooms](../../manage/skype-room-systems-v2/skype-room-systems-v2.md)

