---
title: "Get-CsClientVersionPolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d99bfa89-01a7-4dd4-8f6e-96e0a84ab1ce
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsClientVersionPolicy
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about which clients (such as Microsoft Office Communicator 2007 R2) are supported in your Lync Server environment. Client version policies enable you to specify which clients (such as Office Communicator 2007 R2) will be able to log on to your Lync Server system. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsClientVersionPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In the first example, the **Get-CsClientVersionPolicy** cmdlet is called without specifying any additional parameters. This causes the **Get-CsClientVersionPolicy** cmdlet to return a collection of all the client version policies configured for use in your organization. 
  
```
Get-CsClientVersionPolicy
```

### EXAMPLE 2

In Example 2, the **Get-CsClientVersionPolicy** cmdlet returns all the client version policies that have the Identity site:Redmond. Because Identities must be unique, this command will never return more than one item. 
  
```
Get-CsClientVersionPolicy -Identity site:Redmond
```

### EXAMPLE 3

Example 3 returns all the client version policies that have been configured at the site scope. This is done by including the Filter parameter and the filter value "site:*"; that value instructs the **Get-CsClientVersionPolicy** cmdlet to return only those policies that have an Identity beginning with the string value "site:". 
  
```
Get-CsClientVersionPolicy -Filter site:*
```

### EXAMPLE 4

The command used in Example 4 displays detailed information about the individual rules configured for each client version policy. To do this, the **Get-CsClientVersionPolicy** cmdlet is first used to retrieve a collection of all the client version policies configured for use in the organization. That collection is then piped to the **Select-Object** cmdlet, which uses the ExpandProperty filter to expand the property values for the Rules property. When this property is expanded, detailed information about each rule (including such property values as build number, major version, and minor version) is displayed on the screen. 
  
```
Get-CsClientVersionPolicy | Select-Object -ExpandProperty Rules
```

## Detailed Description
<a name="sectionSection1"> </a>

Client version policies represent a collection of client version rules; in turn, client version rules are used to determine which client applications are allowed to log on to Lync Server. When a user attempts to log on to Lync Server, his or her client application sends a SIP header to the server; this header includes detailed information about the application itself, including the software's major version, minor version, and build number. The version information included in the SIP header is then checked against a collection of client version rules to see if any rules apply to that particular application. If such a rule exists, Lync Server will then take the action specified by the rule. For example, the rule might tell Lync Server to allow the logon, to block it, or to allow the logon but then silently upgrade the client application to the latest version (for example, upgrade Communicator 2007 R2 to Lync).
  
Client version policies, which can be applied at the global scope, the site scope, the service scope (Registrar service only), or the per-user scope, give you flexibility in determining which client applications can be used to access the system. For example, you might want to prevent users from logging on to Lync Server by using Communicator 2007 R2 because it does not support the same features and capabilities as Lync 2013. However, due to hardware or software conflicts, you might also have a group of users who cannot upgrade to Lync. In that case, you can create a separate rule -- and a separate client version policy -- that allows those users to log on from within Communicator 2007 R2.
  
The **Get-CsClientVersionPolicy** cmdlet provides a way for you to retrieve all of the client version policies currently in use in your organization, as well as to view the individual rules that make up each of those policies. 
  
It's important to note that client version policies do not apply to federated users; instead, federated users are bound by the client version policies used in their own organization. For example, suppose a federated user uses client A, a client allowed by the federated organization. As long as the federated organization allows the use of client A, this user will be able to communicate with your organization using that client. This will be true even if your client version policy blocks the use of client A. Client version policies enforced in your organization do not override the client version policies used in a federated organization.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsClientVersionPolicy** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsClientVersionPolicy\b"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the policy (or policies) to be retrieved. For example, this syntax returns all the policies that have been configured at the site scope: -Filter "site:\*". This syntax returns all the policies that have been configured at the per-user scope: -Filter "tag:\*".  <br/> You cannot use both the Filter and the Identity parameters in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the policy to be returned. To return the global policy, use this syntax: -Identity global. To return a policy configured at the site scope, use syntax similar to this: -Identity "site:Redmond". To return a policy configured at the service scope, use syntax similar to this: -Identity "Registrar:atl-cs-001.litwareinc.com". The Registrar service is the only service that can host a client version policy.  <br/> Policies can also be configured at the per-user scope. To return one of these policies, use syntax similar to this: -Identity "SalesDepartmentPolicy".  <br/> If this parameter is not included then all of the client version policies configured for use in your organization will be returned.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the client version policy data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsClientVersionPolicy** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsClientVersionPolicy** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersion policy object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Grant-CsClientVersionPolicy](grant-csclientversionpolicy.md)
  
[New-CsClientVersionPolicy](new-csclientversionpolicy.md)
  
[Remove-CsClientVersionPolicy](remove-csclientversionpolicy.md)
  
[Set-CsClientVersionPolicy](set-csclientversionpolicy.md)

