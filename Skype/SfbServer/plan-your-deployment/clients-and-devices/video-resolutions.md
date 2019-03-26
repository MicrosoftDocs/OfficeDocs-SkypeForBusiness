---
title: "Skype for Business client video resolutions"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 2/16/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Admin
ms.custom:
ms.assetid: 8f68f4c2-3194-487c-bd2f-fbe71ba8ad70
description: "Summary: Review the client video requirements while planning for Skype for Business Server."
---

# Skype for Business client video resolutions
 
**Summary:** Review the client video requirements while planning for Skype for Business Server.
  
This article describes video hardware support for Skype for Business video calls and describes how to determine the expected video quality for various computer, tablet, and mobile device configurations. 
  
IT Professionals will find this information useful in assessing the suitability of laptops already in use in their organization, or under consideration for use. They can also search the [Solutions Catalog](https://partnersolutions.skypeforbusiness.com/solutionscatalog) for information on specific devices.
  
## Windows desktop, Mac and tablet video requirements and capabilities

Skype for Business uses hardware acceleration for video encoding and decoding based on the H.264/MPEG-4 Part 10 Advanced Video Coding standard. This allows computers with lower CPU clock speeds to encode and decode higher resolution video. Video hardware requirements vary depending on the computer configuration and the video resolution wanted.
  
Also see [Windows and Mac hardware requirements](https://products.office.com/en-us/office-system-requirements).
  
### Video hardware requirements

|**Feature**|**Requirement**|
|:-----|:-----|
|Hardware accelerated H.264 decoding using DirectX Video Acceleration (DXVA)  <br/> |• Graphics card must support DirectX 9.0 and must expose the DXVA2_ModeH264_VLD_NoFGT decoding mode and the DirectX 9 API.  <br/> • The latest graphics card driver must be installed.  <br/> |
|Hardware accelerated H.264 encoding: Chipset Requirements  <br/> |The following Intel hardware accelerated video encoding solutions are supported:  <br/> • Second- and third-generation Intel HD Graphics 2000, 2500, 3000, and 4000 chipsets (or later versions) with integrated hardware video encoders. Installation of the Intel HD Graphics driver 15.28.9.2884 or the latest driver containing the following is required:  <br/> • Display driver 9.17.10.2884 or the latest driver  <br/> • Hardware media foundation transform (HMFT) version 3.12.10.31 or the latest HMFT  <br/> The following AMD hardware accelerated video encoding solutions are supported:  <br/> • AMD Video Codec Engine, which is available in several discrete graphics cards and in integrated accelerated processing units of AMD A-Series Accelerated Processors. The AMD Video Codec Engine driver 9.12.0.0 or higher must be installed.  <br/> |
|Hardware accelerated H.264 encoding: Camera Requirements  <br/> |USB video cameras with integrated H.264 hardware encoder that conforms to the USB Video Class (UVC) specification version 1.5.  <br/> **Note:** Skype for Business supports UVC 1.5 cameras with Windows 8 or Windows 8.1, which includes support for UVC 1.5. Because Windows 7 does not include support for UVC 1.5, Skype for Business treats UVC 1.5 cameras as regular cameras with no hardware encoding support. <br/> |
   
### Determining H.264 video encoding and decoding capabilities

Generally, there are four major factors that determine the maximum encoding and decoding capability of a particular computer configuration:
  
- Support for hardware accelerated decoding by using DXVA
    
- Support for hardware accelerated encoding
    
- Number of physical cores
    
- Windows Experience Index (WEI)
    
The Windows System Assessment Tool (WinSAT) determines the WEI. When you run the WinSAT tool, it generates a Formal.Assessment XML document on the computer in the %windir%\Performance\WinSAT\DataStore directory. This XML file contains the following two scores that are of particular importance for determining encoding and decoding capabilities:
  
- The VideoEncodeScore indicates the software-based video encoding capability of the computer.
    
- The GraphicsScore value indicates the hardware accelerated encoding capability of the computer.
    
The following three tables explain the maximum encoding and decoding capability for different PC types depending on what hardware acceleration they support. For resolutions of 640x360 and higher, the maximum supported frame rate is 30 frames per second (fps). For resolutions lower than 640x360, the maximum supported frame rate is 15 fps.
  
**Computer Without DXVA And Without Hardware Accelerated Encoder**

|**Capable Encoder Resolution**|**Capable Decoder Resolution**|**Requirement**|
|:-----|:-----|:-----|
|424x240  <br/> |424x240 (640x360 at 15fps for receive only scenarios)  <br/> |1 Core and VideoEncodeScore ≥ 4.0  <br/> |
|640x360  <br/> |640x360  <br/> |2 Cores and VideoEncodeScore ≥ 4.5  <br/> |
|640x360  <br/> |1280x720  <br/> |2 Cores and VideoEncodeScore ≥ 4.5  <br/> |
|640x360  <br/> |1920x1080  <br/> |4 Cores and VideoEncodeScore ≥ 4.5  <br/> |
|1280x720  <br/> |1280x720  <br/> |4 Cores and VideoEncodeScore ≥ 7.3  <br/> |
|1280x720  <br/> |1920x1080  <br/> |4 Cores and VideoEncodeScore ≥ 7.3  <br/> |
|1920x1080  <br/> |1920x1080  <br/> |N/A  <br/> |
   
**Computer With DXVA But Without Hardware Accelerated Encoder**

|**Capable Encoder Resolution**|**Capable Decoder Resolution**|**Requirement**|
|:-----|:-----|:-----|
|424x240  <br/> |1920x1080  <br/> |1 Core and VideoEncodeScore ≥ 3.0  <br/> |
|640x360  <br/> |1920x1080  <br/> |2 Cores and VideoEncodeScore ≥ 4.5  <br/> |
|960x540  <br/> |1920x1080  <br/> |2 Cores and VideoEncodeScore ≥ 6.0  <br/> |
|1280x720  <br/> |1920x1080  <br/> |4 Cores and VideoEncodeScore ≥ 6.7  <br/> |
|1920x1080  <br/> |1920x1080  <br/> |4 Cores and VideoEncodeScore ≥ 8.2  <br/> |
   
> [!NOTE]
> The WinSAT score on Windows 7 is limited to a maximum of 7.9. Therefore, the encoding capability for a computer without a hardware accelerated encoder can only be achieved on Windows 8 or Windows 8.1, where the maximum WinSAT score is 9.9. 
  
**Computer With DXVA And With Intel HD Graphics Hardware Accelerated Encoder**

|**Capable Encoder Resolution**|**Capable Decoder Resolution**|**Requirement**|
|:-----|:-----|:-----|
|1280x720  <br/> |1920x1080  <br/> |All 2nd and 3rd generation Intel HD Graphics  <br/> |
|1920x1080  <br/> |1920x1080  <br/> |2nd and 3rd generation Intel HD Graphics and GraphicsScore ≥ 5.0  <br/> |
   
## Mobile device video capabilities

The following table describes the maximum video resolutions available on supported mobile devices. For more information about mobile device support, [Mobile client feature comparison for Skype for Business](mobile-feature-comparison.md).
  
|**Feature**|**Windows Phone**|**iPhone**|**iPad**|**Android**|
|:-----|:-----|:-----|:-----|:-----|
|H.264 encoding maximum resolution  <br/> |VGA  <br/> |QVGA: iPhone 4S  <br/> VGA: iPhone 5  <br/> 720p: iPhone 5S and later  <br/> |VGA: iPad 2 and later/iPad mini 1 and later  <br/> 720p: iPad Air/iPad mini 2/iPad Pro and later  <br/> |Up to VGA depending on device model  <br/> |
|H.264 decoding maximum resolution  <br/> |VGA  <br/> |QVGA: iPhone 4S  <br/> VGA: iPhone 5  <br/> 720p: iPhone 5S and later  <br/> |VGA: iPad 2 and later/iPad mini 1 and later  <br/> 720p: iPad Air/iPad mini 2/iPad Pro and later  <br/> |Up to VGA depending on device model  <br/> |
   

