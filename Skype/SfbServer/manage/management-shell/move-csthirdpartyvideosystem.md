---
title: "Move-CsThirdPartyVideoSystem"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c1c06149-47f2-4d65-9648-51ba449d64b9
description: "Moves an Active Directory contact object that represents a third-party video system. A third-party video system is a video teleconferencing (VTC) device that provides users with telepresence: the ability to participate in online meetings and conferences with full audio and video capabilities."
---

# Move-CsThirdPartyVideoSystem
 
Moves an Active Directory contact object that represents a third-party video system. A third-party video system is a video teleconferencing (VTC) device that provides users with telepresence: the ability to participate in online meetings and conferences with full audio and video capabilities.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Move-CsThirdPartyVideoSystem -Identity <UserIdParameter> <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 moves the third-party video system with the Identity CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com to the Registrar pool atl-cs-001.litwareinc.com.
  
```
Move-CsThirdPartyVideoSystem -Identity "CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com" -Target "atl-cs-001.litwareinc.com" 
```

### Example 2

Example 2 shows how you can move all the third-party video systems in the organization to the Registrar pool atl-cs-001.litwareinc.com. To do this, the command first uses the Get-CsThirdPartyVideoSystem cmdlet to return a collection of all the available video systems. That collection is then piped to the Move-CsThirdPartyVideoSystem cmdlet, which moves all the video systems to the Registrar pool atl-cs-001.litwareinc.com.
  
```
Get-CsThirdPartyVideoSystem | Move-CsThirdPartyVideoSystem -Target "atl-cs-001.litwareinc.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

Third-party video systems are VTC devices that provide remote users with telepresence capabilities (most notably audio and video). In Skype for Business Server 2015, third-party VTC devices can be configured as Active Directory contact objects, much in the same way that analog phones and common area phones can be configured as contact objects. Associating each VTC device with a contact object makes it easy for administrators to track, and to manage, these devices. VTC contact objects can be created by using the New-CsThirdPartyVideoSystem cmdlet. Note that new contact objects must be assigned to a Skype for Business Server 2015 Registrar at the time they are created. If you later decide to move a contact object to a different pool, you can do so by using the Move-CsThirdPartyVideoSystem cmdlet.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Unique identifier for the third-party video system to be moved. Video systems are identified by using the Active Directory distinguished name of the associated contact object. By default, video systems use a GUID (globally unique identifier) as their common name, which means systems will typically have an Identity similar to this:  <br/> CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com  <br/> |
| _Target_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |The fully qualified domain name (FQDN) of the Registrar pool where the video system should be moved (for example, atl-cs-001.litwareinc.com). In addition to a Registrar pool, the Target can also be the FQDN of a hosting provider.  <br/> |
| _UserList_ <br/> |Required  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _ConcurrentMovesPerFE_ <br/> |Optional  <br/> |System.Int32  <br/> |PARAMVALUE: Int32  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller in order to move the video system. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-cs-001) or its FQDN (e.g., atl-cs-001.litwareinc.com).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, moves the video system but deletes any associated data (such as policies that were assigned to the system). If not present, the video system is moved along with any associated data.  <br/> |
| _IgnoreBackendStoreException_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, instructs the computer to ignore any errors that might occur with the backend database and attempt to move the video system despite those errors.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a video system contact object through the pipeline that represents the video system being moved. By default, the Move-CsThirdPartyVideoSystem cmdlet does not pass objects through the pipeline.  <br/> |
| _ProxyPool_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |This parameter is used only for Skype for Business Online. It should not be used with an on-premises implementation of Skype for Business Server 2015.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The Move-CsThirdPartyVideoSystem cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADThirdPartyVideoSystemContact object.
  
## Return Types
<a name="ReturnTypes"> </a>

By default the Move-CsThirdPartyVideoSystem cmdlet does not return any data or objects. However, if you include the PassThru parameter you can instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADThirdPartyVideoSystemContact object through the pipeline.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsThirdPartyVideoSystem](get-csthirdpartyvideosystem.md)
  
[New-CsThirdPartyVideoSystem](new-csthirdpartyvideosystem.md)
  
[Remove-CsThirdPartyVideoSystem](remove-csthirdpartyvideosystem.md)
  
[Set-CsThirdPartyVideoSystem](set-csthirdpartyvideosystem.md)

