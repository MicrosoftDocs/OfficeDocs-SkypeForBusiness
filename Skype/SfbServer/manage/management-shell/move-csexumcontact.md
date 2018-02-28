---
title: "Move-CsExUmContact"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 35ed6bdc-95ea-4bf8-84ce-c4256dc2c4e5
description: "Moves one or more Exchange Unified Messaging (UM) contacts to a new Registrar pool. This cmdlet was introduced in Lync Server 2010."
---

# Move-CsExUmContact
[]
Moves one or more Exchange Unified Messaging (UM) contacts to a new Registrar pool. This cmdlet was introduced in Lync Server 2010.
  
```
Move-CsExUmContact -Identity <UserIdParameter> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 moves the Exchange UM contact object with the SIP address exum1@fabrikam.com to the Registrar pool with the FQDN atl-cs-001.litwareinc.com. Note that a confirmation prompt will be displayed when you run this command, even though we didn't include the Confirm parameter. This prompt will appear even if you include the Force parameter.
  
```
Move-CsExUmContact -Identity "sip:exum1@fabrikam.com" -Target atl-cs-001.litwareinc.com
```

### EXAMPLE 2

This example moves all Exchange UM contact objects that are Auto Attendants to the Registrar pool with the FQDN atl-cs-001.litwareinc.com. The example begins with a call to the **Get-CsExUmContact** cmdlet, which retrieves all Exchange UM contacts that have been defined. This collection of contacts is then piped to the **Where-Object** cmdlet, which finds all the contacts in the collection that have an AutoAttendant property value of True ($True), meaning the contact is an Auto Attendant.
  
Finally, the collection of contacts where AutoAttendant is True is piped to the **Move-CsExUmContact** cmdlet, which moves those contacts to the Registrar pool specified in the Target parameter.
  
As in Example 1, you will be prompted for confirmation when running this command.
  
```
Get-CsExUmContact | Where-Object {$_.AutoAttendant -eq $True} | Move-CsExUmContact -Target atl-cs-001.litwareinc.com
```

## Detailed Description

Skype for Business Server 2015 works with Exchange UM to provide several voice-related capabilities, including Auto Attendant and Subscriber Access. The **Move-CsExUmContact** cmdlet provides a way for you to move an existing Exchange UM contact object to a new Registrar pool.
  
When an Exchange UM contact object is moved, the AutoAttendant and IsSubscriberAccess properties will be set appropriately based on the value of the OtherIpPhone property of the object.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |The unique identifier of the contact object you want to move. Contact identities can be specified by using one of four formats: 1) the contact's SIP address; 2) the contact's user principal name (UPN); 3) the contact's domain name and logon name, in the form domain\logon (for example, litwareinc\exum1); and, 4) the contact's Active Directory display name (for example, Team Auto Attendant).  <br/> |
| _Target_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |The fully qualified domain name (FQDN) of the Registrar pool to which the contact is being moved.  <br/> |
| _UserList_ <br/> |Required  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _ConcurrentMovesPerFE_ <br/> |Optional  <br/> |System.Int32  <br/> |PARAMVALUE: Int32  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-mcs-001) or its FQDN (for example, atl-mcs-001.litwareinc.com).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _IgnoreBackendStoreException_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, instructs the computer to ignore any errors that might occur with the backend database and attempt to move the contact despite those errors.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a contact object through the pipeline that represents the contact account being moved. By default, the **Move-CsExUmContact** cmdlet does not pass objects through the pipeline. <br/> |
| _ProxyPool_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |This parameter is used only for hosted instances of Skype for Business Server 2015. It should not be used with an on-premises implementation of Skype for Business Server 2015.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

String. Accepts a pipelined string value representing the Identity of an Exchange UM object to be moved.
  
## Return Types

When called with the PassThru parameter, returns an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact.
  
## See also

#### 

[New-CsExUmContact](new-csexumcontact.md)
  
[Remove-CsExUmContact](remove-csexumcontact.md)
  
[Set-CsExUmContact](set-csexumcontact.md)
  
[Get-CsExUmContact](get-csexumcontact.md)

