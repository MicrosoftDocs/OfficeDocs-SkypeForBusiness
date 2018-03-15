---
title: "IIS configuration in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b458babf-bf64-43f0-8a8e-612f5096b63c
description: "To successfully complete this procedure, you should be logged on to the server minimally as a local administrator and a domain user."
---

# IIS configuration in Lync Server 2013
[]
To successfully complete this procedure, you should be logged on to the server minimally as a local administrator and a domain user.
  
Before you configure and install the Front End Server for Lync Server 2013, Standard Edition or the first Front End Server in a pool, you install and configure the server role and Web Services for Internet Information Services (IIS).
  
> [!IMPORTANT]
> If your organization requires that you locate IIS and all Web Services on a drive other than the system drive, you can change the installation location path for the Lync Server 2013 files in the Setup dialog box when you initially install the Lync Server 2013 Administrative tools. You install the Administrative tools before installing IIS. If you install the Setup files to this path, including OCSCore.msi, the rest of the Lync Server 2013 files will be deployed to this drive as well. For dtails, see [Install Lync Server 2013 administrative tools](install-lync-server-administrative-tools.md). For details about how to relocate the INETPUB deployed by Windows Server Manager when installing IIS, see [https://go.microsoft.com/fwlink/p/?linkId=216888](https://go.microsoft.com/fwlink/p/?linkId=216888). 
  
The following table indicates the required IIS 7.5 role services.
  
**IIS 7.5 Role Services**

|**Role Heading**|**Role Service**|
|:-----|:-----|
|Common HTTP features installed  <br/> |Static content  <br/> |
|Common HTTP features installed  <br/> |Default document  <br/> |
|Common HTTP features installed  <br/> |HTTP errors  <br/> |
|Application development  <br/> |ASP.NET  <br/> Windows Server 2012 also requires ASP.NET4.5  <br/> |
|Application development  <br/> |.NET extensibility  <br/> |
|Application development  <br/> |Internet Server API (ISAPI) extensions  <br/> |
|Application development  <br/> |ISAPI filters  <br/> |
|Health and diagnostics  <br/> |HTTP logging  <br/> |
|Health and diagnostics  <br/> |Logging tools  <br/> |
|Health and diagnostics  <br/> |Tracing  <br/> |
|Security  <br/> |Anonymous authentication (installed and enabled by default)  <br/> |
|Security  <br/> |Windows authentication  <br/> |
|Security  <br/> |Client Certificate Mapping authentication  <br/> |
|Security  <br/> |Request filtering  <br/> |
|Performance  <br/> |Static content compression  <br/> Dynamic content compression  <br/> |
|Management Tools  <br/> |IIS Management Console  <br/> |
|Management Tools  <br/> |IIS Management Scripts and Tools  <br/> |
   
On the Windows Server 2008 R2 SP1 x64 operating system, you can use Windows PowerShell 2.0. You must first import the ServerManager module, and then install the IIS 7.5 role and role services.
  
```
Import-Module ServerManager
```

```
Add-WindowsFeature Web-Server, Web-Static-Content, Web-Default-Doc, Web-Scripting-Tools, Web-Windows-Auth, Web-Asp-Net, Web-Log-Libraries, Web-Http-Tracing, Web-Stat-Compression, Web-Dyn-Compression, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Errors, Web-Http-Logging, Web-Net-Ext, Web-Client-Auth, Web-Filtering, Web-Mgmt-Console
```

> [!NOTE]
> Anonymous authentication is installed by default with the IIS server role. You can manage anonymous authentication after the installation of IIS. For details, see "Enable Anonymous Authentication (IIS 7)" at [https://go.microsoft.com/fwlink/p/?linkId=203935](https://go.microsoft.com/fwlink/p/?linkId=203935). 
  
The following table indicates the required IIS 8.0 and IIS 8.5 role services for Windows Server 2012 and Windows Server 2012 R2.
  
> [!NOTE]
> For Windows Server 2012 and Windows Server 2012 R2, the Add-WindowsFeature cmdlet has been replaced by the Install-WindowsFeature cmdlet. For details, see [Install-WindowsFeature](https://go.microsoft.com/fwlink/p/?LinkId=392274). 
  
**IIS 8.0 and IIS 8.5 Role Services**

|**Role Heading**|**Role Service**|
|:-----|:-----|
|Web Server (IIS)  <br/> |Web Server  <br/> |
|Common HTTP Features  <br/> |Default Document  <br/> |
|Common HTTP Features  <br/> |Directory Browsing  <br/> |
|Common HTTP Features  <br/> |HTTP Errors  <br/> |
|Common HTTP Features  <br/> |Static content  <br/> |
|Common HTTP Features  <br/> |HTTP Redirection  <br/> |
|Health and Diagnostics  <br/> |HTTP Logging  <br/> |
|Health and Diagnostics  <br/> |Logging Tools  <br/> |
|Health and Diagnostics  <br/> |Request Monitor  <br/> |
|Health and Diagnostics  <br/> |Tracing  <br/> |
|Security  <br/> |Request Filtering  <br/> |
|Security  <br/> |Basic Authentication  <br/> |
|Security  <br/> |Client Certificate Mapping Authentication  <br/> |
|Security  <br/> |Windows Authentication  <br/> |
|Application Development  <br/> |.Net Extensibility 3.5  <br/> |
|Application Development  <br/> |.Net Extensibility 4.5  <br/> |
|Application Development  <br/> |ASP.Net 3.5  <br/> |
|Application Development  <br/> |ASP.Net 4.5  <br/> |
|Application Development  <br/> |ISAPI Extensions  <br/> |
|Application Development  <br/> |ISAPI Filters  <br/> |
|Application Development  <br/> |Server Side Includes  <br/> |
|Management Tools  <br/> |IIS Management Console  <br/> |
|Management Tools  <br/> |IIS 6 Metabase compatibility  <br/> |
|Management Tools  <br/> |IIS Management Scripts and Tools  <br/> |
|.Net 3.5 Framework Features  <br/> |.Net 3.5 Framework  <br/> |
|.Net 4.5 Framework Features  <br/> |.Net Framework 4.5  <br/> |
|.Net 4.5 Framework Features  <br/> |ASP.Net 4.5  <br/> |
|.Net 4.5 Framework Features  <br/> |HTTP Activation  <br/> |
|.Net 4.5 Framework Features  <br/> |TCP Port Sharing  <br/> |
|Background Intelligent Transfer Service  <br/> |IIS Server Extensions  <br/> |
|Ink and Handwriting Services  <br/> |Ink and Handwriting Services  <br/> |
|Media Foundation  <br/> |Media Foundation  <br/> |
|User Interfaces and Infrastructure  <br/> |Graphical Management Tools and Infrastructure  <br/> |
|User Interfaces and Infrastructure  <br/> |Desktop Experience  <br/> |
|User Interfaces and Infrastructure  <br/> |Server Graphical Shell  <br/> |
|Windows Identity Foundation 3.5  <br/> |Windows Identity Foundation 3.5  <br/> |
|Windows Process Activation Service  <br/> |Process Model  <br/> |
|Windows Process Activation Service  <br/> |Configuration APIs  <br/> |
   
In Windows Server 2012 and Windows Server 2012 R2, you can use Windows PowerShell 3.0 to install the IIS Requirements. Using the ServerManager module in Windows PowerShell 3.0, type:
  
```
Import-Module ServerManager
```

```
Add-WindowsFeature Web-Server, Web-Static-Content, Web-Default-Doc, Web-Http-Errors, Web-Asp-Net, Web-Net-Ext, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Logging, Web-Log-Libraries, Web-Request-Monitor, Web-Http-Tracing, Web-Basic-Auth, Web-Windows-Auth, Web-Client-Auth, Web-Filtering, Web-Stat-Compression, Web-Dyn-Compression, NET-Framework-45-Core, NET-WCF-HTTP-Activation45, Web-Asp-Net45, Web-Mgmt-Tools, Web-Scripting-Tools, Web-Mgmt-Console, Web-Mgmt-Compat, Windows-Identity-Foundation, Server-Media-Foundation, BITS -Source D:\sources\sxs
```

> [!IMPORTANT]
> New with Windows Server 2012 is the -Source parameter that defines where the Windows Server 2012 source media can be found. The media can be defined as a DVD drive (for example, D:\Sources\Sxs), or to a network share that the media files have been copied (for example, \\fileserver\windows2012\sources\Sxs). 
  
## See also

#### 

[IIS requirements for Front End pools and Standard Edition servers in Lync Server 2013](iis-requirements-for-front-end-pools-and-standard-edition-servers.md)

