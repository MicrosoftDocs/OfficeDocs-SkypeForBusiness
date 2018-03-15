---
title: "Enabling network media bypass in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 95c4fa06-49d3-41ac-acdc-7dcda66e5508
description: "Media bypass settings apply globally across a Microsoft Lync Server 2013 deployment. Media bypass allows calls to bypass the Mediation Server. For details about when to use Media bypass, see Planning for media bypass in Lync Server 2013 in the Planning section."
---

# Enabling network media bypass in Lync Server 2013
[]
Media bypass settings apply globally across a Microsoft Lync Server 2013 deployment. Media bypass allows calls to bypass the Mediation Server. For details about when to use Media bypass, see [Planning for media bypass in Lync Server 2013](planning-for-media-bypass.md) in the Planning section. 
  
You can enable and configure media bypass from the Lync Server Control Panel. 
  
### To enable and configure media bypass

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Global**.
    
4. On the **Global** page, click the **Global** configuration. There is always only one configuration, and it is always named Global. 
    
5. On the **Edit** menu, click **View details**.
    
6. On the **Edit Global Setting** page, click the **Enable media bypass** check box. 
    
7. Select one of the following options:
    
  - **Always bypass** Select this option to attempt media bypass on all calls. This option will be unavailable if call admission control (CAC) is enabled. If CAC is not enabled, select this option in the following situations: 
    
  - There is no need for bandwidth control.
    
  - There is no need for fine-grained configuration to determine when bypass should happen.
    
  - There is full connectivity between gateways and clients.
    
  - **Use sites and region configuration** If CAC is enabled, this option is selected by default and cannot be changed. When this option is selected, network configuration sites and regions will be used to determine when media bypass is possible. If you select this option, you can choose to enable bypass for sites that are not mapped. Click the **Enable bypass for non-mapped sites** check box only if you have one or more large sites associated with the same region that do not have bandwidth constraints (for example, a large central site) and you also have some branch sites associated with the same region that do have bandwidth constraints. When you enable bypass for non-mapped sites, configuration is streamlined because you specify only the subnets associated with the branch sites rather than needing to specify all subnets associated with all sites. We recommend that you do not select the **Enable bypass for non-mapped sites** check box if CAC is enabled. 
    
8. Click **Commit** to save your changes. 
    
## See also

#### 

[Disabling network media bypass in Lync Server 2013](disabling-network-media-bypass.md)
#### 

[Global media bypass options in Lync Server 2013](global-media-bypass-options.md)
#### 

[Planning for media bypass in Lync Server 2013](planning-for-media-bypass.md)

