---
title: Remove-CsConferenceDirectory
ms.prod: SKYPEFORBUSINESS
ms.assetid: c2c62a14-f3f3-472f-bf91-1fcea9e45425
---


# Remove-CsConferenceDirectory
[]
Removes an existing conference directory. Conference directories are used to help dial-in conferencing users locate conference information. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsConferenceDirectory -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 deletes the conference directory with the Identity 2.
  
    
    

```

Remove-CsConferenceDirectory -Identity 2
```


### EXAMPLE 2

Example 2 deletes all the conference directories found on the service UserServer:atl-cs-001.litwareinc.com. To do this, the command first calls the **Get-CsConferenceDirectory** cmdlet without any parameters; that returns a collection of all the conference directories currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those directories hosted on the service UserServer:atl-cs-001.litwareinc.com. In turn, that filtered collection is piped to, and deleted by, the **Remove-CsConferenceDirectory** cmdlet.
  
    
    

```
Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "UserServer:atl-cs-001.litwareinc.com"} | Remove-CsConferenceDirectory
```


## Detailed Description

When you create a dial-in conferencing Uniform Resource Identifier (URI) those URIs are assigned unique SIP addresses. However, SIP addresses are difficult to translate to devices that are not SIP-aware; for example, a public switched telephone network (PSTN) telephone can't translate a SIP address. Because of that, Skype for Business Server 2015 uses conference directories as a way to help these devices locate, and connect to, dial-in conferences. This is done by creating a SIP conference directory that is associated with each dial-in conferencing URI, and is identified by an integer value rather than a SIP URI. PSTN telephones and other devices can then use these numbers (rather than a SIP URI) when connecting to conferences; the directory number is included in the PSTN conference identification users enter when connecting to a dial-in conference.
  
    
    
Conference directories are created by using the **New-CsConferenceDirectory** cmdlet. Occasionally, you might need to delete one or more of these directories; for example, you might need to decommission the pool where the directories were hosted. Conference directories can be removed by calling the **Remove-CsConferenceDirectory** cmdlet. Note that if you need to move a directory from one pool to another, you can do so by calling the **Move-CsConferenceDirectory** cmdlet.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Numeric identity of the conference directory to be removed.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, removes the conference directory even if the pool that hosts the directory is currently unavailable. By default, the **Remove-CsConferenceDirectory** cmdlet will not remove directories if the corresponding pool cannot be contacted. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories object. The **Remove-CsConferenceDirectory** cmdlet accepts pipelined input of conference directory objects.
  
    
    

## Return Types

None. Instead, the **Removes-CsConferenceDirectory** cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsConferenceDirectory](get-csconferencedirectory.md)
  
    
    
 [Move-CsConferenceDirectory](move-csconferencedirectory.md)
  
    
    
 [New-CsConferenceDirectory](new-csconferencedirectory.md)
