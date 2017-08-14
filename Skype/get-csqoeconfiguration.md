---
title: Get-CsQoEConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: e2ed87e0-a5ae-41a2-8572-bda0070c59dc
---


# Get-CsQoEConfiguration
[]
Retrieves one or more collections of Quality of Experience (QoE) settings. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Get-CsQoEConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

This example uses the **Get-CsQoEConfiguration** cmdlet to return a collection of all the QoE settings configured for use in your organization.
  
    
    

```

Get-CsQoEConfiguration
```


### EXAMPLE 2

Example 2 uses the Identity parameter to ensure that the **Get-CsQoEConfiguration** cmdlet returns only the QoE settings with the Identity site:Redmond.
  
    
    

```
Get-CsQoEConfiguration -Identity site:Redmond
```


### EXAMPLE 3

In Example 3 the Filter parameter is used to return all the QoE settings that have been configured at the site scope. The wildcard "site:*" returns all the QoE settings that have an Identity beginning with the string value site:. Settings that meet those criteria are settings that have been configured at the site scope.
  
    
    

```
Get-CsQoEConfiguration -Filter site:*
```


### EXAMPLE 4

Example 4 returns a collection of all the QoE settings where the KeepQoEDataForDays property is less than 30 days. To do this, the command first uses the **Get-CsQoEConfiguration** cmdlet to return a collection of all the QoE settings configured in the organization. That collection is then piped to the **Where-Object** cmdlet, which applies a filter that limits the returned data to those settings that have a KeepQoEDataForDays value of less than 30 days.
  
    
    

```
Get-CsQoEConfiguration | Where-Object {$_.KeepQoEDataForDays -lt 30}
```


## Detailed Description

QoE metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay). These metrics are stored in a database apart from other data (such as call detail records), which allows you to enable and disable QoE independent of other data recording. Use this cmdlet to retrieve settings that configure QoE at the global or site level.
  
    
    
QoE is part of the Monitoring Server role; therefore Monitoring Server must be deployed on your Skype for Business Server 2015 installation before QoE recording takes effect or any QoE data can be collected.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a collection (or multiple collections) of QoE configuration settings. To return a collection of all the settings configured at the site scope, use this syntax:  <br/>  `-Filter site:*` <br/> To return a collection of all the settings that have the string value "Western" somewhere in their Identity (the only property you can filter on) use this syntax:  <br/>  `-Filter *Western*` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the settings you want to retrieve. Possible values are global and site:<site name>, where <site name> is the name of the site in your Skype for Business Server 2015 deployment to which you want to apply the changes.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the settings from the local replica of the Central Management store.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

The **Get-CsQoEConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings object.
  
    
    

## See also


#### 


  
    
    
 [New-CsQoEConfiguration](new-csqoeconfiguration.md)
  
    
    
 [Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)
  
    
    
 [Set-CsQoEConfiguration](set-csqoeconfiguration.md)
