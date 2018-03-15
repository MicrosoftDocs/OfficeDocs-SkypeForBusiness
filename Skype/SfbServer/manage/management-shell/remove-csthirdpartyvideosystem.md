---
title: "Remove-CsThirdPartyVideoSystem"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0cd4e84c-8f5b-4714-8fd4-016ff058ac4d
description: "Removes an Active Directory contact object that represents a third-party video system. A third-party video system is a video teleconferencing (VTC) device that provides users with telepresence: the ability to participate in online meetings and conferences with full audio and video capabilities."
---

# Remove-CsThirdPartyVideoSystem
 
Removes an Active Directory contact object that represents a third-party video system. A third-party video system is a video teleconferencing (VTC) device that provides users with telepresence: the ability to participate in online meetings and conferences with full audio and video capabilities.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Remove-CsThirdPartyVideoSystem -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 removes the third-party video system that has the Identity CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com. Video system identities can be returned by using the Get-CsThirdPartyVideoSystem cmdlet.
  
```
Remove-CsThirdPartyVideoSystem -Identity "CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com"
```

### Example 2

In Example 2, the Remove-CsThirdPartyVideoSystem cmdlet is used to delete the video system that has the Active Directory display name Redmond Video System. To do this, the command first uses Get-CsThirdPartyVideoSystem and the Filter parameter to retrieve the Redmond Video System contact object (and does this without having to specify an Identity like CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com.) That contact object is then piped to, and deleted by, the Remove-CsThirdPartyVideoSystem cmdlet.
  
```
Get-CsThirdPartyVideoSystem -Filter {DisplayName -eq "Redmond Video System"} | Remove-CsThirdPartyVideoSystem 
```

### Example 3

Example 3 removes all the third-party video systems configured for use in the organization. To do this, the command first uses the Get-CsThirdPartyVideoSystem cmdlet to return a collection of all the third-party video systems. Those video systems are then piped to, and removed by, the Remove-CsThirdPartyVideoSystem cmdlet.
  
```
Get-CsThirdPartyVideoSystem | Remove-CsThirdPartyVideoSystem
```

## Detailed Description
<a name="DetailedDescription"> </a>

Third-party video systems are VTC devices that provide remote users with telepresence capabilities (most notably audio and video). In Skype for Business Server 2015, third-party VTC devices can be configured as Active Directory contact objects, much in the same way that analog phones and common area phones can be configured as contact objects. Associating each VTC device with a contact object makes it easy for administrators to track, and to manage, these devices. VTC contact objects can be created by using the New-CsThirdPartyVideoSystem cmdlet. These contact objects can later be deleted by using the Remove-CsThirdPartyVideoSystem cmdlet.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Unique identifier for the third party video system to be removed. Video systems are identified by using the Active Directory distinguished name (DN) of the associated contact object. By default, these contacts use a globally unique identifier (GUID) as their common name; that means video systems will typically have an Identity similar to this: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com. Because of that you might find it easier to retrieve video systems by using the Get-CsThirdPartyVideoSystem cmdlet, and then piping the returned objects to the Remove-CsThirdPartyVideoSystem cmdlet.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The Remove-CsThirdPartyVideoSystem cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADThirdPartyVideoSystemContact object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. The Remove-CsThirdPartyVideoSystem cmdlet does not return any objects or data.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsThirdPartyVideoSystem](get-csthirdpartyvideosystem.md)
  
[Move-CsThirdPartyVideoSystem](move-csthirdpartyvideosystem.md)
  
[New-CsThirdPartyVideoSystem](new-csthirdpartyvideosystem.md)
  
[Set-CsThirdPartyVideoSystem](set-csthirdpartyvideosystem.md)

