---
title: New-CsClientVersionPolicy
ms.prod: SKYPEFORBUSINESS
ms.assetid: 8c95493a-ce18-49eb-937f-7348743fcbb4
---


# New-CsClientVersionPolicy
[]
Creates a new client version policy. Client version policies enable you to specify which versions of clients (such as Microsoft Office Communicator 2007 R2) will be able to log on to your Skype for Business Server 2015 system. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsClientVersionPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Rules <PSListModifier>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

In Example 1, a new client version policy is created for the Redmond site. Because no parameters are specified (other than the mandatory Identity parameter), the new policy will contain all of the default values for a client version policy.
  
    
    

```

New-CsClientVersionPolicy -Identity site:Redmond
```


### EXAMPLE 2

The command shown in Example 2 creates a new client version policy for each site in the organization. To accomplish this task, the command first calls the **Get-CsSite** cmdlet without any additional parameters; that returns a collection of all the sites in the topology. This collection of sites is then then piped to the **Select-Object** cmdlet, which extracts the Identity property for each site. Those Identities are then piped to the **ForEach-Object** cmdlet, which takes each site in the collection and creates a new client version policy for that site.
  
    
    

```
Get-CsSite | Select-Object Identity | ForEach-Object {New-CsClientVersionPolicy -Identity ("site:" + $_.Identity)}
```


## Detailed Description

Client version policies represent a collection of client version rules; in turn, client version rules are used to determine which client applications are allowed to log on to Skype for Business Server 2015. When a user attempts to log on to Skype for Business Server 2015, his or her client application sends a SIP header to the server; this header includes detailed information about the application itself, including the software's major version, minor version, and build number. The version information included in the SIP header is then checked against a collection of client version rules to see if any rules apply to that particular application. If such a rule exists, Skype for Business Server 2015 will then take the action specified by the rule. For example, the rule might tell Skype for Business Server 2015 to allow the logon, to block it, or to allow the logon but then silently upgrade the client application to the latest version (for example, upgrade Communicator 2007 R2 to Skype for Business).
  
    
    
Client version policies, which can be applied at the global scope, the site scope, the service scope (Registrar service only), or the per-user scope, give you flexibility in determining which client applications can be used to access the system. For example, as a general rule you might want to prevent users from logging on to Skype for Business Server 2015 by using Communicator 2007 R2; you might want to do that because the older client application does not support the same features and capabilities as Skype for Business. However, due to hardware or software conflicts, you might also have a group of users who cannot upgrade to Skype for Business. In that case, you can create a separate rule -- and a separate client version policy -- that allows those users to log on from within Communicator 2007 R2.
  
    
    
Note, however, that anonymous users are only affected by global policies. That's because anonymous users are not associated with a site or service, and cannot be assigned a per-user policy.
  
    
    
New client version policies are created by using the **New-CsClientVersionPolicy** cmdlet. These new policies can be created at the site scope, the service scope (Registrar service only), or at the per-user scope.
  
    
    
It's important to note that client version policies do not apply to federated users; instead, federated users are bound by the client version policies used in their own organization. For example, suppose a federated user uses client A, a client allowed by the federated organization. As long as the federated organization allows the use of client A, this user will be able to communicate with your organization using that client. This will be true even if your client version policy blocks the use of client A. Client version policies enforced in your organization do not override the client version policies used in a federated organization.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the policy to be created. To create a policy at the site scope, use syntax similar to this:  `-Identity "site:Redmond"`. To create a policy at the service scope, use syntax similar to this:  `-Identity "Registrar:atl-cs-001.litwareinc.com"`. The Registrar service is the only service that can host a client version policy.  <br/> Policies can also be created at the per-user scope. To create a per-user policy, use syntax similar to this:  `-Identity "SalesDepartmentPolicy"`.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to provide explanatory text about the policy. For example, you might include information about the users that the policy should be assigned to.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-<cmdlet>**. <br/> |
| _Rules_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of client version policy rules. You can add and remove rules from a policy by using the **New-CsClientVersionPolicyRule** cmdlet and the **Remove-CsClientVersionPolicyRule** cmdlet. To add a rule at the time you create the new policy, create the rule and store the value in a variable (for example, $x). You can then use syntax similar to this when creating the new policy: <br/>  `New-CsClientVersionPolicy -Identity "RedmondClientVersionPolicy" -Rules @{Add=$x}` <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for whom the new client version policy is being created. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None. The **Get-CsClientVersionPolicy** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **New-CsClientVersionPolicy** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionPolicy object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsClientVersionPolicy](get-csclientversionpolicy.md)
  
    
    
 [Grant-CsClientVersionPolicy](grant-csclientversionpolicy.md)
  
    
    
 [Remove-CsClientVersionPolicy](remove-csclientversionpolicy.md)
  
    
    
 [Set-CsClientVersionPolicy](set-csclientversionpolicy.md)
