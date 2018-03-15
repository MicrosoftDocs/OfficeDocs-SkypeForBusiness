---
title: "Enabling call admission control in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 015f5c8f-2f90-4b9e-8149-b33767e90582
description: "Call admission control (CAC) is a network of regions, sites, and subnets that enable you to place restrictions on audio and video transmissions based on available bandwidth. After you configure the CAC network, you must enable CAC to enforce the bandwidth limitations. You can use Lync Server Control Panel to do this."
---

# Enabling call admission control in Lync Server 2013
[]
Call admission control (CAC) is a network of regions, sites, and subnets that enable you to place restrictions on audio and video transmissions based on available bandwidth. After you configure the CAC network, you must enable CAC to enforce the bandwidth limitations. You can use Lync Server Control Panel to do this.
  
### To enable CAC from Lync Server Control Panel

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Global**.
    
4. On the **Global** page, click the **Global** configuration. 
    
    > [!NOTE]
    > Only one network can be configured for any Microsoft Lync Server 2013 deployment, so there will never be more than one network configuration in the list. You cannot rename the Global configuration. 
  
5. On the **Edit** menu, click **Show details**. 
    
6. On the **Edit Global Setting** page, select the **Enable call admission control** check box, and then click **Commit**.
    
When you click **Commit**, you run a test of the configuration. The **Edit Global Settings** dialog box closes, returning you to the **Global** page. You will receive a warning if any errors or inconsistencies are discovered in your network configuration that will prevent it from working correctly (for example, if every region is not connected to every other region through an interregion route). If you make changes to your network configuration, you can run the validation check again by opening the Global configuration and clicking **Commit**. You do not need to disable CAC first: leave the check box checked and click **Commit**. You can do this at any time without making any configuration changes.
## See also

#### 

[Overview of call admission control in Lync Server 2013](overview-of-call-admission-control.md)
#### 

[Planning for call admission control in Lync Server 2013](planning-for-call-admission-control-cac.md)
  
[Configure call admission control in Lync Server 2013](configure-call-admission-control.md)
  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)
  
[Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)
  
[Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)

