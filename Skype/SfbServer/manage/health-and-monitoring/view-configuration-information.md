---
title: "View CDR configuration information in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 77bd553f-da89-4c84-a5d0-2f7e91d04383
description: "Summary: Learn how to use Call Detail Recording (CDR) in Skype for Business Server."
---

# View CDR configuration information in Skype for Business Server
 
**Summary:** Learn how to use Call Detail Recording (CDR) in Skype for Business Server.
  
Call Detail Recording (CDR) enables you to track usage of such things as peer-to-peer instant messaging sessions, Voice over Internet Protocol (VoIP) phone calls, and conferencing calls. This usage data includes information about who called whom, when they called, and how long they talked.
  
When you install Skype for Business Server, a single, global collection of CDR configuration settings is created for you. Administrators also have the option of creating custom setting collections that can be applied to individual sites. You can view the CDR configuration settings in use in your organization by using Skype for Business Server Control Panel or the [Get-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/get-cscdrconfiguration?view=skype-ps) cmdlet.
  
### To view CDR configuration information by using Skype for Business Server Control Panel

1. In Skype for Business Server Control Panel click **Monitoring and Archiving**.
    
2. A list of all your CDR configuration settings will be displayed in the **Call Detail Recording** tab; for each collection of settings you will see the collection **Name**; whether or not CDR has been enabled (the **CDR** property); and whether or not purging has been enabled (the **CDR purging** property). To see detailed information about a collection, double-click the collection, or select the appropriate collection, click **Edit**, and then click **Show Details**. Note that you can only view detailed information for a single collection of CDR configuration settings at a time.
    
## Viewing CDR configuration information by using Windows PowerShell cmdlets

You can view CDR configuration settings by using Windows PowerShell and the Get-CsCdrConfiguration cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To view CDR configuration information

- To view information about all your CDR configuration settings, type the following command in the Skype for Business Server Management Shell and then press ENTER:
    
  ```
  Get-CsCdrConfiguration
  ```

    That will return information similar to this:
    
<pre>
Identity               : Global
EnableCDR              : True
EnablePurging          : True
KeepCallDetailForDays  : 90
KeepErrorReportForDays : 60
PurgeHourOfDay         : 2
</pre>

For more information, see the help topic for the [Get-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/get-cscdrconfiguration?view=skype-ps) cmdlet.
  

