---
title: "Configuring network site links in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7e9147ae-e727-46c8-8c1a-6c13201f09be
description: "Within a call admission control (CAC) configuration, you can create network inter-site policies that define bandwidth limitations between sites that are directly linked. When network sites share a direct link, bandwidth limitations for audio and video connections can be defined between those two sites. You cannot use the Lync Server Control Panel to configure network site policies, this can be done only by using cmdlets from the Lync Server Management Shell. You can create, modify, and remove a network site link (also known as a network inter-site policy) from the Lync Server Management Shell."
---

# Configuring network site links in Lync Server 2013
[]
Within a call admission control (CAC) configuration, you can create network inter-site policies that define bandwidth limitations between sites that are directly linked. When network sites share a direct link, bandwidth limitations for audio and video connections can be defined between those two sites. You cannot use the Lync Server Control Panel to configure network site policies, this can be done only by using cmdlets from the Lync Server Management Shell. You can create, modify, and remove a network site link (also known as a network inter-site policy) from the Lync Server Management Shell.
  
### To create a network site link

1. Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. From the command prompt, type the following command, substituting values that are valid for your configuration:
    
  ```
  New-CsNetworkInterSitePolicy -Identity Reno_Portland -NetworkSiteID1 Reno -NetworkSiteID2 Portland -BWPolicyProfileID LowBWLimits
  ```

    This example creates a new network site link named Reno_Portland that sets bandwidth limitations between the Reno and Portland network sites. The network sites and the bandwidth policy profile must already exist before running this command.
    
For detailed parameter descriptions, see [New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md) in the Lync Server Management Shell documentation. To retrieve a list of bandwidth policy profiles that can be applied to the network site link, call the **Get-CsNetworkBandwidthPolicyProfile** cmdlet. For details, see [Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md) in the Lync Server Management Shell documentation. 
### To modify a network site link

1. Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Use the **Set-CsNetworkInterSitePolicy** cmdlet to modify the properties of a given network site link. You can modify either (or both) or the connected sites, and you can modify the bandwidth policy profile associated with the link. Here is an example of modifying the bandwidth policy profile of a site link named Reno_Portland: 
    
  ```
  Set-CsNetworkInterSitePolicy -Identity Reno_Portland -BWPolicyProfileID HighBWLimits
  ```

For detailed parameter descriptions, see [Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md) in the Lync Server Management Shell documentation. 
### To delete a network site link

1. Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Use the **Remove-CsNetworkInterSitePolicy** cmdlet to remove a network site link. The following example deletes the Reno_Portland network site link: 
    
  ```
  Remove-CsNetworkInterSitePolicy -Identity Reno_Portland
  ```

For detailed parameter descriptions, see [Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md) in the Lync Server Management Shell documentation. 
## See also

#### 

[Call admission control cmdlets in Lync Server 2013](call-admission-control-cmdlets.md)
#### 

[New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)
  
[Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)
  
[Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)
  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)
  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

