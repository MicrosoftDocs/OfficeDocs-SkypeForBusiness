---
title: 'Lync Server 2013: Supported virtualization technologies and known limitations'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Supported virtualization technologies and known limitations
ms:assetid: 6d3d749d-e840-4c05-afae-d6e69e7616aa
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204982(v=OCS.15)
ms:contentKeyID: 48184428
ms.date: 02/07/2017
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Supported virtualization technologies and known limitations in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2017-02-06_

The Lync VDI plug-in allows audio and video calling for supported virtualization technologies. This extends the functionality outlined for Microsoft Lync Server 2010 in the [Client Virtualization in Microsoft Lync 2010](https://go.microsoft.com/fwlink/?linkid=330447) white paper. In compliance with standard telephone regulations, support for E911 is also included. The following sections describe the virtualization technologies that are supported by the Lync VDI plug-in and the known feature limitations.

<div>

## Support for Virtualization Technologies

The Lync VDI plug-in supports full desktop remoting in the personal virtual desktop scenario, but not in the remote desktop session scenario. These scenarios can be described as follows:

  - **Supported: Personalized Virtual Desktops or Virtual Desktop Infrastructure (VDI).**   In this scenario, each user logs on to a customizable virtual desktop and is able to save files on the desktop that persist across sessions. Microsoft Remote Desktop Services, VMware Horizon View, and Citrix XenDesktop are implementations that have been tested for use with Lync. For information about vendor-specific VDI environments and client hardware that have been tested by Microsoft, see [Infrastructure qualified for Microsoft Lync](https://go.microsoft.com/fwlink/?linkid=313435).

  - **Not supported: Remote Desktop Sessions.**   In this scenario, each user logs on to a generic virtual desktop session that cannot be customized. Example implementations include Microsoft Remote Desktop Sessions (RDSH) and Citrix XenApp combined with Citrix Receiver.

The Lync VDI plug-in does not support other virtualization technologies, such as application virtualization, which allows the use of an application without requiring installation of the full application locally. Example implementations include Citrix XenApp and Microsoft Application Virtualization (App-V). Application streaming, application remoting, and mixed virtualization modes (for example, application remoting in full desktop remoting) are not supported.

To allow extensibility, the Lync VDI plug-in was designed to use platform-independent APIs called Dynamic Virtual Channels (DVCs). For scenarios that are not explicitly supported by Lync, refer to support statements from the VDI solution provider.

</div>

<div>

## Known Feature Limitations

The following are known limitations when you use Lync 2013 in a VDI environment:

  - There is limited support for Call Delegation and Response Group Agent Anonymization features.

  - There is no support for the following features:
    
      - Integrated Audio Device and Video Device tuning pages.
    
      - Multiple-view video.
    
      - Recording of conversations.
    
      - Remote Desktop Services (RDS).
    
      - Joining meetings anonymously (that is, joining Lync meetings hosted by an organization that does not federate with your organization).
    
      - Using the Lync VDI plug-in along with a Lync Phone Edition device.
    
      - Call continuity in case of a network outage.
    
      - Customized ringtones and music-on-hold features.

  - The Lync VDI plug-in is not supported in an Office 365 environment.

</div>

</div>

<span> </span>

</div>

</div>

</div>

