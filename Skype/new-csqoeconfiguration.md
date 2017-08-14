---
title: New-CsQoEConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 4fc607d5-1a85-4de5-9d18-39d0425c82dc
---


# New-CsQoEConfiguration
[]
Creates a new collection of QoE (Quality of Experience) settings. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsQoEConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableExternalConsumer <$true | $false>] [-EnablePurging <$true | $false>] [-EnableQoE <$true | $false>] [-ExternalConsumerIssuedCertId <IssuedCertId>] [-ExternalConsumerName <String>] [-ExternalConsumerURL <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-KeepQoEDataForDays <UInt32>] [-PurgeHourOfDay <UInt32>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command in Example 1 uses the **New-CsQoEConfiguration** cmdlet to create a new set of Quality of Experience settings with the Identity site:Redmond. In addition to the Identity site:Redmond, the new settings also have the EnableQoE property set to False. Because site settings take precedence over global settings, this means that QoE will be disabled for the Redmond site, regardless of whether or not QoE has been enabled at the global scope.
  
    
    

```

New-CsQoEConfiguration -Identity site:Redmond -EnableQoE $False
```


### EXAMPLE 2

This command creates new QoE settings that apply to the Dublin site. In this example we've set the KeepQoEDataForDays parameter to 30, so QoE data will be purged from the database after 30 days rather than the default 60 days. In addition, we've set the PurgeHourOfDay parameter to 4, meaning any data older than the 30 days we just specified will be purged at 4:00 AM.
  
    
    
Note: If you have enabled QoE and call detail recording (CDR), for performance reasons it's a good idea to make sure the PurgeHourOfDay setting is different for QoE than for CDR.
  
    
    



```
New-CsQoEConfiguration -Identity site:Dublin -KeepQoEDataForDays 30 -PurgeHourOfDay 4
```


## Detailed Description

QoE metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay). These metrics are stored in a database apart from other data (such as call detail records), which allows you to enable and disable QoE independent of other data recording. Use this cmdlet to create settings that configure QoE at the site level. (Settings at the global level exist by default and cannot be removed.) 
  
    
    
QoE is part of the Monitoring Server role; therefore Monitoring Server must be deployed on your Skype for Business Server 2015 installation before QoE recording takes effect or any QoE data can be collected.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The site to which the new settings apply. This must be entered in the format site:<site name>, where <site name> is the name of the site in your Skype for Business Server 2015 deployment.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableExternalConsumer_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether an external consumer is able to receive QoE reports.  <br/> Default: False  <br/> |
| _EnablePurging_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether records will be purged after the duration defined in the KeepQoEDataForDays property has elapsed.  <br/> Default: True  <br/> |
| _EnableQoE_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether QoE records will be collected and saved to the monitoring database.  <br/> Note that even if EnableQoE is set to True, QoE data will not be collected unless a Monitoring Server has been deployed and associated with a Registrar pool.  <br/> Default: True  <br/> |
| _ExternalConsumerIssuedCertId_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.BaseTypes.IssuedCertId  <br/> |The certificate ID of the certificate that allows access to the external consumer web service.  <br/> |
| _ExternalConsumerName_ <br/> |Optional  <br/> |System.String  <br/> |The friendly name of the external consumer of the QoE report.  <br/> |
| _ExternalConsumerURL_ <br/> |Optional  <br/> |System.String  <br/> |The URL of the external consumer to which the QoE reports will be posted.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-<cmdlet>**. <br/> |
| _KeepQoEDataForDays_ <br/> |Optional  <br/> |System.UInt32  <br/> |The number of days QoE data will be stored before being purged from the database. This value is ignored if EnablePurging is set to False.  <br/> Must be a value from 1 through 2562.  <br/> Default: 60  <br/> |
| _PurgeHourOfDay_ <br/> |Optional  <br/> |System.UInt32  <br/> |The hour of day that QoE records that have exceeded the number of days specified in the KeepQoEDataForDays property will be purged.  <br/> Must be a value 0 through 23, representing the hour of the day. For example, 0 would be midnight, 13 would be 1:00 PM. Default: 1  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings.
  
    
    

## See also


#### 


  
    
    
 [Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)
  
    
    
 [Set-CsQoEConfiguration](set-csqoeconfiguration.md)
  
    
    
 [Get-CsQoEConfiguration](get-csqoeconfiguration.md)
