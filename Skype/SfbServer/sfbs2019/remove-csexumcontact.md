---
title: "Remove-CsExUmContact"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d79f7082-f58b-4cc3-a90d-230111e32850
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsExUmContact
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes an Auto Attendant or Subscriber Access contact object for hosted Exchange Unified Messaging (UM). This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsExUmContact -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example removes the Exchange UM contact with the SIP address exumsa1@fabrikam.com. 
  
```
Remove-CsExUmContact -Identity sip:exumsa1@fabrikam.com
```

### EXAMPLE 2

This example removes all Exchange UM contacts with LineURI values beginning with tel:425. The first part of this command calls the **Get-CsExUmContact** cmdlet with the Filter parameter, using this expression as the filter: LineURI -like "tel:425*". That filter specifies that we want to retrieve the Exchange UM contact objects that have a LineURI matching the wildcard string tel:425*. In other words, all line URIs that start with the string tel:425 and end with any set of characters. Once we have that collection of objects, we pipe the collection to the **Remove-CsExUmContact** cmdlet, which removes all the items in the collection. 
  
```
Get-CsExUmContact -Filter {LineURI -like "tel:425*"} | Remove-CsExUmContact
```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Server works with Exchange UM to provide several voice-related capabilities, including Auto Attendant and Subscriber Access. When Exchange UM is provided as a hosted service (rather than on-premises), contact objects must be created by using Windows PowerShell to apply the Auto Attendant and Subscriber Access functionality. Any of the objects that are created can be removed with the **Remove-CsExUmContact** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsExUmContact** cmdlet locally: RTCUniversalUserAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsExUmContact"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |The unique identifier of the contact object you want to remove. Contact identities can be specified using one of four formats: 1) The contact's SIP address; 2) the contact's user principal name (UPN); 3) the contact's domain name and logon name, in the form domain\logon (for example, litwareinc\exum1); and, 4) the contact's Active Directory display name (for example, Team Auto Attendant).  <br/> Full data type: Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact object. Accepts pipelined input of Exchange UM contact objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return an object. It removes an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsExUmContact](new-csexumcontact.md)
  
[Set-CsExUmContact](set-csexumcontact.md)
  
[Get-CsExUmContact](get-csexumcontact.md)
  
[Move-CsExUmContact](move-csexumcontact.md)

