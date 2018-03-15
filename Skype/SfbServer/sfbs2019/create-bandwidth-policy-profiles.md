---
title: "Create bandwidth policy profiles in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a71881ef-b04a-465e-9abb-0577bfd182f3
description: "Bandwidth policies define limitations on bandwidth usage for real-time audio and video modalities. Bandwidth policies are applied to bandwidth policy profiles, which can be applied to multiple network sites for call admission control."
---

# Create bandwidth policy profiles in Lync Server 2013
[]
Bandwidth policies define limitations on bandwidth usage for real-time audio and video modalities. Bandwidth policies are applied to bandwidth policy profiles, which can be applied to multiple network sites for call admission control.
  
For guidelines about what bandwidth limits you should set in your CAC deployment, see [Defining your requirements for call admission control in Lync Server 2013](defining-your-organization-s-requirements-for-call-admission-control.md) in the Planning documentation. 
  
For details about working with bandwidth policies and policy profiles, see the Lync Server Management Shell documentation for the following cmdlets:
  
- [New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)
    
- [Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)
    
- [Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)
    
- [Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)
    
The example policies created in the following procedure set limits for overall audio traffic, individual audio sessions, overall video traffic, and individual video sessions. For example, the 5Mb_Link bandwidth policy profile sets the following limits:
  
- Audio Limit: 2,000 kbps
    
- Audio Session Limit: 200 kbps
    
- Video Limit: 1,400 kbps
    
- Video Session Limit: 700 kbps
    
> [!NOTE]
> The minimum Audio Session Limit value is 40 kbps. The minimum Video Session Limit value is 100 kbps. 
  
### To create bandwidth policy profiles by using Management Shell

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. For each bandwidth policy profile that you want to create, run the New-CsNetworkBandwidthPolicyProfile cmdlet. For example, run:
    
  ```
  New-CsNetworkBandwidthPolicyProfile -Identity 5Mb_Link -Description "BW profile for 5Mb links" -AudioBWLimit 2000 -AudioBWSessionLimit 200 -VideoBWLimit 1400  -VideoBWSessionLimit 700
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

### To create bandwidth policy profiles by using Lync Server Control Panel

1. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
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
    

