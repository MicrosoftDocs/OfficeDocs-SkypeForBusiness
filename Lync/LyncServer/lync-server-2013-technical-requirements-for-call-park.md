---
title: 'Lync Server 2013: Technical requirements for Call Park'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Technical requirements for Call Park
ms:assetid: 38bcf302-2b72-4492-9266-f6dc31b566e1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204818(v=OCS.15)
ms:contentKeyID: 48183897
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Technical requirements for Call Park in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-07_

This section describes the following technical requirements for Call Park:

  - Hardware requirements

  - Software requirements

  - Port requirements

  - Audio file requirements

<div>

## Hardware Requirements

The Call Park application has the same hardware requirements as Front End Servers. For details about hardware requirements, see [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md) in the Supportability documentation.

</div>

<div>

## Software Requirements

The Call Park application has the same operating system requirements and software prerequisites as Front End Servers. For details about software requirements, see [Server and tools operating system support in Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) in the Supportability documentation.

All Front End Servers and Standard Edition servers where the Call Park application is deployed must have the Windows Media Format Runtime installed for servers running Windows Server 2008 R2, or Microsoft Media Foundation for servers running Windows Server 2012 or Windows Server 2012 R2. For Windows Server 2008 R2, Windows Media Format Runtime is installed as part of Windows Desktop Experience. Windows Media Format Runtime or Microsoft Media Foundation is required for Windows Media Audio (.wma) files that Call Park plays for music on hold.

</div>

<div>

## Port Requirements

The Call Park application uses the following port:

  - **Port 5075**   Used for SIP listening requests.

<div>


> [!NOTE]  
> This port is a default setting that you can change by using the <STRONG>Set-CsApplicationServer</STRONG> cmdlet. For details about this cmdlet, see the Lync Server Management Shell documentation.



</div>

</div>

<div>

## Audio File Requirements

The Call Park application supports only Windows Media Audio (.wma) files for music on hold. You can use the Microsoft Expression Encoder 4 to customize files for music on hold. To download Expression Encoder 4, see "Expression Encoder 4" at [http://go.microsoft.com/fwlink/p/?linkId=202843](http://go.microsoft.com/fwlink/p/?linkid=202843). Use the tool to convert the file to a .wma format. The recommended format for Call Park music-on-hold files is Media Audio 9, 44 kHz, 16 bits, Mono, CBR, 32 kbps.

<div>


> [!NOTE]  
> The converted file plays over the phone only at 16 kHz, even if it was recorded at 44 kHz.



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

