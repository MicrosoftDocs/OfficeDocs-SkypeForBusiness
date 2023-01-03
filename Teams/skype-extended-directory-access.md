---
title: Manage external meetings and chat with Teams for Life, Skype, and extended directory
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

# Manage external meetings and chat with Teams for Life, Skype, and extended directory

You can configure external meetings and chat in Teams using the *external access* feature. External access is a way for Teams users from outside your organization to find, call, chat, and set up meetings with you in Teams. You can also use external access to communicate with people from other organizations who are still using Skype for Business (online and on-premises) and Skype.

If you want people from other organizations to have access to your teams and channels, use guest access instead. For more information about the differences between external access and guest access, see [Compare external and guest access](communicate-with-users-from-other-organizations.md#compare-external-and-guest-access). 


## Manage contact with external Teams users not managed by an organization

> [!NOTE]
> The Teams and Skype interop capabilities discussed in this article aren't available in GCC, GCC High, or DOD deployments, or in private cloud environments.

Admins can choose to enable or disable communications with external Teams users that are not managed by an organization ("unmanaged"). If enabled, they can also further control if people with unmanaged Teams accounts can initiate contact (see the following image). If **External users with Teams accounts not managed by an organization can contact users in my organization** is turned off, unmanaged Teams users will not be able to search the full email address to find organization contacts and all communications with unmanaged Teams users must be initiated by organization users.

In the Teams admin center, go to **Users** > **External access**.

![Screenshot of external accounts settings](./media/external-access-accounts-not-managed-by-org.png)

To block Teams users in your organization from communicating with external Teams users whose accounts are not managed by an organization:

1. Turn off the **People in my organization can communicate with Teams users whose accounts aren't managed by an organization** setting.
2. Clear the **External users with Teams accounts not managed by an organization can contact users in my organization** checkbox.

To let Teams users in your organization communicate with external Teams users whose accounts are not managed by an organization if your Teams users have initiated the contact:

1. Turn on the **People in my organization can communicate with Teams users whose accounts aren't managed by an organization** setting.
2. Clear the **External users with Teams accounts not managed by an organization can contact users in my organization** checkbox.

To let Teams users in your organization communicate with external Teams users whose accounts are not managed by an organization and receive requests to communicate with those external Teams users:

1. Turn on the **People in my organization can communicate with Teams users whose accounts aren't managed by an organization** setting.
2. Select the **External users with Teams accounts not managed by an organization can contact users in my organization** checkbox.

## Communicate with Skype users

Follow these steps to let Teams users in your organization chat with and call Skype users. Teams users can then search for and start a one-on-one text-only conversation or an audio/video call with Skype users and vice versa.

![Screenshot of Skype users setting.](./media/external-access-skype-settings.png)

### Using the Microsoft Teams admin center

1. In the left navigation, go to **Users** > **External access**.

2. Turn on the **Allow users in my organization to communicate with Skype users** setting.

To learn more about the ways that Teams users and Skype users can communicate, including limitations that apply, see [Teams and Skype interoperability](teams-skype-interop.md).

### Using PowerShell

Organization level settings can be configured using [Set-CSTenantFederationConfiguration](/powershell/module/skype/set-cstenantfederationconfiguration) and user level settings can be configured using [Set-CsExternalAccessPolicy](/powershell/module/skype/set-csexternalaccesspolicy).

The following table shows the cmdlet parameters used for configuring federation.

|Configuration|Organization level (Set-CSTenantFederationConfiguration)|User level (Set-CsExternalAccessPolicy)|
|:-------|:--------|:------------------|
|Enable/disable federation with other Teams organizations and Skype for Business|`-AllowFederatedUsers`|`-EnableFederationAccess`|
|Enable federation with specific domains|`-AllowedDomains`|Not available|
|Disable federation with specific domains|`-BlockedDomains`|Not available|
|Enable/disable federation with Teams users that are not managed by an organization|`-AllowTeamsConsumer`|`-EnableTeamsConsumerAccess`|
|Enable/disable Teams users not managed by an organization from initiating conversations|`-AllowTeamsConsumerInbound`|`-EnableTeamsConsumerInbound`|
|Enable/disable federation with Skype|`-AllowPublicUsers`|`-EnablePublicCloudAccess`|

It's important to note that disabling a policy "rolls down" from tenant to users. For example:

```PowerShell
Set-CsTenantFederationConfiguration -AllowFederatedUsers $false
Set-CsExternalAccessPolicy -EnableFederationAccess $true
```

In this example, although the user level policy is enabled, users would not be able to communicate with managed Teams users or Skype for Business users because this type of federation was turned off at the organization level. Therefore, if you want to enable these controls for a subset of users you must turn on the control at an organization level and create two group policies – one that applies to the users that should have the control turned off, and one that applies to the users that should have the control turned on.


### Enable federation between users in your organization and unmanaged Teams users

To enable federation between users in your organization and unmanaged Teams users:

| If your organization is | Enable federation as follows |
|:---------|:-----------------------|
|Online with no Skype for Business on-premises. This includes organizations that have Teams Only users and/or Skype for Business Online users.| If using Teams admin center:<br>-Make sure **People in my organization can communicate with Teams users whose accounts aren't managed by an organization** is enabled in **External Access**.<br>-If you want unmanaged Teams accounts to initiate chats, check the box for **External users with Teams accounts not managed by an organization can contact users in my organization**.<br><br>If using PowerShell:<br>-Ensure the tenant is enabled for federation: `Get-CsTenantFederationConfiguration` must show `AllowTeamsConsumer=true`.<br>-Ensure the user's effective value of `CsExternalAccessPolicy` has `EnableTeamsConsumerAccess=true`.<br>-Ensure the tenant is enabled for unmanaged users to initiate chats: `Get-CsTenantFederationConfiguration` must show `AllowTeamsConsumerInbound=true`.<br>-Ensure the user's effective value of `CsExternalAccessPolicy` has `EnableTeamsConsumerInbound=true`.|
|On-premises only| Chat with unmanaged Teams users is not supported for on-premises only organizations.|
|Hybrid with some users online (in either Skype for Business or Teams) and some users on-premises. | Follow the previously described steps for online organizations. Note that chat with unmanaged Teams users is not supported for on-premises users.|

> [!IMPORTANT]
> You don't have to add any **Teams domains** as allowed domains in order to enable Teams users to communicate with unmanaged Teams users outside your organization. All **unamanged Teams domains** are allowed.

### Enable federation between users in your organization and consumer users of Skype

To enable federation between users in your organization and consumer users of Skype:

| If your organization is | Enable consumer federation as follows |
|:---------|:-----------------------|
|Online only with no Skype for Business on-premises. This includes organizations that have TeamsOnly users and/or Skype for Business Online users. | If using Teams Admin Center: <br>-Make sure **Allow users in my organization to communicate with Skype users** is enabled in External Access.<br><br>If using PowerShell: <br>-Ensure the tenant is enabled for federation: `Get-CsTenantFederationConfiguration` must show `AllowPublicUsers=true`. <br> - Ensure the user's effective value of `CsExternalAccessPolicy` has `EnablePublicCloudAccess=true`. |
|On-premises only| In on-premises tools: <br> - Ensure Skype is enabled as a federated partner. <br> - Ensure `EnablePublicCloudAccess=true` for the user through `ExternalAccessPolicy` (either via global policy, site policy, or user assigned policy).|
| Hybrid with some users online (in either Skype for Business or Teams) and some users on-premises.| Follow above steps for both online and on-premises organizations.

> [!IMPORTANT]
> You don't have to add any **Skype domains** as allowed domains in order to enable Teams or Skype for Business Online users to communicate with Skype users inside or outside your organization. All **Skype domains** are allowed.

## Related topics

