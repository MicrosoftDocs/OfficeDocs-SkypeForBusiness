---
title: Media quality and network connectivity performance
ms.author: judegn
author: judegn
manager: serdars
ms.reviewer: lola
ms.topic: article
audience: admin
ms.service: msteams
ms.reviewer: lola
description: Use this guidance to prepare your network for Teams deployment and rollout 
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-guidance
ms.collection: 
- Teams
- M365-collaboration
appliesto:
- Microsoft Teams
---
---
# Overview

This topic defines the set of network performance requirements for Teams services and connectivity between your network and Teams based your assessment of the network connectivity. I

## Why is this all so important?

The quality of real-time media (audio, video, and application sharing) over IP is greatly impacted by the quality of end-to-end network connectivity. For optimal Teams media quality, it is important for you to make sure there is a high-quality connection between your company network and Teams. The best way to accomplish this is to set up your internal network and cloud connectivity based on the capacity of your network to accommodate for peak traffic volume for Teams across all connections.
  
Working with a [Microsoft partner](https://partnercenter.microsoft.com/en-us/pcv/search), you can connect a variety of Office 365 applications including Teams in the cloud to your network and real-time voice and video communications capabilities for Teams require network services must be specifically configured to support these Office 365 real-time workloads. This includes a network that has sufficient bandwidth to carry the required volume of traffic and be capable of supporting Quality of Service (QoS) to deliver a business class experience for your users.
  
## Implement Quality of Service (QoS) for Teams

  
## Bypass proxies and WAN optimization devices

All Office 365 including Teams is encrypted and is typically not able to be inspected by proxy devices. For these reasons we recommend bypassing proxy devices for all Office 365 network traffic as defined as connections your users make to [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). Since proxy devices will likely introduce delay in real-time Teams media streams we strongly recommend bypassing proxy devices at a minimum for that traffic.
  
  
## Bypass double encryption

To provide users the best possible audio and video experience, you must implement a solution that prevents Teams media (audio and video) from traversing a Virtual Private Network (VPN) tunnel. All Teams traffic is encrypted with Transport Layer Security (TLS) and the media workloads are encrypted with Secure Real Time Protocol (SRTP). Signaling is encrypted with TLS and the media workloads are encrypted with SRTP. Sending this traffic over the VPN tunnel adds an extra layer of encryption, and additional network hops between the client and Office 365, both of which can result in a degraded session because it increases jitter, packet loss and latency.
  
One option to prevent Teams traffic from traversing the VPN tunnel is *Split Tunneling*. To implement split-tunneling, customers should consult with their VPN vendor on the specifics of how to do this in their software.
  
> [!NOTE]
> This is only required for the Teams media workloads and isn't applicable to other Office 365 services. 
  

## Ensure the right ports and protocols are open

Customers must ensure reachability of the URLs and IP addresses that are required for the O365 service. For a complete listing of all IP addresses and URLs for Teams, see [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2).
  
Skype for Business clients use a variety of ports and protocols. The direction and flow of network traffic for a Skype for Business session will vary depending on the type of interactions (peer-to-peer vs multiparty) and depending on the use of content sharing and voice/video. You must review and open the list of ports and protocols, paying special attention to the source and destination ports. For example, audio traffic uses just 20 ports (50000-50019 TCP/UDP) at the client side, but the destination port could be anywhere in a 10K port range (50000-59999 TCP/UDP) at the service side. This also includes opening TCP 443 and UDP 3478 on the firewall.
  
Additional network configuration might also be required to support Skype for Business Online.
  
  
## Use Phones and Devices Optimized for Skype for Business

In a real-time media session, media devices that are used by all participants such as headsets and web cams have a great impact on the overall audio and video quality. Lower-quality devices or devices with incorrect device drivers will produce lower overall sound quality for audio and lower image quality for video. Certified devices or good quality devices, on the other hand, help with echo cancellation, noise filtering, video resolution and reduce latency.
  
Phones and devices make a huge difference in the quality of audio and video for end users. The Skype for Business certification program is an evolution of the "Lync Compatible" program and validates that the device meets Microsoft standards for audio and video. There are a number of IP Phones, USB audio and video devices, PCs and meeting room devices that have been tested and qualified by Microsoft. You should review the list of devices that are optimized for Skype for Business, and work to provide different devices in order to meet the various needs and personal preferences of your end users in your organization.
  
See the following for more information on supported and certified devices:  
  
- [Getting phones for Skype for Business Online](../what-is-phone-system-in-office-365/getting-phones-for-skype-for-business-online/getting-phones-for-skype-for-business-online.md)
    
- [Phones and Devices for Skype for Business](https://technet.microsoft.com/en-us/office/dn947482.aspx)
    
- [Solutions Catalog for Personal Peripherals](http://partnersolutions.skypeforbusiness.com/solutionscatalog/personal-peripherals-pcs)
    
- [Phones and devices qualified for Microsoft Lync](https://technet.microsoft.com/en-us/office/dn788944.aspx)
    
The environment and surrounding area where users are meeting and using audio and video devices is another big factor for audio and video quality. Users calling from a noisy environment will have echoed, muffled and unclear audio. Users in a dark or low light environment won't be able to produce bright, clear image quality for video. In a conference room setting, the location of the microphone and video device have a direct impact on the sound and image quality that participants will receive.
  
To get a clearer picture of a user's audio and video experience use the Skype for Business app **Tools** > **Options** > **Audio Device** or **Video Device** to make changes to the device in use and customize it's settings. You can also check the audio quality of a call by clicking **Check Call Quality**. If they click **Check Call Quality**, they can then report the quality and issues found with the test call.
  
![Testing audio in the Skype for Business client.](../images/1730a71e-a09d-4702-8eb6-ef1346a091fa.png)
  
## Related topics 

[ExpressRoute and QoS in Skype for Business Online](expressroute-and-qos-in-skype-for-business-online.md)
  
  
 
