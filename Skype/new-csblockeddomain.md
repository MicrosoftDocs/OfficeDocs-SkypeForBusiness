---
title: New-CsBlockedDomain
ms.prod: SKYPEFORBUSINESS
ms.assetid: c7b49baf-759b-485f-9391-58584b227fd5
---


# New-CsBlockedDomain
[]
Adds a new domain to the list of domains blocked for federation. By definition, your users are not allowed to use Skype for Business Server 2015 applications to communicate with people from the blocked domain; for example, users cannot use Skype for Business to exchange instant messages with anyone with a SIP account in a domain that appears on the blocked list. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsBlockedDomain -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

In Example 1, the domain fabrikam.com is added to the list of blocked domains. To do this, the **New-CsBlockedDomain** cmdlet is called, along with the Identity parameter, which is assigned the name of the domain to be blocked. In addition, the Comment parameter is included in order to add a comment to the blocked domain. Note that this command will fail if fabrikam.com is already on the blocked list or on the allowed list.
  
    
    

```

New-CsBlockedDomain -Identity "fabrikam.com" -Comment "Blocked per Ken Myer."
```


### EXAMPLE 2

Example 2 demonstrates how you can use the InMemory parameter to create a new blocked domain that initially exists only in memory. After you modify the property values of this in-memory-only domain you can then call the **Set-CsBlockedDomain** cmdlet to add the domain to the blocked list.
  
    
    
To perform this task, the first line in the command uses the **New-CsBlockedDomain** cmdlet and the InMemory parameter to create a blocked domain with the Identity fabrikam.com. Upon creation, this virtual domain is stored in the variable $x.
  
    
    
In the second line, the Comment property of the virtual domain is modified. After that, line 3 uses the **Set-CsBlockedDomain** cmdlet to add the virtual domain to the blocked list. Without line 3, the virtual domain would exist only in memory and would never be added to the blocked list. Instead, the virtual domain will disappear as soon as you end your Windows PowerShell session or delete the variable $x.
  
    
    



```
$x = New-CsBlockedDomain -Identity "fabrikam.com" -InMemory
$x.Comment = "Blocked per Ken Myer."
Set-CsBlockedDomain -Instance $x
```


## Detailed Description

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another by using SIP applications such as Skype for Business. Skype for Business Server 2015 allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
    
    
Setting up direct federation with another organization involves several tasks. To begin with, you must enable your servers running the Skype for Business Server 2015 Access Edge service to allow federation. In addition, the other organization must enable federation with you; federation cannot be established unless both parties agree to the relationship.
  
    
    
To establish a federated relationship you might also need to manage two federation-related lists: the allowed list and the blocked list. The allowed list represents the organizations you have chosen to federate with; if a domain appears on the allowed list then (depending on your configuration settings) your users will be able to exchange instant messages and presence information with users who have accounts in that federated domain. Conversely, the blocked list represents domains that users are expressly forbidden from federating with; for example, messages sent from a blocked domain will automatically be rejected by Skype for Business Server 2015.
  
    
    
The **New-CsBlockedDomain** cmdlet enables you to add a domain to the list of blocked domains.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Domain_ <br/> |Required  <br/> |System.String  <br/> |FQDN (for example, fabrikam.com) of the domain to be added to the blocked list. You can use either the Identity or the Domain parameter (but not both) in order to specify the domain name. If you use Identity, the Domain property will be set to the same value that is assigned to Identity. If you use Domain, the Identity property will be set to the same value that is assigned to Domain.  <br/> Note that Domains must be unique: if the specified domain already exists on either the blocked or the allowed list, the command will fail.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name (FQDN) of the domain to be added to the blocked list; for example, "fabrikam.com". You can use either the Identity or the Domain parameter (but not both) in order to specify the domain name. If you use Identity, the Domain property will be set to the same value assigned to Identity. If you use Domain, the Identity property will be set to the same value that is assigned to Domain.  <br/> Note that Identities must be unique: if the specified domain already exists on either the blocked or the allowed list, the command will fail.  <br/> |
| _Comment_ <br/> |Optional  <br/> |System.String  <br/> |Optional string value that provides additional information about the blocked domain. For example, you might add a Comment that explains why the domain has been blocked.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-<cmdlet>**. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None. The **New-CsBlockedDomain** cmdlet does not accept pipelined input.
  
    
    

## Return Types

Creates instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.BlockedDomain object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsBlockedDomain](get-csblockeddomain.md)
  
    
    
 [Remove-CsBlockedDomain](remove-csblockeddomain.md)
  
    
    
 [Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)
  
    
    
 [Set-CsBlockedDomain](set-csblockeddomain.md)
