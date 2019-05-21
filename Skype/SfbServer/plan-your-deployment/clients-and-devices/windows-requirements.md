---
title: "Windows client requirements and software support"
ms.author: v-lanac
author: lanachin
ms.reviewer: PhillipGarding
manager: serdars
ms.date: 2/16/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: a6851e38-ba9a-4f19-9aa7-d8accf4d62b3

description: "Summary: Review the Windows client support requirements while planning Skype for Business Server."
---

# Windows client requirements and software support
 
**Summary:** Review the Windows client support requirements while planning Skype for Business Server.
  
This section summarizes software required to support the Skype for Business Windows clients.  These clients are installed when Office 365 installs, and are also available at [Download Skype for Business across all your devices](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-3).
  
> [!NOTE]
> The Online Meeting Add-in for Skype for Business, which supports meeting management from within the Outlook messaging and collaboration client, installs automatically with Skype for Business. 
  
**Software Required for Skype for Business client and the Online Meeting Add-in**

|**System component**|**Supported versions**|
|:-----|:-----|
|Windows Operating system  <br/> |Windows 10  <br/> Windows 8.1  <br/> Windows 8  <br/> Windows 7 operating system  <br/> Windows Server 2008 R2 or later with latest service pack  <br/> **Note:** Skype for Business and the Online Meeting Add-in for Skype for Business are not supported on Windows Vista or Windows XP (any version). <br/> |
|Installation and updates  <br/> |Administrator rights and permissions  <br/> |
|Browser  <br/> |Microsoft Edge  <br/> Internet Explorer 11 Internet browser  <br/>  Internet Explorer 10 Internet browser <br/> Internet Explorer 9 Internet browser  <br/> Internet Explorer 8 Internet browser  <br/> Internet Explorer 7 Internet browser  <br/> Mozilla Firefox web browser  <br/>  Google Chrome web browser  <br/>**Note:** If you are using Skype for Business with Microsoft Exchange Online and your organization has deployed an authenticating HTTP proxy, Internet Explorer 8 or later is required.           |
|Microsoft Office Integration  <br/> | Outlook 2010 or later |
|Microsoft Exchange Integration  <br/> | Microsoft Exchange Server 2010 or later  | 
   
## Hardware

Refer to the Office 365 [System requirements](https://products.office.com/en-us/office-system-requirements) for the hardware required to run the Skype for Business client.
  
## Skype Meetings App and Skype for Business Web App 

The Skype Meetings App and Skype for Business Web App support specific combinations of operating systems and browsers. For details, see [Plan for Meetings clients (Web App and Meetings App)](meetings-clients.md). 
  
## Using Mandatory Profiles

If you plan to use the Skype for Business conferencing features, avoid using Active Directory Domain Services mandatory profiles to sign in to the Skype for Business client. Because mandatory profiles are read-only user profiles, the public key infrastructure (PKI) keys that are required for Skype for Business conferencing cannot be saved to the profile. 
  
## System requirements for Skype for Business for Windows Phone
 
 
Microsoft Skype for Business for Windows Phone provides instant messaging (IM), enhanced presence, and telephony for users in your organization who are connecting from a smartphone or a Windows Professional mobile device. Mobile devices enable users to extend the reach of Skype for Business. This topic describes planning considerations for Skype for Business for Windows Phone that include identifying prerequisites and technical requirements, required components, and deployment guidance.
  
### Skype for Business for Windows Phone Prerequisites

Following are the Skype for Business for Windows Phone prerequisites.
  
- Windows Phone 8.1 or later.
    
- The Windows Phone device must have the latest updates available from Microsoft. For details, see the Windows Phone 8.1 section at [Windows Phone 8 update history](https://go.microsoft.com/fwlink/p/?LinkID=281961).
    
- The device must have 22 MB of available disk space.
    
- The user must have a voice and data plan from a carrier.


## See also

[Plan for Meetings clients (Web App and Meetings App)](meetings-clients.md)
  
[Skype for Business on Mac client requirements](mac-requirements.md)

[Download Skype for Business across all your devices](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-3)
  
[Office 365 system requirements](https://products.office.com/en-us/office-system-requirements)
