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
description: "Learn how to specify which users in your organization can engage in meetings and chat with people outside the organization."
---

# Limit external meetings and chat to specific users

If you've enabled [chat and meetings with trusted organizations](trusted-organizations-meetings-chat.md) or [chat with people not managed by an organization](skype-extended-directory-access.md), you can specify which users in your organization can chat or meet with people outside your organization by using an external access policy.

External access policies are configured by using [Set-CsExternalAccessPolicy](/powershell/module/skype/set-csexternalaccesspolicy) cmdlet.

The following table shows the cmdlet parameters used for configuring who can chat and meet with people outside your organization.

|Configuration|Parameter|
|:-------|:--------|
|Allow or prevent meetings and chat with other Teams organizations and Skype for Business|`-EnableFederationAccess`|
|Allow or prevent chat with Teams users that are not managed by an organization|`-EnableTeamsConsumerAccess`|
|Allow or prevent Teams users not managed by an organization starting conversations|`-EnableTeamsConsumerInbound`|
|Allow or prevent chat with Skype users|`-EnablePublicCloudAccess`|

To limit external meetings and chat to specific users, you must:
- Turn off the control for the default global policy.
- Create a new policy with the control turned on, and assign the appropriate users to it.

> [!NOTE]
> People for whom external meetings have been turned off can still meet with people outside the organization if those people join as guests or anonymous users (if guest sharing or anonymous join are enabled).

You can use the following example script, substituting *parameter* for the control you want to change, *PolicyName* for the name you want to give the policy, and *UserName* for each user for whom you want to enable/disable external access.

Be sure you have installed the [Microsoft Teams PowerShell Module](/microsoftteams/teams-powershell-install) before running the script.

```PowerShell
Connect-MicrosoftTeams

# Disable external access globally
Set-CsExternalAccessPolicy -<parameter> $false

# Create a new external access policy
New-CsExternalAccessPolicy -Identity <PolicyName> -<parameter> $true

# Assign users to the policy
$users_ids = @("<UserName1>", "<UserName2>")
New-CsBatchPolicyAssignmentOperation -PolicyType ExternalAccessPolicy -PolicyName "<PolicyName>" -Identity $users_ids

```

For example, to enable communications with external Teams users not managed by an organization:

```PowerShell
Connect-MicrosoftTeams

Set-CsExternalAccessPolicy -EnableTeamsConsumerAccess $false

New-CsExternalAccessPolicy -Identity ContosoExternalAccess -EnableTeamsConsumerAccess $true

$users_ids = @("MeganB@contoso.com", "AlexW@contoso.com")
New-CsBatchPolicyAssignmentOperation -PolicyType ExternalAccessPolicy -PolicyName "ContosoExternalAccess" -Identity $users_ids

```

You can see the new policy by running `Get-CsExternalAccessPolicy`.

See [New-CsBatchPolicyAssignmentOperation](/powershell/module/teams/new-csbatchpolicyassignmentoperation) for additional examples of how to compile a user list.

## Related topics

[Use guest access and external access to collaborate with people outside your organization](communicate-with-users-from-other-organizations.md)

[New-CsExternalAccessPolicy](/powershell/module/skype/new-csexternalaccesspolicy)

[Set-CsExternalAccessPolicy](/powershell/module/skype/set-csexternalaccesspolicy)