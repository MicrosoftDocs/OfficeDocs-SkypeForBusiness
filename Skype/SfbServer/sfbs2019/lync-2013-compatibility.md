---
title: "Lync 2013 compatibility"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: End User
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ac3a1046-b438-4e21-9d4f-3b0057dd685d

description: "In this articleOffice and Lync 2013Exchange Server and Lync 2013Windows and Lync 2013Macintosh and Lync 2013Public Instant Messaging Clients and Lync 2013"
---

# Lync 2013 compatibility
[]
 **In this article**
  
[Office and Lync 2013](#sectionSection0)
  
[Exchange Server and Lync 2013](#sectionSection1)
  
[Windows and Lync 2013](#sectionSection2)
  
[Macintosh and Lync 2013](#sectionSection3)
  
[Public Instant Messaging Clients and Lync 2013](#sectionSection4)
  
This section describes the compatibility of Lync 2013 with various versions of Microsoft Office suites, Microsoft Exchange Server, Windows operating systems, and selected public instant messaging (IM) clients. 
  
## Office and Lync 2013
<a name="sectionSection0"> </a>

The following table describes the Lync 2013 features that are supported by various versions of Office.
  
**Lync 2013 and Microsoft Office Compatibility**

|**Feature**|**Microsoft Office 2003 with Service Pack 3 (SP3) (required) or the latest service pack (recommended)**|**Microsoft Office 2007**|**Microsoft Office 2010**|**Microsoft Office 2013**|
|:-----|:-----|:-----|:-----|:-----|
|Customize Outlook meeting invitations (add logo, help URL, disclaimer, footer text)  <br/> |No  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|In Outlook, configure meeting option to mute attendee audio and video by default  <br/> |No  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|Unified Contact Store for managing Contacts lists across Office and Lync  <br/> |No  <br/> |No  <br/> |No  <br/> |Yes (requires Exchange 2013)<sup>1</sup> <br/> |
|High-resolution pictures  <br/> |No  <br/> |No  <br/> |No  <br/> |Yes (requires Exchange 2013)<sup>1</sup> <br/> |
|Lync 2013 setup integrated into the Office setup program  <br/> |No  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|OneNote shared notes  <br/> |No  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|PowerPoint presentation content  <br/> |No  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|Presence status in the Microsoft Outlook To and Cc fields  <br/> |No  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|Reply with conference call from the availability menu  <br/> |No  <br/> |No  <br/> |Yes (from the contact card)  <br/> |Yes (from the contact card)  <br/> |
|Presence status in a meeting request on the Scheduling Assistant tab  <br/> |No  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|Reply with IM, or call from the toolbar or ribbon in a received email message  <br/> |No  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|Presence status in the Outlook From field  <br/> |No  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|Reply with IM or voice from availability menu  <br/> |No  <br/> |No  <br/> |Yes (from the contact card)  <br/> |Yes (from the contact card)  <br/> |
|IM and presence in Microsoft Word and Microsoft Excel files (smart tags enabled)  <br/> |No  <br/> |No  <br/> |Microsoft Word only  <br/> |Microsoft Word only  <br/> |
|IM and presence in Microsoft SharePoint sites (Outlook must be installed)  <br/> |No  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
   
<sup>1</sup> For more information, see [Integrating Microsoft Lync Server 2013 and Microsoft Exchange Server 2013](integrating-lync-server-2013-and-exchange-server-2013.md) in the Planning documentation. 
  
The following features are available only with Office 2010 or Office 2013:
  
- Contact card with expanded options, such as video call and desktop sharing
    
- Quick search from the Find a Contact field in Outlook
    
- Reply with an IM or call from the Outlook Home ribbon in the Mail, Calendar, Contacts, and Tasks folders
    
- Lync Contacts list in Outlook To-Do Bar
    
- Office Backstage (File tab) presence status, program sharing, and file transfer
    
- Presence menu in Microsoft Office SharePoint Workspace 2010 (formerly Microsoft Office Groove 2007)
    
- Presence menu extensibility
    
## Exchange Server and Lync 2013
<a name="sectionSection1"> </a>

The following table describes Lync 2013 support for various versions of Exchange Server. Outlook must be installed on the client computer to handle Extended MAPI calls, and some features require the use of Exchange Web Services (EWS).
  
**Lync 2013 and Exchange Server Compatibility**

|**Exchange Server version**|**Lync 2013 support**|
|:-----|:-----|
|Exchange Server 2013  <br/> |Same as Exchange Server 2010 support, with the addition of Unified Contact Store, high-resolution pictures, and archiving integration.  <br/> > [!NOTE]> For details, see [Integrating Microsoft Lync Server 2013 and Microsoft Exchange Server 2013](integrating-lync-server-2013-and-exchange-server-2013.md).           |
|Exchange Server 2010  <br/> |Same as Exchange Server 2007 support, with the addition of Exchange contact sync.  <br/> |
|Exchange Server 2007 with Service Pack 1 (SP1) (required) or the latest service pack (recommended)  <br/> | The following features are available only through EWS:  <br/>  Read or delete items in the Conversation History folder  <br/>  Read or delete voice mail items  <br/>  Display extended free/busy information and meeting subject and location  <br/>  Public folders are optional in Exchange Server 2007 with Service Pack 1 (SP1) (required) or the latest service pack or release (recommended).  <br/> |
|Exchange Server 2003  <br/> |Outlook MAPI only. EWS-only features are not available (see the previous row).  <br/> |
   
## Windows and Lync 2013
<a name="sectionSection2"> </a>

For information about Lync 2013 and Windows supportability, see [Lync client software support in Lync Server 2013](lync-client-software-support.md) in the Planning documentation. 
  
## Macintosh and Lync 2013
<a name="sectionSection3"> </a>

Lync Server 2013 supports certain clients on computers that are running Macintosh operating systems. For details, see [Lync client software support in Lync Server 2013](lync-client-software-support.md) in the Planning documentation. 
  
## Public Instant Messaging Clients and Lync 2013
<a name="sectionSection4"> </a>

If you have configured your server for public IM connectivity, Lync supports the following capabilities with public IM networks. Presence status is filtered to those presence states supported by the public IM client. For details, see [Planning for public instant messaging connectivity in Lync Server 2013](planning-for-public-instant-messaging-connectivity.md) in the Planning documentation and [Manage external access policy in Lync Server 2013](manage-external-access-policy-for-your-organization.md) in the Operations documentation. 
  
In addition, the XMPP integration feature of Lync Server 2013 lets users exchange instant messages and presence information with users of public IM providers that use Extensible Messaging and Presence Protocol, such as Google Talk. For details, see [Planning for extensible messaging and presence protocol (XMPP) federation in Lync Server 2013](planning-for-extensible-messaging-and-presence-protocol-xmpp-federation.md) in the Planning documentation. 
  
**Lync 2013 and Public IM Clients Compatibility**

|**Client**|**Supported Capabilities**|
|:-----|:-----|
|Windows Live Messenger  <br/> |IM, basic presence, audio/video (A/V)\*  <br/> |
|Skype  <br/> |IM, basic presence, audio  <br/> |
|AOL  <br/> |IM and basic presence  <br/> |
|Yahoo!  <br/> |IM and basic presence  <br/> |
|Google Talk  <br/> |IM and basic presence  <br/> |
   
\*A/V is supported with the latest version of Windows Live Messenger. If you are implementing audio/video (A/V) federation with Windows Live Messenger, you must also modify the server encryption level. By default, the encryption level is Required. You must change this setting to Supported by using the Lync Server Management Shell.
  
> [!IMPORTANT]
>  As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License ("PIC USL") is no longer available for purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shut down date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see [Support for public instant messenger connectivity in Lync Server 2013](support-for-public-instant-messenger-connectivity.md). >  The PIC USL is a per-user per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft's ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which is winding down. >  More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. 
  
## See also
<a name="sectionSection4"> </a>

#### 

[Client interoperability in Lync 2013](client-interoperability-in-lync-2013.md)
  
[Lync client software support in Lync Server 2013](lync-client-software-support.md)
  
[Lync Web App supported platforms for Lync Server 2013](lync-web-app-supported-platforms.md)
  
[Lync Windows Store app requirements for Lync Server 2013](lync-windows-store-app-requirements.md)
#### 

[Client system requirements for Lync Server 2013](client-system-requirements.md)

