---
title: Desktop client software support
ms.prod: SKYPEFORBUSINESS
ms.assetid: a6851e38-ba9a-4f19-9aa7-d8accf4d62b3
---



# Desktop client software support
[] **Summary:** Review the client support requirements while planning Skype for Business Server 2015.
This section summarizes software required to support the Skype for Business 2015 and 2016 clients, and the Online Meeting Add-in for the Skype for Business client.
  
    
    


> [!NOTE]
> The Online Meeting Add-in for Skype for Business, which supports meeting management from within the Outlook messaging and collaboration client, installs automatically with Skype for Business. 
  
    
    


**Software Required for Skype for Business and the Online Meeting Add-in for Skype for Business**

|
|
|**System component**|**Supported versions**|
|:-----|:-----|
|Windows Operating system  <br/> |Windows 10  <br/> Windows 8.1  <br/> Windows 8  <br/> Windows 7 operating system  <br/> Windows Server 2008 R2 with latest service pack  <br/> > [!NOTE]> Skype for Business and the Online Meeting Add-in for Skype for Business are not supported on Windows Vista or Windows XP (any version).           |
|Installation and updates  <br/> |Administrator rights and permissions  <br/> |
|Browser  <br/> |Microsoft Edge  <br/> Internet Explorer 11 Internet browser  <br/>  Internet Explorer 10 Internet browser <br/> Internet Explorer 9 Internet browser  <br/> Internet Explorer 8 Internet browser  <br/> Internet Explorer 7 Internet browser  <br/> Mozilla Firefox web browser  <br/> > [!NOTE]> If you are using Skype for Business with Microsoft Exchange Online and your organization has deployed an authenticating HTTP proxy, Internet Explorer 8 or later is required.           |
|Microsoft Office Integration  <br/> | For the full set of integration features: <br/>  Outlook 2016 messaging and collaboration client <br/>  Outlook 2013 messaging and collaboration client <br/>  Outlook 2010 messaging and collaboration client <br/> |
|Microsoft Exchange Integration  <br/> | Microsoft Exchange Server 2016 <br/>  Microsoft Exchange Server 2013 <br/>  Microsoft Exchange Server 2010 <br/> |
   

## Macintosh Operating Systems

Skype for Business is available only for Windows. However, Skype for Business Server 2015 supports the following clients on computers that are running Mac OS 10.5.8 or latest service pack or release (Intel-based) operating systems (Mac OS 10.9 operating system is not currently supported). For details about supported features, see  [Desktop client comparison tables for Skype for Business](desktop-client-comparison-tables-for-skype-for-business.md).
  
    
    

- Microsoft Lync for Mac 2011 (see  [Lync for Mac 2011 Deployment Guide](https://go.microsoft.com/fwlink/p/?LinkId=268786))
    
  
- Microsoft Communicator for Mac 2011 (see  [Communicator for Mac 2011 Deployment Guide](https://go.microsoft.com/fwlink/p/?LinkId=268787))
    
  

## Skype for Business Web App Browsers

Skype for Business Web App supports specific combinations of operating systems and browsers. For details, see  [Plan for Web downloadable clients](plan-for-web-downloadable-clients.md). 
  
    
    

## Microsoft Office Supportability

Skype for Business Server 2015 clients support integration with various versions of Microsoft Office, as summarized in this section.
  
    
    

- Skype for Business integration features are supported on Outlook 2016, Outlook 2013, and Outlook 2010.
    
  
- Skype for Business integration features are supported on Microsoft Exchange Server 2016, Microsoft Exchange Server 2013, and Microsoft Exchange Server 2010.
    
  
- The Online Meeting Add-in for Skype for Business is supported with Office 2016, Office 2013, and Microsoft Office 2010.
    
  

## Using Mandatory Profiles

If you plan to use the Skype for Business conferencing features, avoid using Active Directory Domain Services mandatory profiles to sign in to the Skype for Business client. Because mandatory profiles are read-only user profiles, the public key infrastructure (PKI) keys that are required for Skype for Business conferencing cannot be saved to the profile. 
  
    
    
