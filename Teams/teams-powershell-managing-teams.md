---
title: Manage Teams with Teams PowerShell
ms.reviewer: 
author: BrandonBernier
ms.author: brandber
manager: kojiko
ms.date: 06/30/2020
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.collection: 
  - M365-collaboration
description: Learn to manage Microsoft Teams using Teams PowerShell.
appliesto: 
  - Microsoft Teams
---

# Manage Teams with Teams PowerShell

Teams PowerShell is a powerful ability. You can find detailed instructions on how to use all PowerShell controls for managing Microsoft Teams and Skype for Business, including detailed descriptions of the settings in each policy, in the [Microsoft Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps) and [Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps).

## Create and manage teams using PowerShell

The cmdlets for creating and managing teams are in the [Microsoft Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams/).

Teams are backed by O365 Groups, so when you create a team, you create a group. There are a set of cmdlets provided for operating on the core team and its settings (``new-team``, ``get-team``,  ``set-team``), managing team users (``add-teamuser``, ``remove-teamuser``), as well as cmdlets for managing the channels of the team (``new-teamchannel``, ``remove-teamchannel``). All of these cmdlets can be run as end users, but they'll work only on the teams that you own or are a member of. If you are a Global Admin or Teams Service Administrator, you'll be able to act on all teams in your organization.

```powershell
New-Team -Name "Contoso Marketing" -Description "Collaboration space for Contoso's Marketing department
```

> The **GroupId** used in the Microsoft Teams PowerShell module cmdlets is the same as the **Identity** property returned by ``Get-UnifiedGroup`` in the Exchange PowerShell module.

# Manage policies via PowerShell

> [!NOTE]
> Skype for Business Online Connector is being consolidated into Teams PowerShell. It is currently available in public preview. In time, Skype for Business Online cmdlets that apply to Teams will be natively available in the Teams PowerShell module. Installation steps are available in the [Install Teams PowerShell](teams-powershell-install.md) article.

> [!NOTE]
> The cmdlets will be available in your PowerShell session once you connect to Skype for Business Online. For more information, please see [Manage Skype for Business Online with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

The cmdlets for managing policies are in the [Skype for Business cmdlet module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).

A policy is a group of settings that can be applied granularly to individual users. Each policy type has its own set of cmdlets for creating, viewing, deleting, and updating the policies themselves, and then assigning those policies to users. The general structure is:

- GET commands (for example, ``Get-CsTeamsMeetingPolicy``):  return the policy documents that are available for you to assign in your organization, both the policies created by Microsoft for you to use and the custom policies you’ve created.
   > If you want to find only the custom policies you’ve created in your organization, you can use ``-Filter "tag:*"``.

- NEW commands (for example, ``New-CsTeamsMeetingPolicy``): let you create new policies for your organization that are then available to be assigned to users in your organization. Not all policies support the creation of custom policies. Often this is to ensure that the policies you use in your organization have a supported combination of settings.

- SET commands (for example, ``Set-CsTeamsMeetingPolicy``): lets you set particular values on a given policy. Some policies do not have set commands available, or contain parameters that cannot be customized in the policy. Each PowerShell description will call out which parameters cannot be customized. 
   > To edit the policy that will by default be assigned to users in your organization who do not have a custom policy assigned, run ``Set-Cs<PolicyName> -Identity Global``.

- REMOVE commands (for example, ``Remove-CsTeamsMeetingPolicy``): you can use this cmdlet to delete a custom policy that has been created in your tenant. If you delete a custom policy that has been assigned to at least one user in your organization, that user will fall back to the global policy.
   > You can’t actually remove the global policy in your organization, but if you want to reset the global policy in your organization to the Microsoft-provided default settings, you can run ``Remove-Cs<PolicyName> -Identity Global``.

- GRANT command (for example, ``Grant-CsTeamsMeetingPolicy``): lets you assign a policy to a particular user.
   > To remove a custom policy assignment and make the user fall back to the default policy in your organization, run ``Grant-Cs<PolicyName> -Identity <User Identity> -PolicyName $null``.

> [!TIP]
> Not all policies allow custom policies to be created, and some policies have settings that you can’t customize (so you can view the setting but can’t set a custom value during ``set-`` and ``new-``). The documentation of the specific cmdlet will call out if parameters are not available for use by customers.

Common parameters:

- **Identity**: For ``Get-``, ``Set-``, ``New-``, and ``Remove-``, the **Identity** parameter will always refer to a specific policy instance. For ``Grant``, the **Identity** parameter refers to a specific user object to whom the policy is being applied.

## Manage configurations via PowerShell

The cmdlets for managing your configuration are in the [Skype for Business cmdlet module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).

Configurations are buckets of settings maintained in the service that cannot be specified at a user level. Settings always apply across the whole organization. Your global configuration is the only effective configuration in your organization. Each configuration type comes with two primary cmdlets:

- ``Get-Cs<ConfigurationName>`` (for example, ``Get-CsTeamsClientConfiguration``):

- SET commands (for example, ``Set-CsTeamsClientConfiguration``): set properties in the configuration of that type. Specify the parameters that you want to modify.
   > You can reference the configuration that you’re modifying in one of two ways: by specifying -**Identity Global**, or by running ``Get-Cs<ConfigurationName>`` | ``Set-Cs<ConfigurationName>``.

## What can each admin role do?

Read [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md) to understand which PowerShell cmdlets different admin roles will be able to leverage.

## Related topics

[Installing Teams PowerShell](teams-powershell-install.md)

[Teams PowerShell Release Notes](teams-powershell-release-notes.md)

[Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps)

[Use Teams admin roles to manage Teams](using-admin-roles.md)