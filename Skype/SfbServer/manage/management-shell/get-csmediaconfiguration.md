---
title: "Get-CsMediaConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 071c1733-07c3-4075-8745-367634e37941
description: "Returns information regarding media settings, including the supported level of encryption, whether Siren can be used as a voice codec by the Mediation Server in its interactions with Skype for Business Server 2015 clients, and the maximum allowed video resolution. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsMediaConfiguration
 
Returns information regarding media settings, including the supported level of encryption, whether Siren can be used as a voice codec by the Mediation Server in its interactions with Skype for Business Server 2015 clients, and the maximum allowed video resolution. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsMediaConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 returns all the media configurations in use in your organization; this is done simply by invoking the **Get-CsMediaConfiguration** cmdlet without any additional parameters.
  
```
Get-CsMediaConfiguration
```

### EXAMPLE 2

Example 2 returns only the media configuration that has the Identity site:Redmond1. Because identities must be unique, specifying an Identity ensures that you will never retrieve more than one item.
  
```
Get-CsMediaConfiguration -Identity site:Redmond1
```

### EXAMPLE 3

In Example 3, the Filter parameter is used to return all the media configurations at the site scope. The wildcard string site:\* ensures that Windows PowerShell will return only those media configurations that have identities beginning with the string value site:.
  
```
Get-CsMediaConfiguration -Filter site:*
```

### EXAMPLE 4

In this example, the **Get-CsMediaConfiguration** cmdlet and the **Where-Object** cmdlet are used to return all the media configurations that support (but do not require) encryption. To do this, the command first uses the **Get-CsMediaConfiguration** cmdlet to retrieve all the media configurations in use in your organization. This information is then piped to the **Where-Object** cmdlet, which applies a filter that restricts the returned data to those configurations where the EncryptionLevel property is equal to (-eq) SupportEncryption.
  
```
Get-CsMediaConfiguration | Where-Object {$_.EncryptionLevel -eq "SupportEncryption"}
```

### EXAMPLE 5

This example retrieves all media configurations defined for sites and services with names that contain the string "med". For example, this command will retrieve media configuration settings defined for the site medford1, the site TwoMedfordPlace, and the service MediationServer:redmond.litwareinc.com.
  
```
Get-CsMediaConfiguration -Filter *:*med*
```

## Detailed Description

This cmdlet retrieves one or more collections of settings that define media interactions.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |This parameter filters the results of the Get operation based on the wildcard value passed to this parameter.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the media configuration you want to retrieve. This identifier specifies the scope at which this configuration is applied (global, site, or service).  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the media configuration information from the local replica of the Central Management store, rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

The **Get-CsMediaConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings object.
  
## See also

#### 

[New-CsMediaConfiguration](new-csmediaconfiguration.md)
  
[Remove-CsMediaConfiguration](remove-csmediaconfiguration.md)
  
[Set-CsMediaConfiguration](set-csmediaconfiguration.md)

