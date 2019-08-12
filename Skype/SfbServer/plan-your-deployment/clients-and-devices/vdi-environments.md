---
title: "Plan for Skype for Business in VDI environments"
author: lanachin
ms.author: v-lanac
ms.reviewer: krishra
manager: serdars
ms.date: 1/9/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Admin
ms.custom:
ms.assetid: ea68414b-bb7e-483a-b731-b6b5a44372b1
description: "This topic discusses planning considerations for using Skype for Business while connecting to a remote virtual desktop."
---

# Plan for Skype for Business in VDI environments
 
This topic discusses planning considerations for using Skype for Business while connecting to a remote virtual desktop. 
  
A Virtual Desktop Infrastructure (VDI) environment is used in some organizations where security and compliance issues are especially sensitive. Their users do their work on a virtual desktop with all their desktop applications and files using Remote Desktop Services or a similar remote connection. Using Skype for Business with full audio and video on a connection like that requires heavy loads of audio and video processing on the client homed on a virtual desktop. Additional VDI plug-in software is available that offloads that processing to the end user's local machine, and reduces the load on the virtual desktop.
  
There are three solutions available for the VDI plug-in component, offered by Microsoft, Citrix, or VMWare. For new deployments, Microsoft recommends using either the Citrix HDX RealTime Optimization Pack solution or the VMWare Horizon Virtualization Pack. The original Lync VDI Plug-in is still supported for the remainder of its lifecycle.
  
- The **Lync VDI plug-in** was developed for Lync 2013 and is compatible with either the Lync 2013 or Skype for Business 2015 client running on a virtual desktop. It's a stand-alone application that installs on the local computer and allows the use of local audio and video devices with a client on a virtual desktop. The plug-in does not require a Skype for Business client to be installed on the local computer or thin client, which must run Windows 7, Windows 8, or Windows Server 2008 operating systems. (Thin client devices using these operating systems and supported by Microsoft include: Dell Wyse Z90D7, Dell Wyse R90L7, Dell Wyse X90m7, HP t610 and HP t5740e.) This plug-in is still supported, but no future updates are planned. For Citrix-based virtual environments, the Citrix RealTime Optimization Pack is recommended.
    
- The **Citrix RealTime Optimization Pack** builds on the Lync VDI plug-in and works with Lync 2013 or Skype for Business 2016 clients on a virtual desktop. It was co-developed by Citrix and Microsoft to improve upon the original VDI Plug-in. It can be installed on clients with Windows and non-Windows operating systems (including Windows 10, Mac and Linux). It consists of two components: the RealTime Connector (which is installed on the virtual desktop) and the RealTime Media Engine (which is installed on the end user's local machine). These two components allow the user's local computer to use the Skype for Business client running on the virtual desktop with the A/V processing moved to the local computer. For Citrix-based virtual desktop environments, the Citrix RealTime Optimization Pack is recommended, and further support is planned.
    
- The **VMWare Horizon Virtualization Pack** for Skype for Business, developed in collaboration with VMWare, allows you to deliver Skype for Business in a virtual desktop while delivering a great user experience. The solution works by leveraging a media engine at the client to create an optimized solution, with the client endpoint providing media offload capabilities for audio and video calls. This solution that can deliver audio and video either directly between endpoints for one-on-one collaboration, or offload it to a central Multipoint Control Unit (MCU) for multiparty conference calls or meetings.
    
> [!NOTE]
> The Skype for Business Basic clients are not supported with the Citrix HDX RealTime Optimization Pack or the VMWare Horizon Virtualization Pack. 
  
## Citrix HDX RealTime Optimization Pack
<a name="Citrix_RT"> </a>

Citrix's VDI environment plugin (a feature of XenApp and XenDesktop) is compatible with Lync 2013 and Skype for Business 2015 and 2016 (Full clients using any click to run installer, or MSI installers released after January 2017 PU) clients installed on a virtual desktop. Its overall functioning is based on the Microsoft Lync VDI plug-in, but works on a wider variety of client operating systems, including Windows 10, Macintosh, and Linux.
  
A full list of features and supported technologies can be found on the Citrix website at [Delivering Microsoft Skype for Business to XenApp and XenDesktop Users](https://www.citrix.com/content/dam/citrix/en_us/documents/products-solutions/delivering-microsoft-lync-to-xenapp-and-xendesktop-users.pdf).
  
Review the following links for more information:
  
- Citrix [HDX RealTime Optimization Pack 2.1](https://docs.citrix.com/en-us/hdx-optimization/2-1.mdl)
    
- [Technical Overview](https://docs.citrix.com/en-us/hdx-optimization/2-1/about.mdl)
    
- [CTX200279 Skype for Business Feature Support](https://support.citrix.com/article/CTX200279)
    
## VMWare Horizon Virtualization Pack
<a name="Citrix_RT"> </a>

VMWare's VDI environment solution is compatible with Skype for Business 2015 and 2016 Full clients installed on a virtual desktop. Its overall functioning is based on the Microsoft Lync VDI plug-in, but works on a wider variety of client operating systems, including Windows 10, Macintosh, and Linux. 
  
A full discussion of features and supported technologies can be found on the VMWare website at the following links:
  
- [What's New in VMware Horizon 7.4 &amp; Horizon Client 4.7](https://blogs.vmware.com/euc/2018/01/vmware-horizon-7-4-horizon-client-4-7-whats-new.mdl)
    
- [Horizon Virtualization Pack for Skype for Business](https://www.vmware.com/products/horizon/skype-for-business.mdl)
    
- [Microsoft Skype for Business With VMWare Horizon](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/products/horizon/vmware-skype-for-business-solution-brief.pdf)
    
## Microsoft's Lync VDI plug-in
<a name="Citrix_RT"> </a>

With the Microsoft Lync VDI plug-in solution, the user has to be on a Windows computer or thin client and have Microsoft's Lync VDI plugin installed to handle audio/video streams from the client on the virtual desktop. A user will:
  
1. Connect an audio/video device (like a headset or camera) to a local computer.
    
2. Connect to a remote virtual desktop with a Lync 2013 or Skype for Business 2015 client.
    
3. Enter credentials for Skype for Business on the virtual desktop.
    
4. Re-enter user credentials to establish a connection with the Lync VDI plug-in on the local Windows computer or thin client.
    
After a connection is established, the user is ready to make and receive audio and video calls. Traffic on the network and the load on the virtual desktop are minimized, since the local computer handles the audio/video processing.
  
Microsoft's Lync VDI plug-in is only supported on certain Windows operating systems and only supports Lync 2013 or Skype for Business 2015 clients. See [Supported virtualization technologies and known limitations](vdi-environments.md#Supported_virt) for more details on supported technologies and limitations.
  
Review the following links for more information:
  
- [Supported virtualization technologies and known limitations](vdi-environments.md#Supported_virt)
    
- [Lync VDI plug-in prerequisites](vdi-environments.md#VDI_prereq)
    
- [Deploy the Lync VDI plug-in with Skype for Business Server](../../deploy/deploy-clients/deploy-the-lync-vdi-plug-in.md)
    
- Citrix Knowledge Center article [CTX138408](https://support.citrix.com/article/CTX138408)
    
The Microsoft VDI plugin is available at [Microsoft Lync VDI 2013 plugin (32 bit)](https://www.microsoft.com/en-us/download/details.aspx?id=35457) or [Microsoft Lync VDI 2013 plugin (64 bit)](https://www.microsoft.com/en-us/download/details.aspx?id=35454). This plugin is supported with the Skype for Business 2015 client, despite the name.
  
### Supported virtualization technologies and known limitations
<a name="Supported_virt"> </a>

The Lync VDI plug-in allows audio and video calling for supported virtualization technologies. In compliance with standard telephone regulations, support for E911 is also included. The following sections describe the virtualization technologies that are supported by the Lync VDI plug-in and the known feature limitations.
  
#### Support for Virtualization Technologies

The Lync VDI plug-in supports full desktop remote sessions in the personal virtual desktop scenario, but not in the remote desktop session scenario. These scenarios can be described as follows:
  
- **Supported: Personalized Virtual Desktops or Virtual Desktop Infrastructure (VDI).** In this scenario, each user logs on to a customizable virtual desktop and is able to save files on the desktop that persist across sessions. Microsoft Remote Desktop Services and VMware Horizon View are example implementations that have been tested for use with Skype for Business 2015. Other implementations undergoing validation include Citrix XenDesktop. For information about vendor-specific VDI environments and client hardware that have been tested by Microsoft, see [Infrastructure qualified for Microsoft Lync](https://go.microsoft.com/fwlink/?LinkID=313435).
    
- **Not supported: Remote Desktop Sessions.** In this scenario, each user logs on to a generic virtual desktop session that can't be customized. Examples include Microsoft Remote Desktop Sessions (RDSH) and Citrix XenApp combined with Citrix Receiver.
    
The Lync VDI plug-in does not support other virtualization technologies, such as application virtualization, which allows the use of an application without requiring installation of the full application locally. Example implementations include Citrix XenApp and Microsoft Application Virtualization (App-V). Application streaming, application remoting, and mixed virtualization modes (for example, application remoting in full desktop remoting) are not supported.
  
The Lync VDI plug-in was designed to use platform-independent APIs called Dynamic Virtual Channels (DVCs). For scenarios that are not explicitly supported, refer to support statements from the VDI solution provider.
  
#### Lync VDI plug-in prerequisites
<a name="VDI_prereq"> </a>

In a VDI environment, the virtual machines and the user's local computer must meet the requirements outlined in this section.
  
> [!NOTE]
>  Your virtualization solution provider can supply details about how to install and deploy their environment. For general information about deploying a virtualized environment based on Hyper-V and Remote Desktop Services, see the following articles in the Microsoft Library: [Hyper-V](https://go.microsoft.com/fwlink/p/?linkid=247514), [Remote Desktop Services in Windows Server 2008 R2](https://go.microsoft.com/fwlink/p/?linkid=247513) 
  
Virtual machines must be configured with Windows 8, Windows 7, or Windows Server 2008 R2 with the latest service packs.
  
The user's local computer must meet the following requirements:
  
- The user must be homed on Skype for Business Server or Lync Server 2013.
    
- The local computer must be running Windows Embedded Standard 7 with SP1, Windows 7 with SP1, or Windows 8.
    
- If you're using Remote Desktop Services, choose the 32-bit or 64-bit Lync VDI plug-in to match the local computer's operating system. It's not required for both the local computer and the virtual machine to have 32-bit or 64-bit operating systems. If you're using another virtualization solution or platform, refer to your provider's requirements.
    
- The local computer must be running the [latest version of the remote desktop client](https://go.microsoft.com/fwlink/p/?LinkId=268032). Install the latest updates of Remote Desktop Services client from Microsoft or the latest remote desktop client software from your virtualization solution provider. 
    
- On the local computer, the remote desktop client settings must be configured so that audio plays on the local computer and remote recording is disabled. To configure these settings for Remote Desktop Connection in Windows, see the next section, "To configure Remote Desktop Connection settings." 
    
The Microsoft VDI plugin is available at [Microsoft Lync VDI 2013 plugin (32 bit)](https://www.microsoft.com/en-us/download/details.aspx?id=35457) or [Microsoft Lync VDI 2013 plugin (64 bit)](https://www.microsoft.com/en-us/download/details.aspx?id=35454).
  
#### Known Feature Limitations
<a name="VDI_prereq"> </a>

The following are known limitations when you use the Skype for Business 2015 client in a VDI environment:
  
There is limited support for Call Delegation and Response Group Agent Anonymization features.
  
There is no support for the following features:
  
- Integrated Audio Device and Video Device tuning pages.
    
- Multiple-view video.
    
- Recording of conversations.
    
- Joining meetings anonymously (that is, joining Skype for Business meetings hosted by an organization that does not federate with your organization).
    
- Using the Lync VDI plug-in along with a Lync Phone Edition device.
    
- Call continuity in case of a network outage.
    
- Customized ringtones and music-on-hold features.
    
The Lync VDI plug-in is not supported in an Office 365 environment.
  
> [!NOTE]
> The Citrix RealTime Optimization Pack does support Office 365. For Citrix-based virtual environments, review Citrix's [Technical Overview](https://docs.citrix.com/en-us/hdx-optimization/2-0/hdx-realtime-optimization-pack-about.mdl) documentation for the list of supported features and versions.
  
## See also
<a name="Citrix_RT"> </a>

[Deploy the Lync VDI plug-in with Skype for Business Server](../../deploy/deploy-clients/deploy-the-lync-vdi-plug-in.md)

