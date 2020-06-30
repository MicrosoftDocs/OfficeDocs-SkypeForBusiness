---
title: Teams PowerShell Release Notes
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
description: Learn about the latest changes in Teams PowerShell.
appliesto: 
  - Microsoft Teams
---

# Teams PowerShell Release Notes

This page provides the latest Teams PowerShell change log for both General Availability and Public Preview releases.

## Release Notes

> [!NOTE]
> **-preview** in the version column below represents updates to Teams PowerShell public preview.

| Date | Version | Updates |
|------- | -------------------- | ------------------------------ |
| June 2020 | [1.1.0-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/1.1.0-preview) | <li>Skype for Business Online Connector integration<li>Get-Team optimizations<li>Enhanced reliability</li> |
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
| [Get-CsGroupPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/get-csgrouppolicyassignmentoperation?view=teams-ps) | Yes | **No** |
| [Get-CsOnlinePowerShellEndpoint](https://docs.microsoft.com/powershell/module/teams/get-csonlinepowershellendpoint?view=teams-ps) | Yes | **No** |
| [Get-CsPolicyPackage](https://docs.microsoft.com/powershell/module/teams/get-cspolicypackage?view=teams-ps) | Yes | Yes |
| [Get-CsUserPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/get-csuserpolicyassignment?view=teams-ps) | Yes | Yes |
| [Get-CsUserPolicyPackage](https://docs.microsoft.com/powershell/module/teams/get-csuserpolicypackage?view=teams-ps) | Yes | Yes |
| [Get-CsUserPolicyPackageRecommendation](https://docs.microsoft.com/powershell/module/teams/get-csuserpolicypackagerecommendation?view=teams-ps) | Yes | Yes |
| [Get-Team](https://docs.microsoft.com/powershell/module/teams/get-team?view=teams-ps) | Yes | Yes |
| [Get-TeamChannel](https://docs.microsoft.com/powershell/module/teams/get-teamchannel?view=teams-ps) | Yes | Yes|
| [Get-TeamChannelUser](https://docs.microsoft.com/powershell/module/teams/get-teamchanneluser?view=teams-ps) | Yes | Yes|
| [Get-TeamUser](https://docs.microsoft.com/powershell/module/teams/get-teamuser?view=teams-ps) | Yes | Yes |
| [Get-TeamsApp](https://docs.microsoft.com/powershell/module/teams/get-teamsapp?view=teams-ps) | Yes | Yes |
| [Get-TeamsAppInstallation](https://docs.microsoft.com/powershell/module/teams/get-teamsappinstallation?view=teams-ps) | Yes | Yes |
| [Grant-CsUserPolicyPackage](https://docs.microsoft.com/powershell/module/teams/grant-csuserpolicypackage?view=teams-ps) | Yes | Yes |
| [New-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicyassignmentoperation?view=teams-ps) | Yes | Yes |
| [New-CsGroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/new-csgrouppolicyassignment?view=teams-ps) | Yes | **No** |
| [New-CsBatchPolicyPackageAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicypackageassignmentoperation?view=teams-ps) | Yes | Yes |
| [New-CsOnlineSession](https://docs.microsoft.com/powershell/module/teams/new-csonlinesession?view=teams-ps) | Yes | **No** |
| [New-Team](https://docs.microsoft.com/powershell/module/teams/new-team?view=teams-ps) | Yes | Yes |
| [New-TeamChannel](https://docs.microsoft.com/powershell/module/teams/new-channel?view=teams-ps) | Yes | Yes |
| [New-TeamsApp](https://docs.microsoft.com/powershell/module/teams/new-teamsapp?view=teams-ps) | Yes | Yes |
| [Remove-CsGroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/remove-csgrouppolicyassignment?view=teams-ps) | Yes | **No** |
| [Remove-Team](https://docs.microsoft.com/powershell/module/teams/remove-team?view=teams-ps) | Yes | Yes |
| [Remove-TeamChannel](https://docs.microsoft.com/powershell/module/teams/remove-teamchannel?view=teams-ps) | Yes | Yes |
| [Remove-TeamChannelUser](https://docs.microsoft.com/powershell/module/teams/remove-teamchanneluser?view=teams-ps) | Yes | Yes |
| [Remove-TeamsApp](https://docs.microsoft.com/powershell/module/teams/remove-teamsapp?view=teams-ps) | Yes | Yes |
| [Remove-TeamsAppInstallation](https://docs.microsoft.com/powershell/module/teams/remove-teamsappinstallation?view=teams-ps) | Yes | **No** |
| [Remove-TeamTargetingHierarchy](https://docs.microsoft.com/powershell/module/teams/remove-teamtargetinghierarchy?view=teams-ps) | Yes | **No**|
| [Remove-TeamUser](https://docs.microsoft.com/powershell/module/teams/remove-teamuser?view=teams-ps) | Yes | Yes |
| [Set-CsGroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/set-csgrouppolicyassignment?view=teams-ps) | Yes | **No** |
| [Set-Team](https://docs.microsoft.com/powershell/module/teams/set-team?view=teams-ps) | Yes | Yes |
| [Set-TeamArchivedState](https://docs.microsoft.com/powershell/module/teams/set-teamarchivedstate?view=teams-ps) | Yes | Yes |
| [Set-TeamChannel](https://docs.microsoft.com/powershell/module/teams/set-teamchannel?view=teams-ps) | Yes | Yes |
| [Set-TeamPicture](https://docs.microsoft.com/powershell/module/teams/set-teampicture?view=teams-ps) | Yes | Yes |
| [Set-TeamsApp](https://docs.microsoft.com/powershell/module/teams/set-teamapp?view=teams-ps) | Yes | Yes |
| [Set-TeamTargetingHierarchy](https://docs.microsoft.com/powershell/module/teams/set-teamtargetinghierarchy?view=teams-ps) | Yes | **No** |
| [Update-TeamsAppInstallation](https://docs.microsoft.com/powershell/module/teams/update-teamappinstallation?view=teams-ps) | Yes | **No** |

## Related topics

[Teams PowerShell Overview](teams-powershell-overview.md)

[Installing Teams PowerShell](teams-powershell-install.md)

[Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Microsoft Teams cmdlet reference](https://docs.microsoft.com/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps)
