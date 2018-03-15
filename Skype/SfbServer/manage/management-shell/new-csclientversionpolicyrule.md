---
title: "New-CsClientVersionPolicyRule"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d28df005-0db0-4b17-9ca0-9dc9ed063d73
description: "Creates a new client version policy rule. Client version policy rules help determine whether users can use a specific client application to log on to Skype for Business Server 2015."
---

# New-CsClientVersionPolicyRule
 
Creates a new client version policy rule. Client version policy rules help determine whether users can use a specific client application to log on to Skype for Business Server 2015.
  
```
New-CsClientVersionPolicyRule -Identity <XdsIdentity> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 demonstrates how you can create a new client version policy rule. Policy rules have Identities that are composed of two parts: the scope where the announcement is to be assigned, and a 36-character GUID. Creating an Identity for a new client version policy rule first requires you to use the .NET Framework method NewGuid to create a new GUID. This step is carried out in the first command in the example, with the resulting GUID being stored in the variable $x. 
  
After the GUID has been created, you can then use the **New-CsClientVersionPolicyRule** cmdlet to create the new rule. This command uses four parameters: Parent, with a parameter value representing the scope (site:Redmond) for the new rule; RuleId, with the parameter value $x (representing the newly-created GUID); MajorVersion (4); and UserAgent (InHouse). In this case, the UserAgent parameter represents an in-house client application.
  
```
$x = [guid]::NewGuid()

New-CsClientVersionPolicyRule -Parent "site:Redmond" -RuleId $x -MajorVersion 4 -UserAgent InHouse
```

### EXAMPLE 2

The commands shown in Example 2 represent a variation of the command shown in Example 1: in this case, however, the new rule is initially created in memory only, and only later added to Skype for Business Server 2015. To carry out this task, the first command in the example creates the GUID portion of the Identity. In command 2, a new in-memory-only client version policy rule is created; the InMemory parameter ensures that the rule exists only in memory and is not immediately added to the Skype for Business Server 2015 infrastructure. As in Example 1, the Parent and RuleId parameters are used to specify the scope and GUID for the new rule, the two pieces that make up the rule Identity.
  
After the virtual rule has been created, the next two commands are used to assign values to the MajorVersion and UserAgent properties, respectively. When those tasks are complete, the final command in the example and the **Set-CsClientVersionPolicyRule** cmdlet is used to create the actual client version policy rule and assign the rule to the Redmond site.
  
```
$x = [guid]::NewGuid()

$z = New-CsClientVersionPolicyRule -Parent "site:Redmond" -RuleId $x -InMemory
$z.MajorVersion = 4 
$z.UserAgent = "Inhouse"
Set-CsClientVersionPolicyRule -Instance $z
```

## Detailed Description

Client version policy rules are used to determine which client applications are allowed to log on to Skype for Business Server 2015. When a user attempts to log on to Skype for Business Server 2015, his or her client application sends a SIP header to the server; this header includes detailed information about the application itself, including the software's major version, minor version, and build number. The version information is then checked against a collection of client version rules to see if any rules apply to that particular application. For example, suppose a user attempts to log on by using Microsoft Office Communicator 2007 R2. Before the user can log on to Skype for Business Server 2015, the system will check to see if there is a client version rule that applies to Office Communicator 2007 R2. If a rule exists, Skype for Business Server 2015 will then take the action specified by the rule. That action must be one of the following:
  
Allow. The user will be allowed to log on.
  
AllowAndUpgrade. The user will be allowed to log on, and his or her copy of Communicator 2007 R2 will automatically be upgraded to the latest version of Skype for Business. Upgrades are carried out using either Microsoft Update or Windows Server Update Services, depending on how you have configured your system.
  
AllowWithUrl. The user will be allowed to log on, and a message will be displayed pointing the user to a URL where the latest version of Skype for Business can be downloaded and installed. The URL must point to a website that you have created yourself; no such site is created for you when you install Skype for Business Server 2015.
  
Block. The user will not be allowed to log on.
  
BlockAndUpgrade. The user will not be allowed to log on, but his or her copy of Communicator 2007 R2 will automatically be upgraded to the latest version of Skype for Business. The user can then try to log on by using the new client application. Upgrades are carried out using either Microsoft Update or Windows Server Update Services, depending on how you have configured your system.
  
BlockWithUrl. The user will not be allowed to log on, but a message will be displayed pointing him or her to a URL where the latest version of Skype for Business can be downloaded and installed. The URL must point to a website that you have created yourself; no such site is created for you when you install Skype for Business Server 2015.
  
Client version policy rules are collected in client version policies, policies that can be configured at the global scope, the site scope, the service scope (Registrar service), or the per-user scope. New client version rules are created by using the **New-CsClientVersionPolicyRule** cmdlet. When you create a new rule you must also specify the Identity for that rule; that Identity consists of a scope (for example, site:Redmond) and a globally unique identifier (GUID). You can either put together an Identity yourself, or provide the scope (the Parent parameter) and the GUID (the RuleId parameter) to have the **New-CsClientVerisonPolicyRule** cmdlet create the Identity for you.
  
It's important to note that client version policies do not apply to federated users; instead, federated users are bound by the client version policies used in their own organization. For example, suppose a federated user uses client A, a client allowed by the federated organization. As long as the federated organization allows the use of client A, this user will be able to communicate with your organization using that client. This will be true even if your client version policy blocks the use of client A. Client version policies enforced in your organization do not override the client version policies used in a federated organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the client version policy rule to be created. The Identity of a client version policy rule consists of the scope where the rule has been configured plus a globally unique identifier (GUID). That means that a rule will have an Identity similar to this: site:Redmond/1987d3c2-4544-489d-bbe3-59f79f530a83.  <br/> Instead of using the Identity parameter you can use the Parent and RuleId parameters to have the **New-CsClientVerisonPolicyRule** cmdlet create the Identity for you. <br/> |
| _Parent_ <br/> |Required  <br/> |System.String  <br/> |Scope information for the new rule. To use the Parent parameter and create a new rule for the global policy, use this syntax: -Parent global. To create a new rule for a site policy, use syntax similar to this:  `-Parent "site:Redmond"`. To create a new rule for a service policy, use syntax similar to this:  `-parent "Registrar:atl-cs-001.litwareinc.com"`. To create a new rule for a per-user policy, use syntax similar to this:  `-Parent "RedmondClientVersionPolicy"`.  <br/> You must use either the Identity parameter or both the Parent and RuleId parameters when creating a new rule.  <br/> |
| _RuleId_ <br/> |Required  <br/> |System.String  <br/> |Globally unique identifier (GUID) for the rule. In Windows PowerShell, you can create a GUID by using the following command:  <br/>  `$x = [guid]::NewGuid()` <br/> |
| _Action_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.Action  <br/> |Action to be taken any time the rule is triggered (that is, any time someone attempts to log on by using the specified software). Valid values are:  <br/> Allow. The user will be allowed to log on.  <br/> AllowWithUrl. The user will be allowed to log on, and a message will be displayed pointing him or her to a URL where the latest version of Lync can be downloaded and installed.  <br/> AllowAndUpgrade. The user will be allowed to log on, and his or her copy of Communicator will automatically be upgraded to the latest version of Lync.  <br/> Block. The user will not be allowed to log on.  <br/> BlockWithUrl. The user will not be allowed to log on, but a message will be displayed pointing him or her to a URL where the latest version of Lync can be downloaded and installed.  <br/> BlockAndUpgrade. The user will not be allowed to log on, but his or her copy of Communicator will automatically be upgraded to the latest version of Lync. The user can then try to log on by using the new client application.  <br/> |
| _ActionUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL where users can download the latest version of Lync. This property is required if the Action is set to BlockWithUrl or AllowWithUrl.  <br/> |
| _BuildNumber_ <br/> |Optional  <br/> |System.UInt16  <br/> |Build number of the software. For example, if your copy of Communicator is version 2.0.6362.111, then the BuildNumber is 6362. Build numbers represent internal versions of the software during the development process, and help to ensure that you are using the final release version as opposed to a pre-release version.  <br/> |
| _CompareOp_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.CompareOp  <br/> |Comparison operator used to determine if the client software attempting to log on was released before, after, or at the same time as the version specified in the rule. Valid values are:  <br/> EQL (equal to)  <br/> NEQ (not equal to)  <br/> GTR (greater than)  <br/> GEQ (greater than or equal to)  <br/> LSS (less than)  <br/> LEQ (less than or equal to)  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide additional information about the client version rule. For example, the Description might include information about who to contact if you believe the rule should be changed.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not the client version rule is to be used. If the Enabled property is set to False ($False), then the rule will be ignored any time a user attempts to log on with the specified software. The default value is True.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _MajorVersion_ <br/> |Optional  <br/> |System.UInt16  <br/> |Major version of the software. For example, if your copy of Communicator is version 2.0.6362.111, then the MajorVersion is 2. Major versions equate to primary releases of the software. You must assign a value to the MajorVersion property any time you create a new rule.  <br/> |
| _MinorVersion_ <br/> |Optional  <br/> |System.UInt16  <br/> |Minor version of the software. For example, if your copy of Communicator is version 2.0.6362.111, then the MinorVersion is 0. Minor versions equate to interim releases of the software.  <br/> |
| _Priority_ <br/> |Optional  <br/> |System.Int32  <br/> |Relative priority of the rule. Rules are processed in priority order, with the rule that has priority 0 being processed first, the rule that has priority 1 being processed second, and so on. If you assign a priority that is already in use, the new rule will use that priority and other rules will be renumbered accordingly.  <br/> |
| _QfeNumber_ <br/> |Optional  <br/> |System.UInt16  <br/> |Quick fix engineering number of the software. For example, if your copy of Communicator is version 2.0.6362.111, then the QfeNumber is 111. QFE numbers represent planned updates to an application that are made available after the software's official release.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for whom the new client version policy rule is being created. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _UserAgent_ <br/> |Optional  <br/> |System.String  <br/> |Designator used to identify the software client. For example, OC is the user agent designation for Communicator.  <br/> |
| _UserAgentFullName_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide a friendly name for the user agent. For example, instead of relying on the user agent UCCP to identify the agent administrators might spell the name out in full: Microsoft Unified Communications Client.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **New-CsClientVersionPolicyRule** cmdlet does not accept pipelined input.
  
## Return Types

The **New-CsClientVersionPolicyRule** cmdlet creates new instances of Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.Rule object.
  
## See also

#### 

[Get-CsClientVersionPolicyRule](get-csclientversionpolicyrule.md)
  
[Remove-CsClientVersionPolicyRule](remove-csclientversionpolicyrule.md)
  
[Set-CsClientVersionPolicyRule](set-csclientversionpolicyrule.md)

