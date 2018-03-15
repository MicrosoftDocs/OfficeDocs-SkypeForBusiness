---
title: "Supported virtualization technologies and known limitations in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 2/6/2017
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6d3d749d-e840-4c05-afae-d6e69e7616aa
description: "The Lync VDI plug-in allows audio and video calling for supported virtualization technologies. This extends the functionality outlined for Microsoft Lync Server 2010 in the Client Virtualization in Microsoft Lync 2010 white paper. In compliance with standard telephone regulations, support for E911 is also included. The following sections describe the virtualization technologies that are supported by the Lync VDI plug-in and the known feature limitations."
---

# Supported virtualization technologies and known limitations in Lync Server 2013
[]
The Lync VDI plug-in allows audio and video calling for supported virtualization technologies. This extends the functionality outlined for Microsoft Lync Server 2010 in the [Client Virtualization in Microsoft Lync 2010](https://go.microsoft.com/fwlink/?LinkId=330447) white paper. In compliance with standard telephone regulations, support for E911 is also included. The following sections describe the virtualization technologies that are supported by the Lync VDI plug-in and the known feature limitations. 
  
## Support for Virtualization Technologies

The Lync VDI plug-in supports full desktop remoting in the personal virtual desktop scenario, but not in the remote desktop session scenario. These scenarios can be described as follows:
  
- **Supported: Personalized Virtual Desktops or Virtual Desktop Infrastructure (VDI).** In this scenario, each user logs on to a customizable virtual desktop and is able to save files on the desktop that persist across sessions. Microsoft Remote Desktop Services, VMware Horizon View, and Citrix XenDesktop are implementations that have been tested for use with Lync. For information about vendor-specific VDI environments and client hardware that have been tested by Microsoft, see [Infrastructure qualified for Microsoft Lync](https://go.microsoft.com/fwlink/?LinkID=313435).
    
- **Not supported: Remote Desktop Sessions.** In this scenario, each user logs on to a generic virtual desktop session that cannot be customized. Example implementations include Microsoft Remote Desktop Sessions (RDSH) and Citrix XenApp combined with Citrix Receiver. 
    
The Lync VDI plug-in does not support other virtualization technologies, such as application virtualization, which allows the use of an application without requiring installation of the full application locally. Example implementations include Citrix XenApp and Microsoft Application Virtualization (App-V). Application streaming, application remoting, and mixed virtualization modes (for example, application remoting in full desktop remoting) are not supported.
  
To allow extensibility, the Lync VDI plug-in was designed to use platform-independent APIs called Dynamic Virtual Channels (DVCs). For scenarios that are not explicitly supported by Lync, refer to support statements from the VDI solution provider.
  
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
    

