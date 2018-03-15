---
title: "Viewing network bandwidth policy profile information in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: eed453fc-04e9-4971-959c-6fad54bf1c96
description: "As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. In Microsoft Lync Server 2013, only audio and video modalities can be assigned bandwidth limitations. You can set overall bandwidth limitations and session limitations. You can use the Lync Server Control Panel to create, modify, or delete a container profile for these policies. Each bandwidth policy profile can be associated with one or more network sites. Use the following procedures to view a bandwidth policy profile. To create or modify a bandwidth policy profile, see Creating or modifying bandwidth policy profiles in Lync Server 2013."
---

# Viewing network bandwidth policy profile information in Lync Server 2013
[]
As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. In Microsoft Lync Server 2013, only audio and video modalities can be assigned bandwidth limitations. You can set overall bandwidth limitations and session limitations. You can use the Lync Server Control Panel to create, modify, or delete a container profile for these policies. Each bandwidth policy profile can be associated with one or more network sites. Use the following procedures to view a bandwidth policy profile. To create or modify a bandwidth policy profile, see [Creating or modifying bandwidth policy profiles in Lync Server 2013](creating-or-modifying-bandwidth-policy-profiles.md).
  
### To view a bandwidth policy profile

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Bandwidth Policy**.
    
4. On the **Bandwidth Policy** page, click the bandwidth policy profile that you want to view. 
    
5. On the **Edit** menu, click **Show details**.
    
## Viewing Network Bandwidth Policy Profile Information by Using Windows PowerShell Cmdlets

Network bandwidth profiles can be viewed by using Windows PowerShell and the Get-CsNetworkBandwidthPolicyProfile cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view network bandwidth policy profile information

- To view information about all your network bandwidth policy profiles, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsNetworkBandwidthPolicyProfile
  ```

    That will return information similar to this:
    
  ```
  Identity          : RedmondBandwidthPolicy
  BWPolicy          : {BWLimit=200;BWSessionLimit=200;
                      BWPolicyModality=Audio, 
                      BWLimit=1400;BWSessionLimit=500;
                      BWPolicyModality=Video}
  BWPolicyProfileID : RedmondBandwidthPolicy
  Description       :
  
  ```

For more information, see the help topic for the [Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md) cmdlet. 
  
## See also

#### 

[Creating or modifying bandwidth policy profiles in Lync Server 2013](creating-or-modifying-bandwidth-policy-profiles.md)
  
[Deleting network bandwidth policy profiles in Lync Server 2013](deleting-network-bandwidth-policy-profiles.md)
#### 

[Configure call admission control in Lync Server 2013](configure-call-admission-control.md)

