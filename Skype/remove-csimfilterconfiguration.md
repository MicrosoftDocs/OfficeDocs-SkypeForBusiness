---
title: Remove-CsImFilterConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 0c6f5f69-ae41-46d6-b817-fa1c6751c615
---


# Remove-CsImFilterConfiguration
[]
Removes the specified instant messaging (IM) filter configuration. (IM filter settings are used to prevent users from sending instant messages that contain hyperlinks.) This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsImFilterConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

In Example 1, the **Remove-CsImFilterConfiguration** cmdlet is used to remove the IM filter configuration with the Identity site:Redmond. When an IM filter configuration is removed from a site, that site will automatically begin using the global settings in its place.
  
    
    

```

Remove-CsImFilterConfiguration -Identity site:Redmond
```


### EXAMPLE 2

In Example 2, all the IM filter configurations at the site scope are removed. To carry out this task, the command first uses the **Get-CsImFilterConfiguration** cmdlet and the Filter parameter to return all the configurations at the site scope; the wildcard string site:* tells the **Get-CsImFilterConfiguration** cmdlet to return only those configurations that have an Identity that begins with the string value site:. The filtered collection of configurations is then piped to the **Remove-CsImFilterConfiguration** cmdlet, which deletes each configuration in the collection.
  
    
    

```
Get-CsImFilterConfiguration -Filter site:* | Remove-CsImFilterConfiguration
```


## Detailed Description

When sending instant messages, users can embed a Uniform Resource Identifier (URI) within the text of that message to refer other participants in the conversation to a particular website or share. Skype for Business Server 2015 can be configured so that hyperlinks with certain prefixes are blocked or are not active. (In other words, the participants can't simply click the link and be taken to the site the URI refers to; they must copy and paste the link manually into a browser.) 
  
    
    
The **Remove-CsImFilterConfiguration** cmdlet removes the IM filter configuration for a specified identity (such as a specific site). Running this cmdlet against the Global identity will simply reset the global configuration to the default settings.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identity of the configuration to be removed. This will be either Global or Site:<site name> (where <site name> represents the name of the site to which the settings apply).  <br/> Full Data Type: Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration object. Accepts pipelined input of IM filter configuration objects.
  
    
    

## Return Types

Removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration.
  
    
    

## See also


#### 


  
    
    
 [New-CsImFilterConfiguration](new-csimfilterconfiguration.md)
  
    
    
 [Set-CsImFilterConfiguration](set-csimfilterconfiguration.md)
  
    
    
 [Get-CsImFilterConfiguration](get-csimfilterconfiguration.md)
