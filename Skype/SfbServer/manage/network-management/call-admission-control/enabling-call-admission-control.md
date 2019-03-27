---
title: 'Enabling call admission control'
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: " After you configure the call admission control (CAC) network, you must enable CAC to enforce the bandwidth limitations."
---

# Enabling call admission control in Skype for Business Server

Call admission control (CAC) is a network of regions, sites, and subnets that enable you to place restrictions on audio and video transmissions based on available bandwidth. After you configure the CAC network, you must enable CAC to enforce the bandwidth limitations. You can use the Skype for Business Server Control Panel to do this.


## To enable CAC from the Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Global**.

4.  On the **Global** page, click the **Global** configuration.
   
    > [!NOTE]  
    > Only one network can be configured for any Skype for Business Server deployment, so there will never be more than one network configuration in the list. You cannot rename the Global configuration.

5.  On the **Edit** menu, click **Show details**.

6.  On the **Edit Global Setting** page, select the **Enable call admission control** check box, and then click **Commit**.

When you click **Commit**, you run a test of the configuration. The **Edit Global Settings** dialog box closes, returning you to the **Global** page. You will receive a warning if any errors or inconsistencies are discovered in your network configuration that will prevent it from working correctly (for example, if every region is not connected to every other region through an interregion route).

If you make changes to your network configuration, you can run the validation check again by opening the Global configuration and clicking **Commit**. You do not need to disable CAC first: leave the check box checked and click **Commit**. You can do this at any time without making any configuration changes.

## See Also

[Plan for call admission control](../../../plan-your-deployment/enterprise-voice-solution/call-admission-control.md) 
 
[Deploy call admission control](../../../deploy/deploy-enterprise-voice/deploy-call-admission-control.md) 

[Get-CsNetworkConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkConfiguration)  

[Set-CsNetworkConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkConfiguration)  

[Remove-CsNetworkConfiguration](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkConfiguration)  
