---
title: Microsoft Teams PowerShell Release Notes
ms.reviewer: brandber
author: BrandBer
ms.author: brandber
manager: kojiko
ms.date: 06/30/2020
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.collection: 
  - M365-collaboration
description: Learn about the latest changes in Teams PowerShell.
appliesto: 
  - Microsoft Teams
---

# Microsoft Teams PowerShell Release Notes

This page provides the latest Teams PowerShell change log for both General Availability and Public Preview releases.

## Release Notes

> [!NOTE]
> **-preview** in the version column below represents updates to Teams PowerShell public preview.

| Date | Version | Updates |
|------- | -------------------- | ------------------------------ |
| April 2021 | [2.2.0-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/2.2.0-preview) | <li>Fixes for integrated Windows authentication to use -AccountId with Connect-MicrosoftTeams.</li><li>Added cmdlet to get details of total change notification events that can be sent to users.</li><li>Added cmdlet to get multi-geo region for users and groups.</li><li>Handling of values passed to TeamsEnvironment name was case sensitive. This has been fixed.</li><li>Major refactor of remote session management within the module to facilitate unit tests. There should be no functional change for tenant admins.</li>|
| April 2021 | [2.1.0-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/2.1.0-preview) | <li>Fixed formatting of existing cmdlets (for example, Get-CsTeamsNetworkRoamingPolicy, Get-CsTeamsMeetingPolicy, Get-CsTeamsMessagingPolicy, and more).</li><li>Updated parameter list of policy management cmdlets.</li>|
| March 2021 | [2.0.0](https://www.powershellgallery.com/packages/MicrosoftTeams/2.0.0) | <li>Uses MSAL for authentication & authorization</li> <li>Connect-MicrosoftTeams is the entry point for all cmdlets.</li><li>New-csOnlineSession is no longer available. It has been replaced with Connect-MicrosoftTeams.</li><li>Enable-csonlinesessionforreconnection is no longer required. The feature has been natively implemented in Teams PowerShell Module.</li> <li>Refactored Policy Package cmdlets and adds group package assignment</li><li>Significant performance enhancements for Get-Team cmdlet</li> <li>Improved logging and debugging option for existing cmdlets </li> <li>Added template management cmdlets</li> <li>Deprecation of New-CsOnlineSession</li>|
| February 2021 | [1.1.11-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.11-preview) | <li>Added template management cmdlets</li><li>Mezzo and batching enhancements for Get-Team cmdlet</li> <li>Improved logging and debugging option for existing cmdlets </li> <li>Refactored Policy Package cmdlets</li>|
| December 2020 | [1.1.10-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.10-preview) | <li>Updates to New-team cmdlet with increased retries and sleep duration</li>|
| December 2020 | [1.1.9-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.9-preview) | <li>Updates for Skype for Business Online Integration</li><li>Fix for the duplicate prompt with Connect-Microsoft Teams</li>|
| November 2020 | [1.1.8-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.8-preview) | <li>Adds custom policy package cmdlets</li><li>Fixes for the targeting hierarchy upload commands</li>|
| November 2020 | [1.1.7-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.7-preview) | <li>Uses MSAL for authentication & authorization</li><li>Refactored Policy Package cmdlets and adds group package assignment</li><li>Refactored targeting hierarchy upload commands to use an asynchronous model</li> <li>User will be prompted twice during initial authentication when they do not use the -credential parameter. Users can pass credentials using the -credential parameter to avoid a duplicate prompt. This behavior will be fixed in the next release.</li> |
| September 2020 | [1.1.6](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.6) | <li>Skype for Business Online Connector integration</li> |
| September 2020 | [1.1.5-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.5-preview) | <li>Skype for Business Online Connector integration</li> |
| July 2020 | [1.1.4](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.4) | <li>Added [group policy assignment cmdlets](./assign-policies.md#assign-a-policy-to-a-group)</li> |
| June 2020 | [1.1.3-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.3-preview) | <li>Skype for Business Online Connector integration<li>Get-Team optimizations<li>Enhanced reliability</li> |
| June 2020 | [1.0.7](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.7) | <li>Added Cmdlet preloading<li>.Net Framework optimizations</li>   |
| April 2020 | [1.0.6](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.6) | <li>Authenticode and assembly signing<li>Added Get-CsPolicyPackage<li>Added Get-CsUserPolicyPackage<li>Added Get-CsUserPolicyPackageRecommendation<li>Added Grant-CsUserPolicyPackage<li>Added New-CsBatchPolicyPackageAssignmentOperation<li>Added Set-TeamArchivedState<li>Added Set-TeamPicture<li>Removed Get-TeamHelp</li>  |
| March 2020 | [1.0.5](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.5) |<li>Added New-CsBatchPolicyAssignmentOperation</li> |
| Feb 2020 | [1.0.4](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.4) | <li>Get-Team optimizations</li>  |

### Cmdlet availability

> [!NOTE]
> The list in the following table only includes cmdlets that are natively part of the Teams PowerShell module. The Teams cmdlets in the [Skype for Business Online Connector module](/powershell/skype/intro?view=skype-ps) are not displayed. However, as those cmdlets are migrated natively into Teams PowerShell, we'll add them to this table.

| Cmdlet | Available in Public Preview | Available in GA |
| -| -- | --|
| [Add-TeamChannelUser](/powershell/module/teams/add-teamchanneluser?view=teams-ps) | Yes | **No** |
| [Add-TeamUser](/powershell/module/teams/add-teamuser?view=teams-ps) | Yes | Yes |
| [Add-TeamsAppInstallation](/powershell/module/teams/add-teamsappinstallation?view=teams-ps) | Yes | **No**|
| [Connect-MicrosoftTeams](/powershell/module/teams/connect-microsoftteams?view=teams-ps) | Yes | Yes |
| [Disconnect-MicrosoftTeams](/powershell/module/teams/disconnect-microsoftteams?view=teams-ps) | Yes | Yes |
| [Get-CsBatchPolicyAssignmentOperation](/powershell/module/teams/get-csbatchpolicyassignmentoperation?view=teams-ps) | Yes | Yes |
| [Get-CsGroupPolicyAssignmentOperation](/powershell/module/teams/get-csgrouppolicyassignment?view=teams-ps) | Yes | **No** |
| [Get-CsOnlinePowerShellEndpoint](/powershell/module/skype/get-csonlineapplicationendpoint?view=skype-ps) | Yes | Yes |
| [Get-CsPolicyPackage](/powershell/module/teams/get-cspolicypackage?view=teams-ps) | Yes | Yes |
| [Get-CsTeamTemplate](/powershell/module/teams/get-csteamtemplate?view=teams-ps) | Yes | Yes |
| [Get-CsTeamTemplateList](/powershell/module/teams/get-csteamtemplatelist?view=teams-ps) | Yes | Yes |
| [Get-CsUserPolicyAssignment](/powershell/module/teams/get-csuserpolicyassignment?view=teams-ps) | Yes | Yes |
| [Get-CsUserPolicyPackage](/powershell/module/teams/get-csuserpolicypackage?view=teams-ps) | Yes | Yes |
| [Get-CsUserPolicyPackageRecommendation](/powershell/module/teams/get-csuserpolicypackagerecommendation?view=teams-ps) | Yes | Yes |
| [Get-Team](/powershell/module/teams/get-team?view=teams-ps) | Yes | Yes |
| [Get-TeamChannel](/powershell/module/teams/get-teamchannel?view=teams-ps) | Yes | Yes|
| [Get-TeamChannelUser](/powershell/module/teams/get-teamchanneluser?view=teams-ps) | Yes | **No** |
| [Get-TeamUser](/powershell/module/teams/get-teamuser?view=teams-ps) | Yes | Yes |
| [Get-TeamsApp](/powershell/module/teams/get-teamsapp?view=teams-ps) | Yes | Yes |
| [Get-TeamsAppInstallation](/powershell/module/teams/get-teamsappinstallation?view=teams-ps) | Yes | **No** |
| [Grant-CsUserPolicyPackage](/powershell/module/teams/grant-csuserpolicypackage?view=teams-ps) | Yes | Yes |
| [New-CsBatchPolicyAssignmentOperation](/powershell/module/teams/new-csbatchpolicyassignmentoperation?view=teams-ps) | Yes | Yes |
| [New-CsGroupPolicyAssignment](/powershell/module/teams/new-csgrouppolicyassignment?view=teams-ps) | Yes | Yes |
| [New-CsBatchPolicyPackageAssignmentOperation](/powershell/module/teams/new-csbatchpolicypackageassignmentoperation?view=teams-ps) | Yes | Yes |
| [New-CsOnlineSession](/powershell/module/skype/new-csonlinesession?view=skype-ps) | Yes | Yes |
| [New-CsTeamTemplate](/powershell/module/teams/new-csteamtemplate?view=teams-ps) | Yes | Yes |
| [New-Team](/powershell/module/teams/new-team?view=teams-ps) | Yes | Yes |
| [New-TeamChannel](/powershell/module/teams/new-teamchannel?view=teams-ps) | Yes | Yes |
| [New-TeamsApp](/powershell/module/teams/new-teamsapp?view=teams-ps) | Yes | Yes |
| [Remove-CsGroupPolicyAssignment](/powershell/module/teams/remove-csgrouppolicyassignment?view=teams-ps) | Yes | Yes |
| [Remove-CsTeamTemplate](/powershell/module/teams/remove-csteamtemplate?view=teams-ps) | Yes | Yes |
| [Remove-Team](/powershell/module/teams/remove-team?view=teams-ps) | Yes | Yes |
| [Remove-TeamChannel](/powershell/module/teams/remove-teamchannel?view=teams-ps) | Yes | Yes |
| [Remove-TeamChannelUser](/powershell/module/teams/remove-teamchanneluser?view=teams-ps) | Yes | **No** |
| [Remove-TeamsApp](/powershell/module/teams/remove-teamsapp?view=teams-ps) | Yes | Yes |
| [Remove-TeamsAppInstallation](/powershell/module/teams/remove-teamsappinstallation?view=teams-ps) | Yes | **No** |
| [Remove-TeamTargetingHierarchy](./set-up-your-team-hierarchy.md#remove-your-hierarchy) | Yes | **No**|
| [Remove-TeamUser](/powershell/module/teams/remove-teamuser?view=teams-ps) | Yes | Yes |
| [Set-CsGroupPolicyAssignment](/powershell/module/teams/set-csgrouppolicyassignment?view=teams-ps) | Yes | **No** |
| [Set-Team](/powershell/module/teams/set-team?view=teams-ps) | Yes | Yes |
| [Set-TeamArchivedState](/powershell/module/teams/set-teamarchivedstate?view=teams-ps) | Yes | Yes |
| [Set-TeamChannel](/powershell/module/teams/set-teamchannel?view=teams-ps) | Yes | Yes |
| [Set-TeamPicture](/powershell/module/teams/set-teampicture?view=teams-ps) | Yes | Yes |
| [Set-TeamsApp](/powershell/module/teams/set-teamapp?view=teams-ps) | Yes | Yes |
| [Set-TeamTargetingHierarchy](/powershell/module/teams/set-teamtargetinghierarchy?view=teams-ps) | Yes | **No** |
| [Update-CsTeamTemplate](/powershell/module/teams/update-csteamtemplate?view=teams-ps) | Yes | Yes |
| [Update-TeamsAppInstallation](/powershell/module/teams/update-teamappinstallation?view=teams-ps) | Yes | **No** |
| [Enable-CsOnlineSessionForReconnection](/skypeforbusiness/set-up-your-computer-for-windows-powershell/diagnose-problems-with-the-skype-for-business-online-connector) | **No** | **No** |

## Related topics

[Teams PowerShell Overview](teams-powershell-overview.md)

[Installing Teams PowerShell](teams-powershell-install.md)

[Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Microsoft Teams cmdlet reference](/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](/powershell/skype/intro?view=skype-ps)
