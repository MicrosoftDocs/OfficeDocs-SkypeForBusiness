---
title: "Set-CsQoEConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 199f0127-7444-4f88-993a-8e6a33fdcb61
description: "Modifies an existing collection of QoE (Quality of Experience) settings. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsQoEConfiguration
[]
Modifies an existing collection of QoE (Quality of Experience) settings. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsQoEConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command in Example 1 uses the **Set-CsQoEConfiguration** cmdlet to modify the Quality of Experience settings for the Redmond site (-Identity site:Redmond). The new settings turn off QoE by setting the EnableQoE parameter to False.
  
```
Set-CsQoEConfiguration -Identity site:Redmond -EnableQoE $False
```

### EXAMPLE 2

This command modifies QoE settings that apply to the Dublin site. In this example we've set the KeepQoEDataForDays parameter to 45, so QoE data will be purged from the database after 45 days. In addition, we've set the PurgeHourOfDay parameter to 4, meaning any data older than the 45 days we just specified will be purged at 4:00 AM.
  
Note: If you have enabled QoE and call detail recording (CDR), for performance reasons it's a good idea to make sure the PurgeHourOfDay setting is different for QoE than for CDR.
  
```
Set-CsQoEConfiguration -Identity site:Dublin -KeepQoEDataForDays 45 -PurgeHourOfDay 4
```

## Detailed Description

QoE metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay). These metrics are stored in a database apart from other data (such as call detail records), which allows you to enable and disable QoE independent of other data recording. Use this cmdlet to modify settings that configure QoE at the global or site level.
  
QoE is part of the Monitoring Server role; therefore Monitoring Server must be deployed on your Skype for Business Server 2015 installation before QoE recording takes effect or any QoE data can be collected.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableExternalConsumer_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether an external consumer is able to receive QoE reports.  <br/> |
| _EnablePurging_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether records will be purged after the duration defined in the KeepQoEDataForDays property has elapsed.  <br/> |
| _EnableQoE_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether QoE records will be collected and saved to the monitoring database.  <br/> Note that even if EnableQoE is set to True, QoE data will not be collected unless a Monitoring Server has been deployed and associated with a Registrar pool.  <br/> |
| _ExternalConsumerIssuedCertId_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.BaseTypes.IssuedCertId  <br/> |The certificate ID of the certificate that allows access to the external consumer web service.  <br/> |
| _ExternalConsumerName_ <br/> |Optional  <br/> |System.String  <br/> |The friendly name of the external consumer of the QoE report.  <br/> |
| _ExternalConsumerURL_ <br/> |Optional  <br/> |System.String  <br/> |The URL of the external consumer to which the QoE reports will be posted.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the settings you want to modify. Possible values are global and site:\<site name\>, where \<site name\> is the name of the site in your Skype for Business Server 2015 deployment to which you want to apply the changes.  <br/> |
| _Instance_ <br/> |Optional  <br/> |QoESettings  <br/> |An object reference to a QoE configuration object. This object must be of type QoESettings and can be retrieved by calling the **Get-CsQoEConfiguration** cmdlet. <br/> |
| _KeepQoEDataForDays_ <br/> |Optional  <br/> |System.UInt32  <br/> |The number of days QoE data will be stored before being purged from the database. This value is ignored if EnablePurging is set to False.  <br/> Must be a value from 1 through 2562.  <br/> |
| _PurgeHourOfDay_ <br/> |Optional  <br/> |System.UInt32  <br/> |The hour of the day that QoE records that have exceeded the number of days specified in the KeepQoEDataForDays property will be purged.  <br/> Must be a value 0 through 23, representing the hour of the day. For example, 0 would be midnight, 13 would be 1:00 PM.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings object. Accepts pipelined input of QoE configuration objects.
  
## Return Types

The **Set-CsQoEConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings object.
  
## See also

#### 

[New-CsQoEConfiguration](new-csqoeconfiguration.md)
  
[Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)
  
[Get-CsQoEConfiguration](get-csqoeconfiguration.md)

