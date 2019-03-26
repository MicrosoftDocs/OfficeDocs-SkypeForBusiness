---
title: 'Lync Server 2013: Lync client video requirements'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Lync client video requirements
ms:assetid: 8f68f4c2-3194-487c-bd2f-fbe71ba8ad70
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688132(v=OCS.15)
ms:contentKeyID: 49733731
ms.date: 01/29/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Lync client video requirements for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-01-29_

This section describes video hardware support for Lync 2013 video calls and describes how to determine the expected video quality for various computer, tablet, and mobile device configurations.

<div>

## Windows Desktop and Tablet Video Requirements and Capabilities

Lync 2013 introduces hardware acceleration for video encoding and decoding based on the H.264/MPEG-4 Part 10 Advanced Video Coding standard. This feature allows computers with lower CPU clock speeds to encode and decode higher resolution video. Video hardware requirements vary depending on the computer configuration and the video resolution wanted.

<div>

## Video Hardware Requirements


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Requirement</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Hardware accelerated H.264 decoding using DirectX Video Acceleration (DXVA)</p></td>
<td><ul>
<li><p>Graphics card must support DirectX 9.0 and must expose the DXVA2_ModeH264_VLD_NoFGT decoding mode.</p></li>
<li><p>The latest graphics card driver must be installed.</p></li>
</ul>
<div>

> [!NOTE]  
> For details about decoding modes, see <A href="http://go.microsoft.com/fwlink/p/?linkid=268530">http://go.microsoft.com/fwlink/p/?LinkId=268530</A>.


</div></td>
</tr>
<tr class="even">
<td><p>Hardware accelerated H.264 encoding: Chipset Requirements</p></td>
<td><p>The following Intel hardware accelerated video encoding solutions are supported:</p>
<ul>
<li><p>Second and third generation Intel HD Graphics 2000, 2500, 3000, and 4000 chipsets (or later versions) with integrated hardware video encoders. Installation of the Intel HD Graphics driver 15.28.9.2884 or the latest driver containing the following is required:</p>
<ul>
<li><p>Display driver 9.17.10.2884 or the latest driver</p></li>
<li><p>Hardware media foundation transform (HMFT) version 3.12.10.31 or the latest HMFT</p></li>
</ul></li>
</ul>
<p>The following AMD hardware accelerated video encoding solutions are supported (requires CU1 Updates for Lync Server 2013):</p>
<ul>
<li><p>AMD Video Codec Engine, which is available in several discrete graphics cards and in integrated accelerated processing units of AMD A-Series Accelerated Processors. The AMD Video Codec Engine driver 9.12.0.0 or higher must be installed.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Hardware accelerated H.264 encoding: Camera Requirements</p></td>
<td><p>USB video cameras with integrated H.264 hardware encoder that conforms to the USB Video Class (UVC) specification version 1.5.</p>
<div>

> [!NOTE]  
> Lync 2013 supports UVC 1.5 cameras with Windows 8 or Windows 8.1, which includes support for UVC 1.5. Because Windows 7 does not include support for UVC 1.5, Lync 2013 treats UVC 1.5 cameras as regular cameras with no hardware encoding support.


</div></td>
</tr>
</tbody>
</table>


</div>

<div>

## Determining H.264 Video Encoding and Decoding Capabilities

Generally, there are four major factors that determine the maximum encoding and decoding capability of a particular computer configuration:

  - Support for hardware accelerated decoding by using DXVA

  - Support for hardware accelerated encoding

  - Number of physical cores

  - Windows Experience Index (WEI)

The Windows System Assessment Tool (WinSAT) determines the WEI. When you run the WinSAT tool, it generates a Formal.Assessment XML document on the computer in the %windir%\\Performance\\WinSAT\\DataStore directory. This XML file contains the following two scores that are of particular importance for determining encoding and decoding capabilities:

  - The VideoEncodeScore indicates the software-based video encoding capability of the computer.

  - The GraphicsScore value indicates the hardware accelerated encoding capability of the computer.

The following three tables explain the maximum encoding and decoding capability for different PC types depending on what hardware acceleration they support. For resolutions of 640x360 and higher, the maximum supported frame rate is 30 frames per second (fps). For resolutions lower than 640x360, the maximum supported frame rate is 15 fps.

### Computer Without DXVA And Without Hardware Accelerated Encoder

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Capable Encoder Resolution</th>
<th>Capable Decoder Resolution</th>
<th>Requirement</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>424x240</p></td>
<td><p>424x240 (640x360 at 15fps for receive only scenarios)</p></td>
<td><p>1 Core and VideoEncodeScore ≥ 4.0</p></td>
</tr>
<tr class="even">
<td><p>640x360</p></td>
<td><p>640x360</p></td>
<td><p>2 Cores and VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="odd">
<td><p>640x360</p></td>
<td><p>1280x720</p></td>
<td><p>2 Cores and VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="even">
<td><p>640x360</p></td>
<td><p>1920x1080</p></td>
<td><p>4 Cores and VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="odd">
<td><p>1280x720</p></td>
<td><p>1280x720</p></td>
<td><p>4 Cores and VideoEncodeScore ≥ 7.3</p></td>
</tr>
<tr class="even">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>4 Cores and VideoEncodeScore ≥ 7.3</p></td>
</tr>
<tr class="odd">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>N/A</p></td>
</tr>
</tbody>
</table>


### Computer With DXVA But Without Hardware Accelerated Encoder

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Capable Encoder Resolution</th>
<th>Capable Decoder Resolution</th>
<th>Requirement</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>424x240</p></td>
<td><p>1920x1080</p></td>
<td><p>1 Core and VideoEncodeScore ≥ 3.0</p></td>
</tr>
<tr class="even">
<td><p>640x360</p></td>
<td><p>1920x1080</p></td>
<td><p>2 Cores and VideoEncodeScore ≥ 4.5</p></td>
</tr>
<tr class="odd">
<td><p>960x540</p></td>
<td><p>1920x1080</p></td>
<td><p>2 Cores and VideoEncodeScore ≥ 6.0</p></td>
</tr>
<tr class="even">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>4 Cores and VideoEncodeScore ≥ 6.7</p></td>
</tr>
<tr class="odd">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>4 Cores and VideoEncodeScore ≥ 8.2</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> The WinSAT score on Windows 7 is limited to a maximum of 7.9. Therefore, the encoding capability for a computer without a hardware accelerated encoder can only be achieved on Windows 8 or Windows 8.1, where the maximum WinSAT score is 9.9.



</div>

### Computer With DXVA And With Intel HD Graphics Hardware Accelerated Encoder

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Capable Encoder Resolution</th>
<th>Capable Decoder Resolution</th>
<th>Requirement</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1280x720</p></td>
<td><p>1920x1080</p></td>
<td><p>All 2nd and 3rd generation Intel HD Graphics</p></td>
</tr>
<tr class="even">
<td><p>1920x1080</p></td>
<td><p>1920x1080</p></td>
<td><p>2nd and 3rd generation Intel HD Graphics and GraphicsScore ≥ 5.0</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<div>

## Mobile Device Video Capabilities

The following table describes the maximum video capabilities for supported mobile devices. For more information about mobile device support, see [Planning for mobile clients in Lync Server 2013](lync-server-2013-planning-for-mobile-clients.md).


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Windows Phone</th>
<th>iPhone</th>
<th>iPad</th>
<th>Android</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>H.264 encoding maximum resolution</p></td>
<td><p>VGA</p></td>
<td><p>QVGA: iPhone 4S</p>
<p>VGA: iPhone 5</p>
<p>720p: iPhone 5S and later</p></td>
<td><p>VGA: iPad 2 and later/iPad mini 1 and later</p>
<p>720p: iPad Air/iPad mini 2/iPad Pro and later</p></td>
<td><p>Up to VGA depending on device model</p></td>
</tr>
<tr class="even">
<td><p>H.264 decoding maximum resolution</p></td>
<td><p>VGA</p></td>
<td><p>QVGA: iPhone 4S</p>
<p>VGA: iPhone 5</p>
<p>720p: iPhone 5S and later</p></td>
<td><p>VGA: iPad 2 and later/iPad mini 1 and later</p>
<p>720p: iPad Air/iPad mini 2/iPad Pro and later</p></td>
<td><p>Up to VGA depending on device model</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

