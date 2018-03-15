---
title: "Windows client requirements and software support"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 2/16/2018
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_Skype16
ms.custom: Strat_SB_Admin
ms.assetid: a6851e38-ba9a-4f19-9aa7-d8accf4d62b3

description: "Summary: Review the Windows client support requirements while planning Skype for Business Server 2015."
---

# Windows client requirements and software support
 
**Summary:** Review the Windows client support requirements while planning Skype for Business Server 2015.
  
This section summarizes software required to support the Skype for Business 2015 and 2016 Windows clients.
  
These clients are installed when Office 365 installs, and are also available at [Download Skype for Business across all your devices](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-3).
  
> [!NOTE]
> The Online Meeting Add-in for Skype for Business, which supports meeting management from within the Outlook messaging and collaboration client, installs automatically with Skype for Business. 
  
**Software Required for Skype for Business and the Online Meeting Add-in for Skype for Business**


|**System component**|**Supported versions**|
|:-----|:-----|
|Windows Operating system  <br/> |Windows 10  <br/> Windows 8.1  <br/> Windows 8  <br/> Windows 7 operating system  <br/> Windows Server 2008 R2 with latest service pack  <br/> **Note:** Skype for Business and the Online Meeting Add-in for Skype for Business are not supported on Windows Vista or Windows XP (any version). <br/> |
|Installation and updates  <br/> |Administrator rights and permissions  <br/> |
|Browser  <br/> |Microsoft Edge  <br/> Internet Explorer 11 Internet browser  <br/>  Internet Explorer 10 Internet browser <br/> Internet Explorer 9 Internet browser  <br/> Internet Explorer 8 Internet browser  <br/> Internet Explorer 7 Internet browser  <br/> Mozilla Firefox web browser  <br/> **Note:** If you are using Skype for Business with Microsoft Exchange Online and your organization has deployed an authenticating HTTP proxy, Internet Explorer 8 or later is required.           |
|Microsoft Office Integration  <br/> |For the full set of integration features:  <br/> • Outlook 2016 messaging and collaboration client  <br/> • Outlook 2013 messaging and collaboration client  <br/> • Outlook 2010 messaging and collaboration client  <br/> |
|Microsoft Exchange Integration  <br/> |• Microsoft Exchange Server 2016  <br/> • Microsoft Exchange Server 2013  <br/> • Microsoft Exchange Server 2010  <br/> |
   
## Hardware

Refer to the Office 365 [System requirements](https://products.office.com/en-us/office-system-requirements) for the hardware required to run the Skype for Business client.
  
## Skype for Business Web App Browsers

Skype for Business Web App supports specific combinations of operating systems and browsers. For details, see [Plan for Meetings clients (Web App and Meetings App)](meetings-clients.md). 
  
## Microsoft Office Supportability

Skype for Business Server 2015 clients support integration with various versions of Microsoft Office.
  
- Skype for Business integration features are supported on Outlook 2016, Outlook 2013, and Outlook 2010.
    
- Skype for Business integration features are supported on Microsoft Exchange Server 2016, Microsoft Exchange Server 2013, and Microsoft Exchange Server 2010.
    
- The Online Meeting Add-in for Skype for Business is supported with Office 2016, Office 2013, and Microsoft Office 2010.
    
## Using Mandatory Profiles

If you plan to use the Skype for Business conferencing features, avoid using Active Directory Domain Services mandatory profiles to sign in to the Skype for Business client. Because mandatory profiles are read-only user profiles, the public key infrastructure (PKI) keys that are required for Skype for Business conferencing cannot be saved to the profile. 
  
## Macintosh Operating Systems

The Skype for Business on Mac support requirements are detailed in [Skype for Business on Mac client requirements](mac-requirements.md).
  
## See also

#### 

[Plan for Meetings clients (Web App and Meetings App)](meetings-clients.md)
  
[Skype for Business on Mac client requirements](mac-requirements.md)
#### 

[Download Skype for Business across all your devices](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-3)
  
[Office 365 system requirements](https://products.office.com/en-us/office-system-requirements)

