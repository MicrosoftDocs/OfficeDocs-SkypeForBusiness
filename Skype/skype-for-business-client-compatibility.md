---
title: Skype for Business client compatibility
ms.prod: SKYPEFORBUSINESS
ms.assetid: ac3a1046-b438-4e21-9d4f-3b0057dd685d
---



# Skype for Business client compatibility
[]Understand the ways you can access Skype for Business features from Outlook and other Microsoft Office applications.
This topic describes the compatibility of Skype for Business with various versions of Microsoft Office suites. 
  
    
    


## Office and Skype for Business

The following table describes the Skype for Business features that are supported by various versions of Office once Exchange is deployed and integrated as described in  [Integrate Skype for Business Server 2015 with Exchange Server](integrate-skype-for-business-server-2015-with-exchange-server.md).
  
    
    

**Skype for Business and Microsoft Office Compatibility**


|**Feature**|**Microsoft Office 2010**|**Microsoft Office 2013, 2015, and 2016**|
|:-----|:-----|:-----|
|Outlook features  <br/> |||
|Customize Outlook meeting invitations (add logo, help URL, disclaimer, footer text)  <br/> |No  <br/> |Yes  <br/> |
|Configure meeting option to mute attendee audio and video by default  <br/> |No  <br/> |Yes  <br/> |
|Unified Contact Store for managing Contacts lists across Office and Skype for Business  <br/> |No  <br/> |Yes (requires Exchange 2013 or later)  <br/> |
|High-resolution profile pictures  <br/> |No  <br/> |Yes (requires Exchange 2013 or later)  <br/> |
|Presence status in the Microsoft Outlook To and Cc fields  <br/> |Yes  <br/> |Yes  <br/> |
|Setup integrated into the Office setup program  <br/> |No  <br/> |Yes  <br/> |
|OneNote shared notes  <br/> |No  <br/> |Yes  <br/> |
|PowerPoint presentation content  <br/> |Yes  <br/> |Yes  <br/> (VBSS also available)  <br/> |
||||
|Reply with conference call from the availability menu  <br/> |Yes (from the contact card)  <br/> |Yes (from the contact card)  <br/> |
|Presence status in a meeting request on the Scheduling Assistant tab  <br/> |Yes  <br/> |Yes  <br/> |
|Reply with IM, or call from the toolbar or ribbon in a received email message  <br/> |Yes  <br/> |Yes  <br/> |
|Presence status in the Outlook From field  <br/> |Yes  <br/> |Yes  <br/> |
|Reply with IM or voice from availability menu  <br/> |Yes (from the contact card)  <br/> |Yes (from the contact card)  <br/> |
|IM and presence in Microsoft Word and Microsoft Excel files (smart tags enabled)  <br/> |Microsoft Word only  <br/> |Microsoft Word only  <br/> |
|IM and presence in Microsoft SharePoint sites (Outlook must be installed)  <br/> |Yes  <br/> |Yes  <br/> |
   
The following features are available only with Office 2010, Office 2013, or Office 2015:
  
    
    

- Contact card with expanded options, such as video call and desktop sharing
    
  
- Quick search from the Find a Contact field in Outlook
    
  
- Reply with an IM or call from the Outlook Home ribbon in the Mail, Calendar, Contacts, and Tasks folders
    
  
- Skype for Business Contacts list in Outlook To-Do Bar
    
  
- Office Backstage (File tab) presence status, program sharing, and file transfer
    
  
- Presence menu in Microsoft Office SharePoint Workspace 2010 
    
  
- Presence menu extensibility
    
  

## Exchange Server and Skype for Business

The following table describes Skype for Business support for various versions of Exchange Server. Outlook must be installed on the client computer to handle Extended MAPI calls, and some features require the use of Exchange Web Services (EWS).
  
    
    

**Skype for Business and Exchange Server Compatibility**


|**Exchange Server version**|**Skype for Business support**|
|:-----|:-----|
|Exchange Server 2016  <br/> |Same as Exchange Server 2013 support  <br/> |
|Exchange Server 2013  <br/> |Same as Exchange Server 2010 support, with the addition of Unified Contact Store, high-resolution pictures, and archiving integration.  <br/> > [!NOTE]> For details, see  [Integrate Skype for Business Server 2015 with Exchange Server](integrate-skype-for-business-server-2015-with-exchange-server.md).           |
|Exchange Server 2010  <br/> | The following features are available only through EWS: <br/>  Read or delete items in the Conversation History folder <br/>  Read or delete voice mail items <br/>  Display extended free/busy information and meeting subject and location <br/>  Exchange contact sync <br/>  Public folders are optional in Exchange Server 2010. <br/> |
   

## See also


#### 


  
    
    
 [Desktop client software support](desktop-client-software-support.md)
  
    
    
 [Plan for Web downloadable clients](plan-for-web-downloadable-clients.md)
#### 


  
    
    
 [Client Interoperability in Lync 2013](http://technet.microsoft.com/library/0f126571-91a2-45d5-855c-1e4ddb45fc04.aspx)
  
    
    
 [Client System Requirements](http://technet.microsoft.com/library/38f3a465-dac1-4381-bc59-270a4ef07ced.aspx)
  
    
    
 [Lync Windows Store App Requirements](http://technet.microsoft.com/library/5f2e0a40-8450-4f61-b6f6-913fc1906020.aspx)
