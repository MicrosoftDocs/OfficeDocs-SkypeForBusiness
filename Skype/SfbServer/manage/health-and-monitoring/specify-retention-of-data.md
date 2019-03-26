---
title: "Specify retention of CDR data in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c0fd6056-87bc-4136-902a-f1b37cd3a1ca
description: "Summary: Learn how to manage call detail recording (CDR) data for Skype for Business Server."
---

# Specify retention of CDR data in Skype for Business Server
 
**Summary:** Learn how to manage call detail recording (CDR) data for Skype for Business Server.
  
By default, call detail recording (CDR) data is purged after 60 days. You can use the settings on the **Call Detail Recording** page to retain the data for a longer or shorter period of time. If you disable CDR, data that was captured before CDR was enabled will also be subject to purging.
  
> [!NOTE]
> You should configure CDR and Quality of Experience (QoE) to retain data for the same number of days. Each call in the call detail reports (CDRs), available from the Monitoring Server Reports webpage, includes CDR and QoE information. If the purging duration for CDR and QoE is different, some calls might only include CDR data, while other may only include QoE data. 
  
Use the following procedures to configure purge settings for CDR data. 
  
### To specify retention of CDR data

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Call Detail Recording**.
    
4. On the **Call Detail Recording** page, click the appropriate site in the table, click **Edit**, and then click **Show Details**.
    
5. To turn on purging, select **Enable purging of CDRs**.
    
6. In **Keep CDRs for maximum duration (days):** select the maximum number of days that call detail recordings should be retained.
    
7. In **Keep error report data for maximum duration (days):** select the maximum number of days that error reports should be retained.
    
8. Click **Commit**.
    
## Specifying CDR retention by using Windows PowerShell cmdlets

You can create CDR retention settings by using Windows PowerShell and the Set-CsCdrConfiguration cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To specify CDR retention for a specific location

- This command enables purging of CDR data for the Redmond site, and configures the site to maintain both CDR data and error reports data for 20 days.
    
  ```
  Set-CsCdrConfiguration -Identity "site:Redmond" -EnablePurging -KeepCallDetailForDays 20 -KeepErrorReportForDays 20
  ```

### To specify CDR retention for multiple locations

- This command configures CDR retention for all the CDR configuration settings in use in an organization.
    
  ```
  Get-CsCdrConfiguration | Set-CsCdrConfiguration-EnablePurging -KeepCallDetailForDays 20 -KeepErrorReportForDays 20
  ```

For more information, see the help topic for the [Set-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/set-cscdrconfiguration?view=skype-ps) cmdlet.
  
## See also

[Call detail recording (CDR) in Skype for Business Server](call-detail-recording-cdr.md)
