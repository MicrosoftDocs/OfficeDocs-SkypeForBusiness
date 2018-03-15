---
title: "Remove-CsClientVersionPolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2fd9ca4c-8b4f-41f0-b051-5b486376008c
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsClientVersionPolicy
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes the specified client version policy. Client version policies enable you to specify which clients (such as Microsoft Office Communicator 2007 R2) will be able to log on to your Lync Server system. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsClientVersionPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 deletes the client version policy for the Redmond site. 
  
```
Remove-CsClientVersionPolicy -Identity site:Redmond
```

### EXAMPLE 2

In Example 2, all of the client version policies configured at the per-user scope are deleted. To do this, the command first calls the **Get-CsClientVersionPolicy** cmdlet and includes the Filter parameter; the filter value "tag:*" limits the returned data to policies configured at the per-user scope. This filtered collection is then piped to the **Remove-CsClientVersionPolicy** cmdlet, which deletes each item in the collection. 
  
```
Get-CsClientVersionPolicy -Filter tag:* | Remove-CsClientVersionPolicy
```

## Detailed Description
<a name="sectionSection1"> </a>

Client version policies represent a collection of client version rules; in turn, client version rules are used to determine which client applications are allowed to log on to Lync Server. When a user attempts to log on to Lync Server, his or her client application sends a SIP header to the server; this header includes detailed information about the application itself, including the software's major version, minor version, and build number. The version information included in the SIP header is then checked against a collection of client version rules to see if any rules apply to that particular application. If such a rule exists, Lync Server will then take the action specified by the rule. For example, the rule might tell Lync Server to allow the logon, to block it, or to allow the logon but then silently upgrade the client application to the latest version (for example, upgrade Communicator 2007 R2 to Lync 2013).
  
Client version policies, which can be applied at the global scope, the site scope, the service scope (Registrar service only), or the per-user scope, give you flexibility in determining which client applications can be used to access the system. For example, as a general rule you might want to prevent users from logging on to Lync Server by using Communicator 2007 R2; that's because Communicator 2007 R2 does not support the same features and capabilities as Lync 2013. However, due to hardware or software conflicts you might also have a group of users who cannot upgrade to Lync 2013. In that case, you can create a separate rule -- and a separate client version policy -- that allows those users to log on from within Communicator 2007 R2.
  
You can create new policies by using the **New-CsClientVersionPolicy** cmdlet. These custom policies can later be removed by running the **Remove-CsClientVersionPolicy** cmdlet. When you remove a client version policy, users previously governed by that policy will automatically inherit the next policy in the management hierarchy. For example, if you delete a per-user policy, users will automatically be governed by the appropriate service policy. If no service policy exists, then users will be governed by the appropriate site policy. If no site policy exists, then users will be governed by the global policy. 
  
Note that there will always be a global policy, meaning that no users will be left unmanaged by client version policies. Although you can run the **Remove-CsClientVersionPolicy** cmdlet against the global policy, the policy will not actually be deleted. Instead, all of the policy rules will be reset to their default values. 
  
It's important to note that client version policies do not apply to federated users; instead, federated users are bound by the client version policies used in their own organization. For example, suppose a federated user uses client A, a client allowed by the federated organization. As long as the federated organization allows the use of client A, this user will be able to communicate with your organization using that client. This will be true even if your client version policy blocks the use of client A. Client version policies enforced in your organization do not override the client version policies used in a federated organization.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsClientVersionPolicy** cmdlet: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsClientVersionPolicy\b"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the policy to be deleted. To remove a policy configured at the site scope, use syntax similar to this: -Identity "site:Redmond". To remove a policy configured at the service scope, use syntax similar to this: -Identity "Registrar:atl-cs-001.litwareinc.com". The Registrar service is the only service that can host a client version policy.  <br/> Policies can also be removed at the per-user scope. To remove per-user policies, use syntax similar to this: -Identity "SalesDepartmentPolicy".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionPolicy object. The **Remove-CsClientVersionPolicy** cmdlet accepts pipelined instances of the client version policy object. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Remove-CsClientVersionPolicy** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionPolicy object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsClientVersionPolicy](get-csclientversionpolicy.md)
  
[Grant-CsClientVersionPolicy](grant-csclientversionpolicy.md)
  
[New-CsClientVersionPolicy](new-csclientversionpolicy.md)
  
[Set-CsClientVersionPolicy](set-csclientversionpolicy.md)

