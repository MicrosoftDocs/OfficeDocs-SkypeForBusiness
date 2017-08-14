---
title: New-CsConferenceDirectory
ms.prod: SKYPEFORBUSINESS
ms.assetid: fd5a4369-10cd-4337-94df-51bcaee4fde9
---


# New-CsConferenceDirectory
[]
Creates a new conference directory for use in your organization. Conference directories are used to help dial-in conferencing users locate conference information. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsConferenceDirectory -HomePool <String> -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

Creates a new conference directory with the Identity 42. This directory will be hosted on the pool atl-cs-001.litwareinc.com.
  
    
    

```

New-CsConferenceDirectory -Identity 42 -HomePool "atl-cs-001.litwareinc.com"
```


## Detailed Description

When you create a dial-in conferencing Uniform Resource Identifier (URI), those URIs are assigned unique SIP addresses. However, SIP addresses are difficult to translate to devices that are not SIP-aware; for example, a public switched telephone network (PSTN) telephone can't translate a SIP address. Because of that, Skype for Business Server 2015 uses conference directories as a way to help these devices locate, and connect to, dial-in conferences. This is done by creating a SIP conference directory that is associated with each dial-in conferencing URI, and is identified by an integer value rather than a SIP URI. PSTN telephones and other devices can then use these numbers (rather than a SIP URI) when connecting to conferences; the directory number is included in the PSTN conference identification users enter when connecting to a dial-in conference.
  
    
    
New conference directories can be created by calling the **New-CsConferenceDirectory** cmdlet.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _HomePool_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the Registrar pool where the new conference directory will be hosted. For example:  `-Identity atl-cs-001.litwareinc.com`.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique numeric identifier for the new conference directory. Identities can be any integer value between 0 and 9999 inclusive; however, Identities must be unique. (For example, you cannot have two directories with the Identity 575.) You do not need to follow a numeric order when creating new directories. For example, you can create a directory with the Identity 999 followed by a directory with the Identity 2 followed by a directory with the Identity 438, and so on.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None. The **New-CsConferenceDirectory** cmdlet does not accept pipelined input.
  
    
    

## Return Types

Creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsConferenceDirectory](get-csconferencedirectory.md)
  
    
    
 [Move-CsConferenceDirectory](move-csconferencedirectory.md)
  
    
    
 [Remove-CsConferenceDirectory](remove-csconferencedirectory.md)
