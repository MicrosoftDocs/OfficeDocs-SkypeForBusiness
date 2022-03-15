---
title: "Configure accounts for Microsoft Teams Rooms"
ms.author: czawideh
author: cazawideh
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.service: msteams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
ms.custom: 
ms.assetid: 
description: "Read this topic to learn about configuring accounts for Microsoft Teams Rooms (including Surface Hub) and common area phones."
---

# Configure accounts for Microsoft Teams Rooms
 
This topic introduces how to create accounts used by Microsoft Teams Rooms. Your infrastructure will likely fall into one of the following configurations:
  
- Online deployment: Your organization's environment is deployed entirely on Microsoft 365 or Office 365..
    
- On-premises deployment: Your organization has servers that it controls, where Active Directory, Exchange, and Skype for Business Server are hosted. For more information, see [Deploy Microsoft Teams Rooms with Skype for Business Server](with-skype-for-business-server-2015.md)
    
- Hybrid deployments: Your organization has a mix of services, with some hosted on premises and some hosted online through Microsoft 365 or Office 365. With Microsoft Teams Rooms, the following hybrid scenarios are supported:
    
  - Exchange Online with Skype for Business Server on premises.
    
  - Exchange on premises with Microsoft Teams.
    
Which configuration you have will affect how you prepare for device setup.
  
Microsoft Teams Rooms need to have a "resource account" in Active Directory, Exchange, and (if necessary) Skype for Business. The account is used to access the meeting calendar and establish Microsoft Teams and/or Skype for Business connectivity. People can book this account by scheduling a meeting with it. Microsoft Teams Rooms will be able to join that meeting and provide various features to the meeting attendees.
  
> [!IMPORTANT]
> Without a resource account, none of these features will work.
  
Every resource account is unique to a single Microsoft Teams Rooms installation.
  
- The resource account must be configured correctly.
    
- Your infrastructure must be configured to allow Microsoft Teams Rooms to validate the resource account and to reach the appropriate Microsoft services.

> [!NOTE] 
> If using Microsoft Teams panels, the Teams Rooms resource account signs in to both Teams Rooms and associated Teams panels.
    
> [!IMPORTANT]
> It is highly recommended that account creation be done well in advance of actual hardware installation. Ideally, account preparation is started two to three weeks before installation.
> 
In hybrid environments that are not using Skype for Business, it is highly recommended to create the account natively in Azure Active Directory. If the account must be created using on-premises Active Directory, password sync must be enabled in Azure Active Directory (AAD) Connect sync because Microsoft Teams Rooms authentication requires Microsoft 365 or Office 365 authentication. When setting up the account, make sure that the account's e-mail address matches its User Principal Name (UPN) in AAD. 
  
You can think of a resource account as the account that people recognize as a conference room's or shared space's name. When you want to schedule a meeting using that space, you invite the resource account to that meeting.
  
If you already have an Exchange resource mailbox account set up for the space where you're installing Microsoft Teams Rooms, you can change that account into a Teams Rooms resource account. Once that's done, all you need to do is sign in to Microsoft Teams Rooms with that account.
  
## Basic configuration

These properties represent the minimum configuration for a resource account to work with Microsoft Teams Rooms. Your resource account may require further setup.
  
|**Property**|**Purpose**|
|:-----|:-----|
|Exchange mailbox (Exchange 2013 SP1 or later, or Exchange Online)  <br/> |The Exchange mailbox gives the resource account the capability to receive and send mail and meeting requests, and to display a meeting calendar on Microsoft Teams Rooms. The Microsoft Teams Rooms mailbox must be a resource mailbox of type "room".  <br/> |
|Skype for Business is enabled  <br/> |Skype for Business can be enabled in order to use various Skype for Business conferencing features, like video calls, IM, and screen-sharing.  <br/> |
|Password-enabled  <br/> |The resource account must be enabled with a password, or it cannot authenticate with Microsoft Teams, Exchange, or Skype for Business Server. Password expiration must be disabled on all Teams Rooms resource accounts.   <br/> |
   
## Advanced configuration

While the properties for basic configuration will allow the resource account to be set up in a simple environment, it is possible your environment has other restrictions on accounts that must be met in order for Microsoft Teams Rooms to successfully use the resource account.
  
|**Property**|**Purpose**|
|:-----|:-----|
|Certificate-based authentication  <br/> |Certificates may be required for both Exchange and Skype for Business Server. To deploy certificates, you can load them when logged in as Admin.  <br/> |

## See also

[Plan for Microsoft Teams Rooms](rooms-plan.md)
  
[Configure a Microsoft Teams Rooms console](console.md)
  
[Manage Microsoft Teams Rooms](rooms-manage.md)
