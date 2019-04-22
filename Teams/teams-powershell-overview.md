---
title: Teams PowerShell Overview
ms.reviewer: 
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/06/2018
ms.topic: conceptual
ms.service: msteams
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
description: Learn to use the PowerShell controls for managing Microsoft Teams.
appliesto: 
- Microsoft Teams
---

# Teams PowerShell Overview

Microsoft Teams has a rich set of tools for IT admins to manage the product through the Microsoft Teams admin center, PowerShell controls, and Graph APIs. This guide explains how we structure our PowerShell cmdlets for IT admins to use, and provides pointers to further documentation. Note that different Teams admin roles have access to different cmdlets. For more information, see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md).

## Which modules do you need to use?

The PowerShell controls for managing Teams are in two different PowerShell modules: 
- [Microsoft Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams/) : The Teams PowerShell module contains all the cmdlets you need to create and manage teams.  
- [Skype for Business PowerShell module](https://www.microsoft.com/en-us/download/details.aspx?id=39366): The Skype for Business PowerShell module contains the cmdlets to manage policies, configurations, and other Teams tools. 

The reference documentation for the PowerShell controls will tell you which module contains the cmdlet you're investigating. (Eventually, the two modules will be combined.)

## What can each admin role do?

Read [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md) to understand which PowerShell cmdlets different admin roles will be able to leverage.

## Creating and managing teams via PowerShell

The cmdlets for creating and managing teams are in the [Microsoft Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams/). 

Teams are backed by O365 Groups, so when you create a team, you create a group. There are a set of cmdlets provided for operating on the core team and its settings (``new-team``, ``get-team``,  ``set-team``), managing team users (``add-teamuser``, ``remove-teamuser``), as well as cmdlets for managing the channels of the team (``new-teamchannel``, ``remove-teamchannel``). All of these cmdlets can be run as end users, but they'll work only on the teams that you own or are a member of. If you are a Global Admin or Teams Service Administrator, you'll be able to act on all teams in your organization.

> The **GroupId** used in the Microsoft Teams PowerShell module cmdlets is the same as the **Identity** property returned by ``Get-UnifiedGroup`` in the Exchange PowerShell module.

## Managing policies via PowerShell

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

<!--more info here?-->

## Managing configurations via PowerShell

The cmdlets for managing your configuration are in the [Skype for Business cmdlet module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).

Configurations are buckets of settings maintained in the service that cannot be specified at a user level. Settings always apply across the whole organization. Your global configuration is the only effective configuration in your organization. Each configuration type comes with two primary cmdlets:

- ``Get-Cs<ConfigurationName>`` (for example, ``Get-CsTeamsClientConfiguration``): 

- SET commands (for example, ``Set-CsTeamsClientConfiguration``): set properties in the configuration of that type. Specify the parameters that you want to modify.
   > You can reference the configuration that you’re modifying in one of two ways: by specifying -**Identity Global**, or by running ``Get-Cs<ConfigurationName>`` | ``Set-Cs<ConfigurationName>``.

## Other PowerShell tools

You can find detailed instructions on how to use all PowerShell controls for managing Microsoft Teams and Skype for Business, including detailed descriptions of the settings in each policy, in the [Microsoft Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps) and [Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps).

## Learn more

- [Microsoft Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps)
- [Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps)
- [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md)
