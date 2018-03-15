---
title: "Deleting network bandwidth policy profiles in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4d6beda8-6aa5-4d5e-8a07-363598f0e0c8
description: "As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. In Microsoft Lync Server 2013, only audio and video modalities can be assigned bandwidth limitations. You can set overall bandwidth limitations and session limitations. You can use the Lync Server Control Panel to create, modify, or delete a container profile for these policies. Use the following procedures to delete a network bandwidth policy profiles. For details on creating or modifying a network bandwidth policy profile, see Creating or modifying bandwidth policy profiles in Lync Server 2013."
---

# Deleting network bandwidth policy profiles in Lync Server 2013
[]
As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. In Microsoft Lync Server 2013, only audio and video modalities can be assigned bandwidth limitations. You can set overall bandwidth limitations and session limitations. You can use the Lync Server Control Panel to create, modify, or delete a container profile for these policies. Use the following procedures to delete a network bandwidth policy profiles. For details on creating or modifying a network bandwidth policy profile, see [Creating or modifying bandwidth policy profiles in Lync Server 2013](creating-or-modifying-bandwidth-policy-profiles.md).
  
### To delete a bandwidth policy profile

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Bandwidth Policy**.
    
4. On the **Bandwidth Policy** page, click the bandwidth policy profile that you want to delete. 
    
    > [!NOTE]
    > You can delete more than one profile at a time. To do this, press CTRL and select multiple profiles while holding down the CTRL key. Or, to select all profiles, click **Select all** on the **Edit** menu. 
  
5. On the **Edit** menu, click **Delete**.
    
    > [!CAUTION]
    > You cannot delete a bandwidth policy profile that is associated with a network site. You must first remove the association with the network site before you can delete the profile. For details about how to modify the network site, see [Creating or modifying network sites in Lync Server 2013](creating-or-modifying-network-sites.md). 
  
## See also

#### 

[Creating or modifying bandwidth policy profiles in Lync Server 2013](creating-or-modifying-bandwidth-policy-profiles.md)
  
[Viewing network bandwidth policy profile information in Lync Server 2013](viewing-network-bandwidth-policy-profile-information.md)
#### 

[Configure call admission control in Lync Server 2013](configure-call-admission-control.md)
  
[Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)

