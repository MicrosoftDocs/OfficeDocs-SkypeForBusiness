---
title: Grant-CsLocationPolicy
ms.prod: SKYPEFORBUSINESS
ms.assetid: f820f892-c247-447c-947a-00414189842e
---


# Grant-CsLocationPolicy
[]
Assigns an Enhanced 9-1-1 (E9-1-1) location policy to individual users or groups. The E9-1-1 service enables those who answer 911 calls to determine the caller's geographic location. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Grant-CsLocationPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

In Example 1, the **Grant-CsLocationPolicy** cmdlet is used to assign the Reno location policy to user Ken Myer.
  
    
    

```

Grant-CsLocationPolicy -Identity "Ken Myer" -PolicyName Reno
```


### EXAMPLE 2

In Example 2, the AccountingArea policy is assigned to all the users who are in the Accounting department. To return a collection of all the users in the Accounting department, the **Get-CsUser** cmdlet is used along with the LDAPFilter parameter. The query value passed to LDAPFilter--"Department=Accounting"--returns all the users who have an Active Directory Department setting of Accounting. This collection is then passed to the **Grant-CsLocationPolicy** cmdlet, which proceeds to assign the AccountingArea policy to each user in the collection.
  
    
    

```
Get-CsUser -LDAPFilter "Department=Accounting" | Grant-CsLocationPolicy -PolicyName AccountingArea
```


### EXAMPLE 3

This example grants the location policy Reno to the user with the Identity (in this case, the display name) Ken Myer. In addition, the example includes the parameter PassThru, which will cause the user information for user Ken Myer to be displayed after the location policy has been granted. However, rather than immediately displaying the user information to the console, that information is piped to the **Select-Object** cmdlet, which will display only the DisplayName and LocationPolicy properties of the user.
  
    
    
One thing to notice with this example is that the newly granted location policy will appear in the output under LocationPolicy, but it will appear as an Anchor value rather than as a policy name. (An Anchor value is a numeric value automatically assigned to a policy at the time it is created.) To see that the policy name has been applied, run the command  `Get-CsUser -Identity "Ken Myer" | Select-Object DisplayName, LocationPolicy`.
  
    
    



```
Grant-CsLocationPolicy -Identity "Ken Myer" -PolicyName Reno -PassThru | Select-Object DisplayName, LocationPolicy
```


## Detailed Description

The location policy is used to apply settings that relate to E9-1-1 functionality. The location policy determines whether a user is enabled for E9-1-1, and if so, what the behavior is of an emergency call. For example, you can use the location policy to define what number constitutes an emergency call (911 in the United States), whether corporate security should be automatically notified, and how the call should be routed. This cmdlet grants a location policy to a specific user or group.
  
    
    
IMPORTANT: The location policy behaves differently from other policies in Skype for Business Server 2015 in terms of order of scope. For all other policies, if a policy is defined at the per-user scope, the policy is applied to any user granted that policy. If the user has not been granted a per-user policy, the site policy is applied. If there is no site policy, the global policy is applied. Location policies are applied in the same way, with one exception: a per-user location policy can also be assigned to a network site. (A network site consists of a group of subnets.) If the user is making the emergency call from a location that is mapped to a network site within the organization, the user-level policy assigned to that network site is used. This functionality will override a per-user policy that has been granted to that user. If the user calls from a location that is unknown or unmapped in the organization, the standard policy scoping will be applied.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account the policy should be assigned to. User identities can be specified using one of four formats: 1) The user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). Note that the SAMAccountName cannot be used as an identity.  <br/> In addition, you can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity "* Smith" would grant the policy to all the users with the last name Smith.  <br/> |
| _PolicyName_ <br/> |Required  <br/> |System.String  <br/> |The Identity of the location policy to apply to the user.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Including this parameter (which does not take a value) displays the user information when the cmdlet completes. Normally there is no output when this cmdlet is run.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   

## Input Types

String. Accepts a pipelined string value representing the Identity of a user account to which the location policy is being granted.
  
    
    

## Return Types

When used with the PassThru parameter, returns an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADUserOrAppContact.
  
    
    

## See also


#### 


  
    
    
 [New-CsLocationPolicy](new-cslocationpolicy.md)
  
    
    
 [Remove-CsLocationPolicy](remove-cslocationpolicy.md)
  
    
    
 [Set-CsLocationPolicy](set-cslocationpolicy.md)
  
    
    
 [Get-CsLocationPolicy](get-cslocationpolicy.md)
  
    
    
 [Test-CsLocationPolicy](test-cslocationpolicy.md)
  
    
    
 [Get-CsUser](get-csuser.md)
