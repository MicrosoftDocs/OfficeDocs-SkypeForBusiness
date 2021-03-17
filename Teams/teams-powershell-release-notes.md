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
| March  2021 | [2.0](https://www.powershellgallery.com/packages/MicrosoftTeams/) | <li>Connect-MicrosoftTeams is the entry point for all cmdlets.</li><li>New-csOnlineSession is no longer avaiable. It has been replaced with Connect-MicrosoftTeams.</li><li>Enable-csonlinesessionforreconnection is no longer required. The feature has beenn natively implemented in Teams PowerShell Module.</li>|
| November 2020 | [1.1.9-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.9-preview) | <li>Bug fixes and improvements</li>|
| November 2020 | [1.1.8-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.8-preview) | <li>Bug fixes and improvements</li>|
| March 2021 | [2.0.0](https://www.powershellgallery.com/packages/MicrosoftTeams/2.0.0) | <li>Uses MSAL for authentication & authorization</li><li>Refactored Policy Package cmdlets and adds group package assignment</li><li>Significant performance enhancements for Get-Team cmdlet</li> <li>Improved logging and debugging option for existing cmdlets </li> <li>Added template management cmdlets</li> <li>Deprecation of New-CsOnlineSession</li>|
| February 2021 | [1.1.11-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.11-preview) | <li>Added template management cmdlets</li><li>Mezzo and batching enhancements for Get-Team cmdlet</li> <li>Improved logging and debugging option for existing cmdlets </li> <li>Refactored Policy Package cmdlets</li>|
| December 2020 | [1.1.10-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.10-preview) | <li>Updates to New-team cmdlet with increased retries and sleep duration</li>|
| December 2020 | [1.1.9-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.9-preview) | <li>Updates for Skype for Business Online Integration</li><li>Fix for the duplicate prompt with Connect-Microsoft Teams</li>|
| November 2020 | [1.1.8-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.8-preview) | <li>Adds custom policy package cmdlets</li><li>Fixes for the targeting hierarchy upload commands</li>|
| November 2020 | [1.1.7-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.7-preview) | <li>Uses MSAL for authentication & authorization</li><li>Refactored Policy Package cmdlets and adds group package assignment</li><li>Refactored targeting hierarchy upload commands to use an asynchronous model</li> <li>User will be prompted twice during initial authentication when they do not use the -credential parameter. Users can pass credentials using the -credential parameter to avoid a duplicate prompt. This behavior will be fixed in the next release.</li> |
| September 2020 | [1.1.6](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.6) | <li>Skype for Business Online Connector integration</li> |
| September 2020 | [1.1.5-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.5-preview) | <li>Skype for Business Online Connector integration</li> |
| July 2020 | [1.1.4](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.4) | <li>Added [group policy assignment cmdlets](https://docs.microsoft.com/microsoftteams/assign-policies#assign-a-policy-to-a-group)</li> |
| June 2020 | [1.1.3-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.3-preview) | <li>Skype for Business Online Connector integration<li>Get-Team optimizations<li>Enhanced reliability</li> |
| June 2020 | [1.0.7](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.7) | <li>Added Cmdlet preloading<li>.Net Framework optimizations</li>   |
| April 2020 | [1.0.6](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.6) | <li>Authenticode and assembly signing<li>Added Get-CsPolicyPackage<li>Added Get-CsUserPolicyPackage<li>Added Get-CsUserPolicyPackageRecommendation<li>Added Grant-CsUserPolicyPackage<li>Added New-CsBatchPolicyPackageAssignmentOperation<li>Added Set-TeamArchivedState<li>Added Set-TeamPicture<li>Removed Get-TeamHelp</li>  |
| March 2020 | [1.0.5](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.5) |<li>Added New-CsBatchPolicyAssignmentOperation</li> |
| Feb 2020 | [1.0.4](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.4) | <li>Get-Team optimizations</li>  |

### Cmdlet availability

> [!NOTE]
> The list in the table below only includes cmdlets that are natively part of the Teams PowerShell module. The Teams cmdlets in the S[kype for Business Online Connector module](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps) are not displayed. However, as those cmdlets are migrated natively into Teams PowerShell, we'll add them to this table.

| Cmdlet | Available in Public Preview | Available in GA |
| -| -- | --|
| [Add-TeamChannelUser](https://docs.microsoft.com/powershell/module/teams/add-teamchanneluser?view=teams-ps) | Yes | **No** |
| [Add-TeamUser](https://docs.microsoft.com/powershell/module/teams/add-teamuser?view=teams-ps) | Yes | Yes |
| [Add-TeamsAppInstallation](https://docs.microsoft.com/powershell/module/teams/add-teamsappinstallation?view=teams-ps) | Yes | **No**|
| [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps) | Yes | Yes |
| [Disconnect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/disconnect-microsoftteams?view=teams-ps) | Yes | Yes |
| [Get-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/get-csbatchpolicyassignmentoperation?view=teams-ps) | Yes | Yes |
| [Get-CsGroupPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/get-csgrouppolicyassignment?view=teams-ps) | Yes | **No** |
| [Get-CsOnlinePowerShellEndpoint](https://docs.microsoft.com/powershell/module/skype/get-csonlineapplicationendpoint?view=skype-ps) | Yes | Yes |
| [Get-CsPolicyPackage](https://docs.microsoft.com/powershell/module/teams/get-cspolicypackage?view=teams-ps) | Yes | Yes |
| [Get-CsUserPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/get-csuserpolicyassignment?view=teams-ps) | Yes | Yes |
| [Get-CsUserPolicyPackage](https://docs.microsoft.com/powershell/module/teams/get-csuserpolicypackage?view=teams-ps) | Yes | Yes |
| [Get-CsUserPolicyPackageRecommendation](https://docs.microsoft.com/powershell/module/teams/get-csuserpolicypackagerecommendation?view=teams-ps) | Yes | Yes |
| [Get-Team](https://docs.microsoft.com/powershell/module/teams/get-team?view=teams-ps) | Yes | Yes |
| [Get-TeamChannel](https://docs.microsoft.com/powershell/module/teams/get-teamchannel?view=teams-ps) | Yes | Yes|
| [Get-TeamChannelUser](https://docs.microsoft.com/powershell/module/teams/get-teamchanneluser?view=teams-ps) | Yes | **No** |
| [Get-TeamUser](https://docs.microsoft.com/powershell/module/teams/get-teamuser?view=teams-ps) | Yes | Yes |
| [Get-TeamsApp](https://docs.microsoft.com/powershell/module/teams/get-teamsapp?view=teams-ps) | Yes | Yes |
| [Get-TeamsAppInstallation](https://docs.microsoft.com/powershell/module/teams/get-teamsappinstallation?view=teams-ps) | Yes | **No** |
| [Grant-CsUserPolicyPackage](https://docs.microsoft.com/powershell/module/teams/grant-csuserpolicypackage?view=teams-ps) | Yes | Yes |
| [New-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicyassignmentoperation?view=teams-ps) | Yes | Yes |
| [New-CsGroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/new-csgrouppolicyassignment?view=teams-ps) | Yes | Yes |
| [New-CsBatchPolicyPackageAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicypackageassignmentoperation?view=teams-ps) | Yes | Yes |
| [New-CsOnlineSession](https://docs.microsoft.com/powershell/module/skype/new-csonlinesession?view=skype-ps) | Yes | Yes |
| [New-Team](https://docs.microsoft.com/powershell/module/teams/new-team?view=teams-ps) | Yes | Yes |
| [New-TeamChannel](https://docs.microsoft.com/powershell/module/teams/new-teamchannel?view=teams-ps) | Yes | Yes |
| [New-TeamsApp](https://docs.microsoft.com/powershell/module/teams/new-teamsapp?view=teams-ps) | Yes | Yes |
| [Remove-CsGroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/remove-csgrouppolicyassignment?view=teams-ps) | Yes | Yes |
| [Remove-Team](https://docs.microsoft.com/powershell/module/teams/remove-team?view=teams-ps) | Yes | Yes |
| [Remove-TeamChannel](https://docs.microsoft.com/powershell/module/teams/remove-teamchannel?view=teams-ps) | Yes | Yes |
| [Remove-TeamChannelUser](https://docs.microsoft.com/powershell/module/teams/remove-teamchanneluser?view=teams-ps) | Yes | **No** |
| [Remove-TeamsApp](https://docs.microsoft.com/powershell/module/teams/remove-teamsapp?view=teams-ps) | Yes | Yes |
| [Remove-TeamsAppInstallation](https://docs.microsoft.com/powershell/module/teams/remove-teamsappinstallation?view=teams-ps) | Yes | **No** |
| [Remove-TeamTargetingHierarchy](https://docs.microsoft.com/microsoftteams/set-up-your-team-hierarchy#remove-your-hierarchy) | Yes | **No**|
| [Remove-TeamUser](https://docs.microsoft.com/powershell/module/teams/remove-teamuser?view=teams-ps) | Yes | Yes |
| [Set-CsGroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/set-csgrouppolicyassignment?view=teams-ps) | Yes | **No** |
| [Set-Team](https://docs.microsoft.com/powershell/module/teams/set-team?view=teams-ps) | Yes | Yes |
| [Set-TeamArchivedState](https://docs.microsoft.com/powershell/module/teams/set-teamarchivedstate?view=teams-ps) | Yes | Yes |
| [Set-TeamChannel](https://docs.microsoft.com/powershell/module/teams/set-teamchannel?view=teams-ps) | Yes | Yes |
| [Set-TeamPicture](https://docs.microsoft.com/powershell/module/teams/set-teampicture?view=teams-ps) | Yes | Yes |
| [Set-TeamsApp](https://docs.microsoft.com/powershell/module/teams/set-teamsapp?view=teams-ps) | Yes | Yes |
| [Set-TeamTargetingHierarchy](https://docs.microsoft.com/microsoftteams/set-up-your-team-hierarchy#apply-your-hierarchy) | Yes | **No** |
| [Update-TeamsAppInstallation](https://docs.microsoft.com/powershell/module/teams/update-teamsappinstallation?view=teams-ps) | Yes | **No** |

## Related topics

[Teams PowerShell Overview](teams-powershell-overview.md)

[Installing Teams PowerShell](teams-powershell-install.md)

[Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Microsoft Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps)
