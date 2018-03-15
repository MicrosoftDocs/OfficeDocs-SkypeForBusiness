---
title: "Get-CsConferenceDirectory"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2b7927ab-c6b3-42ce-9c27-9825cd47fd77
description: "Returns information about the conference directories configured for use in your organization. Conference directories are used to help dial-in conferencing users locate conference information. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsConferenceDirectory
 
Returns information about the conference directories configured for use in your organization. Conference directories are used to help dial-in conferencing users locate conference information. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsConferenceDirectory [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns information about all the conference directories configured for use in your organization. 
  
```
Get-CsConferenceDirectory
```

### EXAMPLE 2

Example 2 returns information about the conference directory with the Identity 2. Because identities must be unique this command will never return more than a single conference directory.
  
```
Get-CsConferenceDirectory -Identity 2
```

### EXAMPLE 3

Example 3 returns all the conference directories housed on the service UserServer:atl-cs-001.litwareinc.com. To do this, the command first calls the **Get-CsConferenceDirectory** cmdlet without any parameters in order to return a collection of all the conference directories found in your organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those directories where the ServiceID matches the string value "UserServer:atl-cs-001.litwareinc.com".
  
```
Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "UserServer:atl-cs-001.litwareinc.com"}
```

## Detailed Description

When you create a dial-in conferencing Uniform Resource Identifier (URI), those URIs are assigned unique SIP addresses. However, SIP addresses are difficult for devices that are not SIP-aware to translate; for example, a public switched telephone network (PSTN) telephone can't translate a SIP address. Because of that, Skype for Business Server 2015 uses conference directories as a way to help these devices locate, and connect to, dial-in conferences. This is done by creating a SIP conference directory that is associated with each dial-in conferencing URI, and is identified by an integer value rather than a SIP URI. PSTN telephones and other devices can use these numbers (rather than a SIP URI) when connecting to conferences; the directory number is included in the PSTN conference identification users enter when connecting to a dial-in conference.
  
The **Get-CsConferenceDirectory** cmdlet enables you to return information about all the conference directories configured for use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards to specify the Identity of the conference directory (or directories) to be retrieved. Because directory Identities are numeric, this parameter might be of minimal value. However, this syntax will return all the conference directories that have an Identity that begins with the number 3:  `-Filter "3*"`.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Numeric identifier (for example, 7) of the conference directory to be returned. If this parameter is omitted, then the **Get-CsConferenceDirectory** cmdlet returns information about all the conference directories in use in your organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the conference directory data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsConferenceDirectory** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsConferenceDirectory** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories object.
  
## See also

#### 

[Move-CsConferenceDirectory](move-csconferencedirectory.md)
  
[New-CsConferenceDirectory](new-csconferencedirectory.md)
  
[Remove-CsConferenceDirectory](remove-csconferencedirectory.md)

