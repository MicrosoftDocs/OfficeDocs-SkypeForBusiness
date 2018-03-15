---
title: "Get-CsUserPoolInfo"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7be81a85-c536-4d5c-b866-af7380e45c0f
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsUserPoolInfo
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the Registrar pool, backup Registrar pool, and User Services pool that a user has been assigned to. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsUserPoolInfo -Identity <UserIdParameter> [-LocalStore <SwitchParameter>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This command returns user pool information for a single user: the user with the SIP address sip:kenmyer@litwareinc.com.
  
```
Get-CsUserPoolInfo "sip:kenmyer@litwareinc.com"
```

### EXAMPLE 2

In Example 2, user pool information is returned for all the users who have been enabled for Lync Server. To carry out this task, the command first calls the **Get-CsUser** cmldet without any parameters in order to return a collection of all the Lync Server-enabled users. This collection is then piped to the **Get-CsUserPoolInfo** cmdlet, which displays pool information for each user in the collection. 
  
```
Get-CsUser | Get-CsUserPoolInfo
```

### EXAMPLE 3

The command shown in Example 3 is a variation of the command used in Example 2. In Example 2, pool information is returned for all the users who have been enabled for Lync Server. However, it is possible to have users who have been enabled for Lync Server but have not been assigned a Registrar pool. The command shown in Example 2 displays an error message for each user who meets those criteria; those error messages are suppressed in Example 3. 
  
To suppress the error message, Example 3 again uses the **Get-CsUser** cmdlet to return a collection of all the Lync Server-enabled users. This time, however, the collection is piped to the **Where-Object** cmdlet, which picks out only users where the RegistrarPool property is not equal to a null value. (In other words, users who have been assigned a Registrar pool.) That filtered collection is then piped to the **Get-CsUserPoolInfo** cmdlet, which displays pool information for each user in the filtered collection. 
  
```
Get-CsUser | Where-Object {$_.RegistrarPool -ne $Null} | Get-CsUserPoolInfo
```

### EXAMPLE 4

In Example 4, pool information is displayed for all the users who have been assigned the primary pool redmond-cs-001.litwareinc.com. To do this, the **Get-CsUser** cmdlet is called along with the Filter parameter; the filter value {RegistrarPool -eq "redmond-cs-001.litwareinc.com"} returns only those users where the fully qualified domain name of the RegistrarPool property is equal to redmond-cs-001.litwareinc.com. That collection is then piped to the **Get-CsUserPoolInfo** cmdlet, which retrieves pool information for each user in the collection. 
  
```
Get-CsUser -Filter {RegistrarPool -eq "redmond-cs-001.litwareinc.com"} | Get-CsUserPoolInfo
```

### EXAMPLE 5

The command shown in Example 5 returns pool information for all the users who have not been assigned a backup Registrar pool. To carry out this task, the command first calls the **Get-CsUser** cmdlet to return a collection of all the users who have been enabled for Lync Server. That information is then piped to the **Get-CsUserPoolInfo** cmdlet, which retrieves pool information for each user in the collection. Finally, that pool information is piped to the **Where-Object** cmdlet, which displays data only for those users where the BackupPoolFqdn property is equal to a null value. 
  
```
Get-CsUser | Get-CsUserPoolInfo | Where-Object {$_.BackupPoolFqdn -eq $Null}
```

## Detailed Description
<a name="sectionSection1"> </a>

When a user is enabled for Lync Server, he or she must be homed on a Registrar pool. This pool is responsible for authenticating the user and for keeping track of his or her current status and location. If you need to know the Registrar pool that a user has been assigned to you can retrieve that information by using a command similar to this:
  
```
Get-CsUser "Ken Myer" | Select-Object RegistrarPool
```

In many cases, simply knowing a user's Registrar pool might be all the information you need. In other cases, however, you might also want to know such things as the backup Registrar pool the user has been assigned to (that is, the pool to be used if the primary Registrar pool is unavailable); the names of the individual computers that make up these pools; and the User Services pool the user has been assigned to. That type of detailed information can be returned by running the **Get-CsUserPoolInfo** cmdlet. 
  
For Lync Server 2013, the Get-CsUserPoolInfo cmdlet has been modified to return information about a user's primary Front End servers in his or her primary pool and in his or her replica pool. When a pool has multiple Front End servers, each user is assigned to a routing group which, in turn, is assigned to primary Front End server and a replica Front End server. When a user logs on, by default he or she is registered with the primary Front End server; in the Get-CsUserPoolInfo output that server is listed as the PrimaryPoolPrimaryRegistrar. If the user's primary pool has been failed over, then that user will be registered with the primary Front End server on the backup (replica) pool. That server is listed in the output as the BackupPoolPrimaryRegistrar.
  
Note that replica information will be shown only if the user's primary pool has been assigned a backup pool.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsUserPoolInfo** cmdlet locally: RTCUniversalReadOnlyAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell command-line interface prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsUserPoolInfo"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user whose user pool information is to be retrieved. Identities can be specified using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory Domain Services display name (for example, Ken Myer). You can also reference a user account by using the user's Active Directory distinguished name.  <br/> You can use the asterisk (\*) wildcard character when using the Display Name as the user Identity. For example, the Identity "\* Smith" returns information for users who have a last name that ends with the string value " Smith".  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the user pool information from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

String or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Get-CsUserPoolInfo** cmdlet accepts a pipelined string value representing the SamAccountName of a user account that has been enabled for Lync Server. The cmdlet also accepts pipelined instances of the Active Directory user object. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsUserPoolInfo** cmdlet returns instances of the Microsoft.Rtc.Management.Xds.GetOCsUserPoolInfoCmdlet+UserInformation object. 
  

