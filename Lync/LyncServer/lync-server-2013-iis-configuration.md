---
title: 'Lync Server 2013: IIS configuration'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: IIS configuration
ms:assetid: b458babf-bf64-43f0-8a8e-612f5096b63c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412871(v=OCS.15)
ms:contentKeyID: 48185169
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# IIS configuration in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-17_

To successfully complete this procedure, you should be logged on to the server minimally as a local administrator and a domain user.

Before you configure and install the Front End Server for Lync Server 2013, Standard Edition or the first Front End Server in a pool, you install and configure the server role and Web Services for Internet Information Services (IIS).

<div class=" ">


> [!IMPORTANT]  
> If your organization requires that you locate IIS and all Web Services on a drive other than the system drive, you can change the installation location path for the Lync Server 2013 files in the Setup dialog box when you initially install the Lync Server 2013 Administrative tools. You install the Administrative tools before installing IIS. If you install the Setup files to this path, including OCSCore.msi, the rest of the Lync Server 2013 files will be deployed to this drive as well. For dtails, see <A href="lync-server-2013-install-lync-server-administrative-tools.md">Install Lync Server 2013 administrative tools</A>. For details about how to relocate the INETPUB deployed by Windows Server Manager when installing IIS, see <A href="http://go.microsoft.com/fwlink/p/?linkid=216888">http://go.microsoft.com/fwlink/p/?linkId=216888</A>.



</div>

The following table indicates the required IIS 7.5 role services.

### IIS 7.5 Role Services

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Role Heading</th>
<th>Role Service</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Common HTTP features installed</p></td>
<td><p>Static content</p></td>
</tr>
<tr class="even">
<td><p>Common HTTP features installed</p></td>
<td><p>Default document</p></td>
</tr>
<tr class="odd">
<td><p>Common HTTP features installed</p></td>
<td><p>HTTP errors</p></td>
</tr>
<tr class="even">
<td><p>Application development</p></td>
<td><p>ASP.NET</p>
<p>Windows Server 2012 also requires ASP.NET4.5</p></td>
</tr>
<tr class="odd">
<td><p>Application development</p></td>
<td><p>.NET extensibility</p></td>
</tr>
<tr class="even">
<td><p>Application development</p></td>
<td><p>Internet Server API (ISAPI) extensions</p></td>
</tr>
<tr class="odd">
<td><p>Application development</p></td>
<td><p>ISAPI filters</p></td>
</tr>
<tr class="even">
<td><p>Health and diagnostics</p></td>
<td><p>HTTP logging</p></td>
</tr>
<tr class="odd">
<td><p>Health and diagnostics</p></td>
<td><p>Logging tools</p></td>
</tr>
<tr class="even">
<td><p>Health and diagnostics</p></td>
<td><p>Tracing</p></td>
</tr>
<tr class="odd">
<td><p>Security</p></td>
<td><p>Anonymous authentication (installed and enabled by default)</p></td>
</tr>
<tr class="even">
<td><p>Security</p></td>
<td><p>Windows authentication</p></td>
</tr>
<tr class="odd">
<td><p>Security</p></td>
<td><p>Client Certificate Mapping authentication</p></td>
</tr>
<tr class="even">
<td><p>Security</p></td>
<td><p>Request filtering</p></td>
</tr>
<tr class="odd">
<td><p>Performance</p></td>
<td><p>Static content compression</p>
<p>Dynamic content compression</p></td>
</tr>
<tr class="even">
<td><p>Management Tools</p></td>
<td><p>IIS Management Console</p></td>
</tr>
<tr class="odd">
<td><p>Management Tools</p></td>
<td><p>IIS Management Scripts and Tools</p></td>
</tr>
</tbody>
</table>


On the Windows Server 2008 R2 SP1 x64 operating system, you can use Windows PowerShell 2.0. You must first import the ServerManager module, and then install the IIS 7.5 role and role services.

   ```
    Import-Module ServerManager
   ```

   ```
    Add-WindowsFeature Web-Server, Web-Static-Content, Web-Default-Doc, Web-Scripting-Tools, Web-Windows-Auth, Web-Asp-Net, Web-Log-Libraries, Web-Http-Tracing, Web-Stat-Compression, Web-Dyn-Compression, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Errors, Web-Http-Logging, Web-Net-Ext, Web-Client-Auth, Web-Filtering, Web-Mgmt-Console
   ```

<div class=" ">


> [!NOTE]  
> Anonymous authentication is installed by default with the IIS server role. You can manage anonymous authentication after the installation of IIS. For details, see “Enable Anonymous Authentication (IIS 7)” at <A href="http://go.microsoft.com/fwlink/p/?linkid=203935">http://go.microsoft.com/fwlink/p/?linkId=203935</A>.



</div>

The following table indicates the required IIS 8.0 and IIS 8.5 role services for Windows Server 2012 and Windows Server 2012 R2.

<div class=" ">


> [!NOTE]  
> For Windows Server 2012 and Windows Server 2012 R2, the Add-WindowsFeature cmdlet has been replaced by the Install-WindowsFeature cmdlet. For details, see <A href="http://go.microsoft.com/fwlink/p/?linkid=392274">Install-WindowsFeature</A>.



</div>

### IIS 8.0 and IIS 8.5 Role Services

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Role Heading</th>
<th>Role Service</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Web Server (IIS)</p></td>
<td><p>Web Server</p></td>
</tr>
<tr class="even">
<td><p>Common HTTP Features</p></td>
<td><p>Default Document</p></td>
</tr>
<tr class="odd">
<td><p>Common HTTP Features</p></td>
<td><p>Directory Browsing</p></td>
</tr>
<tr class="even">
<td><p>Common HTTP Features</p></td>
<td><p>HTTP Errors</p></td>
</tr>
<tr class="odd">
<td><p>Common HTTP Features</p></td>
<td><p>Static content</p></td>
</tr>
<tr class="even">
<td><p>Common HTTP Features</p></td>
<td><p>HTTP Redirection</p></td>
</tr>
<tr class="odd">
<td><p>Health and Diagnostics</p></td>
<td><p>HTTP Logging</p></td>
</tr>
<tr class="even">
<td><p>Health and Diagnostics</p></td>
<td><p>Logging Tools</p></td>
</tr>
<tr class="odd">
<td><p>Health and Diagnostics</p></td>
<td><p>Request Monitor</p></td>
</tr>
<tr class="even">
<td><p>Health and Diagnostics</p></td>
<td><p>Tracing</p></td>
</tr>
<tr class="odd">
<td><p>Security</p></td>
<td><p>Request Filtering</p></td>
</tr>
<tr class="even">
<td><p>Security</p></td>
<td><p>Basic Authentication</p></td>
</tr>
<tr class="odd">
<td><p>Security</p></td>
<td><p>Client Certificate Mapping Authentication</p></td>
</tr>
<tr class="even">
<td><p>Security</p></td>
<td><p>Windows Authentication</p></td>
</tr>
<tr class="odd">
<td><p>Application Development</p></td>
<td><p>.Net Extensibility 3.5</p></td>
</tr>
<tr class="even">
<td><p>Application Development</p></td>
<td><p>.Net Extensibility 4.5</p></td>
</tr>
<tr class="odd">
<td><p>Application Development</p></td>
<td><p>ASP.Net 3.5</p></td>
</tr>
<tr class="even">
<td><p>Application Development</p></td>
<td><p>ASP.Net 4.5</p></td>
</tr>
<tr class="odd">
<td><p>Application Development</p></td>
<td><p>ISAPI Extensions</p></td>
</tr>
<tr class="even">
<td><p>Application Development</p></td>
<td><p>ISAPI Filters</p></td>
</tr>
<tr class="odd">
<td><p>Application Development</p></td>
<td><p>Server Side Includes</p></td>
</tr>
<tr class="even">
<td><p>Management Tools</p></td>
<td><p>IIS Management Console</p></td>
</tr>
<tr class="odd">
<td><p>Management Tools</p></td>
<td><p>IIS 6 Metabase compatibility</p></td>
</tr>
<tr class="even">
<td><p>Management Tools</p></td>
<td><p>IIS Management Scripts and Tools</p></td>
</tr>
<tr class="odd">
<td><p>.Net 3.5 Framework Features</p></td>
<td><p>.Net 3.5 Framework</p></td>
</tr>
<tr class="even">
<td><p>.Net 4.5 Framework Features</p></td>
<td><p>.Net Framework 4.5</p></td>
</tr>
<tr class="odd">
<td><p>.Net 4.5 Framework Features</p></td>
<td><p>ASP.Net 4.5</p></td>
</tr>
<tr class="even">
<td><p>.Net 4.5 Framework Features</p></td>
<td><p>HTTP Activation</p></td>
</tr>
<tr class="odd">
<td><p>.Net 4.5 Framework Features</p></td>
<td><p>TCP Port Sharing</p></td>
</tr>
<tr class="even">
<td><p>Background Intelligent Transfer Service</p></td>
<td><p>IIS Server Extensions</p></td>
</tr>
<tr class="odd">
<td><p>Ink and Handwriting Services</p></td>
<td><p>Ink and Handwriting Services</p></td>
</tr>
<tr class="even">
<td><p>Media Foundation</p></td>
<td><p>Media Foundation</p></td>
</tr>
<tr class="odd">
<td><p>User Interfaces and Infrastructure</p></td>
<td><p>Graphical Management Tools and Infrastructure</p></td>
</tr>
<tr class="even">
<td><p>User Interfaces and Infrastructure</p></td>
<td><p>Desktop Experience</p></td>
</tr>
<tr class="odd">
<td><p>User Interfaces and Infrastructure</p></td>
<td><p>Server Graphical Shell</p></td>
</tr>
<tr class="even">
<td><p>Windows Identity Foundation 3.5</p></td>
<td><p>Windows Identity Foundation 3.5</p></td>
</tr>
<tr class="odd">
<td><p>Windows Process Activation Service</p></td>
<td><p>Process Model</p></td>
</tr>
<tr class="even">
<td><p>Windows Process Activation Service</p></td>
<td><p>Configuration APIs</p></td>
</tr>
</tbody>
</table>


In Windows Server 2012 and Windows Server 2012 R2, you can use Windows PowerShell 3.0 to install the IIS Requirements. Using the ServerManager module in Windows PowerShell 3.0, type:

   ```
    Import-Module ServerManager
   ```

   ```
    Add-WindowsFeature Web-Server, Web-Static-Content, Web-Default-Doc, Web-Http-Errors, Web-Asp-Net, Web-Net-Ext, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Logging, Web-Log-Libraries, Web-Request-Monitor, Web-Http-Tracing, Web-Basic-Auth, Web-Windows-Auth, Web-Client-Auth, Web-Filtering, Web-Stat-Compression, Web-Dyn-Compression, NET-Framework-45-Core, NET-WCF-HTTP-Activation45, Web-Asp-Net45, Web-Mgmt-Tools, Web-Scripting-Tools, Web-Mgmt-Console, Web-Mgmt-Compat, Windows-Identity-Foundation, Server-Media-Foundation, BITS -Source D:\sources\sxs
   ```

<div class=" ">


> [!IMPORTANT]  
> New with Windows Server 2012 is the –Source parameter that defines where the Windows Server 2012 source media can be found. The media can be defined as a DVD drive (for example, D:\Sources\Sxs), or to a network share that the media files have been copied (for example, \\fileserver\windows2012\sources\Sxs).



</div>

<div>

## See Also


[IIS requirements for Front End pools and Standard Edition servers in Lync Server 2013](lync-server-2013-iis-requirements-for-front-end-pools-and-standard-edition-servers.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

