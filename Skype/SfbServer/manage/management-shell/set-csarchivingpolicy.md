---
title: "Set-CsArchivingPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2213f1e7-ebdb-4a70-83d9-41eee6d0e14f
description: "Modifies an existing instant messaging (IM) archiving policy. An archiving policy gives you the ability to archive all IM sessions and conferences that take place between internal users; you can also archive sessions that take place between internal users and federated partners. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsArchivingPolicy
[]
Modifies an existing instant messaging (IM) archiving policy. An archiving policy gives you the ability to archive all IM sessions and conferences that take place between internal users; you can also archive sessions that take place between internal users and federated partners. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsArchivingPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

In this example, the **Set-CsArchivingPolicy** cmdlet is used to modify the global archiving policy. In this case, the ArchiveInternal property is set to True.
  
```
Set-CsArchivingPolicy -Identity global -ArchiveInternal $True
```

### EXAMPLE 2

Example 2 is a variation of the command shown in Example 1. This time, however, all of the archiving policies in the organization are configured to allow for the archiving of IM sessions. To do this, the command first uses the **Get-CsArchivingPolicy** cmdlet to return a collection of all the IM session archiving policies currently in use. That collection is then piped to the **Set-CsArchivingPolicy** cmdlet, which sets the ArchiveInternal property of each policy to True.
  
```
Get-CsArchivingPolicy | Set-CsArchivingPolicy -ArchiveInternal $True
```

## Detailed Description

Many organizations find it useful to keep an archive of all the IM sessions that their users take part in. Other organizations are legally required to keep such an archive. In order to archive IM sessions with Skype for Business Server 2015, you must perform two steps. First, you need to enable archiving at the global and/or the site scope by using the **Set-CsArchivingConfiguration** cmdlet. This gives you the ability to archive IM sessions; however, it does not automatically begin archiving those sessions.
  
To actually save transcripts of your IM sessions, you must complete step two: create one or more archiving policies that determine which users will have their IM sessions recorded and which type of IM sessions (internal and/or external) will be archived. Internal IM sessions are sessions where all the participants are authenticated users who have Active Directory accounts within your organization; external IM sessions are sessions where at least one participant is an unauthenticated user who does not have an Active Directory account within your organization. You can choose to archive only internal sessions, only external sessions, or both internal and external sessions.
  
Archiving policies (created using the **New-CsArchivingPolicy** cmdlet) can be assigned to the global site or to the site scope. In addition, these policies can be assigned to the per-user scope; that means that a policy can be created and then applied to a specific user or group of users. For example, you might have a global policy that archives internal IM sessions for all of your users. In addition, you might create a second policy, one that archives both internal and external sessions and apply that second policy only to your sales staff. Because per-user policies take precedence over global and site policies, members of the sales staff will have all their IM sessions archived. Other users (users who are not part of the sales department and are not affected by the sales policy) will have only their internal IM sessions archived.
  
The **Set-CsArchivingPolicy** cmdlet enables you to modify the property values for any of the IM session archiving policies currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ArchiveExternal_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether external IM sessions are archived. (An external IM session is one in which at least one of the participants is an unauthenticated user who does not have an Active Directory account within your organization.) The default value is False, which means that IM sessions that include external users are not archived.  <br/> |
| _ArchiveInternal_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether internal IM sessions are archived. (An internal IM session is one in which all the participants are authenticated users who have Active Directory accounts within your organization.) The default value is False, which means that internal IM sessions are not archived.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide additional text regarding the policy. For example, the Description property might be used to detail which users the policy should be applied to.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the archiving policy to be modified. Archiving policies can be configured at the global, site, or per-user scopes. To modify the global policy, use this syntax:  `-Identity global`. To modify a site policy, use syntax similar to this:  `-Identity site:Redmond`. To modify a per-user policy, use syntax similar to this:  `-Identity SalesArchivingPolicy`. If this parameter is not specified, then the global policy will be modified.  <br/> Wildcards are not allowed when specifying an Identity.  <br/> |
| _Instance_ <br/> |Optional  <br/> |IMArchivingPolicy object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for whom the archiving policy is being modified. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.IM.IMArchivingPolicy object. The **Remove-CsArchivingPolicy** cmdlet accepts pipelined input of archiving policy objects.
  
## Return Types

The **Set-CsArchivingPolicy** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Policy.IM.IMArchivingPolicy object.
  
## See also

#### 

[Get-CsArchivingPolicy](get-csarchivingpolicy.md)
  
[Grant-CsArchivingPolicy](grant-csarchivingpolicy.md)
  
[New-CsArchivingPolicy](new-csarchivingpolicy.md)
  
[Remove-CsArchivingPolicy](remove-csarchivingpolicy.md)

