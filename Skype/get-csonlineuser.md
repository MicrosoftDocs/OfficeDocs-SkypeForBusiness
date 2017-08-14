---
title: Get-CsOnlineUser
ms.prod: SKYPEFORBUSINESS
ms.assetid: 2bfafd70-a7d9-4308-a353-5ecf44249b53
---


# Get-CsOnlineUser
[]
Returns information about users who have accounts homed on Microsoft Lync Online. This cmdlet can only be used with Skype for Business Online.
  
    
    


```

Get-CsOnlineUser [[-Identity] <UserIdParameter>] [-Filter <String>] [-LdapFilter <String>] [-OnOfficeCommunicationServer] [-OnLyncServer] [-UnAssignedUser] [-OU <OUIdParameter>] [-DomainController <Fqdn>] [-Credential <PSCredential>] [-ResultSize <Unlimited`1>] [-Verbose]
```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 returns information for all the users configured as online users.
  
    
    

```
Get-CsOnlineUser
```


### Example 2

In Example 2 information is returned for a single online user: the user with the SIP address "sip:kenmyer@litwareinc.com".
  
    
    

```
Get-CsOnlineUser -Identity "sip:kenmyer@litwareinc.com"
```


### Example 3

The command shown in Example 3 returns information for all the online users who have been enabled for Lync Online but are not currently assigned to a Registrar pool.
  
    
    

```
Get-CsOnlineUser -UnassignedUser
```


### Example 4

Example 4 uses the Filter parameter to limit the returned data to online users who have been assigned the per-user archiving policy RedmondArchiving. To do this, the filter value {ArchivingPolicy -eq "RedmondArchiving"} is employed; that syntax limits returned data to users where the ArchivingPolicy property is equal to (-eq) "RedmondArchiving".
  
    
    

```
Get-CsOnlineUser -Filter {ArchivingPolicy -eq "RedmondArchiving"}
```


### Example 5

Example 5 returns information only for user accounts that have been configured so that the account does not appear in Microsoft Exchange address lists. (That is, the Active Directory attribute msExchHideFromAddressLists is True.) To carry out this task, the Filter parameter is included along with the filter value {HideFromAddressLists -eq $True}.
  
    
    

```
Get-CsOnlineUser -Filter {HideFromAddressLists -eq $True}
```


### Example 6

The command shown in Example 6 returns information for all the online users assigned to the tenant with the TenantID "bf19b7db-6960-41e5-a139-2aa373474354". To accomplish the task, the command includes the Filter parameter along with the filter value {TenantId -eq "bf19b7db-6960-41e5-a139-2aa373474354"}. This filter limits the returned data to online users assigned to the tenant "bf19b7db-6960-41e5-a139-2aa373474354".
  
    
    

```
Get-CsOnlineUser -Filter {TenantId -eq "bf19b7db-6960-41e5-a139-2aa373474354"}
```


## Detailed Description
<a name="DetailedDescription"> </a>

The **Get-CsOnlineUser** cmdlet returns information about users who have accounts homed on Microsoft Lync Online. The returned information includes standard Active Directory account information (such as the department the user works in, his or her address and phone number, etc.) as well as Lync Server specific information: the **Get-CsOnlineUser** cmdlet returns information about such things as whether or not the user has been enabled for Enterprise Voice and which per-user policies (if any) have been assigned to the user.
  
    
    
Note that the **Get-CsOnlineUser** cmdlet does not have a TenantId parameter; that means you cannot use a command similar to this in order to limit the returned data to users who have accounts with a specific Lync Online tenant:
  
    
    



```
Get-CsOnlineUser -TenantId "bf19b7db-6960-41e5-a139-2aa373474354"
```

However, if you have multiple Lync Online tenants you can return users from a specified tenant by using the Filter parameter and a command similar to this:
  
    
    



```
Get-CsOnlineUser -Filter {TenantId -eq "bf19b7db-6960-41e5-a139-2aa373474354"}
```

That command will limit the returned data to user accounts belong to the tenant with the TenantId "bf19b7db-6960-41e5-a139-2aa373474354". If you do not know your tenant IDs you can return that information by using this command:
  
    
    



```
Get-CsTenant
```

If you have a hybrid or "split domain" deployment (that is, a deployment in which some users have accounts homed on Lync Online while other users have accounts homed on an on-premises version of Lync Server) keep in mind that the **Get-CsOnlineUser** cmdlet only returns information for Lync Online users. However, the [Get-CsUser](get-csuser.md) cmdlet will return information for both Lync Online users and on-premises Lync Server users. If you want to exclude Lync Online users from the data returned by the **Get-CsUser** cmdlet, use the following command:
  
    
    



```
Get-CsUser -Filter {TenantId -eq "00000000-0000-0000-0000-000000000000"}
```

By definition, users homed on the on-premises version of Lync Server will always have a TenantId equal to 00000000-0000-0000-0000-000000000000. Users homed on Lync Online will a TenantId that is equal to some value other than 00000000-0000-0000-0000-000000000000.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Credential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |Enables you to run the **Get-CsOnlineUser** cmdlet under alternate credentials. This might be required if the account you used to log on to the Windows does not have the necessary privileges required to work with user objects. <br/> To use the Credential parameter you must first create a PSCredential object by using the **Get-Credential** cmdlet. For details, see the **Get-Credential** cmdlet help topic. <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller in order to retrieve user information. To connect to a particular domain controller, include the DomainController parameter followed by the fully qualified domain name (FQDN) (for example, atl-cs-001.litwareinc.com).  <br/> |
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering on Lync Server specific attributes. For example, you can limit returned data to users who have been assigned a specific voice policy, or users who have not been assigned a specific voice policy.  <br/> The Filter parameter uses the same Windows PowerShell filtering syntax that is used by the Where-Object cmdlet. For example, a filter that returns only users who have been enabled for Enterprise Voice would look like this, with EnterpriseVoiceEnabled representing the Active Directory attribute, -eq representing the comparison operator (equal to), and $True (a built-in Windows PowerShell variable) representing the filter value:  <br/> {EnterpriseVoiceEnabled -eq $True}  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account to be retrieved. User Identities can be specified using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). You can also reference a user account by using the user's Active Directory distinguished name.  <br/> You can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity "* Smith" returns all the users who have a display name that ends with the string value " Smith".  <br/> |
| _LdapFilter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering on generic Active Directory attributes (that is, attributes that are not specific to Lync Server). For example, you can limit returned data to users who work in a specific department, or users who have a specified manager or job title.  <br/> The LdapFilter parameter uses the LDAP query language when creating filters. For example, a filter that returns only users who work in the city of Redmond would look like this: "l=Redmond", with "l" (a lowercase L) representing the Active Directory attribute (locality); "=" representing the comparison operator (equal to); and "Redmond" representing the filter value.  <br/> |
| _OnLyncServer_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns a collection of users homed on Lync Server. Users with accounts on previous versions of the software will not be returned when you use this parameter.  <br/> |
| _OnOfficeCommunicationServer_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns a collection of users homed on a previous version of Lync Server (for example, Microsoft Office Communications Server 2007 R2). Users with accounts on the current version of the software will not be returned when you use this parameter.  <br/> |
| _OU_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |Enables you to return information about user accounts in a specific organizational unit (OU) or container. The OU parameter returns data from both the specified OU and any of its child OUs. For example, if the Finance OU has two child OUs -- AccountsPayable and AccountsReceivable -- users will be returned from each of these three OUs.  <br/> When specifying an OU, use the distinguished name (DN) of that container; for example: -OU "OU=Finance,dc=litwareinc,dc=com". To return user accounts from the Users container, use this syntax:  <br/> -OU "cn=Users,dc=litwareinc,dc=com"  <br/> |
| _ResultSize_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.Unlimited  <br/> |Enables you to limit the number of records returned by the cmdlet. For example, to return seven users (regardless of the number of users that are in your forest) include the ResultSize parameter and set the parameter value to 7. Note that there is no way to guarantee which seven users will be returned.  <br/> The result size can be set to any whole number between 0 and 2147483647, inclusive. If set to 0 the command will run, but no data will be returned. If you set the ResultSize to 7 but you have only three users in your forest, the command will return those three users, and then complete without error.  <br/> |
| _UnassignedUser_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to return a collection of all the users who have been enabled for Lync Online but are not currently assigned to a Registrar pool. Users are not allowed to log on to unless they are assigned to a Registrar pool.  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

The **Get-CsOnlineUser** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADUser object, as well as string values that represent a valid user account Identity (for example, "sip:kenmyer@litwareinc.com").
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsOnlineUser** cmdlet returns instances of the Microsoft.Rtc.Management.ADConnect.Schema.ADOCOnlineUser object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsUser](get-csuser.md)
