---
title: "Remove-CsCommonAreaPhone"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: f2c93bec-4b99-4b69-abe0-d2d9e33dcadd
description: "Removes an existing common area phone from the collection of phones managed by using Skype for Business Server 2015. Common area phones are phones that are located in building lobbies, employee lounges, or other areas where they are likely to be used by a number of different people and for a number of different uses. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsCommonAreaPhone
 
Removes an existing common area phone from the collection of phones managed by using Skype for Business Server 2015. Common area phones are phones that are located in building lobbies, employee lounges, or other areas where they are likely to be used by a number of different people and for a number of different uses. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsCommonAreaPhone -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 deletes the common area phone that has the display name "Building 14 Lobby". To do this, the command first calls the **Get-CsCommonAreaPhone** cmdlet along with the Filter parameter and the filter value "{DisplayName -eq "Building 14 Lobby"}". The returned object is then piped to, and deleted by, the **Remove-CsCommonAreaPhone** cmdlet.
  
```
Get-CsCommonAreaPhone -Filter {DisplayName -eq "Building 14 Lobby"} | Remove-CsCommonAreaPhone
```

### EXAMPLE 2

In Example 2, the command deletes all the common area phones that have not been assigned a dial plan. This task is carried out by first using the **Get-CsCommonAreaPhone** cmdlet and the Filter parameter to return the specified items; the filter value {DialPlan -eq $Null} limits the returned data to common area phones that have not been assigned a dial plan. This filtered collection is then piped to the **Remove-CsCommonAreaPhone** cmdlet, which deletes each phone in the collection.
  
```
Get-CsCommonAreaPhone -Filter {DialPlan -eq $Null} | Remove-CsCommonAreaPhone
```

### EXAMPLE 3

Example 3 deletes all the common area phones that have contact objects located in the Redmond OU in Active Directory. To carry out this task, the **Get-CsCommonAreaPhone** cmdlet is first called in order to return all the common area phones with contact objects in the Redmond OU; the OU parameter and the parameter value "ou=Redmond,dc=litwareinc,dc=com" is used to limit the returned data to the specified organizational unit. The returned collection is then piped to the **Remove-CsCommonAreaPhone** cmdlet, which deletes each phone in that collection.
  
```
Get-CsCommonAreaPhone -OU "ou=Redmond,dc=litwareinc,dc=com" | Remove-CsCommonAreaPhone
```

## Detailed Description

Common area phones are IP telephones that are not associated with an individual user. Instead of being located in someone's office, common area phones are typically located in building lobbies, cafeterias, employee lounges, meeting rooms and other locations where a large number of people are likely to gather. This presents administrators with a management challenge; that's because phone use in Skype for Business Server 2015 is typically maintained by using voice policies and dial plans that are assigned to individual users. Common area phones do not have individual users assigned to them.
  
One solution to this challenge is to create Active Directory contact objects for all your common area phones. (These contact objects can be created by using the **New-CsCommonAreaPhone** cmdlet.) Like user accounts, these contact objects can be assigned policies and voice plans. As a result, you will be able to maintain control over common area phones even though those phones are not associated with an individual user. For example, if you do not want people to have the ability to transfer or park calls from a common area phone, you can create a voice policy that prohibits call transfers and call parking, and then assign that policy to the common area phone. (Or, more correctly, to the contact object that represents the common area phone.) For example, this command assigns the voice policy CommonAreaPhoneVoicePolicy to all your common area phones:
  
```
Get-CsCommonAreaPhone | Grant-CsVoicePolicy -PolicyName "CommonAreaPhoneVoicePolicy"

```

From time-to-time you might need to delete the contact object associated with a common area phone. For example, if you remove the phone from an employee lounge then there is no need to have a contact object associated with that phone. The **Remove-CsCommonAreaPhone** cmdlet provides a way for you to delete common area phones. When you run this cmdlet, the phone will be deleted from the list of common area phones returned by the **Get-CsCommonAreaPhone** cmdlet. In addition, the contact object associated with that phone will be deleted from Active Directory Domain Services.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Unique identifier for the common area phone. Common area phones are identified using the Active Directory distinguished name of the associated contact object. By default, common area phones use a globally unique identifier (GUID) as their common name, which means phones will typically have an Identity similar to this: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com. Because of that, you might find it easier to retrieve common area phones by using the **Get-CsCommonAreaPhone** cmdlet, and then piping the returned objects to the **Remove-CsCommonAreaPhone** cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact object. The **Remove-CsCommonAreaPhone** cmdlet accepts pipelined instances of the common area phone object.
  
## Return Types

The **Remove-CsCommonAreaPhone** cmdlet deletes existing instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact object.
  
## See also

#### 

[Get-CsCommonAreaPhone](get-cscommonareaphone.md)
  
[Move-CsCommonAreaPhone](move-cscommonareaphone.md)
  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)
  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)

