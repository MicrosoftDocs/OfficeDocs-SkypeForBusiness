---
title: "IIS requirements for Front End pools and Standard Edition servers in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e8a6c7ac-b6d5-4c7e-abe9-d8ea5eedbc62
description: "For Standard Edition servers and Front End Servers, and Directors, the Lync Server 2013 installer creates virtual directories in Internet Information Services (IIS) for the following purposes:"
---

# IIS requirements for Front End pools and Standard Edition servers in Lync Server 2013
[]
For Standard Edition servers and Front End Servers, and Directors, the Lync Server 2013 installer creates virtual directories in Internet Information Services (IIS) for the following purposes:
  
- To enable users to download files from the Address Book Service
    
- To enable clients to obtain updates 
    
- To enable conferencing
    
- To enable users to download meeting content
    
- To enable users to expand distribution groups
    
- To enable phone conferencing
    
- To enable response group features
    
In addition, the cumulative update for Lync Server 2010: November 2011 installer creates virtual directories in IIS for the following purposes:
  
- On Front End Servers or Standard Edition servers to support mobility functionality, such as instant messaging (IM) and presence, on mobile devices
    
- On Front End Servers or Standard Edition servers and on Directors to enable mobile devices to automatically discover mobility resources
    
> [!NOTE]
> If you are deploying mobility, we recommend that you use IIS 7.5. The Lync Server Mobility Service installer sets some ASP.NET flags to improve performance. IIS 7.5 is installed by default on Windows Server 2008 R2, and the Mobility Service installer automatically changes the ASP.NET settings. If you use IIS 7.0 on Windows Server 2008, you need to manually change these settings. 
  
Lync Server requires the following IIS modules to be installed:
  
> [!IMPORTANT]
> If your organization requires that you locate IIS and all Web Services on a drive other than the system drive, you can change the installation location path for the Lync Server files in the Setup dialog box. If you install the Setup files to this path, including OCSCore.msi, the rest of the Lync Server files will be deployed to this drive as well. For details about how to relocate the INETPUB deployed by Windows Server Manager when installing IIS, see [https://go.microsoft.com/fwlink/p/?linkId=216888](https://go.microsoft.com/fwlink/p/?linkId=216888). 
  
- Static Content
    
- Default Document
    
- HTTP Errors
    
- ASP.NET
    
- .NET Extensibility
    
- Internet Server API (ISAPI) Extensions
    
- ISAPI Filters
    
- HTTP Logging
    
- Logging Tools
    
- Tracing
    
- Windows Authentication
    
- Request Filtering
    
- Static Content Compression
    
- Dynamic Content Compression
    
- IIS Management Console 
    
- IIS Management Scripts and Tools
    
- Anonymous Authentication (installed by default when IIS is installed) 
    
- Client Certificate Mapping Authentication 
    
The following table lists the URIs for the virtual directories for internal access and the file system resources to which they refer.
  
**Virtual Directories for Internal Access**

|**Feature**|**Virtual directory URI**|**Refers to**|
|:-----|:-----|:-----|
|Address Book Server  <br/> |https:// _\<Internal FQDN\>_/ABS/int/Handler  <br/> |Location of Address Book Server download files for internal users.  <br/> |
|Autodiscover Service  <br/> |https:// _\<Internal FQDN\>_/Autodiscover  <br/> |Location of the Lync Server Autodiscover Service that locates mobility resources for internal mobile device users.  <br/> |
|Client updates  <br/> |http:// _\<Internal FQDN\>_/AutoUpdate/Int  <br/> |Location of update files for internal computer-based clients.  <br/> |
|Conf  <br/> |http:// _\<Internal FQDN\>_/Conf/Int  <br/> |Location of conferencing resources for internal users.  <br/> |
|Device updates  <br/> |http:// _\<Internal FQDN\>_/DeviceUpdateFiles_Int  <br/> |Location of unified communications (UC) device update files for internal UC devices.  <br/> |
|Meeting  <br/> |http:// _\<Internal FQDN\>_/etc/place/null  <br/> |Location of meeting content for internal users.  <br/> |
|Mobility Service  <br/> |https:// _\<Internal FQDN\>_/Mcx  <br/> |Location of Mobility Service resources for internal mobile device users.  <br/> |
|Group Expansion and Address Book Web Query service  <br/> |http:// _\<Internal FQDN\>_/GroupExpansion/int/service.asmx  <br/> |Location of the Web service that enables group expansion for internal users. Also, the location of the Address Book Web Query service that provides global address list information to internal Lync Mobile Microsoft Lync 2010 Mobile clients.  <br/> |
|Phone Conferencing  <br/> |http:// _\<Internal FQDN\>_/PhoneConferencing/Int  <br/> |Location of phone conferencing data for internal users.  <br/> |
|Device updates  <br/> |http:// _\<Internal FQDN\>_/RequestHandler  <br/> |Location of the Device Update Web service Request Handler that enables internal UC devices to upload logs and check for updates.  <br/> |
|Response Group application  <br/> |http:// _\<Internal FQDN\>_/RgsConfig  <br/> http:// _\<Internal FQDN\>_/RgsClients  <br/> |Location of Response Group Configuration Tool.  <br/> |
   
> [!NOTE]
> For Front End pools in a consolidated configuration, you must deploy IIS before you can add servers to the pool. 
  
> [!SECURITY NOTE]
> You must use the IIS administrative snap-in to assign the certificate used by the IIS web component server. 
  

