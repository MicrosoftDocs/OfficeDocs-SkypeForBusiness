---
title: "Create or modify a collection of CDR configuration settings in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c830be5a-2a82-468d-9c46-d3fec0f79fd0
description: "Summary: Learn about Call detail recording (CDR) in Skype for Business Server."
---

# Create or modify a collection of CDR configuration settings in Skype for Business Server
 
**Summary:** Learn about Call detail recording (CDR) in Skype for Business Server.
  
Call detail recording (CDR) enables you to track usage of such things as peer-to-peer instant messaging sessions, Voice over Internet Protocol (VoIP) phone calls, and conferencing calls. This usage data includes information about who called whom, when they called, and how long they talked.
  
When you install Skype for Business Server a single, global collection of CDR configuration settings is created for you. Administrators also have the option of creating custom settings at the site scope. Whenever these site-scoped settings are used, they take precedence over the global settings. For example, if you create site-scoped settings for the Redmond site then those settings (rather than the global settings) will be used to manage CDR in Redmond.
  
You can create CDR configuration settings by using either Skype for Business Server Control Panel or the [New-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/new-cscdrconfiguration?view=skype-ps) cmdlet. You can use Skype for Business Server Control Panel or the [Set-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/set-cscdrconfiguration?view=skype-ps) cmdlet to modify existing settings. If you are using Skype for Business Server Control Panel to create or modify settings, the following options will be available to you:
  
|**UI setting**|**PowerShell parameter**|**Description**|
|:-----|:-----|:-----|
|Name  <br/> |Identity  <br/> |Unique identifier for the CDR configuration settings being created. These settings can only be created at the site scope.  <br/> |
|Enable monitoring of CDRs  <br/> |EnableCDR  <br/> |Indicates whether or not CDR is enabled.  <br/> |
|Enable purging of CDRs  <br/> |EnablePurging  <br/> |Indicates whether or not CDR records will periodically be deleted from the CDR database.  <br/> |
|Keep CDRs for maximum duration (days)  <br/> |KeepCallDetailForDays  <br/> |Indicates the number of days that CDR records will be kept in the CDR database. Any records older than the specified number of days will automatically be deleted. (Note that purging will take only place if purging has been enabled.)  <br/> |
|Keep error report data for maximum duration (days)  <br/> |KeepErrorReportForDays  <br/> |Indicates the number of days that CDR error reports are kept. Any reports older than the specified number of days will automatically be deleted. CDR error reports are diagnostic reports uploaded by client applications.  <br/> |
   
> [!NOTE]
> The New-CsCdrConfiguration and Set-CsCdrConfiguration cmdlets include additional options not available in Skype for Business Server Control Panel. See the [New-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/new-cscdrconfiguration?view=skype-ps) and the [Set-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/set-cscdrconfiguration?view=skype-ps) help topics for more information.
  
### To create CDR configuration settings by using Skype for Business Server Control Panel

1. In Skype for Business Server Control Panel click **Monitoring and Archiving**.
    
2. On the **Call Detail Recording** tab, click **New**.
    
3. In the **Select a Site** dialog box, select the site where the new configuration settings are to be created. If the dialog box is empty, that means all of your sites have already been assigned a collection of CDR configuration settings. Each site is limited to a single such collection. In that case you can either delete and then re-create the settings, or simply modify the existing settings.
    
4. In the **New Call Detail Recording (CDR) Setting** dialog, make the desired selections and then click **Commit**.
    
### To modify existing CDR configuration settings by using Skype for Business Server Control Panel

1. In Skype for Business Server Control Panel click **Monitoring and Archiving**.
    
2. Double-click the collection of settings to be modified, or select the collection, click **Edit**, and then click **Show Details**. Note that you can only modify a single collection at a time. To make the same changes to multiple collections, use the Skype for Business Server Management Shell instead.
    
3. In the **Edit Call Detail Recording (CDR) Setting** dialog, make the desired selections and then click **Commit**.
    
## Creating CDR configuration settings by using Windows PowerShell Cmdlets

You can create CDR configuration settings can also be created by using Windows PowerShell and the **New-CsCdrConfiguration** cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To create a new collection of CDR configuration settings

 This command creates a new collection of CDR configuration settings applied to the Redmond site:
    
  ```
  New-CsCdrConfiguration -Identity "site:Redmond"
  ```

### To create a collection of CDR configuration settings that disable call detail recording

 Because no parameters (other than the mandatory Identity parameter) were specified in the preceding command, the new collection of configuration settings will use the default values for all its properties. To create settings that use different property values, simply include the appropriate parameter and parameter value. For example, to create a collection of Call Detail configuration settings that, by default, allow disable Call Detail recording use a command like this:
    
  ```
  New-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $False
  ```

### To specify multiple property values when creating a new collection of CDR configuration settings

 You can modify multiple property values by including multiple parameters. For example, this command configures the new settings to keep Call Detail records for 30 days and error reports for 90 days:
    
  ```
  New-CsCdrConfiguration -Identity "site:Redmond" -KeepCallDetailForDays 30 -KeepErrorReportForDays 90
  ```

For more information, see the help topic for the [New-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/new-cscdrconfiguration?view=skype-ps) cmdlet.
  

