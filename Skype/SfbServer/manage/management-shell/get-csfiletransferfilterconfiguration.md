---
title: "Get-CsFileTransferFilterConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6f43c203-acd6-4dbf-a071-752bf0c1727c
description: "Returns the file transfer filter configurations in your organization. These configurations are used to block a user's ability to transfer certain types of files (for example, files with a .vbs or .ps1 file extension) using a Skype for Business Server 2015 client. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsFileTransferFilterConfiguration
[]
Returns the file transfer filter configurations in your organization. These configurations are used to block a user's ability to transfer certain types of files (for example, files with a .vbs or .ps1 file extension) using a Skype for Business Server 2015 client. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsFileTransferFilterConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns a collection of all the file transfer filter configurations in use in your organization. This is the default behavior any time you call the **Get-CsFileTransferFilterConfiguration** cmdlet without any additional parameters.
  
```
Get-CsFileTransferFilterConfiguration
```

### EXAMPLE 2

Example 2 returns a single file transfer filter configuration: the configuration that has the Identity site:Redmond. Because identities must be unique, this command can never return more than one configuration.
  
```
Get-CsFileTransferFilterConfiguration -Identity site:Redmond
```

### EXAMPLE 3

Example 3 uses the Filter parameter to return a collection of all the file transfer filter configurations at the site level. The Filter value "site:*" instructs the **Get-CsFileTransferFilterConfiguration** cmdlet to return only those configurations that have an Identity that begins with the string value "site:".
  
```
Get-CsFileTransferFilterConfiguration -Filter site:*
```

### EXAMPLE 4

The command shown in Example 4 returns only those file transfer filter configurations that include .xls in their list of prohibited file extensions. To do this, the **Get-CsFileTransferFilterConfiguration** cmdlet is first used to return a collection of all the configurations in use in your organization. That collection is then piped to the **Where-Object** cmdlet, which applies a filter that restricts the returned data to those configurations where the Extensions property includes (-contains) the string value ".xls".
  
```
Get-CsFileTransferFilterConfiguration | Where-Object {$_.Extensions -contains ".xls"}
```

### EXAMPLE 5

Example 5 returns all the file transfer filter configurations that are currently disabled. To accomplish this task, the **Get-CsFileTransferFilterConfiguration** cmdlet is used to return a collection of all the configurations in use in your organization. This collection is then piped to the **Where-Object** cmdlet, which, in turn, selects only those configuration where the Enabled property is equal to (-eq) False ($False).
  
```
Get-CsFileTransferFilterConfiguration | Where-Object {$_.Enabled -eq $False}
```

### EXAMPLE 6

Example 6 shows a complete list of the file extensions prohibited by the global file transfer filter configuration. The command begins with a call to the **Get-CsFileTransferFilterConfiguration** cmdlet, specifying the Global configuration. The returned information is then piped to the **Select-Object** cmdlet, which uses the ExpandProperty parameter to "expand" the value of the Extensions property. That results in the complete list of file extensions being displayed on the screen, one file extension per line.
  
```
Get-CsFileTransferFilterConfiguration -Identity Global | Select-Object -ExpandProperty Extensions
```

## Detailed Description

When sending instant messages, users can attach and send files to the other participants in the conversation. Skype for Business Server 2015 can be configured so that files with certain extensions--typically extensions of file types that could potentially prove harmful--are not allowed to be sent using the Skype for Business Server 2015 client.
  
The **Get-CsFileTransferFilterConfiguration** cmdlet provides a way for you to retrieve a particular collection of settings (these settings can be configured at the global scope or at the site scope). File transfer filter configurations include the list of file extensions that are blocked from transfers, to what degree filtering is enabled (all file transfers are blocked or only files with the specified extensions), and whether file transfer filtering is enabled.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the file transfer filter configurations to be returned. For example, to return all the file transfer filter configurations at the site scope, use this syntax:  `-Filter "site:*"`. By design, file transfer filter configurations that have an Identity (the only property you can filter for) that begins with the string value "site:" were configured at the site scope.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the file transfer filter configuration you want to retrieve. To refer to the global settings, use this syntax:  `-Identity global`. To refer to settings configured at the site scope, use syntax similar to this:  `-Identity site:Redmond`. Note that you cannot use wildcard values when specifying an Identity. If you want to use wildcards, use the Filter parameter instead.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the file transfer filter configuration from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

The **Get-CsFileTransferFilterConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileTransferFilterConfiguration object.
  
## See also

#### 

[New-CsFileTransferFilterConfiguration](new-csfiletransferfilterconfiguration.md)
  
[Remove-CsFileTransferFilterConfiguration](remove-csfiletransferfilterconfiguration.md)
  
[Set-CsFileTransferFilterConfiguration](set-csfiletransferfilterconfiguration.md)

