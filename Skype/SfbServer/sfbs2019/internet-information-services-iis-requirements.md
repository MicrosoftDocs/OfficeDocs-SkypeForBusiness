---
title: "Internet Information Services (IIS) requirements in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4f57a605-a8a9-4c5a-9a18-05ecb3d9ab6b
description: "Several Lync Server 2013 components require Internet Information Services (IIS). This topic describes the specific IIS features required to support Lync Server. The topics in this section describe the requirements of specific components for IIS."
---

# Internet Information Services (IIS) requirements in Lync Server 2013
[]
Several Lync Server 2013 components require Internet Information Services (IIS). This topic describes the specific IIS features required to support Lync Server. The topics in this section describe the requirements of specific components for IIS.
  
When the Web Server (IIS) role is enabled on Windows Server 2008, various role services are installed by default. The following table describes the additional role services that must be installed when the Web Server (IIS) role is enabled on Windows Server 2008. 
  
|**Role service**|**Feature**|
|:-----|:-----|
|Common HTTP Features  <br/> |HTTP Redirection  <br/> |
|Application Development  <br/> |ASP.NET  <br/> |
|Application Development  <br/> |.NET Extensibility  <br/> |
|Application Development  <br/> |ISAPI Extensions  <br/> |
|Application Development  <br/> |ISAPI Filters  <br/> |
|Health and Diagnostics  <br/> |Logging Tools  <br/> |
|Health and Diagnostics  <br/> |Tracing  <br/> |
|Security  <br/> |Basic Authentication  <br/> |
|Security  <br/> |Windows Authentication  <br/> |
|Management Tools  <br/> |IIS Management Scripts and Tools  <br/> |
|Management Tools  <br/> |IIS 6 Management Compatibility  <br/> |
   
> [!SECURITY NOTE]
> If you are using IIS 7.0 on a Windows Server 2008 operating system, Lync Server Setup disables kernel mode authentication in IIS. 
  
## In this section

- [IIS requirements for Front End pools and Standard Edition servers in Lync Server 2013](iis-requirements-for-front-end-pools-and-standard-edition-servers.md)
    

