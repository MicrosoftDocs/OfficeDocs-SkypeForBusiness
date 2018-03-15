---
title: "Creating or modifying bandwidth policy profiles in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 08a2e18f-9b0d-4a2f-aa14-13bbf79ec745
description: "As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. In Microsoft Lync Server 2013, only audio and video modalities can be assigned bandwidth limitations. You can set overall bandwidth limitations and session limitations. You can use the Lync Server Control Panel to create, modify, or delete a container profile for these policies. Each bandwidth policy profile can be associated with one or more network sites. Use the following procedures to create or modify a bandwidth policy profile. To delete a bandwidth policy profile, see Deleting network bandwidth policy profiles in Lync Server 2013"
---

# Creating or modifying bandwidth policy profiles in Lync Server 2013
[]
As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. In Microsoft Lync Server 2013, only audio and video modalities can be assigned bandwidth limitations. You can set overall bandwidth limitations and session limitations. You can use the Lync Server Control Panel to create, modify, or delete a container profile for these policies. Each bandwidth policy profile can be associated with one or more network sites. Use the following procedures to create or modify a bandwidth policy profile. To delete a bandwidth policy profile, see [Deleting network bandwidth policy profiles in Lync Server 2013](deleting-network-bandwidth-policy-profiles.md)
  
### To create a new bandwidth policy profile

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Bandwidth Policy**.
    
4. On the **Bandwidth Policy** page, click **New**. 
    
5. In **New Bandwidth Policy Profile**, type a name in the **Name** field. This name must be unique among all bandwidth policy profiles. 
    
6. In the **Audio limit** field, type a numeric value. This value is the maximum amount of bandwidth to allocate for all audio connections, expressed in kbps. 
    
7. Enter a numeric value in the **Audio session limit** field. This value is the maximum amount of bandwidth to allocate for an individual audio connection, expressed in kbps. This value must be 40 or higher. 
    
8. Enter a numeric value in the **Video limit** field. This value is the maximum amount of bandwidth to allocate for all video connections, expressed in kbps. 
    
9. Enter a numeric value in the **Video session limit** field. This value is the maximum amount of bandwidth to allocate for an individual video connection, expressed in kbps. This value must be 100 or higher. 
    
10. (Optional) Type a value in the **Description** field to provide more information about this bandwidth policy profile that cannot be expressed by the name alone. 
    
11. Click **Commit**.
    
    > [!NOTE]
    > Creating a new bandwidth policy profile does not automatically enforce bandwidth restrictions. You must first associate the policy profile with a site. For details about how to associate a policy profile with a site, see [Creating or modifying network sites in Lync Server 2013](creating-or-modifying-network-sites.md). 
  
### To modify a bandwidth policy profile

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Bandwidth Policy**.
    
4. On the **Bandwidth Policy** page, click the bandwidth policy profile that you want to modify. 
    
5. On the **Edit** menu, click **Show details**.
    
6. On the **Edit Bandwidth Policy Profile** page, modify the fields as necessary (for details, see the "To create a bandwidth policy profile" section earlier in this topic). 
    
7. Click **Commit**.
    
    > [!NOTE]
    > When you modify the bandwidth policy profile, it will immediately update the bandwidth limitations of all network sites associated with this bandwidth policy profile. 
  
## See also

#### 

[Deleting network bandwidth policy profiles in Lync Server 2013](deleting-network-bandwidth-policy-profiles.md)
#### 

[Configure call admission control in Lync Server 2013](configure-call-admission-control.md)
  
[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)
  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)
  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

