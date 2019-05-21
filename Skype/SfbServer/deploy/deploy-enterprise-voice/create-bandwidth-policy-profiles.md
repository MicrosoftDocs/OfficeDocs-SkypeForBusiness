---
title: "Create bandwidth policy profiles in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: a71881ef-b04a-465e-9abb-0577bfd182f3
description: "Create or modify bandwidth policies, which are used by Enterprise Voice call admission control in Skype for Business Server."
---

# Create bandwidth policy profiles in Skype for Business Server 
 
Create or modify bandwidth policies, which are used by Enterprise Voice call admission control in Skype for Business Server. 
  
Bandwidth policies define limitations on bandwidth usage for real-time audio and video modalities. Bandwidth policies are applied tobandwidth policy profiles, which can be applied to multiple network sites for call admission control.
  
For guidelines about what bandwidth limits you should set in your CAC deployment, see [Plan for call admission control in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/call-admission-control.md).
  
The example policies created in the following procedure set limits for overall audio traffic, individual audio sessions, overall video traffic, and individual video sessions. For example, the 5Mb_Link bandwidth policy profile sets the following limits: 
  
- Audio Limit: 2,000 kbps
    
- Audio Session Limit: 200 kbps
    
- Video Limit: 1,400 kbps
    
- Video Session Limit: 700 kbps
    
> [!NOTE]
> The minimum Audio Session Limit value is 40 kbps. The minimum Video Session Limit value is 100 kbps. 
  
### To create bandwidth policy profiles by using Skype for Business Server Management Shell

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. For each bandwidth policy profile that you want to create, run the New-CsNetworkBandwidthPolicyProfile cmdlet. For example, run:
    
   ```
   New-CsNetworkBandwidthPolicyProfile -Identity 5Mb_Link -Description "BW profile for 5Mb links" -AudioBWLimit 2000 -AudioBWSessionLimit 200 -VideoBWLimit 1400   -VideoBWSessionLimit 700
   ```

   ```
   New-CsNetworkBandwidthPolicyProfile -Identity 10Mb_Link -Description "BW profile for 10Mb links" -AudioBWLimit 4000 -AudioBWSessionLimit 200 -VideoBWLimit 2800 -VideoBWSessionLimit 700
   ```

   ```
   New-CsNetworkBandwidthPolicyProfile -Identity 50Mb_Link -Description "BW profile for 50Mb links" -AudioBWLimit 20000 -AudioBWSessionLimit 200 -VideoBWLimit 14000 -VideoBWSessionLimit 700
   ```

   ```
   New-CsNetworkBandwidthPolicyProfile -Identity 25Mb_Link -Description "BW profile for 25Mb links" -AudioBWLimit 10000 -AudioBWSessionLimit 200 -VideoBWLimit 7000 -VideoBWSessionLimit 700
   ```

### To create bandwidth policy profiles by using Skype for Business Server Control Panel

1. Open Skype for Business Server Control Panel.
    
2. In the left navigation bar, click **Network Configuration**.
    
3. Click the **Policy Profile** navigation button.
    
4. Click **New**.
    
5. On the **New Policy Profile** page, click **Name** and then type a name for the bandwidth policy profile.
    
6. Click **Audio limit**, and then type in the maximum number of kbps to allow for all audio sessions combined.
    
7. Click **Audio session limit**, and then type in the maximum number of kbps to allow for each individual audio session.
    
8. Click **Video limit**, and then type in the maximum number of kbps to allow for all video sessions combined.
    
9. Click **Video session limit**, and then type in the maximum number of kbps to allow for each individual video session.
    
10. Optionally, click **Description**, and then type additional information to describe this bandwidth policy profile.
    
11. Click **Commit**.
    
12. To finish creating bandwidth policy profiles for your topology, repeat steps 4 through 11 with settings for other bandwidth policy profiles.
    
## See also

[New-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/powershell/module/skype/new-csnetworkbandwidthpolicyprofile?view=skype-ps)
  
[Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/powershell/module/skype/get-csnetworkbandwidthpolicyprofile?view=skype-ps)
  
[Set-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/powershell/module/skype/set-csnetworkbandwidthpolicyprofile?view=skype-ps)
  
[Remove-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/powershell/module/skype/remove-csnetworkbandwidthpolicyprofile?view=skype-ps)
