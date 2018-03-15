---
title: "New-CsThirdPartyVideoSystem"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 594ad110-69d5-477a-a641-bfc5472ba446
description: "Creates an Active Directory contact object that represents a third-party video system. A third-party video system is a video teleconferencing device (VTC) that provides users with telepresence: the ability to participate in online meetings and conferences with full audio and video capabilities."
---

# New-CsThirdPartyVideoSystem
 
Creates an Active Directory contact object that represents a third-party video system. A third-party video system is a video teleconferencing device (VTC) that provides users with telepresence: the ability to participate in online meetings and conferences with full audio and video capabilities.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
New-CsThirdPartyVideoSystem -OU <OUIdParameter> <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

In Example 1, a new third-party video system contact object is created in the Telecommunications OU. This new contact object will be homed on the Registrar pool Redmond-cs-001.litwareinc.com; will have the display name Redmond Video System; and will use the SIP address sip:redmondvideo@litwareinc.com.
  
```
New-CsThirdPartyVideoSystem -RegistrarPool "redmond-cs-001.litwareinc.com" -OU "ou=Telecommunications,dc=litwareinc,dc=com" -DisplayName "Redmond Video System" -SipAddress "sip:redmondvideo@litwareinc.com"
```

### Example 2

The command shown in Example 2 creates a new third-party video system by associating that system with an existing Active Directory contact object. To carry out that task you need to include three parameters: RegistrarPool, which specifies the Registrar pool where the new video system account will be homed; DN, which specifies the Active Directory distinguished name of the existing contact object; and SipAddress, which assigns a SIP address to the new video system.
  
```
New-CsThirdPartyVideoSystem -RegistrarPool "redmond-cs-001.litwareinc.com" -DN "cn=RedmondVideoSystem,ou=Telecommunications,dc=litwareinc,dc=com" -SipAddress "sip:redmondvideo@litwareinc.com" 
```

## Detailed Description
<a name="DetailedDescription"> </a>

Third-party video systems are VTC devices that provide remote users with telepresence capabilities (most notably audio and video). In Skype for Business Server 2015, third-party VTC devices can be configured as Active Directory contact objects, much in the same way that analog phones and common area phones can be configured as contact objects. Associating each VTC device with a contact object makes it easy for administrators to track, and to manage, these devices. VTC contact objects can be created by using the New-CsThirdPartyVideoSystem cmdlet.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _DN_ <br/> |Required  <br/> |Microsoft.Rtc.Management.ADConnect.Core.ADObjectId  <br/> |Enables you to associate an existing Active Directory contact object with a third-party video system. If you have a contact object you want to associate with video system, use the DN parameter followed by the distinguished name of that contact. For example:  <br/>  `-DN "cn=Building 14 Lobby,dc=litwareinc,dc=com"` <br/> Note that the command will fail if the specified contact does not exist. Note, too that you cannot use the OU and the DN parameters in the same command.  <br/> |
| _OU_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |Distinguished name of the Active Directory organizational unit (OU) where the contact object should be located. For example:  <br/>  `-OU "ou=Redmond,dc=litwareinc,dc=com"` <br/>  If you include the OU parameter, a new contact will be created in the specified OU, and the contact will automatically be assigned a GUID (globally unique identifier) as its common name. As a result, the contact object will have a name similar to this: {ce84964a-c4da-4622-ad34-c54ff3ed361f}. <br/> |
| _RegistrarPool_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the Registrar pool where the contact object should be homed. For example:  <br/>  `-RegistrarPool "atl-cs-001.litwareinc.com"` <br/> |
| _SipAddress_ <br/> |Required  <br/> |System.String  <br/> |Unique identifier that allows the video system to communicate with SIP devices such as Skype for Business. The SIP address must be prefaced by the prefix "sip:". For example:  <br/> sip:contoso_video@litwareinc.com  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DisplayName_ <br/> |Optional  <br/> |System.String  <br/> |Configures the Active Directory display name of the video system.  <br/> |
| _LineUri_ <br/> |Optional  <br/> |System.String  <br/> |Phone number for the VTC device. The line URI should be specified by using the E.164 format, and be prefixed by the "TEL:" prefix. For example:  <br/>  `-LineURI "TEL:+14255551297"` <br/> Any extension number should be added to the end of the line URI; for example:  <br/>  `-LineURI "TEL:+14255551297;ext=51297"` <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a contact object through the pipeline that represents the third-party video system being modified. By default, the New-CsThirdPartyVideoSystem cmdlet does not pass objects through the pipeline.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The New-CsThirdPartyVideoSystem cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The New-CsThirdPartyVideoSystem cmdlet creates new instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADThirdPartyVideoSystemContact object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsThirdPartyVideoSystem](get-csthirdpartyvideosystem.md)
  
[Move-CsThirdPartyVideoSystem](move-csthirdpartyvideosystem.md)
  
[Remove-CsThirdPartyVideoSystem](remove-csthirdpartyvideosystem.md)
  
[Set-CsThirdPartyVideoSystem](set-csthirdpartyvideosystem.md)

