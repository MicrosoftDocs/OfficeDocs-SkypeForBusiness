---
title: "Create Quality of Experience configuration settings in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 64f05569-07c7-4f76-a96b-ea4125a510d5
description: "Summary: Learn about Quality of Experience (QoE) settings in Skype for Business Server."
---

# Create Quality of Experience configuration settings in Skype for Business Server
 
**Summary:** Learn about Quality of Experience (QoE) settings in Skype for Business Server.
  
Quality of Experience (QoE) metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay). These metrics are stored in a database apart from other data (such as call detail records), which allows you to enable and disable QoE independent of other data recording.
  
When you install Skype for Business Server, a single, global collection of QoE configuration settings is created for you. Administrators also have the option of creating custom settings at the site scope. Whenever these site-scoped settings are used, they take precedence over the global settings. For example, if you create site-scoped settings for the Redmond site then those settings (rather than the global settings) will be used to manage QoE in Redmond.
  
QoE configuration settings can be created by using either Skype for Business Server Control Panel or the [New-CsQoEConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csqoeconfiguration?view=skype-ps) cmdlet. If you are using Skype for Business Server Control Panel to create new settings the following options will be available to you:
  
|**UI setting**|**PowerShell parameter**|**Description**|
|:-----|:-----|:-----|
|Name  <br/> |Identity  <br/> |Unique identifier for the settings to be created. QoE configuration settings can only be created at the site scope.  <br/> |
|Enable monitoring of QoE data  <br/> |EnableQoE  <br/> |Specifies whether QoE records will be collected and saved to the monitoring database.  <br/> |
|Enable purging of QoE data  <br/> |EnablePurging  <br/> |Specifies whether records will be purged after the duration defined in the **Keep QoE data for a maximum duration (days)** property has elapsed. <br/> |
|Keep QoE data for maximum duration (days)  <br/> |KeepQoEDataForDays  <br/> |Number of days QoE data will be stored before being purged from the database. This value is ignored if purging is disabled.  <br/> |
   
> [!NOTE]
> The New-CsQoEConfiguration cmdlet includes additional options not available in Skype for Business Server Control Panel. For more information, see the [New-CsQoEConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csqoeconfiguration?view=skype-ps) help topic.
  
### To create QoE configuration settings by using Skype for Business Server Control Panel

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see **Delegate Setup Permissions**.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Quality of Experience Data**.
    
4. On the **Quality of Experience Data** page, click **New**.
    
5. In **Select a Site**, click the site to which the policy is to be applied, and click **OK**.
    
6. In **New Quality of Experience Setting**, do the following:
    
   - Select **Enable monitoring of QoE data** to turn on monitoring.
    
   - Select **Enable purging of QoE data** to turn on purging.
    
   - In **Keep QoE for maximum duration (days)**, select the maximum number of days that QoE records should be retained.
    
7. Click **Commit**.
    
## Creating QoE Configuration Settings by Using Windows PowerShell Cmdlets

You can create QoE configuration settings by using Windows PowerShell and the New-CsQoEConfiguration cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To create a new collection of QoE configuration settings

 This command creates a new collection of QoE configuration settings applied to the Redmond site:
    
  ```
  New-CsQoEConfiguration -Identity "site:Redmond"
  ```

### To create a new collection of QoE configuration settings where QoE monitoring is disabled

 Because no parameters (other than the mandatory Identity parameter) were specified in the preceding command, the new collection of configuration settings will use the default values for all its properties. To create settings that use different property values, simply include the appropriate parameter and parameter value. For example, to create a collection of Quality of Experience configuration settings that, by default, allow disable QoE recording use a command like this:
    
  ```
  New-CsQoEConfiguration -Identity "site:Redmond" -EnableQoE $False
  ```

### To specify multiple property values when creating a new collection of QoE configuration settings

 You can multiple property values by including multiple parameters. For example, this command configures the new settings to keep QoE data for 30 days and to purge old data at 3:00 AM:
    
  ```
  New-CsQoEConfiguration -Identity "site:Redmond" -KeepQoEDataForDays 30 -PurgeHourOfDay 3
  ```

For more information, see the help topic for the [New-CsQoEConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csqoeconfiguration?view=skype-ps) cmdlet.
  

