---
title: "Video based Screen Sharing for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
ms.date: 2/20/2018
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 50755399-2228-4324-81db-c2bfc824c299
description: "Skype for Business Server planning and configuration information for Video-based Screen Sharing (VbSS)"
---

# Video based Screen Sharing for Skype for Business Server 
 
Video-based Screen Sharing (VbSS) in Skype For Business Server 2015 is now available for download: [Skype for Business Server 2015 Cumulative Update KB3061064](https://www.microsoft.com/en-us/download/details.aspx?id=47690). VbSS is included with Skype for Business Server 2019.
  
Video-based Screen Sharing, or VbSS, grew out of Lync screen-sharing. The difference between VbSS and traditional screen-sharing has to do with the underlying protocols used, and what they excel at. Screen-sharing uses the remote desktop protocol (RDP), which is great at creating thousands of 1-to-1 sessions between people's computers. Newer technology, VbSS, will make use of User Datagram Protocol (UDP).
  
Skype for Business Server wanted to improve people's 1-to-1, and their 1-to-many (multi-party) conversations and meeting experiences. VbSS makes use of the media platform (which relies on UDP as the underlying protocol), with the goal of improving your video start times, the viewing quality of what you're watching (especially if what you're watching is moving fast), and reliability overall.
  
Part of the goal of improving screen-sharing is that transitions between VbSS and RDP be as seamless as possible when they occur. Since VbSS is an update to underlying technology that is used in screen sharing for Skype for Business Server, it may be difficult to detect which technology you're leveraging unless you're looking at SIP details in the network traffic, or you're sharing content that is fast moving or 3-D. If, for example, your workplace has a lot of legacy clients, RDP will still be available as a failsafe to your meetings and conversations. Skype for Business Server uses internal logic to decide which of the two methods (VbSS or traditional screen-sharing) to apply when clients connect. RDP can, and will, be substituted for VbSS when the situation calls for it, so that your viewing experience won't be interrupted.
  
## Planning

### VbSS pros and cons

Switching to VbSS aims to make three key improvements:
  
1. Make screen-sharing (up to 5%) more reliable compared to RDP alone.

2. Make the session setup and video experience faster compared to RDP alone (setup in half the time, with a 6:1 improvement in frames-per-second).

3. Works much better than RDP in low bandwidth conditions, even when sharing high motion content, such as 3-D graphics.
    
Please keep in mind that these numbers rely on the health and proper performance tuning of your network, and may involve networks external to your own, if your clients are on mobile devices.
  
You should also be aware that some fidelity/crispness of your shared content has been traded for reliability, speed, and efficiency. In most cases this will not be readily visible to users.
  
### Ports and protocols

**Required server ports**

|**Server role**|**Service name**|**Port or port range**|**Protocol**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|
|Front End Servers  <br/> |Skype for Business Server Application Sharing service  <br/> |5065  <br/> |TCP  <br/> |Used for incoming SIP listening requests for application sharing.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Application Sharing service  <br/> |49152-65535  <br/> |TCP/UDP  <br/> |Media port range used for application sharing.  <br/> |
   
**Required client ports**

|**Component**|**Port range**|**Protocol**|**Notes**|
|:-----|:-----|:-----|:-----|
|Clients  <br/> |1024-65535  <br/> |TCP/UDP  <br/> |Application sharing.  <br/> |
   
If QoS is enabled for the following media ports and VbSS is also enabled, during a conference that includes desktop sharing the AS MCU will use the video port settings shown in bold below for the screen share traffic. 
  
> [!IMPORTANT]
> These settings are a special case, and these exact settings must be used when implementing both of these features. This overrides other recommended settings in the [documentation for QoS](https://technet.microsoft.com/en-us/library/gg405409%28v=ocs.15%29.aspx). For application sharing you will also need to specify ASMCUSVC.exe in the QoS GPO in addition to defining these port values. 
  
**Application Server QoS/VbSS required settings**

|**Property**|**Port value**|**Protocol**|
|:-----|:-----|:-----|
|AudioPortStart  <br/> |49152  <br/> |UDP  <br/> |
|AudioPortCount  <br/> |8348  <br/> |UDP  <br/> |
|**VideoPortStart** <br/> |**57501** <br/> |UDP  <br/> |
|**VideoPortCount** <br/> |**8034** <br/> |UDP  <br/> |
|AppSharingPortStart  <br/> |40803  <br/> |TCP  <br/> |
|AppSharingPortCount  <br/> |8348  <br/> |TCP  <br/> |
   
### Capacity planning

Each Front End Server running Skype for Business Server 2015 Cumulative Update 2 (CU2) or later supports up to 375 participants for screen sharing using RDP (though only 250 per meeting). This capacity doesn't change post-CU3, when VbSS is introduced and used.
  
That being said, we've done performance and stress testing in our lab, and the following measurements should also be considered with regard to your own deployment (depending on usage, of course).
  
Assuming:
  
- You're using Skype for Business Server 2015 CU2 or later in your deployment.
    
- All the users in your Skype for Business Server environment have screen resolutions higher than 1920x1080.
    
At full capacity (which as noted above, is 375 screen sharing participants per Front End Server in total, though only 250 per meeting), your Front End Server may be utilizing ~89% of the 1 Gigabit of network card. This is because the existing screen sharing technology in Skype for Business Server CU2 (RDP) transmits the on-screen content at the native resolution of the presenter's PC. So with higher screen resolutions factored in, you may already be experiencing network bottlenecks for screen sharing with Skype for Business Server 2015 CU2.
  
To mitigate this, one or more of the following options may be helpful:
  
- Upgrade your Front End Server from a 1 Gigabit network card to a 10 Gigabit Ethernet card.

- Increase the number of Front End Servers to load-balance traffic.

- Limit the bandwidth (bitrate) used for VbSS and RDP by putting a cap on the maximum bandwidth used by either channels.
    
The numbers in this table are influenced by individual networks and by the content being shared. Please test to establish baselines for your network or networks.
  
|**1080p Content**|**RDP Average**|**RDP Peak**|**VbSS Average**|**VbSS Peak**|
|:-----|:-----|:-----|:-----|:-----|
|PPT  <br/> |200kbps  <br/> |12mbps  <br/> |100kbps  <br/> |3mbps  <br/> |
|CAD  <br/> |3mbps  <br/> |7mbps  <br/> |1mbps  <br/> |3mbps  <br/> |
|Video  <br/> |5mbps  <br/> |7mbps  <br/> |1.3mbps  <br/> |2.2mbps  <br/> |
   
### Network bandwidth requirements for media traffic

The VbSS bandwidth is:
  
|**Video codec**|**Resolution and aspect ratio**|**Maximum video payload bit rate (Kbps)**|**Minimum video payload bit rate (Kbps)**|
|:-----|:-----|:-----|:-----|
|H.264  <br/> |1920x1080 (16:9)  <br/> (The aspect ratio depends on the sharer's monitor resolution, and will not always be 16:9)  <br/> |4000  <br/> |1500  <br/> |
   
## Clients and servers support

Video-based Screen Sharing requires Skype for Business Server 2015 CU3 or later, and a current version of the supporting clients listed in [Mobile client feature comparison for Skype for Business](../plan-your-deployment/clients-and-devices/mobile-feature-comparison.md) and [Meetings support](../plan-your-deployment/clients-and-devices/desktop-feature-comparison.md#BKMK_Conferencing). 
  
There are situations where screen-sharing will transition to RDP, like these:
  
- If your account is hosted in an environment where the ASMCU doesn't meet the minimum build that supports VbSS.
- If someone who uses an older version of the Skype for Business client joins your session, for example anyone using any Windows client version that is lower than 16.0.6330.1000, Skype for Business Room System Devices, or Skype for Business Mobile Apps. 
- If a user is sharing from the Skype for Business Web App.
- If someone is using Skype for Business on Mac and not is homed on Skype for Business Online or Skype for Business Server 2015 with the July, 2018 cumulative update (or later).
- If someone starts any Program/Windows Sharing.
- If someone starts recording the session.
- If someone invokes Remote Screen Control during the session. 
- Meetings with more than 250 participants (where VbSS is not currently supported).

Be aware that once the session transitions to RDP it will not transition back to VbSS. Again, the transition from VbSS is meant to be seamless, and, with hope, will not be easy to detect in most situations.
    
> [!NOTE]
> It's not supported to block, or attempt to block, transition from VbSS to RDP in Skype for Business screen-sharing. 
  
## Enabling, disabling, and configuring VbSS

The great thing is, once you've installed the Skype for Business Server 2015 Cumulative Update 3 (CU3) or later, all your users will be enabled for 1-to-1 and multi-party VbSS by default. This may be problematic for you if you have a reason to not have this functionality enabled for all your users. In that case, you're able to use these steps to disable users (the enable users steps will follow):
  
### How to disable users from using VbSS

- You can assign a user policy that doesn't allow VbSS to any users who shouldn't be using VbSS by running this cmdlet in the Skype for Business Management Console (replace [PolicyName] with the policy you're doing this for):
    
  ```
  Set-CsConferencingPolicy -Identity [PolicyName] -ApplicationSharingMode RDP
  ```

- You also can update the global conferencing policy, which will affect all users without an assigned policy:
    
  ```
  Set-CsConferencingPolicy -ApplicationSharingMode RDP
  ```

    For more information on this command, see [Set-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csconferencingpolicy?view=skype-ps).
    
- If you need to turn VbSS off completely, you can run this command:
    
  ```
  Set-CsMediaConfiguration -EnableVideoBasedSharing $false
  ```

    For more information on this command, see [Set-CsMediaConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csmediaconfiguration?view=skype-ps).
    
> [!NOTE]
> In a multiparty Skype for Business meeting, all client endpoints will respect the policy setting for the meeting organizer. 
  
### How to enable users to use VbSS

- You can assign a specific user policy that allows VbSS to any users who need to be using VbSS by running this cmdlet in the Skype for Business Management Console (replace [PolicyName] with the policy you're doing this for):
    
  ```
  Set-CsConferencingPolicy -Identity [PolicyName] -ApplicationSharingMode VideoWithFallback
  ```

- You also can update the global conferencing policy, which will affect all users without an assigned policy:
    
  ```
  Set-CsConferencingPolicy -ApplicationSharingMode VideoWithFallback
  ```

    For more information on this command, see [Set-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csconferencingpolicy?view=skype-ps).
    
- If you need to turn VbSS back on after turning it off (it's on by default), you can run this command:
    
  ```
  Set-CsMediaConfiguration -EnableVideoBasedSharing $true
  ```

    For more information on this command, see [Set-CsMediaConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csmediaconfiguration?view=skype-ps).
    
> [!NOTE]
> In a multi-party Skype for Business meeting, all client endpoints will respect the policy setting for the meeting organizer. 
  
## See also

[Skype for Business Server 2015 Cumulative Update KB3061064](https://www.microsoft.com/en-us/download/details.aspx?id=47690)
  
[Video-based screen-sharing (VBSS) is available in Skype for Business Server 2015](https://support.microsoft.com/en-us/kb/3170163)
