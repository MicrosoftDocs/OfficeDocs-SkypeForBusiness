---
title: "Technical requirements for Call Park in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 38bcf302-2b72-4492-9266-f6dc31b566e1
description: "In this articleHardware RequirementsSoftware RequirementsPort RequirementsAudio File Requirements"
---

# Technical requirements for Call Park in Lync Server 2013
[]
 **In this article**
  
[Hardware Requirements](#sectionSection0)
  
[Software Requirements](#sectionSection1)
  
[Port Requirements](#sectionSection2)
  
[Audio File Requirements](#sectionSection3)
  
This section describes the following technical requirements for Call Park:
  
- Hardware requirements
    
- Software requirements
    
- Port requirements
    
- Audio file requirements
    
## Hardware Requirements
<a name="sectionSection0"> </a>

The Call Park application has the same hardware requirements as Front End Servers. For details about hardware requirements, see [Server hardware platforms for Lync Server 2013](server-hardware-platforms.md) in the Supportability documentation. 
  
## Software Requirements
<a name="sectionSection1"> </a>

The Call Park application has the same operating system requirements and software prerequisites as Front End Servers. For details about software requirements, see [Server and tools operating system support in Lync Server 2013](server-and-tools-operating-system-support.md) in the Supportability documentation. 
  
All Front End Servers and Standard Edition servers where the Call Park application is deployed must have the Windows Media Format Runtime installed for servers running Windows Server 2008 R2, or Microsoft Media Foundation for servers running Windows Server 2012 or Windows Server 2012 R2. For Windows Server 2008 R2, Windows Media Format Runtime is installed as part of Windows Desktop Experience. Windows Media Format Runtime or Microsoft Media Foundation is required for Windows Media Audio (.wma) files that Call Park plays for music on hold.
  
## Port Requirements
<a name="sectionSection2"> </a>

The Call Park application uses the following port:
  
- **Port 5075** Used for SIP listening requests. 
    
> [!NOTE]
> This port is a default setting that you can change by using the **Set-CsApplicationServer** cmdlet. For details about this cmdlet, see the Lync Server Management Shell documentation. 
  
## Audio File Requirements
<a name="sectionSection3"> </a>

The Call Park application supports only Windows Media Audio (.wma) files for music on hold. You can use the Microsoft Expression Encoder 4 to customize files for music on hold. To download Expression Encoder 4, see "Expression Encoder 4" at [https://go.microsoft.com/fwlink/p/?linkId=202843](https://go.microsoft.com/fwlink/p/?linkId=202843). Use the tool to convert the file to a .wma format. The recommended format for Call Park music-on-hold files is Media Audio 9, 44 kHz, 16 bits, Mono, CBR, 32 kbps.
  
> [!NOTE]
> The converted file plays over the phone only at 16 kHz, even if it was recorded at 44 kHz. 
  

