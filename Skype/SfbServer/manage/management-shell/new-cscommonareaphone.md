---
title: "New-CsCommonAreaPhone"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6082d24d-de92-4a3c-8639-5d28341cbc84
description: "Creates a new common area phone that can be managed by using Skype for Business Server 2015. Common area phones are phones that are located in building lobbies, employee lounges, or other areas where they are likely to be used by a number of different people and for a number of different uses. This cmdlet was introduced in Lync Server 2010."
---

# New-CsCommonAreaPhone
 
Creates a new common area phone that can be managed by using Skype for Business Server 2015. Common area phones are phones that are located in building lobbies, employee lounges, or other areas where they are likely to be used by a number of different people and for a number of different uses. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsCommonAreaPhone -OU <OUIdParameter> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 creates a new common area phone for the phone number 1-425-555-6710. (Note that the LineUri must be specified using the E.164 format.) In addition to specifying the phone number, the command also specifies the Registrar pool (RegistrarPool); the Active Directory display name (DisplayName); and the distinguished name of the OU where the corresponding contact object should be created (OU). 
  
```
New-CsCommonAreaPhone -LineUri tel:+14255556710 -RegistrarPool redmond-cs-001.litwareinc.com -DisplayName "Building 14 Lobby" -OU "ou=Telecommunications,dc=litwareinc,dc=com"
```

### EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In Example 2, however, the new common area phone is associated with an existing Active Directory contact object. To do this, the command employs the DN parameter instead of the OU parameter, using the distinguished name of the existing contact object (cn=Building 14 Lobby,ou=Telecommunications,dc=litwareinc,dc=com) as the parameter value. In this command the DisplayName is also left out, which means that the new common area phone will use the display name already assigned to the existing contact object. 
  
```
New-CsCommonAreaPhone -LineUri tel:+14255556710 -RegistrarPool redmond-cs-001.litwareinc.com -DN "cn=Building 14 Lobby,ou=Telecommunications,dc=litwareinc,dc=com"
```

## Detailed Description

Common area phones are IP telephones that are not associated with an individual user. Instead of being located in someone's office, common area phones are typically located in building lobbies, cafeterias, employee lounges, meeting rooms and other locations where a large number of people are likely to gather. This presents administrators with a management challenge; that's because phone use in Skype for Business Server 2015 is typically maintained by using voice policies and dial plans that are assigned to individual users. Common area phones do not have individual users assigned to them. 
  
One solution to this challenge is to create Active Directory contact objects for all your common area phones. (These contact objects can be created by using the **New-CsCommonAreaPhone** cmdlet.) Like user accounts, these contact objects can be assigned policies and voice plans. As a result, you will be able to maintain control over common area phones even though those phones are not associated with an individual user. For example, if you do not want people to have the ability to transfer or park calls from a common area phone, you can create a voice policy that prohibits call transfers and call parking, and then assign that policy to the common area phone. (Or, more correctly, to the contact object that represents the common area phone.) This command assigns the voice policy CommonAreaPhoneVoicePolicy to all your common area phones:
  
```
Get-CsCommonAreaPhone | Grant-CsVoicePolicy -PolicyName "CommonAreaPhoneVoicePolicy"

```

As noted, new common area phones can be created by using the **New-CsCommonAreaPhone** cmdlet. The **New-CsCommonAreaPhone** cmdlet can either create new contact objects for use with common area phones or it can associate existing contact objects with a new common area phone. For more details, see the OU and the DN parameter descriptions in this topic.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _DN_ <br/> |Required  <br/> |Microsoft.Rtc.Management.ADConnect.Core.ADObjectId  <br/> |Enables you to associate an existing Active Directory contact object with the new common area phone. If you have a contact object you want to associate with a common area phone, use the DN parameter followed by the distinguished name of that contact. For example:  `-DN "cn=Building 14 Lobby,dc=litwareinc,dc=com"`. Note that your command will fail if the specified contact does not exist. Your command will also fail if the specified contact has already been enabled for Skype for Business Server 2015. In that case, you must first disable the contact using the **Disable-CsUser** and cmdlet then run the **New-CsCommonAreaPhone** cmdlet. <br/> The DN parameter is particularly useful in organizations that have already created contact objects for conference rooms and other entities. These contacts are often used for scheduling purposes. By using the DN parameter you can create a new common area phone using one of these pre-existing contact objects.  <br/> You cannot use the OU and the DN parameters in the same command.  <br/> |
| _LineUri_ <br/> |Required  <br/> |System.String  <br/> |Phone number for the common area phone. The line Uniform Resource Identifier (URI) should be specified using the E.164 format, and be prefixed by the "TEL:" prefix. For example: TEL:+14255551297. Any extension number should be added to the end of the line URI, for example: TEL:+14255551297;ext=51297.  <br/> |
| _OU_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |Distinguished name of the Active Directory organizational unit (OU) where the contact object should be located. For example:  `-OU "ou=Redmond,dc=litwareinc,dc=com"`.  <br/> If you include the OU parameter, a new contact will be created in the specified OU, and the contact will automatically be assigned a globally unique identifier (GUID) as its common name. As a result, the contact object will have a name similar to this: {ce84964a-c4da-4622-ad34-c54ff3ed361f}.  <br/> |
| _RegistrarPool_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the Registrar pool where the contact object should be homed. For example:  `-RegistrarPool "atl-cs-001.litwareinc.com"`.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to set the Active Directory Description attribute for the common area phone. In turn, this provides a way for you to supply additional information about the phone; for example, you might want to provide details about who to contact in case of problems with the phone.  <br/> |
| _DisplayName_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to set the Active Directory display name of the common area phone.  <br/> |
| _DisplayNumber_ <br/> |Optional  <br/> |System.String  <br/> |Phone number as displayed in Skype for Business. The DisplayNumber property can be formatted any way you prefer; for example 1-800-555-1234; 1-(800)-555-1234; 1.800.555.1234; and so on. When choosing a display number, keep in mind that this number will be shown on the display screen of the common area phone only if the number can be normalized. (Normalization is the process of translating number strings into a standard phone number format.) If a normalization rule does not exist for the phone number format used when configuring the display number, the display screen of the common area phone will show the value of the LineUri property rather than the value of the DisplayNumber property.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns an object representing the common area phone.  <br/> |
| _SipAddress_ <br/> |Optional  <br/> |System.String  <br/> |Unique identifier that allows the common area phone to communicate with SIP devices such as Skype for Business. The SIP address must be prefaced by the prefix "sip:" and must include a valid SIP domain. For example: sip:bldg14lobby@litwareinc.com.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

None. The **New-CsCommonAreaPhone** cmdlet does not accept pipelined input.
  
## Return Types

The **New-CsCommonAreaPhone** cmdlet creates new instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact object.
  
## See also

#### 

[Get-CsCommonAreaPhone](get-cscommonareaphone.md)
  
[Move-CsCommonAreaPhone](move-cscommonareaphone.md)
  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)
  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)

