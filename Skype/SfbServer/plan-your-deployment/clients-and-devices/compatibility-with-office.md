---
title: "Skype for Business compatibility with Office apps"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 2/16/2018
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.custom: Strat_SB_Admin
ms.assetid: ac3a1046-b438-4e21-9d4f-3b0057dd685d
description: "Understand the ways you can access Skype for Business features from Outlook and other Microsoft Office applications."
---

# Skype for Business compatibility with Office apps
 
Understand the ways you can access Skype for Business features from Outlook and other Microsoft Office applications.
  
This topic describes the compatibility of Skype for Business with various versions of Microsoft Office suites. 
  
## Office and Skype for Business

The following table describes the Skype for Business features that are supported by various versions of Office once Exchange is deployed and integrated as described in [Integrate Skype for Business Server 2015 with Exchange Server](../../deploy-1/integrate-with-exchange-server/integrate-with-exchange-server.md).
  
**Skype for Business and Microsoft Office Compatibility**

|**Feature**|**Microsoft Office 2010**|**Microsoft Office 2013, 2015, and 2016**|**Office 2016 for Mac** &#x2776; |
|:-----|:-----|:-----|:-----|
|**Outlook features** <br/> ||||
|Customize Outlook meeting invitations (add logo, help URL, disclaimer, footer text)  <br/> |No  <br/> |Yes  <br/> |No  <br/> |
|Configure meeting option to mute attendee audio and video by default  <br/> |No  <br/> |Yes  <br/> |No  <br/> |
|Unified Contact Store for managing Contacts lists across Office and Skype for Business  <br/> |No  <br/> |Yes (requires Exchange 2013 or later)  <br/> |Yes  <br/> |
|High-resolution profile pictures  <br/> |No  <br/> |Yes (requires Exchange 2013 or later)  <br/> |Yes  <br/> |
|Presence status in the Microsoft Outlook From, To, and Cc fields  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Reply with IM or call from the availability menu  <br/> |Yes (from the contact card)  <br/> |Yes (from the contact card)  <br/> |Yes (from the contact card)  <br/> |
|Presence status in a meeting request on the Scheduling Assistant tab  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Reply with IM or call from the toolbar or ribbon in a received email message  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|**Other Office apps** <br/> ||||
|OneNote shared notes  <br/> |No  <br/> |Yes  <br/> |No  <br/> |
|Setup integrated into the Office setup program  <br/> |No  <br/> |Yes  <br/> |No  <br/> |
|PowerPoint presentation content  <br/> |Yes  <br/> |Yes  <br/> (VBSS also available)  <br/> |Yes  <br/> |
|IM and presence in Microsoft Word and Microsoft Excel files (smart tags enabled)  <br/> |Microsoft Word only  <br/> |Microsoft Word only  <br/> |No  <br/> |
|IM and presence in Microsoft SharePoint sites (Outlook must be installed)  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
   
&#x2776; - Assumes you have installed and are currently running a Skype for Business on Mac client or the Lync 2011 for Mac client.
  
## Exchange Server and Skype for Business

The following table describes Skype for Business support for various versions of Exchange Server. Outlook must be installed on the client computer to handle Extended MAPI calls, and some features require the use of Exchange Web Services (EWS).
  
**Skype for Business and Exchange Server Compatibility**

|**Exchange Server version**|**Skype for Business support**|
|:-----|:-----|
|Exchange Server 2016  <br/> |Same as Exchange Server 2013 support  <br/> |
|Exchange Server 2013  <br/> |Same as Exchange Server 2010 support, with the addition of  <br/>&bull;&nbsp;&nbsp;Unified Contact Store  <br/>&bull;&nbsp;&nbsp;High-resolution pictures  <br/>&bull;&nbsp;&nbsp;Archiving integration  <br/> **Note:** For details, see [Integrate Skype for Business Server 2015 with Exchange Server](../../deploy-1/integrate-with-exchange-server/integrate-with-exchange-server.md).  <br/> |
|Exchange Server 2010  <br/> |The following features are available only through EWS:  <br/>&bull;&nbsp;&nbsp;Read or delete items in the Conversation History folder  <br/>&bull;&nbsp;&nbsp;Read or delete voice mail items  <br/>&bull;&nbsp;&nbsp;Display extended free/busy information and meeting subject and location  <br/>&bull;&nbsp;&nbsp;Exchange contact sync  <br/> Public folders are optional in Exchange Server 2010.  <br/> |
   
## See also
 

[Windows client requirements and software support](windows-requirements.md)
  
[Plan for Meetings clients (Web App and Meetings App)](meetings-clients.md)
#### 

[Client Interoperability in Lync 2013](http://technet.microsoft.com/library/0f126571-91a2-45d5-855c-1e4ddb45fc04.aspx)
  
[Client System Requirements](http://technet.microsoft.com/library/38f3a465-dac1-4381-bc59-270a4ef07ced.aspx)
  
[Lync Windows Store App Requirements](http://technet.microsoft.com/library/5f2e0a40-8450-4f61-b6f6-913fc1906020.aspx)

