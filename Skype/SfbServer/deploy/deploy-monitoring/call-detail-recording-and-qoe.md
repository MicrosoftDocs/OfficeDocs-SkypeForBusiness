---
title: "Configure call detail recording and Quality of Experience settings in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 009a0499-4f8c-450d-9c72-a565a08e9f7a
description: "Summary: Learn how to configure CDR and QoE in Skype for Business Server."
---

# Configure call detail recording and Quality of Experience settings in Skype for Business Server
 
**Summary:** Learn how to configure CDR and QoE in Skype for Business Server.
  
Configure CDR and QoE monitoring using SQL Server Reporting Services reports for Skype for Business Server.
  
## Configure CDR and QoE

After you have associated a monitoring store with a Front End pool, set up the monitoring store, and then installed and configured SQL Server Reporting Services and Monitoring Reports you can manage Call Detail Recording (CDR) and Quality of Experience (QoE) monitoring by using Skype for Business Server Management Shell. Skype for Business Server Management Shell cmdlets allow you to enable and disable CDR and/or QoE monitoring for a particular site or for your entire Skype for Business Server deployment; that can be done with a command as simple as this:
  
```
Set-CsQoEConfiguration -Identity "global" -EnableQoE $False
```

When you install Skype for Business Server, you will also install a predefined collection of global configuration settings for both CDR and QoE. Default values for some of the more commonly-used settings used by Call Detail Recording are shown in the following table:
  
|**Property**|**Description**|**Default Value**|
|:-----|:-----|:-----|
|EnableCDR  <br/> |Indicates whether or not CDR is enabled. If True, all CDR records will be collected and written to the monitoring database.  <br/> |True  <br/> |
|EnablePurging  <br/> |Indicates whether or not CDR records will periodically be deleted from the database. If True, records will be deleted after the time period specified by the properties KeepCallDetailForDays (for CDR records) and KeepErrorReportForDays (for CDR errors). If False, CDR records will be maintained indefinitely.  <br/> |True  <br/> |
|KeepCallDetailForDays  <br/> |Indicates the number of days that CDR records will be kept in the database; any records older than the specified number of days will automatically be deleted. However, this will occur only if purging has been enabled.  <br/> KeepCallDetailForDays can be set to any integer value between 1 and 2562 days (approximately 7 years).  <br/> |60 days  <br/> |
|KeepErrorReportForDays  <br/> |Indicates the number of days that CDR error reports are kept; any reports older than the specified number of days will automatically be deleted. CDR error reports are diagnostic reports uploaded by client applications such as Skype for Business Server.  <br/> You can set this property to any integer value between 1 and 2562 days.  <br/> |60 days  <br/> |
   
Similarly, default values for selected QoE settings are shown in this table:
  
|**Property**|**Description**|**Default Value**|
|:-----|:-----|:-----|
|EnableQoE  <br/> |Indicates whether or not QoE monitoring is enabled. If True, all QoE records will be collected and written to the monitoring database.  <br/> |True  <br/> |
|EnablePurging  <br/> |Indicates whether or not QoE records will periodically be deleted from the database. If True, records will be deleted after the time period specified by the KeepQoEDataForDays property. If False, QoE records will be maintained indefinitely.  <br/> |True  <br/> |
|KeepQoEDataForDays  <br/> |Indicates the number of days that QoE records will be kept in the database; any records older than the specified number of days will automatically be deleted. However, this will occur only if purging has been enabled.  <br/> KeepCallDetailForDays can be set to any integer value between 1 and 2562 days.  <br/> |60 days  <br/> |
   
If you need to modify these global settings you can do so by using the Set-CsCdrConfiguration and the Set-CsQoEConfiguration cmdlets. For example, this command (run from within the Skype for Business Server Management Shell) disables CDR monitoring at the global scope; that's done by setting the EnableCDR property to False ($False):
  
```
Set-CsCdrConfiguration -Identity "global" -EnableCDR $False
```

Note that disabling monitoring does not dissociate the monitoring store from the Front End pool, nor does it uninstall or otherwise affect the backend monitoring database. When you use Skype for Business Server Management Shell to disable either CDR or QoE monitoring all you really do is temporarily stop Skype for Business Server from collecting and archiving monitoring data. If you want to resume, in this case, the collection and archiving of CDR data, all you need to do is set the EnableCDR property back to True ($True):
  
```
Set-CsCdrConfiguration -Identity "global" -EnableCDR $True
```

Similarly, this command disables the purging of QoE records at the global scope:
  
```
Set-CsQoEConfiguration -Identity "global" -EnablePurging $False
```

In addition to the global settings, CDR and QoE configurations settings can be assigned to the site scope. This provides additional management flexibility when it comes to monitoring; for example, an administrator can enable CDR monitoring for the Redmond site but disable CDR monitoring for the Dublin site. To create new CDR configuration settings at the site scope, use a command similar to this:
  
```
New-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $False
```

Keep in mind that settings configured at the site scope take precedence over settings configured at the global scope. For example, suppose CDR monitoring is enabled at the global scope, but disabled at the site scope (for the Redmond site). That means that call detail recording information will not be archived for users in the Redmond site. However, users in other sites (that is, users managed by the global settings instead of the Redmond site settings) will have their call detail recording information archived.
  
New QoE configuration settings can be created at the site scope by using a command like this one:
  
```
New-CsQoEConfiguration -Identity "site:Redmond" -KeepQoEDataForDays 15
```

For more information, type the following commands from within the Skype for Business Server Management Shell:
  
```
Get-Help New-CsCdrConfiguration | more
Get-Help Set-CsCdrConfiguration | more
Get-Help New-CsQoEConfiguration | more
Get-Help Set-CsQoEConfiguration | more
```
