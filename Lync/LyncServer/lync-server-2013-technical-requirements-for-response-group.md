---
title: 'Lync Server 2013: Technical requirements for Response Group'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Technical requirements for Response Group
ms:assetid: 477488bd-124f-437b-9327-732a0d7271ca
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204863(v=OCS.15)
ms:contentKeyID: 48184044
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Technical requirements for Response Group in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-07_

This section describes the following technical requirements for the Response Group application:

  - Hardware requirements

  - Software requirements

  - Port requirements

  - Audio file requirements

  - Response Group configuration tool requirements

<div>

## Hardware Requirements

The Response Group application has the same hardware requirements as Front End Servers. For details about hardware requirements, see [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md) in the Supportability documentation.

</div>

<div>

## Software Requirements

The Response Group application has the same operating system requirements and software prerequisites as Front End Servers. For details about software requirements, see [Server and tools operating system support in Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) in the Supportability documentation.

If you use Windows Media Audio (.wma) files for Response Group music and announcements, all Front End Servers or Standard Editions servers that run the Response Group application must have the Windows Media Format Runtime installed for servers running Windows Server 2008 R2, or Microsoft Media Foundation for servers running Windows Server 2012 or Windows Server 2012 R2. For Windows Server 2008 R2, Windows Media Format Runtime is installed as part of Windows Desktop Experience.

For more details about audio requirements, see "Audio File Requirements" later in this section.

</div>

<div>

## Port Requirements

The Response Group application uses the following ports:

  - **Port 5071**   Used for SIP listening requests

  - **Port 8404**   Used for interserver communications
    
    <div>
    

    > [!NOTE]  
    > This port is used for the Match Making service and is required when the Response Group application is deployed in a pool that has more than one Front End Server.

    
    </div>

<div>


> [!NOTE]  
> These ports are default settings that you can change by using the <STRONG>Set-CsApplicationServer</STRONG> cmdlet. For details about this cmdlet, see the Lync Server Management Shell documentation.



</div>

</div>

<div>

## Audio File Requirements

The Response Group application supports wave (.wav) file format and Windows Media audio (.wma) file format for Response Group messages, on-hold music, or interactive voice response (IVR) questions.

The Windows Media audio file format requires that the Windows Media Format Runtime is installed on Front End Servers running Windows Server 2008 R2 and Windows Server 2008. For more details, see "Software Requirements" earlier in this section.

<div>

## Supported Wave File Formats

All wave files must meet the following requirements:

  - 8-bit or 16-bit file

  - Linear pulse code modulation (LPCM), A-Law, or mu-Law format

  - Mono or stereo

  - 4MB or less

For the best performance of wave files, a 16 kHz, mono, 16-bit Wave file is recommended.

</div>

<div>

## Supported Windows Media Audio File Formats

If you use a Windows Media audio file, consider using low bit rates, and verify the performance of your system under load.

You can use the Microsoft Expression Encoder 4 to convert a file to the Windows Media Audio format. To download Expression Encoder 4, see [http://go.microsoft.com/fwlink/p/?linkId=202843](http://go.microsoft.com/fwlink/p/?linkid=202843).

</div>

</div>

<div>

## Response Group Configuration Tool Requirements

The Response Group Configuration Tool supports the combinations of operating systems and web browsers described in the following table.

<div>


> [!NOTE]  
> 32-bit or 64-bit versions of the operating systems are supported. Only 32-bit versions of Internet Explorer are supported.



</div>

### Supported Operating Systems and Web Browsers

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Operating system</th>
<th>Web browser</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Vista with Service Pack (SP) 2</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8 (native mode)</p>
<p>Internet Explorer 9 (native mode)</p></td>
</tr>
<tr class="even">
<td><p>Windows 7</p>
<p>Windows 7 with Service Pack 1</p></td>
<td><p>Internet Explorer 8 (native mode)</p>
<p>Internet Explorer 9 (native mode)</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2008 with Service Pack 2</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8 (native mode)</p>
<p>Internet Explorer 9 (native mode)</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2008 R2</p>
<p>Windows Server 2008 R2 with Service Pack 1</p></td>
<td><p>Internet Explorer 8 (native mode)</p>
<p>Internet Explorer 9 (native mode)</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Response Group Agent Console

The agent console supports the combinations of operating systems and web browsers described in the following table.

<div>


> [!NOTE]  
> 32-bit or 64-bit versions of the operating systems are supported. Only 32-bit versions of Internet Explorer are supported.



</div>

### Supported Operating Systems and Web Browsers

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Operating system</th>
<th>Web browser</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Vista with Service Pack (SP) 2</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8 (native mode)</p>
<p>Internet Explorer 9 (native mode)</p></td>
</tr>
<tr class="even">
<td><p>Windows 7</p>
<p>Windows 7 with Service Pack 1</p></td>
<td><p>Internet Explorer 8 (native mode)</p>
<p>Internet Explorer 9 (native mode)</p>
<p>Firefox 10.0</p>
<p>Chrome 18.0</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2008 with Service Pack 2</p></td>
<td><p>Internet Explorer 7</p>
<p>Internet Explorer 8 (native mode)</p>
<p>Internet Explorer 9 (native mode)</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2008 R2</p>
<p>Windows Server 2008 R2 with Service Pack 1</p></td>
<td><p>Internet Explorer 8 (native mode)</p>
<p>Internet Explorer 9 (native mode)</p>
<p>Firefox 10.0</p>
<p>Chrome 18.0</p></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

