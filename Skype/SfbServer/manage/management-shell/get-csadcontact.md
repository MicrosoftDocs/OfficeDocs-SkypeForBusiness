---
title: "Get-CsAdContact"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a5f599fb-8ede-432d-a6bf-c850c68fc71e
description: "In a multi-forest topology, returns information about user accounts from forests other than your home forest; these are users who have been replicated as contact objects by Microsoft Forefront Identity Manager 2010 (or a previous version of the product). The Get-CsAdContact cmdlet returns any user who has a value configured for the msRTCSIP-OriginatorSid attribute. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsAdContact
[]
In a multi-forest topology, returns information about user accounts from forests other than your home forest; these are users who have been replicated as contact objects by Microsoft Forefront Identity Manager 2010 (or a previous version of the product). The **Get-CsAdContact** cmdlet returns any user who has a value configured for the msRTCSIP-OriginatorSid attribute. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsAdContact [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LDAPFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns a collection of all the multi-forest contacts found in Active Directory Domain Services. Calling the **Get-CsAdContact** cmdlet without any additional parameters returns all the property values for all the Active Directory contacts.
  
```
Get-CsAdContact
```

### EXAMPLE 2

Example 2 also returns a collection of all the Active Directory contacts. In this case, however, that collection is piped to the **Select-Object** cmdlet, which specifies the only two attributes that will be displayed on the screen: DisplayName and SipAddress.
  
```
Get-CsAdContact | Select-Object DisplayName, SipAddress
```

### EXAMPLE 3

Example 3 returns information for a single Active Directory contact: the contact with the Identity "Ken Myer".
  
```
Get-CsAdContact -Identity "Ken Myer"
```

### EXAMPLE 4

In Example 4, the command returns all the Active Directory contacts who work for Fabrikam. To do this, the **Get-CsAdContact** cmdlet is called, along with the LdapFilter parameter. In this example, the limits the returned data to contacts that have their Organization attribute set to "Fabrikam".
  
```
Get-CsAdContact -LdapFilter "Organization=Fabrikam"
```

### EXAMPLE 5

The two commands shown in Example 5 illustrate the use of the Credential parameter, which enables you to run the **Get-CsAdContact** cmdlet under alternate credentials. In the first command, the **Get-Credential** cmdlet is called in order to create a PSCredential object for the account litwareinc\administrator. This command displays a Credential Request dialog box for the user litwareinc\administrator; after you supply the password for this account, that credential information will be stored in the variable $x. In the second command, the **Get-CsAdContact** cmdlet is called along with the Credential parameter. The parameter value $x indicates that the **Get-CsAdContact** cmdlet should be run under the account litwareinc\administrator.
  
```
$x = Get-Credential -Credential "litwareinc\administrator"
Get-CsAdContact -Credential $x

```

## Detailed Description

In a multi-forest topology, users from other forests are represented as contacts. These contacts are not equivalent to Active Directory contacts; if you use Active Directory Users and Computers to create a new contact, that user will not be returned by the **Get-CsAdContact** cmdlet. Instead, the **Get-CsAdContact** cmdlet only returns information about users from forests other than your home forest. If you do not have a multi-forest topology then you will not need to call the **Get-CsAdContact** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Credential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |Enables you to run the **Get-CsAdContact** cmdlet under alternate credentials; this might be required if the account you used to log on to Windows does not have the necessary privileges required to work with contact objects. <br/> To use the Credential parameter you must first create a PSCredential object using the **Get-Credential** cmdlet. For details, see the Help topic for Get-Credential. <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller in order to retrieve contact information. To connect to a particular domain controller, include the DomainController parameter followed by the fully qualified domain name (for example, atl-cs-001.litwareinc.com).  <br/> |
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering on attributes specific to Skype for Business Server 2015.  <br/> The Filter parameter uses the same Windows PowerShell filtering syntax used by the **Where-Object** cmdlet. For example, a filter that returns only contacts who have a SIP address that ends with "fabrikam.com" would look like this: {SipAddress -like "*@fabrikam.com"}, with SipAddress representing the Active Directory attribute; -like representing the comparison operator; and "*@fabrikam.com" representing the filter value. <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the contact to be returned. Contact Identities can be specified by using one of three formats: 1) the contact's SIP address; 2) the contact's Active Directory distinguished name; and, 3) the contact's Active Directory display name (for example, Ken Myer).  <br/> You can use the asterisk (\*) wildcard character when using the Display Name as the contact Identity. For example, the Identity "\* Smith" returns all the contacts with a display name that ends in the string value "Smith".  <br/> |
| _LDAPFilter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering on generic Active Directory attributes. For example, you can limit returned data to contacts who work in a specific department, or contacts that have a specified manager or job title.  <br/> The LdapFilter parameter uses the LDAP query language when creating filters. For example, a filter that returns the contact that has the telephone number 1-425-555-1298 would look like this: "telephoneNumber=1-425-555-1298", with "telephoneNumber" representing the Active Directory attribute; "=" representing the comparison operator (equal to); and "1-425-555-1298" representing the filter value.  <br/> |
| _OU_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |Enables you to limit the retrieved information from a specific Active Directory organizational unit (OU) or container. This parameter returns data from both the specified OU and any of its child OUs. For example, if the Finance OU has two child OUs: AccountsPayable and AccountsReceivable. contacts will be returned from each of these three OUs.  <br/> When specifying an OU, use the distinguished name of that container; for example: OU=Finance,dc=litwareinc,dc=com.  <br/> |
| _ResultSize_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.Unlimited  <br/> |Enables you to limit the number of records returned by the cmdlet. For example, to return seven contacts (regardless of the number of contacts that are in your forest) include the ResultSize parameter and set the parameter value to 7. Note that there is no way to guarantee which 7 users will be returned.  <br/> The result size can be set to any whole number between 0 and 2147483647, inclusive. If set to 0 the command will run, but no data will be returned. If you set the ResultSize to 7 but you have only three contacts in your forest, the command will return those three contacts and then complete without error.  <br/> |
   
## Input Types

String. The **Get-CsAdContact** cmdlet accepts a pipelined string value representing the Identity of a user account.
  
## Return Types

The **Get-CsAdContact** cmdlet returns instances of the Microsoft.Rtc.Management.ADConnect.Schema.ADContact object.
  
## See also

#### 

[Get-CsAdUser](get-csaduser.md)
  
[Get-CsUser](get-csuser.md)

