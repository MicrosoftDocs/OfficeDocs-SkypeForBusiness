---
title: Manage Teams with Microsoft Teams PowerShell
ms.reviewer: brandber
author: brandber
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

# Manage Teams with Microsoft Teams PowerShell

This article shows you how to use Microsoft Teams PowerShell to manage Teams.

Use this guidance in conjunction with the [Microsoft Teams cmdlet reference](/powershell/teams/).

To manage Teams in the Teams admin center, see [Manage Teams with Azure Cloud Shell](#manage-teams-with-azure-cloud-shell).

## Create and manage teams using PowerShell

The cmdlets for creating and managing teams are in the [Microsoft Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams/).

Teams are backed by Office 365 Groups, so when you create a team, you create a group. There are a set of cmdlets provided for operating on the core team and its settings (``new-team``, ``get-team``,  ``set-team``), managing team users (``add-teamuser``, ``remove-teamuser``), and cmdlets for managing the channels of the team (``new-teamchannel``, ``remove-teamchannel``). All of these cmdlets can be run as end users, but they work only on the teams that you own or are a member of. If you're a Global Administrator or Teams Administrator, you can act on all teams in your organization.

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

```powershell
New-Team -DisplayName "Contoso Marketing" -Description "Collaboration space for Contoso's Marketing department"
```

> [!NOTE]
> The **GroupId** used in the Microsoft Teams PowerShell module cmdlets is the same as the **Identity** property returned by ``Get-UnifiedGroup`` in the Exchange PowerShell module.

## Manage Teams with Azure Cloud Shell

Cloud Shell is an interactive, authenticated, browser-accessible shell that lets you manage your resources. For more information on Cloud Shell, see [Azure Cloud Shell](/azure/cloud-shell/overview).

To access the Azure Cloud Shell and use PowerShell to manage Teams, sign in to the Teams admin center.

1. Select the Cloud Shell icon in the top right corner.

    ![Screenshot of Teams admin center header with Cloud Shell icon.](media/cloud-shell-icon-select.png)

1. When prompted, choose **PowerShell**.

    ![Screenshot of Azure Cloud Shell prompt.](media/cloud-shell.png)

1. Run the following command to start a Teams PowerShell session:

    ```powershell
    Connect-MicrosoftTeams
    ```

After you complete these steps, you're ready to run Teams PowerShell commands.


## Manage policies via PowerShell

Find the cmdlets for managing policies in the [Microsoft Teams cmdlet module](/powershell/module/teams).

A policy is a group of settings that can be applied granularly to individual users. Each policy type has its own set of cmdlets for creating, viewing, deleting, and updating the policies themselves, and then assigning those policies to users. The general structure is:

- **GET** commands (for example, ``Get-CsTeamsMeetingPolicy``): Returns the policy documents that are available for you to assign in your organization, including the policies created by Microsoft for you to use and the custom policies you’ve created.
  - To find only the custom policies you’ve created in your organization, use ``-Filter "tag:*"``.

- **NEW** commands (for example, ``New-CsTeamsMeetingPolicy``): Creates new policies for your organization to assign to users in your organization. Not all policies support the creation of custom policies. Often this is to ensure that the policies you use in your organization have a supported combination of settings.

- **SET** commands (for example, ``Set-CsTeamsMeetingPolicy``): Sets particular values on a given policy. Some policies don't have SET commands available, or they contain parameters that can't be customized in the policy. The PowerShell descriptions tell you which parameters can't be customized.
  - To edit the policy that will by default be assigned to users in your organization who don't have a custom policy assigned, run ``Set-Cs<PolicyName> -Identity Global``.

- **REMOVE** commands (for example, ``Remove-CsTeamsMeetingPolicy``): Deletes a custom policy that has been created in your tenant. If you delete a custom policy that has been assigned to at least one user in your organization, that user falls back to the global policy.
  - You can’t actually remove the global policy in your organization, but if you want to reset the global policy in your organization to the Microsoft-provided default settings, run ``Remove-Cs<PolicyName> -Identity Global``.

- **GRANT** command (for example, ``Grant-CsTeamsMeetingPolicy``): Assigns a policy to a particular user.
  - To remove a custom policy assignment and make the user fall back to the default policy in your organization, run ``Grant-Cs<PolicyName> -Identity <User Identity> -PolicyName $null``.

> [!TIP]
> Not all policies allow custom policies to be created, and some policies have settings that you can’t customize (so you can view the setting but can’t set a custom value during ``set-`` and ``new-``). The documentation for each cmdlet calls out whether parameters are available for use by customers.

Common parameters:

- **Identity**: For ``Get-``, ``Set-``, ``New-``, and ``Remove-``, the **Identity** parameter refers to a specific policy instance. For ``Grant``, the **Identity** parameter refers to a specific user object to whom the policy is being applied.

## Manage configurations via PowerShell

Find the cmdlets for managing your configuration in the [Microsoft Teams cmdlet module](/powershell/module/teams).

Configurations are buckets of settings maintained in the service that can't be specified at a user level. Settings always apply across the whole organization. Your global configuration is the only effective configuration in your organization. Each configuration type comes with two primary cmdlets:

- ``Get-Cs<ConfigurationName>`` (for example, ``Get-CsTeamsClientConfiguration``):

- SET commands (for example, ``Set-CsTeamsClientConfiguration``): set properties in the configuration of that type. Specify the parameters that you want to modify.
    > [!NOTE]
    > You can reference the configuration that you’re modifying in one of two ways: by specifying -**Identity Global**, or by running ``Get-Cs<ConfigurationName>`` | ``Set-Cs<ConfigurationName>``.

## What can each admin role do?

Read [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md) to understand which admin roles can run each PowerShell cmdlet.

## Related topics

[Installing Teams PowerShell](teams-powershell-install.md)

[Teams PowerShell Release Notes](teams-powershell-release-notes.md)

[Teams cmdlet reference](/powershell/teams/)

[Use Teams admin roles to manage Teams](using-admin-roles.md)
