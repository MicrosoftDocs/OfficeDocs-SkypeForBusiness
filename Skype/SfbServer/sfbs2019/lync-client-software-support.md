---
title: "Lync client software support in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: End User
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a6851e38-ba9a-4f19-9aa7-d8accf4d62b3

description: "In this articleMacintosh Operating SystemsLync Web App BrowsersMicrosoft Office SupportabilityUsing Mandatory Profiles"
---

# Lync client software support in Lync Server 2013
[]
 **In this article**
  
[Macintosh Operating Systems](#sectionSection0)
  
[Lync Web App Browsers](#sectionSection1)
  
[Microsoft Office Supportability](#sectionSection2)
  
[Using Mandatory Profiles](#sectionSection3)
  
This section summarizes software support for Lync 2013 and the Online Meeting Add-in for Lync 2013.
  
> [!NOTE]
> The Online Meeting Add-in for Lync 2013, which supports meeting management from within the Outlook messaging and collaboration client, installs automatically with Lync 2013. 
  
**Software Requirements for Lync 2013 and the Online Meeting Add-in for Lync 2013**

|**System component**|**Minimum requirement**|
|:-----|:-----|
|Windows Operating system  <br/> |Windows 10  <br/> Windows 8.1  <br/> Windows 8  <br/> Windows 7 operating system  <br/> Windows Server 2008 R2 with latest service pack  <br/> > [!NOTE]> Lync 2013 and the Online Meeting Add-in for Lync 2013 are not supported on Windows Vista or Windows XP (any version).           |
|Installation and updates  <br/> |Administrator rights and permissions  <br/> |
|Browser  <br/> |Internet Explorer 11 Internet browser  <br/>  Internet Explorer 10 Internet browser  <br/> Internet Explorer 9 Internet browser  <br/> Internet Explorer 8 Internet browser  <br/> Internet Explorer 7 Internet browser  <br/> Mozilla Firefox web browser  <br/> > [!NOTE]> If you are using Lync with Microsoft Exchange Online and your organization has deployed an authenticating HTTP proxy, Internet Explorer 9 or Internet Explorer 8 is required.           |
|Microsoft Office Integration  <br/> | For the full set of integration features:  <br/>  Outlook 2013 messaging and collaboration client  <br/>  Outlook 2010 messaging and collaboration client  <br/> |
|Microsoft Exchange Integration  <br/> | For the full set of integration features:  <br/>  Microsoft Exchange Server 2013  <br/>  Microsoft Exchange Server 2010  <br/> |
   
## Macintosh Operating Systems
<a name="sectionSection0"> </a>

Lync 2013 is available only for Windows. However, Lync Server 2013 supports the following clients on computers that are running Mac OS 10.5.8 or latest service pack or release (Intel-based) operating systems (Mac OS 10.9 operating system is not currently supported). For details about supported features, see [Desktop client comparison tables for Lync Server 2013](desktop-client-comparison-tables.md).
  
- Microsoft Lync for Mac 2011 (see "Lync for Mac 2011 Deployment Guide" at [https://go.microsoft.com/fwlink/p/?LinkId=268786](https://go.microsoft.com/fwlink/p/?LinkId=268786))
    
- Microsoft Communicator for Mac 2011 (see "Communicator for Mac 2011 Deployment Guide" at [https://go.microsoft.com/fwlink/p/?LinkId=268787](https://go.microsoft.com/fwlink/p/?LinkId=268787))
    
## Lync Web App Browsers
<a name="sectionSection1"> </a>

Lync Web App supports specific combinations of operating systems and browsers. For details, see [Lync Web App supported platforms for Lync Server 2013](lync-web-app-supported-platforms.md) in the Planning documentation. 
  
## Microsoft Office Supportability
<a name="sectionSection2"> </a>

Lync Server 2013 clients support integration with various versions of Microsoft Office, as summarized in this section.
  
- Lync 2013 integration features are supported on Outlook 2013 and Microsoft Outlook 2010.
    
- Lync 2013 integration features are supported on Microsoft Exchange Server 2013 and Microsoft Exchange Server 2010.
    
- The Online Meeting Add-in for Lync 2013 is supported with Office 2013 and Microsoft Office 2010.
    
## Using Mandatory Profiles
<a name="sectionSection3"> </a>

If users are planning to use Lync 2013 conferencing features, they should not use Active Directory Domain Services mandatory profiles to sign in to the Lync 2013 client. Because mandatory profiles are read-only user profiles, the public key infrastructure (PKI) keys that are required for Lync 2013 conferencing cannot be saved to the profile. For details, see Microsoft Knowledge Base article 2552221, "Lync 2010 conferencing feature fails when the user is signed in using a mandatory user profile," at [http://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=2552221](http://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=2552221). 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Lync client hardware support in Lync Server 2013](lync-client-hardware-support.md)
  
[Lync client video requirements for Lync Server 2013](lync-client-video-requirements.md)
  
[Supported clients from previous deployments in Lync Server 2013](supported-clients-from-previous-deployments.md)

