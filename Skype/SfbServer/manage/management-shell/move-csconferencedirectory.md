---
title: "Move-CsConferenceDirectory"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c43207fa-06dd-4360-ae32-b2f17f7100d2
description: "Moves an existing conference directory from one pool to another. Conference directories are used to help dial-in conferencing users locate conference information. This cmdlet was introduced in Lync Server 2010."
---

# Move-CsConferenceDirectory
[]
Moves an existing conference directory from one pool to another. Conference directories are used to help dial-in conferencing users locate conference information. This cmdlet was introduced in Lync Server 2010.
  
```
Move-CsConferenceDirectory -Identity <XdsGlobalRelativeIdentity> -TargetPool <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 moves the conference directory with the Identity 3 to the pool atl-cs-002.litwareinc.com.
  
```
Move-CsConferenceDirectory -Identity 3 -TargetPool atl-cs-002.litwareinc.com
```

### EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In this case, however, the Force parameter is included to ensure that the move takes place even if the target pool is currently unavailable.
  
```
Move-CsConferenceDirectory -Identity 3 -TargetPool atl-cs-002.litwareinc.com -Force
```

### EXAMPLE 3

Example 3 moves all the existing conference directories to the target pool atl-cs-002.litwareinc.com. To carry out this task the command first uses the **Get-CsConferenceDirectory** cmdlet to return a collection of all the conference directories currently in use in the organization. This collection is then piped to the **Move-CsConferenceDirectory** cmdlet, which moves each directory in the collection to the target pool.
  
```
Get-CsConferenceDirectory | Move-CsConferenceDirectory -TargetPool atl-cs-002.litwareinc.com 
```

## Detailed Description

When you create a dial-in conferencing Uniform Resource Identifier (URI), those URIs are assigned unique SIP addresses. However, SIP addresses are difficult to translate to devices that are not SIP-aware; for example, a public switched telephone network (PSTN) telephone can't translate a SIP address. Because of that, Skype for Business Server 2015 uses conference directories as a way to help these devices locate, and connect to, dial-in conferences. This is done by creating a SIP conference directory that is associated with each dial-in conferencing URI, and is identified by an integer value rather than a SIP URI. PSTN telephones and other devices can then use these numbers instead of a SIP URI when connecting to conferences; the directory number is included in the PSTN conference identification users enter when connecting to a dial-in conference.
  
Occasionally, you might need to move a conference directory from one pool to another; for example, if you decommission a pool you might need to move your existing conference directories to a new location. The **Move-CsConferenceDirectory** cmdlet enables you to move conference directories to a different pool.
  
> [!IMPORTANT]
> Before you move a conference directory it is highly recommended that you make a backup copy of that directory. This can be done by using the Export-CsUserData cmdlet and the ConferenceDirectoryFilter parameter. For example, this command backs up conference directory 3 to the file C:\Logs\ConferenceDirectory3.zip: >  `Export-CsUserData -PoolFqdn "atl-cs-001.litwareinc.com" -ConferenceFilterDirectory 3 -FileName "C:\Logs\ConferenceDirectory3.zip"`
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Numeric identity of the conference directory to be moved.  <br/> |
| _TargetPool_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the pool where the conference directory is to be moved. For example:  `-Identity atl-cs-002.litwareinc.com`.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, moves the conference directory even if the target pool is currently unavailable. By default, the **Move-CsConferenceDirectory** cmdlet will not move directories if the target pool cannot be contacted. <br/> Before running the **Move-CsConferenceDirectory** cmdlet, note that if you use the -Force parameter, the dial-in code for existing meetings will be lost. Users will still be able to join meetings using a Lync client, but unable to dial-in to meetings by phone dial in. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Move-CsConferenceDirectory** cmdlet does not accept pipelined input.
  
## Return Types

None.
  
## See also

#### 

[Get-CsConferenceDirectory](get-csconferencedirectory.md)
  
[New-CsConferenceDirectory](new-csconferencedirectory.md)
  
[Remove-CsConferenceDirectory](remove-csconferencedirectory.md)

