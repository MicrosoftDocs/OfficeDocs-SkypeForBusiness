---
title: 'IIS requirements for Front End pools and Standard Edition servers'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: IIS requirements for Front End pools and Standard Edition servers
ms:assetid: e8a6c7ac-b6d5-4c7e-abe9-d8ea5eedbc62
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399038(v=OCS.15)
ms:contentKeyID: 48185888
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# IIS requirements for Front End pools and Standard Edition servers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-19_

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
> If your organization requires that you locate IIS and all Web Services on a drive other than the system drive, you can change the installation location path for the Lync Server files in the Setup dialog box. If you install the Setup files to this path, including OCSCore.msi, the rest of the Lync Server files will be deployed to this drive as well. For details about how to relocate the INETPUB deployed by Windows Server Manager when installing IIS, see <A href="http://go.microsoft.com/fwlink/p/?linkid=216888">http://go.microsoft.com/fwlink/p/?linkId=216888</A>.


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

### Virtual Directories for Internal Access

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Virtual directory URI</th>
<th>Refers to</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Address Book Server</p></td>
<td><p>https://&lt;Internal FQDN&gt;/ABS/int/Handler</p></td>
<td><p>Location of Address Book Server download files for internal users.</p></td>
</tr>
<tr class="even">
<td><p>Autodiscover Service</p></td>
<td><p>https://&lt;Internal FQDN&gt;/Autodiscover</p></td>
<td><p>Location of the Lync Server Autodiscover Service that locates mobility resources for internal mobile device users.</p></td>
</tr>
<tr class="odd">
<td><p>Client updates</p></td>
<td><p>http://&lt;Internal FQDN&gt;/AutoUpdate/Int</p></td>
<td><p>Location of update files for internal computer-based clients.</p></td>
</tr>
<tr class="even">
<td><p>Conf</p></td>
<td><p>http://&lt;Internal FQDN&gt;/Conf/Int</p></td>
<td><p>Location of conferencing resources for internal users.</p></td>
</tr>
<tr class="odd">
<td><p>Device updates</p></td>
<td><p>http://&lt;Internal FQDN&gt;/DeviceUpdateFiles_Int</p></td>
<td><p>Location of unified communications (UC) device update files for internal UC devices.</p></td>
</tr>
<tr class="even">
<td><p>Meeting</p></td>
<td><p>http://&lt;Internal FQDN&gt;/etc/place/null</p></td>
<td><p>Location of meeting content for internal users.</p></td>
</tr>
<tr class="odd">
<td><p>Mobility Service</p></td>
<td><p>https://&lt;Internal FQDN&gt;/Mcx</p></td>
<td><p>Location of Mobility Service resources for internal mobile device users.</p></td>
</tr>
<tr class="even">
<td><p>Group Expansion and Address Book Web Query service</p></td>
<td><p>http://&lt;Internal FQDN&gt;/GroupExpansion/int/service.asmx</p></td>
<td><p>Location of the Web service that enables group expansion for internal users. Also, the location of the Address Book Web Query service that provides global address list information to internal Lync Mobile Microsoft Lync 2010 Mobile clients.</p></td>
</tr>
<tr class="odd">
<td><p>Phone Conferencing</p></td>
<td><p>http://&lt;Internal FQDN&gt;/PhoneConferencing/Int</p></td>
<td><p>Location of phone conferencing data for internal users.</p></td>
</tr>
<tr class="even">
<td><p>Device updates</p></td>
<td><p>http://&lt;Internal FQDN&gt;/RequestHandler</p></td>
<td><p>Location of the Device Update Web service Request Handler that enables internal UC devices to upload logs and check for updates.</p></td>
</tr>
<tr class="odd">
<td><p>Response Group application</p></td>
<td><p>http://&lt;Internal FQDN&gt;/RgsConfig</p>
<p>http://&lt;Internal FQDN&gt;/RgsClients</p></td>
<td><p>Location of Response Group Configuration Tool.</p></td>
</tr>
</tbody>
</table>


> [!NOTE]
> For Front End pools in a consolidated configuration, you must deploy IIS before you can add servers to the pool.


<table>
<thead>
<tr class="header">
<th><img src="images/Gg398321.security(OCS.15).gif" title="security" alt="security" />Security Note:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>You must use the IIS administrative snap-in to assign the certificate used by the IIS web component server.</td>
</tr>
</tbody>
</table>



</div>

<span> </span>

</div>

</div>

</div>

