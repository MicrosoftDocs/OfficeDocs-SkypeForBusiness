---
title: "Delete an existing collection of CDR configuration settings in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8ebf5da8-c0fc-498c-8d85-527d3be8479a
description: "Summary: Learn how to remove CDR configuration settings in Skype for Business Server."
---

# Delete an existing collection of CDR configuration settings in Skype for Business Server
 
**Summary:** Learn how to remove CDR configuration settings in Skype for Business Server.
  
Call Detail Recording (CDR) enables you to track usage of such things as peer-to-peer instant messaging sessions, Voice over Internet Protocol (VoIP) phone calls, and conferencing calls. This usage data includes information about who called whom, when they called, and how long they talked.
  
When you install Skype for Business Server, a single, global collection of CDR configuration settings is created for you. Administrators also have the option of creating custom setting collections that can be applied to individual sites. By design, settings configured at the site scope take precedence over settings configured at the global scope. If you delete site-scoped settings, then CDR will be managed in that site by using the global settings.
  
Note that you can also "delete" the global settings. However, the global settings will not actually be removed. Instead, all the properties in that collection will be reset to their default values. For example, by default purging is enabled in a collection of CDR configuration settings. Suppose you modify the global collection so that purging is disabled. If you later delete the global settings, all the properties will be reset to their default values. In this case, that means that purging will once again be enabled.
  
You can remove CDR configuration settings by using the Skype for Business Server Control Panel or the [Remove-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-cscdrconfiguration?view=skype-ps) cmdlet.
  
### To remove CDR configuration settings with Skype for Business Server Control Panel

1. In Skype for Business Server Control Panel, click **Monitoring and Archiving**. 
    
2. On the **Call Detail Recording** tab, select the collection (or collections) of CDR settings to be removed. To select multiple collections, click the first collection, hold down the Ctrl key, and click additional collections.
    
3. Click **Edit**, and then click **Delete**.
    
4. In the Skype for Business Server Control Panel dialog box, click **OK**.
    
## Removing CDR configuration settings by using Windows PowerShell Cmdlets

You can delete call detail recording configuration settings by using Windows PowerShell and the **Remove-CsCdrConfiguration** cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To remove a specified collection of CDR configuration settings

 This command removes the CDR configuration settings applied to the Redmond site:
    
  ```
  Remove-CsCdrConfiguration -Identity "site:Redmond"
  ```

### To remove all the CDR configuration settings applied to the site scope

 This command removes all the CDR configuration settings applied to the site scope:
    
  ```
  Get-CsCdrConfiguration -Filter "site:*" | Remove-CsCdrConfiguration
  ```

### To remove all the CDR configuration settings that disable call detail recording

 This command removes all the CDR configuration settings where Call Detail recording has been disabled:
    
  ```
  Get-CsCdrConfiguration | Where-Object {$_.EnableCDR -eq $False} | Remove-CsCdrConfiguration
  ```

For more information, see the help topic for the [Remove-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-cscdrconfiguration?view=skype-ps) cmdlet.
  
## See also

[Manually purge the call detail recording and Quality of Experience databases in Skype for Business Server](../../deploy/deploy-monitoring/purgecall-detail-recording-and-qoe.md)

