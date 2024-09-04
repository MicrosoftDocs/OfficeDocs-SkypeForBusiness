---
title: IT Admins - Manage external meetings and chat with people and organizations using Microsoft identities
ms.author: heidip
author: jacktremper
manager: pamgreen
ms.reviewer: nigolc
ms.date: 06/28/2024
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - m365initiative-externalcollab
  - Tier1
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
- ms.teamsadmincenter.externalaccess.overview
- chat-teams-channels-revamp
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
description: For IT admins - Learn how to configure chat and meetings with people outside your organization who use Microsoft Entra ID, Microsoft Teams Essentials, or Skype.
---

# IT Admins - Manage external meetings and chat with people and organizations using Microsoft identities

With the *external access* feature in Teams, you can allow users in your organization to chat and meet with people outside the organization who are using Microsoft as an identity provider. You can configure external access with:

- Other Microsoft 365 organizations (chat and meetings)
- Teams users not managed by an organization (those users with a [Microsoft account](https://account.microsoft.com)) (chat only)
- Skype users (chat only)

Users in your organization can accept or block incoming chats from people outside the organization. For details, see [Accept or block people outside your org who send you a chat](https://support.microsoft.com/office/4b5b917d-895a-4379-a204-a111b2e24f41).

People from outside your organization won't have access to your teams, sites, or other Microsoft 365 resources. If you want them to have access to your teams and channels, see [Collaborate with guests in a team](/microsoft-365/solutions/collaborate-as-team) and [Collaborate with external participants in a shared channel](/microsoft-365/solutions/collaborate-teams-direct-connect).

> [!NOTE]
> Your users can add apps when they host meetings or chats with people outside your organization. They can also use apps shared by external users when they join meetings or chats hosted externally. The data policies of the hosting user's organization, as well as the data sharing practices of any third-party apps shared by that user's organization, are applied. [Learn more about use of apps by people outside your organization](apps-external-users.md).

## Related settings

There are other settings in Teams—including guest access and anonymous access—that affect meetings with people outside your organization. See [Plan for meetings with external participants in Microsoft Teams](plan-meetings-external-participants.md) for more information.

The meeting lobby can control how people outside your organization join meetings. For more information, see [Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md) and [Configure the Microsoft Teams meeting lobby for sensitive meetings](configure-lobby-sensitive-meetings.md).

### Organization settings and user policies for external access

Each external access option has both an organization setting and user policies. The organization settings apply to your entire organization. User policies determine which users can use the options that you've configured at the organization level.

Configure the organization settings to specify which types of external meetings and chat you want to allow. Then configure user policies for the users who should have access to these features. Both the organization settings and user policies are turned on by default.

For a user to use external access, both the organization setting and a user policy must allow it.

Use the procedures on the tabs in this article to configure organization settings and user policies.

## [**Organization settings**](#tab/organization-settings)

In this section, you can configure:

- [Meetings and chat with trusted Microsoft 365 organizations](#specify-trusted-microsoft-365-organizations)
- [Chat with external Teams users not managed by an organization](#manage-chats-and-meetings-with-external-teams-users-not-managed-by-an-organization)
- [Chat and calls with Skype users](#manage-chat-and-calls-with-skype-users)

You can also [configure these settings by using PowerShell](#configure-organization-settings-by-using-powershell)

### Specify trusted Microsoft 365 organizations

For meetings and chat with other Microsoft 365 organizations, you can specify which domains you want to trust. By default, all external domains are allowed. You can allow or block certain domains in order to define which organizations your organization trusts for external meetings and chat.

In order to chat and meet with people in external domains, the organizations that you trust must also trust your organization, and their users must be enabled for external access. If not, they won't be able to chat with users in your organization and are considered anonymous when joining meetings hosted by your organization. [Learn more about meetings with other Microsoft 365 organizations](plan-meetings-external-participants.md#meetings-with-other-microsoft-365-organizations).

You can specify which domains are allowed or which domains are blocked. If you specify blocked domains, all other domains are allowed; if you specify allowed domains, all other domains are blocked. There are four scenarios for configuring trusted organizations:

- **Allow all external domains** - The default setting in Teams, and it lets users in your organization find, call, chat, and set up meetings with people external to your organization in any domain.

    In this scenario, your users can communicate with all external domains that are running Teams or Skype for Business so long as the other organization has also enabled external access.

- **Allow only specific external domains** - By adding domains to an **Allow** list, you limit external access to only the allowed domains. Once you set up a list of allowed domains, all other domains are blocked.

- **Block specific domains** - By adding domains to a **Block** list, you can communicate with all external domains *except* the ones you've blocked.  Once you set up a list of blocked domains, all other domains are allowed.

- **Block all external domains** - Prevents users in your organization from finding, calling, chatting, and setting up meetings with people external to your organization in any domain.

> [!NOTE]
> People from blocked domains can still join meetings anonymously if anonymous access is allowed. To learn more, see [Manage anonymous participant access to Teams meetings](anonymous-users-in-meetings.md).

![Screenshot of external domains settings](./media/external-access-domain-settings.png)

To allow specific domains

1. In the Teams admin center, go to **Users** > **External access**.

2. Under **Choose which domains your users have access to**, choose **Allow only specific external domains**.

3. Select **Allow domains**.

4. In the **Domain** box, type the domain that you want to allow and then click **Done**.

5. If you want to allow another domain, click **Add a domain**.

6. Click **Save**.

To block specific domains

1. In the Teams admin center, go to **Users** > **External access**.

2. Under **Choose which domains your users have access to**, choose **Block only specific external domains**.

3. Select **Block domains**.

4. In the **Domain** box, type the domain that you want to allow and then click **Done**.

5. If you want to block another domain, click **Add a domain**.

6. Click **Save**.

By default, when you block domains, subdomains aren't blocked. For example, if you block contoso.com, marketing.contoso.com isn't blocked. If you want to block all subdomains, you can use the [Set-CsTenantFederationConfiguration](/powershell/module/teams/set-cstenantfederationconfiguration) PowerShell cmdlet with the `-BlockAllSubdomains` parameter. For example:

```powershell
Set-CsTenantFederationConfiguration -BlockAllSubdomains $True
```

#### Block federation with Teams trial-only tenants

You can control your organization's external access with Teams trial-only tenants (that don't have any purchased seats), by using the `-ExternalAccessWithTrialTenants` setting in PowerShell (at least version 6.4.0 is required).

The default value for this setting is **Blocked**, but you can override it to **Allowed**, using:
`Set-CsTenantFederationConfiguration -ExternalAccessWithTrialTenants "Allowed"`

To block external communication with trial-only tenants:
`Set-CsTenantFederationConfiguration -ExternalAccessWithTrialTenants "Blocked"`

When set to **Blocked**, users from these trial-only tenants aren't able to search and contact your users via chats, Teams calls, and meetings (using the users' authenticated identities) and your users aren't able to reach users in these trial-only tenants. Users from the trial-only tenant are also removed from existing chats.

Users from trial-only tenants are blocked by default (with no option to override) from external communication with users in other Microsoft 365 cloud environments and with Microsoft Skype for Business server users. Two tenants with only trial subscriptions can federate with each other if the -ExternalAccessWithTrialTenants is Allowed by both tenants.

#### Diagnostic Tool

If you're an administrator, you can use the following diagnostic tool to validate if a Teams user can communicate with a Teams user in a trusted organization:

1. Select **Run Tests** below, which populates the diagnostic in the Microsoft 365 Admin Center.

   > [!div class="nextstepaction"]
   > [Run Tests: Teams Trusted Organizations](https://aka.ms/TeamsFederationDiag)

2. In the Run diagnostic pane, enter the **Session Initiation Protocol (SIP) Address** and the **Federated tenant's domain name**, and then select **Run Tests**.

3. The tests return the best next steps to address any setting or policy configurations that are preventing communication with the external Teams user.

#### Skype for Business Online

If you want chats and calls to arrive in the user's Skype for Business client, configure your users to be in any mode other than TeamsOnly. For more information, see [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md).

### Manage chats and meetings with external Teams users not managed by an organization

You can choose to enable or disable chats and meetings with external unmanaged Teams users (those not managed by an organization, such as Microsoft Teams (free)). If enabled, you can also control if people with unmanaged Teams accounts can start chats and meetings with users in your organization.

> [!NOTE]
> Chats and meetings with external unmanaged Teams users isn't available in GCC, GCC High, or DOD deployments, or in private cloud environments.

To allow chats and meetings with unmanaged Teams accounts:

1. In the Teams admin center, go to **Users** > **External access**.
2. Turn on the **People in my organization can communicate with Teams users whose accounts aren't managed by an organization** setting.
3. If you want to allow external unmanaged Teams users to start the conversation, select the **External users with Teams accounts not managed by an organization can contact users in my organization** checkbox.
5. Select **Save**.

![Screenshot of external accounts settings](./media/external-access-accounts-not-managed-by-org.png)

If **External users with Teams accounts not managed by an organization can contact users in my organization** is turned off, unmanaged Teams users can't search by email address to find users in your organization. All communications with unmanaged Teams users must be initiated by users in your organization.

To prevent chat with unmanaged Teams accounts:

1. In the Teams admin center, go to **Users** > **External access**.
1. Turn off the **People in my organization can communicate with Teams users whose accounts aren't managed by an organization** setting.
1. Select **Save**.

### Manage chat and calls with Skype users

Follow these steps to let Teams users in your organization chat with and call Skype users. Teams users can then search for and start a one-on-one text-only conversation or an audio/video call with Skype users and vice versa.

Meetings aren't supported with Skype users. If invited to a meeting, they're considered anonymous when joining.

> [!NOTE]
> External communication with Skype users isn't available in GCC, GCC High, or DOD deployments, or in private cloud environments.

To configure chat and calls with Skype users:

1. In the Teams admin center, go to **Users** > **External access**.
2. Turn the **Allow users in my organization to communicate with Skype users** setting on or off.
    ![Screenshot of Skype users setting.](./media/external-access-skype-settings.png)
3. Select **Save**.

To learn more about the ways that Teams users and Skype users can communicate, including limitations that apply, see [Teams and Skype interoperability](teams-skype-interop.md).

### Configure organization settings by using PowerShell

Trusted organizations can be configured by using the [Set-CSTenantFederationConfiguration](/powershell/module/teams/set-cstenantfederationconfiguration) cmdlet.

The following table shows the cmdlet parameters used for configuring trusted organizations.

|Configuration|Parameter|
|:-------|:--------|
|Allow or prevent meetings and chat with other Teams organizations and Skype for Business|`-AllowFederatedUsers`|
|Specify allowed domains|`-AllowedDomains`|
|Specify blocked domains|`-BlockedDomains`|
|Block subdomains|`-BlockAllSubdomains`|

Chat with Teams users not managed by an organization and Skype users can be configured by using the [Set-CSTenantFederationConfiguration](/powershell/module/teams/set-cstenantfederationconfiguration) cmdlet.

The following table shows the cmdlet parameters used for configuring chat with Skype and unmanaged Teams users.

|Configuration|Parameter|
|:-------|:--------|
|Allow or prevent chat with Teams users that aren't managed by an organization|`-AllowTeamsConsumer`|
|Allow or prevent Teams users not managed by an organization starting conversations|`-AllowTeamsConsumerInbound`|
|Allow or prevent chat with Skype users|`-AllowPublicUsers`|

Before you can run these cmdlets you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

## [**User policies**](#tab/user-policies)

If you've enabled one of the external access settings for the organization, you can specify which users in your organization can chat or meet with people outside your organization by using an external access policy (both of these must be enabled for users to chat or meet with people outside your organization.).

For meeting organizers who aren't enabled for external access, meeting attendees from other organizations are considered anonymous when joining their meetings.

### Configure external access policies

External access policies are configured by using [Set-CsExternalAccessPolicy](/powershell/module/teams/set-csexternalaccesspolicy) cmdlet.

The following table shows the cmdlet parameters used for configuring who can chat and meet with people outside your organization.

|Configuration|Parameter|
|:-------|:--------|
|Allow or prevent meetings and chat with other Teams organizations and Skype for Business|`-EnableFederationAccess`|
|Allow or prevent chat with Teams users that aren't managed by an organization|`-EnableTeamsConsumerAccess`|
|Allow or prevent Teams users not managed by an organization starting conversations|`-EnableTeamsConsumerInbound`|
|Allow or prevent chat with Skype users|`-EnablePublicCloudAccess`|

To limit external meetings and chat to specific users, you must:

- Turn off the control for the default global policy.
- Create a new policy with the control turned on, and assign the appropriate users to it.

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

The parameters for configuring external access are:

- EnableFederationAccess - controls chat and meetings with other Microsoft 365 organizations
- EnableTeamsConsumerAccess - controls chat with Teams users not managed by an organization

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

---

## Compliance and external access

See the following references to understand how external access works with compliance features in Microsoft 365.

- [eDiscovery in external access and guest environments](/microsoftteams/ediscovery-investigation#ediscovery-in-external-access-and-guest-environments)
- [Message retention with external access users](/microsoft-365/compliance/retention-policies-teams#messages-and-external-users)
- [Data loss prevention and Microsoft Teams](/microsoft-365/compliance/dlp-microsoft-teams)

## Related topics

[Use guest access and external access to collaborate with people outside your organization](communicate-with-users-from-other-organizations.md)

[Search the audit log for events in Microsoft Teams](audit-log-events.md)
