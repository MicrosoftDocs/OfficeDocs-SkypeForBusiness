---
title: "Delete Quality of Experience configuration settings in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: fd0c4c2f-3bfb-42cb-9b6a-f0f8d5aa9e81
description: "Summary: Learn how to delete Quality of Experience (QoE) settings in Skype for Business Server."
---

# Delete Quality of Experience configuration settings in Skype for Business Server
 
**Summary:** Learn how to delete Quality of Experience (QoE) settings in Skype for Business Server.
  
Quality of Experience (QoE) metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay). These metrics are stored in a database apart from other data (such as call detail records), which allows you to enable and disable QoE independent of other data recording.
  
When you install Skype for Business Server, a single, global collection of QoE configuration settings is created for you. Administrators also have the option of creating custom setting collections that can be applied to individual sites. By design, settings configured at the site scope take precedence over settings configured at the global scope. If you delete site-scoped settings, then QoE will be managed in that site by using the global settings.
  
Note that you can also "delete" the global settings. However, the global settings will not actually be removed. Instead, all the properties in that collection will be reset to their default values. For example, by default purging is enabled in a collection of QoE configuration settings. Suppose you modify the global collection so that purging is disabled. If you later delete the global settings, all the properties will be reset to their default values. In this case, that means that purging will once again be enabled.
  
You can remove QoE configuration settings by using the Skype for Business Server Control Panel or by using the [Remove-CsQoEConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-csqoeconfiguration?view=skype-ps) cmdlet.
  
### To delete QoE configuration settings by using Skype for Business Server Control Panel

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see **Delegate Setup Permissions**.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Quality of Experience Data**.
    
4. On the **Quality of Experience Data** page, click the policy that you want, click **Edit**, and then click **Delete**.
    
5. Click **OK**.
    
## Removing QoE Configuration Settings by Using Windows PowerShell Cmdlets

You can delete QoE configuration settings by using Windows PowerShell and the **Remove-CsQoEConfiguration** cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To remove a specified collection of QoE configuration settings

 This command removes the QoE configuration settings applied to the Redmond site:
    
  ```
  Remove-CsQoEConfiguration -Identity "site:Redmond"
  ```

### To remove all of the QoE configuration settings applied to the site scope

 This command removes all the QoE configuration settings applied to the site scope:
    
  ```
  Get-CsQoEConfiguration -Filter "site:*" | Remove-CsQoEConfiguration
  ```

### To remove all of the QoE configuration settings where QoE monitoring is disabled

 This command removes all the QoE configuration settings where QoE monitoring has been disabled:
    
  ```
  Get-CsQoEConfiguration | Where-Object {$_.EnableQoE -eq $False} | Remove-CsQoEConfiguration
  ```

For details, see [Remove-CsQoEConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-csqoeconfiguration?view=skype-ps).
  
## See also

[Manually purge the call detail recording and Quality of Experience databases in Skype for Business Server](../../deploy/deploy-monitoring/purgecall-detail-recording-and-qoe.md)

