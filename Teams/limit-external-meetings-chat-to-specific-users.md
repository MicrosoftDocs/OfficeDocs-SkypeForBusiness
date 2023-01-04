---
title: Limit external meetings and chat to specific users
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: alsolom
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - m365initiative-externalcollab
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
- ms.teamsadmincenter.externalaccess.overview
- chat-teams-channels-revamp
appliesto: 
  - Microsoft Teams
ms.localizationpriority: normal
description:  
---

# Limit external meetings and chat to specific users


## Limit external access to specific people

If you've enabled any of the external access controls at an organization level, you can limit external access to specific users using PowerShell.

You can use the following example script, substituting *Control* for the control you want to change, *PolicyName* for the name you want to give the policy, and *UserName* for each user for whom you want to enable/disable external access.


### Using PowerShell

Organization level settings can be configured using [Set-CSTenantFederationConfiguration](/powershell/module/skype/set-cstenantfederationconfiguration) and user level settings can be configured using [Set-CsExternalAccessPolicy](/powershell/module/skype/set-csexternalaccesspolicy).

The following table shows the cmdlet parameters used for configuring federation.

|Configuration|Organization level (Set-CSTenantFederationConfiguration)|User level (Set-CsExternalAccessPolicy)|
|:-------|:--------|:------------------|
|Enable/disable meetings and chat with other Teams organizations and Skype for Business|`-AllowFederatedUsers`|`-EnableFederationAccess`|
|Specify allowed domains|`-AllowedDomains`|Not available|
|Specify blocked domains|`-BlockedDomains`|Not available|
|Enable/disable chat with Teams users that are not managed by an organization|`-AllowTeamsConsumer`|`-EnableTeamsConsumerAccess`|
|Enable/disable Teams users not managed by an organization initiating conversations|`-AllowTeamsConsumerInbound`|`-EnableTeamsConsumerInbound`|
|Enable/disable chat with Skype users|`-AllowPublicUsers`|`-EnablePublicCloudAccess`|

It's important to note that disabling a policy "rolls down" from tenant to users. For example:

```PowerShell
Set-CsTenantFederationConfiguration -AllowFederatedUsers $false
Set-CsExternalAccessPolicy -EnableFederationAccess $true
```

In this example, although the user level policy is enabled, users would not be able to communicate with managed Teams users or Skype for Business users because this type of federation was turned off at the organization level. Therefore, if you want to enable these controls for a subset of users you must turn on the control at an organization level and create two group policies – one that applies to the users that should have the control turned off, and one that applies to the users that should have the control turned on.



Be sure you have installed the [Microsoft Teams PowerShell Module](/microsoftteams/teams-powershell-install) before running the script.

```PowerShell
Connect-MicrosoftTeams

# Disable external access globally
Set-CsExternalAccessPolicy -<Control> $false

# Create a new external access policy
New-CsExternalAccessPolicy -Identity <PolicyName> -<Control> $true

# Assign users to the policy
$users_ids = @("<UserName1>", "<UserName2>")
New-CsBatchPolicyAssignmentOperation -PolicyType ExternalAccessPolicy -PolicyName "<PolicyName>" -Identity $users_ids

```

For example, enable communications with external Teams users not managed by an organization:

```PowerShell
Connect-MicrosoftTeams

Set-CsExternalAccessPolicy -EnableTeamsConsumerAccess $false

New-CsExternalAccessPolicy -Identity ContosoExternalAccess -EnableTeamsConsumerAccess $true

$users_ids = @("MeganB@contoso.com", "AlexW@contoso.com")
New-CsBatchPolicyAssignmentOperation -PolicyType ExternalAccessPolicy -PolicyName "ContosoExternalAccess" -Identity $users_ids

```

See [New-CsBatchPolicyAssignmentOperation](/powershell/module/teams/new-csbatchpolicyassignmentoperation) for additional examples of how to compile a user list.

You can see the new policy by running `Get-CsExternalAccessPolicy`.

See also [New-CsExternalAccessPolicy](/powershell/module/skype/new-csexternalaccesspolicy) and [Set-CsExternalAccessPolicy](/powershell/module/skype/set-csexternalaccesspolicy).


## Related topics

