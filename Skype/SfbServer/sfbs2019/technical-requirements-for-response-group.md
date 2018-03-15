---
title: "Technical requirements for Response Group in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 477488bd-124f-437b-9327-732a0d7271ca
description: "In this articleHardware RequirementsSoftware RequirementsPort RequirementsAudio File RequirementsResponse Group Configuration Tool RequirementsResponse Group Agent Console"
---

# Technical requirements for Response Group in Lync Server 2013
[]
 **In this article**
  
[Hardware Requirements](#sectionSection0)
  
[Software Requirements](#sectionSection1)
  
[Port Requirements](#sectionSection2)
  
[Audio File Requirements](#sectionSection3)
  
[Response Group Configuration Tool Requirements](#sectionSection4)
  
[Response Group Agent Console](#sectionSection5)
  
This section describes the following technical requirements for the Response Group application:
  
- Hardware requirements
    
- Software requirements
    
- Port requirements
    
- Audio file requirements
    
- Response Group configuration tool requirements
    
## Hardware Requirements
<a name="sectionSection0"> </a>

The Response Group application has the same hardware requirements as Front End Servers. For details about hardware requirements, see [Server hardware platforms for Lync Server 2013](server-hardware-platforms.md) in the Supportability documentation. 
  
## Software Requirements
<a name="sectionSection1"> </a>

The Response Group application has the same operating system requirements and software prerequisites as Front End Servers. For details about software requirements, see [Server and tools operating system support in Lync Server 2013](server-and-tools-operating-system-support.md) in the Supportability documentation. 
  
If you use Windows Media Audio (.wma) files for Response Group music and announcements, all Front End Servers or Standard Editions servers that run the Response Group application must have the Windows Media Format Runtime installed for servers running Windows Server 2008 R2, or Microsoft Media Foundation for servers running Windows Server 2012 or Windows Server 2012 R2. For Windows Server 2008 R2, Windows Media Format Runtime is installed as part of Windows Desktop Experience.
  
For more details about audio requirements, see "Audio File Requirements" later in this section.
  
## Port Requirements
<a name="sectionSection2"> </a>

The Response Group application uses the following ports:
  
- **Port 5071** Used for SIP listening requests 
    
- **Port 8404** Used for interserver communications 
    
    > [!NOTE]
    > This port is used for the Match Making service and is required when the Response Group application is deployed in a pool that has more than one Front End Server. 
  
> [!NOTE]
> These ports are default settings that you can change by using the **Set-CsApplicationServer** cmdlet. For details about this cmdlet, see the Lync Server Management Shell documentation. 
  
## Audio File Requirements
<a name="sectionSection3"> </a>

The Response Group application supports wave (.wav) file format and Windows Media audio (.wma) file format for Response Group messages, on-hold music, or interactive voice response (IVR) questions.
  
The Windows Media audio file format requires that the Windows Media Format Runtime is installed on Front End Servers running Windows Server 2008 R2 and Windows Server 2008. For more details, see "Software Requirements" earlier in this section.
  
### Supported Wave File Formats

All wave files must meet the following requirements:
  
- 8-bit or 16-bit file
    
- Linear pulse code modulation (LPCM), A-Law, or mu-Law format
    
- Mono or stereo
    
- 4MB or less
    
For the best performance of wave files, a 16 kHz, mono, 16-bit Wave file is recommended. 
  
### Supported Windows Media Audio File Formats

If you use a Windows Media audio file, consider using low bit rates, and verify the performance of your system under load.
  
You can use the Microsoft Expression Encoder 4 to convert a file to the Windows Media Audio format. To download Expression Encoder 4, see [https://go.microsoft.com/fwlink/p/?linkId=202843](https://go.microsoft.com/fwlink/p/?linkId=202843).
  
## Response Group Configuration Tool Requirements
<a name="sectionSection4"> </a>

The Response Group Configuration Tool supports the combinations of operating systems and web browsers described in the following table.
  
> [!NOTE]
> 32-bit or 64-bit versions of the operating systems are supported. Only 32-bit versions of Internet Explorer are supported. 
  
**Supported Operating Systems and Web Browsers**

|**Operating system**|**Web browser**|
|:-----|:-----|
|Windows Vista with Service Pack (SP) 2  <br/> |Internet Explorer 7  <br/> Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> |
|Windows 7  <br/> Windows 7 with Service Pack 1  <br/> |Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> |
|Windows Server 2008 with Service Pack 2  <br/> |Internet Explorer 7  <br/> Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> |
|Windows Server 2008 R2  <br/> Windows Server 2008 R2 with Service Pack 1  <br/> |Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> |
   
## Response Group Agent Console
<a name="sectionSection5"> </a>

The agent console supports the combinations of operating systems and web browsers described in the following table.
  
> [!NOTE]
> 32-bit or 64-bit versions of the operating systems are supported. Only 32-bit versions of Internet Explorer are supported. 
  
**Supported Operating Systems and Web Browsers**

|**Operating system**|**Web browser**|
|:-----|:-----|
|Windows Vista with Service Pack (SP) 2  <br/> |Internet Explorer 7  <br/> Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> |
|Windows 7  <br/> Windows 7 with Service Pack 1  <br/> |Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> Firefox 10.0  <br/> Chrome 18.0  <br/> |
|Windows Server 2008 with Service Pack 2  <br/> |Internet Explorer 7  <br/> Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> |
|Windows Server 2008 R2  <br/> Windows Server 2008 R2 with Service Pack 1  <br/> |Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> Firefox 10.0  <br/> Chrome 18.0  <br/> |
||
   

