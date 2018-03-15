---
title: "Get-CsExUmContact"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 5/22/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9c7b2afb-4d7f-4b5a-99dd-6f8978dd5728
description: "Retrieves one or more hosted Exchange Unified Messaging (UM) contact objects. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsExUmContact
 
Retrieves one or more hosted Exchange Unified Messaging (UM) contact objects. This cmdlet was introduced in Lync Server 2010.
  
> [!NOTE]
> This cmdlet can be used only with Skype for Business on-premises. 
  
```
Get-CsExUmContact [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LdapFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

```

## Examples

### EXAMPLE 1

This example retrieves all Exchange UM contacts defined within a Skype for Business Server 2015 deployment.
  
```
Get-CsExUmContact
```

### EXAMPLE 2

This example retrieves the Exchange UM contact with the SIP address sip:exum1@fabrikam.com
  
```
Get-CsExUmContact -Identity sip:exum1@fabrikam.com
```

### EXAMPLE 3

In this example, we use the Filter parameter to retrieve all Exchange UM contacts that are not enabled for Skype for Business Server 2015. We do this by filtering on the Enabled property to see if the value of this property is equal to (-eq) False ($False). Contacts returned by this command will not function.
  
```
Get-CsExUmContact -Filter {Enabled -eq $False}
```

### EXAMPLE 4

This command filters on the LineURI property to retrieve all Exchange UM contacts with a LineURI beginning with tel:555. In other words, it retrieves all contacts with a phone number that begins with 555.
  
```
Get-CsExUmContact -Filter {LineURI -like "tel:555*"}
```

### EXAMPLE 5

The command in this example uses the OU parameter to retrieve all Exchange UM contacts that are in the Active Directory OU OU=ExUmContacts,DC=Vdomain,DC=com.
  
```
Get-CsExUmContact -OU "OU=ExUmContacts,DC=Vdomain,DC=com"
```

## Detailed Description

Skype for Business Server 2015 works with Exchange UM to provide several voice-related capabilities, including Auto Attendant and Subscriber Access. When Exchange UM is provided as a hosted service (rather than on-premises), contact objects must be created by using Windows PowerShell to apply the Auto Attendant and Subscriber Access functionality. This cmdlet retrieves one or more of these contacts.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Credential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |Enables you to run the cmdlet under alternate credentials; this might be required if the account you used to log on to Windows does not have the necessary privileges required to work with contact objects.  <br/> To use the Credential parameter, you must first create a PSCredential object by calling the **Get-Credential** cmdlet. <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller in order to retrieve contact information. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-mcs-001) or its fully qualified domain name (for example, atl-mcs-001.litwareinc.com).  <br/> Full data type: Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering on Skype for Business Server 2015-specific attributes. For example, you can limit returned data to contacts that have line URIs beginning with "tel:555".  <br/> The Filter parameter uses a subset of the Windows PowerShell filtering syntax used by the **Where-Object** cmdlet. For example, a filter that returns only contacts who have been enabled for Enterprise Voice would look like this: {EnterpriseVoiceEnabled -eq $True}, with EnterpriseVoiceEnabled representing the Active Directory attribute; -eq representing the comparison operator (equal to); and $True (a built-in Windows PowerShell variable) representing the filter value. <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |The unique identifier of the contact object you want to retrieve. Contact identities can be specified using one of four formats: 1) the contact's SIP address; 2) the contact's user principal name (UPN); 3) the contact's domain name and logon name, in the form domain\logon (for example, litwareinc\exum1); and, 4) the contact's Active Directory display name (for example, Team Auto Attendant).  <br/> Full data type: Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |
| _LdapFilter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering "generic" Active Directory attributes (that is, attributes that are not specific to Skype for Business Server 2015).  <br/> The LdapFilter parameter uses LDAP query language when creating filters.  <br/> |
| _OU_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |Enables you to limit the retrieved information to a specific Active Directory organizational unit (OU). Note that this returns data from the specified OU and any child OUs.  <br/> When specifying an OU, use the distinguished name of that container; for example, OU=ExUmContacts,dc=litwareinc,dc=com.  <br/> |
| _ResultSize_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.Unlimited  <br/> |Enables you to limit the number of records returned by a command. For example, to return just seven contacts (regardless of how many contacts are in your forest) simply include the ResultSize parameter and set the parameter value to 7. Note that there is no way to guarantee which seven contacts will be returned. If you set the ResultSize to 7 but you have only three contacts in your forest, the command will return those three contacts, and then complete without error.  <br/> The result size can be set to any whole number between 0 and 2147483647, inclusive. If set to 0 the command will run, but no data will be returned.  <br/> Full data type: Microsoft.Rtc.Management.ADConnect.Core.Unlimited  <br/> |
   
## Input Types

String. Accepts a pipelined string value representing the Identity of an Exchange UM contact object.
  
## Return Types

Returns an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact.
  
## See also

#### 

[New-CsExUmContact](new-csexumcontact.md)
  
[Remove-CsExUmContact](remove-csexumcontact.md)
  
[Set-CsExUmContact](set-csexumcontact.md)
  
[Move-CsExUmContact](move-csexumcontact.md)

