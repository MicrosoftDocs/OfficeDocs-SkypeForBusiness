---
title: New-CsAVEdgeConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: b6bcf426-9037-4679-99dc-e94bfb8f72a6
---


# New-CsAVEdgeConfiguration
[]
Creates a new collection of configuration settings for computers running the A/V Edge service (these computers are also known as A/V Edge servers). An A/V Edge server enables internal users to share audio and video data with external users (that is, users who are not logged on to your internal network). This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsAVEdgeConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaxBandwidthPerPortKb <UInt32>] [-MaxBandwidthPerUserKb <UInt32>] [-MaxTokenLifetime <TimeSpan>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 creates a new collection of A/V Edge configuration settings for the Redmond site. In this example, the MaxTokenLifetime property is set to 4 hours (04 hours : 00 minutes : 00 seconds).
  
    
    

```

New-CsAVEdgeConfiguration -Identity site:Redmond -MaxTokenLifetime "04:00:00"
```


### EXAMPLE 2

Example 2 demonstrates how you can create a new collection of A/V Edge configuration settings in memory, and then later transform those virtual settings into an actual collection of A/V Edge settings. To do this, the first command in the example creates a new collection of settings for the Redmond site; the InMemory parameter is added to ensure that these settings are created in memory only and are not immediately applied to the Redmond site. (Because these settings exist in memory only, they must be stored in a variable, in this case, a variable named $x.)
  
    
    
In the second command, the value of the MaxTokenLifetime property is set to 4 hours (04 hours : 00 minutes : 00 seconds). The third command then uses the **Set-CsAVEdgeConfiguration** cmdlet to apply the settings stored in $x to the Redmond site.
  
    
    



```
$x = New-CsAVEdgeConfiguration -Identity site:Redmond -InMemory
$x.MaxTokenLifetime = "04:00:00"
Set-CsAVEdgeConfiguration -Instance $x
```


## Detailed Description

An A/V Edge server provides a way for audio and video traffic to be exchanged across an organization's firewall. Among other things, this enables users to use Skype for Business Server 2015 across the Internet, and then exchange audio and video data with users who have logged onto the system from inside the firewall. Edge Server configuration settings can be assigned at the global scope, the site scope, and the service scope. The A/V Edge configuration settings enable administrators to manage the amount of time that user authentication is valid before it must be renewed, and to limit the amount of bandwidth that can be used by a single user or a single port. 
  
    
    
The **New-CsAVEdgeConfiguration** cmdlet enables you to create new collections of A/V Edge configuration settings at either the site or the service scope. As noted, A/V Edge settings can also be configured at the global scope. However, you cannot create a new collection at the global scope.
  
    
    
Note that any given site or service can host, at most, a single collection of A/V Edge configuration settings. If the Redmond site already hosts a collection of A/V Edge settings, you cannot create a new collection with the Identity site:Redmond.
  
    
    
Unless instructed by Microsoft support personnel, it is recommended that you do not change the default A/V Edge configuration settings. Because of that, you will probably not need to create a new collection of settings for a site or service. 
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of A/V Edge configuration settings to be created. To create a collection of settings to be applied at the site scope, use syntax similar to this:  `-Identity site:Redmond`. (Note that this command will fail if a collection of A/V Edge configuration settings have already been applied to the Redmond site.) Settings configured at the service scope should use syntax similar to this:  `-Identity service:EdgeServer:atl-cs-001.litwareinc.com`.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-<cmdlet>**. <br/> |
| _MaxBandwidthPerPortKb_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum amount of bandwidth (in kilobits per second) that can be allocated to a single port. The maximum bandwidth can be set to any integer value between 1 and 4294967296 (4096 gigabits) per second; the default value is 3000.  <br/> |
| _MaxBandwidthPerUserKb_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum amount of bandwidth (in kilobits per second) that can be allocated to any one user. The maximum bandwidth can be set to any integer value between 1 and 4294967296 (4096 gigabits) per second; the default value is 10000.  <br/> |
| _MaxTokenLifetime_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |The maximum amount of time that an authentication token can be used before it expires and must be renewed. Token lifetimes are expressed using the following format: Days.Hours:Minutes:Seconds. For example, 13 days must be expressed like this, with a period (.) following the number of days, and colons (:) used to separate the hours, minutes, and seconds:  <br/> 13.00:00:00  <br/> The default value of 8 hours must be expressed like this:  <br/> 08:00:00  <br/> The minimum allowed token lifetime is 1 minute (00:01:00); the maximum allowed lifetime is 180 days (180.00:00:00).  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _PermissionListIgnoreSeconds_ <br/> |Optional  <br/> |System.UInt64  <br/> |PARAMVALUE: UInt64  <br/> |
   

## Input Types

None. The **New-CsAVEdgeConfiguration** cmdlet does not accept pipelined input.
  
    
    

## Return Types

Creates instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.MediaRelaySettings object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)
  
    
    
 [Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)
  
    
    
 [Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)
