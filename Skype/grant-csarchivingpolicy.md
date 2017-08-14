---
title: Grant-CsArchivingPolicy
ms.prod: SKYPEFORBUSINESS
ms.assetid: 675f5d8d-d8f9-4d19-b11b-75df48b09467
---


# Grant-CsArchivingPolicy
[]
Enables you to assign instant messaging (IM) session archiving policies to users or sets of users. These policies give you the ability to archive all IM sessions that take place between internal users, and/or to archive all IM sessions that take place between internal users and external partners. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Grant-CsArchivingPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

In Example 1, the archiving policy RedmondArchivingPolicy is assigned to the user with the display name "Ken Myer". Note that, with the **Grant-CsArchivingPolicy** cmdlet, the Identity property refers to the Identity of the user, not the Identity of the archiving policy. Instead, the policy to be assigned is specified by using the PolicyName parameter; the parameter value is the policy Identity (minus the "tag:" prefix).
  
    
    

```

Grant-CsArchivingPolicy -Identity "Ken Myer" -PolicyName RedmondArchivingPolicy
```


### EXAMPLE 2

In Example 2, all of the users with accounts in the Redmond organizational unit (OU) are assigned the archiving policy RedmondArchivingPolicy. To do this, the **Get-CsUser** cmdlet and the OU parameter are used to return a collection of all the users who have accounts in the OU with the distinguished name "OU=Redmond,dc=litwareinc,dc=com". This collection is then piped to the **Grant-CsArchivingPolicy** cmdlet, which assigns the policy RedmondArchivingPolicy to each user in the collection.
  
    
    

```
Get-CsUser -OU "OU=Redmond,dc=litwareinc,dc=com" | Grant-CsArchivingPolicy -PolicyName RedmondArchivingPolicy
```


### EXAMPLE 3

The command shown in Example 3 assigns the policy RedmondArchivingPolicy to all the users who work in Redmond. To carry out this task, the **Get-CsUser** cmdlet is called along with the LdapFilter parameter; the LDAP filter value "l=Redmond" returns a collection of all the users who work in the city of Redmond. (In the LDAP query language, l, a lowercase L, is short for "locality", or city.) This collection is then piped to the **Grant-CsArchivingPolicy** cmdlet, which assigns the RedmondArchivingPolicy policy to each user in the collection.
  
    
    

```
Get-CsUser -LdapFilter "l=Redmond" | Grant-CsArchivingPolicy -PolicyName RedmondArchivingPolicy
```


### EXAMPLE 4

In Example 4 all the users homed on the Registrar pool atl-cs-001.litwareinc.com are assigned the policy RedmondArchivingPolicy. To do this, the **Get-CsUser** cmdlet is first used to return all the users who have been enabled for Skype for Business Server 2015. This collection is then piped to the **Where-Object** cmdlet, which selects only those users who have a RegistrarPool that is equal to atl-cs-001-litwareinc.com. This filtered collection is then piped to the **Grant-CsArchivingPolicy** cmdlet, which assigns the policy RedmondArchivingPolicy to each user in the collection.
  
    
    

```
Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Grant-CsArchivingPolicy -PolicyName RedmondArchivingPolicy
```


### EXAMPLE 5

Example 5 locates all the users who have been assigned the policy RedmondArchivingPolicy and then assigns each of these users a different policy: NorthAmericaArchivingPolicy. To perform this task, the **Get-CsUser** cmdlet is used to return a collection of all the users who have been enabled for Skype for Business Server 2015; the Filter parameter and the filter value {ArchivingPolicy -eq "RedmondArchivingPolicy"} limit the returned data to accounts where the ArchivingPolicy is equal to "RedmondArchivingPolicy". The filtered collection is then piped to the **Grant-CsArchivingPolicy** cmdlet, which assigns the policy NorthAmericaArchivingPolicy to each user in the collection.
  
    
    

```
Get-CsUser -Filter {ArchivingPolicy -eq "RedmondArchivingPolicy"} | Grant-CsArchivingPolicy -PolicyName "NorthAmericaArchivingPolicy"
```


### EXAMPLE 6

Example 6 is a variation of Example 5. This time, however, the policy RedmondArchivingPolicy is unassigned from all the users who were previously assigned that policy: calling the **Grant-CsArchivingPolicy** cmdlet with a PolicyName equal to $Null removes any previously assigned per-user policies.
  
    
    

```
Get-CsUser -Filter {ArchivingPolicy -eq "RedmondArchivingPolicy"} | Grant-CsArchivingPolicy -PolicyName $Null
```


## Detailed Description

Many organizations find it useful to keep an archive of all the IM sessions that their users take part in; other organizations are legally required to keep such an archive. In order to archive IM sessions with Skype for Business Server 2015, you must perform two steps. First, you need to enable archiving at the global and/or the site scope by using the **Set-CsArchivingConfiguration** cmdlet. This gives you the ability to archive IM sessions; however, it does not automatically begin archiving those sessions.
  
    
    
To actually save transcripts of your IM sessions, you must complete step 2: create one or more IM session archiving policies. These policies determine which users will have their IM sessions recorded as well as which type of IM sessions (internal and/or external) will be archived. Internal IM sessions are sessions where all the participants are authenticated users who have Active Directory accounts within your organization. By comparison, external IM sessions are sessions where at least one participant is an unauthenticated user who does not have an Active Directory account within your organization. You can choose to archive only internal sessions, only external sessions, or both internal and external sessions.
  
    
    
Archiving policies can be assigned to the global scope or to the site scope. In addition, these policies can be assigned to the per-user scope and then applied to a specific user or a specific set of users. For example, suppose your global policy only archives only internal IM sessions. In that case, you might create a second policy, one that archives both internal and external sessions and apply that policy only to your sales staff. Because per-user policies take precedence over global and site policies, members of the sales staff will have all their IM sessions archived. Other users (users who are not part of the sales department and are not affected by the sales policy) will have only their internal IM sessions archived.
  
    
    
The **Grant-CsArchivingPolicy** cmdlet is used to assign per-user archiving policies to a user or specified set of users.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account the policy should be assigned to. User Identities can be specified by using one of four formats: 1) The user's SIP address; 2) the user principal name (UPN); 3) the user's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). User Identities can also be referenced by using the user's Active Directory distinguished name.  <br/> In addition, you can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity "* Smith" returns all the users who have a display name that ends in the string value " Smith".  <br/> |
| _PolicyName_ <br/> |Required  <br/> |System.String  <br/> |"Name" of the policy to be assigned. The PolicyName is simply the policy Identity minus the scope designator "tag:". For example, a policy with the Identity tag:Redmond has a PolicyName equal to Redmond; a policy with the Identity tag:RedmondArchivingPolicy has a PolicyName equal to RedmondArchivingPolicy.  <br/> To remove a per-user policy that has been assigned to a user, set PolicyName to a null value:  <br/>  `-PolicyName $Null` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to specify a domain controller to connect to when assigning the policy. If this parameter is not included then the cmdlet will use the first available domain controller.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, causes the cmdlet to pass the user object (or objects) through the Windows PowerShell pipeline. By default, the **Grant-CsArchivingPolicy** cmdlet does not pass objects through the pipeline. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   

## Input Types

String value or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Grant-CsArchivingPolicy** cmdlet accepts pipelined input of string values representing the Identity of a user account. The cmdlet also accepts pipelined input of user objects.
  
    
    

## Return Types

The **Grant-CsArchivingPolicy** cmdlet does not return a value or object. Instead, the cmdlet assigns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.IM.ImArchivingPolicy object to users or groups of users. However, if you include the PassThru parameter, the cmdlet will return instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact.
  
    
    

## See also


#### 


  
    
    
 [Get-CsArchivingPolicy](get-csarchivingpolicy.md)
  
    
    
 [New-CsArchivingPolicy](new-csarchivingpolicy.md)
  
    
    
 [Remove-CsArchivingPolicy](remove-csarchivingpolicy.md)
  
    
    
 [Set-CsArchivingPolicy](set-csarchivingpolicy.md)
