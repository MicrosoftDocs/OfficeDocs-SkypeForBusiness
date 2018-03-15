---
title: "Get-CsAdPrincipal"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: df2c3714-4064-4113-861f-95ce0ae8da81
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsAdPrincipal
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Returns information about Active Directory principals. These principals include Active Directory objects such as users, groups, contacts, containers, and organizational units. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsAdPrincipal [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LDAPFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns all the Active Directory principals in the organization.
  
```
Get-CsAdPrincipal
```

### Example 2

In Example 2, information is returned for a single Active Directory principal: the principal with the SIP address "sip:RedmondMeetingRoom@litwareinc.com". This is done by including the Filter parameter and a filter value that looks for principals where the SipAddress property is equal to (-eq) "sip:RedmondMeetingRoom@litwareinc.com".
  
```
Get-CsAdPrincipal -Filter {SipAddress -eq "sip:RedmondMeetingRoom@litwareinc.com"}
```

### Example 3

In the preceding example, information is returned for all the Active Directory objects. To carry out this task, the command first calls the **Get-CsAdPrincipal** cmdlet without any parameters; this returns a collection of all the Active Directory principals. That collection is then piped to the **Where-Object** cmdlet, which selects only those principals where the ObjectClass property contains the string value "contact". 
  
```
Get-CsAdPrincipal | Where-Object {$_.ObjectClass -contains "contact"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Get-CsAdPrincipa** l cmdlet returns a collection of Active Directory principals that can be used when constructing Persistent Chat membership lists (see the help information for the AllowedMembers and DeniedMembers parameters for the **Set-CsPersistentChatCategory** cmdlet for more details). **Get-CsPrincipal** returns information for Active Directory objects such as: 
  
- **Users** (object class = {top, person, organizationalPerson, user}) 
    
- **Groups** (object class = {top, group}) 
    
- **Contacts** (object class = {top, person, organizationalPerson, contact}) 
    
- **Containers** (object class = {top, container}) 
    
- **Organizational Units** (object class = {top, organizationalUnit}) 
    
- **Domains** (object class = {top, domain, domainDNS}) 
    
Among other things, this means that you can use the **Get-CsAdPrincipal** cmdlet (and the objectClass property) to quickly return information about Active Directory objects such as groups or organizational units. For example, this command returns the names of all your Active Directory OUs: 
  
Get-CsAdPrincipal | Where-Object {$_.ObjectClass -match "organizationalUnit"} | Select-Object Name
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsAdPrincipal"}
  
 **Lync Server Control Panel:** The functions carried out by the Get-CsAdPrincipal cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Credential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |Enables you to run the **Get-CsAdPrincipal** cmdlet under alternate credentials. This might be required if the account you used to log on to Windows does not have the necessary privileges required to work with user objects.  <br/> To use the Credential parameter you must first create a PSCredential object by using the **Get-Credential** cmdlet. For details, see the **Get-Credential** cmdlet help topic.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller in order to retrieve Active Directory principal information. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-dc-001) or its fully qualified domain name (FQDN) (for example, atl-dc-001.litwareinc.com).  <br/> |
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering on attributes specific to Lync Server.  <br/> The Filter parameter uses the much of the same Windows PowerShell filtering syntax used by the **Where-Object** cmdlet. For example, a filter that returns only principals who are not enabled for Lync Server would look like this:  <br/> -Filter {Enabled -ne $True}  <br/> In that example. Enabled represents the Active Directory attribute, -ne represents the comparison operator (not equal to), and $True (a built-in Windows PowerShell variable) represents the value True.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the principal account to be retrieved. Identities are typically specified by using one of four formats: 1) the account SIP address; 2) the user's user principal name (UPN); 3) the account domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the account Active Directory display name (for example, Ken Myer).  <br/> You can also reference a user account by using the user's Active Directory distinguished name.  <br/> You can use the asterisk (\*) wildcard character when using the Display Name as the Identity. For example, the Identity "\* Smith" returns all the users who have a display name that ends with the string value " Smith".  <br/> |
| _LDAPFilter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering on generic Active Directory attributes (that is, attributes that are not specific to Lync Server). For example, you can limit returned data to principals who belong to a specific department or who have a specific manager or job title.  <br/> The LdapFilter parameter uses the LDAP query language when creating filters. For example, a filter that returns only principals located in the city of Redmond would look like this:  <br/> -LdapFilter "l=Redmond"  <br/> In that example, the "l" (a lowercase L) represents the Active Directory attribute (locality); "=" represents the comparison operator (equal to); and "Redmond" represents the filter value.  <br/> |
| _OU_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |Enables you to return information about principals in a specific organizational unit (OU) or container. The OU parameter returns data from both the specified OU and any of its child OUs. For example, if the Finance OU has two child OUs -- AccountsPayable and AccountsReceivable - principals will be returned from each of these three OUs.  <br/> When specifying an OU, use the distinguished name (DN) of that container; for example:  <br/> -OU "OU=Finance,dc=litwareinc,dc=com"  <br/> To return principals from the Users container, use this syntax:  <br/> -OU "cn=Users,dc=litwareinc,dc=com"  <br/> |
| _ResultSize_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.Unlimited  <br/> |Enables you to limit the number of records returned by the cmdlet. For example, to return seven principals (regardless of the number of principals that are in your forest) include the ResultSize parameter and set the parameter value to 7. Note that there is no way to guarantee which seven principals will be returned.  <br/> The result size can be set to any whole number between 0 and 2147483647, inclusive. If set to 0 the command will run, but no data will be returned. If you set the ResultSize to 7 but you have only three principals in your forest, the command will return those three principals, and then complete without error.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

String value or object representing an Active Directory user, group, contact, container, and organizational unit. For example, this syntax returns Active Directory principal information for the Redmond and Dublin OUs:
  
"OU=Redmond,DC=litwareinc,DC=com", "OU=Dublin,DC=litwareinc,DC=com" | Get-CsAdPrincipal
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsAdPrincipal** cmdlet returns instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADPrincipal object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsPersistentChatCategory](new-cspersistentchatcategory.md)
  
[Set-CsPersistentChatCategory](set-cspersistentchatcategory.md)

