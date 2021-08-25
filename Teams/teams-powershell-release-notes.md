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
| August 2021 | [2.5.0](https://www.powershellgallery.com/packages/MicrosoftTeams/2.5.0) |<li>Updates for AccessToken login with Connect-MicrosoftTeams.</li><li>Fixes for Interactive login of Connect-MicrosoftTeams in Cloudshell.</li><li>Improvements to New-Team cmdlet for team creation scenarios.</li><li>TeamsUnassignedNumberTreatment cmdlets are now available.</li><li>Get-CsCsOnlineDialInConferencingBridge and Set-CsOnlineDialInConferencingBridge.</li><li>Releases modernized versions of Get-CsTenant, Get-CsOnlineUser (with -identity parameter only).</li><li>The return type for `New-Team` has changed. See example 4 at: [`New-Team`](https://docs.microsoft.com/en-us/powershell/module/teams/new-team?view=teams-ps).</li>|
| July 2021 | [2.4.1-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/2.4.1-preview) |<li>Grant cmdlets changes now available.</li><li>New Voice related cmdlets are released.</li><li>Removal of certificate thumbprint authentication for -Cs* cmdlets.</li><li>Logging fix for logging files of all cmdlets.</li><li>Fixes issues with *TeamChannelUser cmdlets.</li>|
| June 2021 | [2.4.0-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/2.4.0-preview) |<li>Preview only release of modernized versions of Get-CsTenant, Get-CsOnlineUser (with -identity parameter only), Get-CsOnlineDialInConferencingLanguagesSupported, and Import-CsOnlineAudioFile.</li><li>Modernized versions of Get-CsOnlineDialInConferencingLanguagesSupported and Import-CsOnlineAudioFile are expected to work similar/same to their remoting counterparts.</li><li>Modernized versions of Get-CsTenant and Get-CsOnlineUser (when run with -identity parameter) don't emit deprecated properties.</li><li>Modernized versions of Get-CsTenant and Get-CsOnlineUser (when run with -identity parameter) have some formatting changes when compared to their remoting counter parts.</li><li>Releases [Get\|Set\|Grant\|New\|Remove]-CsTeamsAudioConferencingPolicy cmdlets.</li><li>Releases Get-CsOnlineAudioFile and Remove-CsOnlineAudioFile cmdlets.</li><li>Set-TeamTargetingHierarchy, Remove-TeamTargetingHierarchy, Get-TeamTargetingHierarchyStatus are now available for GCC customers.</li><li>Fixes the endpoint called by the Get-TeamTargetingHierarchyStatus command.</li>|
| May 2021 | [2.3.2-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/2.3.2-preview) |<li>Support for AccessToken login with Connect-MicrosoftTeams. Added -AccessTokens parameter that accepts the array of token. MSGraph and Teams resource token are required  when using the AccessTokens parameter.</li><li>Removed AadAccessToken and MsAccessToken parameters.</li>|
| May 2021 | [2.3.1](https://www.powershellgallery.com/packages/MicrosoftTeams/2.3.1) |<li>Update from .NETCore 2.1 to 3.1</li><li>Added cmdlet to get multi-geo region for users and groups</li><li>Fixes for integrated windows authentication to use -AccountId with Connect-MicrosoftTeams</li><li>TeamsCallHoldPolicy cmdlets are now available</li><li>Updates to input parameters and output formats of many commands</li><li>Fixes large latency issue while remoting commands</li><li>GA custom package features</li>|
| April 2021 | [2.2.0-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/2.2.0-preview) | <li>Fixes for integrated Windows authentication to use -AccountId with Connect-MicrosoftTeams.</li><li>Added cmdlet to get details of total change notification events that can be sent to users.</li><li>Added cmdlet to get multi-geo region for users and groups.</li><li>Handling of values passed to TeamsEnvironment name was case sensitive. This has been fixed.</li><li>Major refactor of remote session management within the module to facilitate unit tests. There should be no functional change for tenant admins.</li>|
| April 2021 | [2.1.0-preview](https://www.powershellgallery.com/packages/MicrosoftTeams/2.1.0-preview) | <li>Fixed output formatting of some remoting cmdlets (for example, Get-CsTeamsNetworkRoamingPolicy, Get-CsTeamsMeetingPolicy, Get-CsTeamsMessagingPolicy, and more).</li><li>Updated parameter list of policy management cmdlets.</li>|
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

## Related topics

[Teams PowerShell Overview](teams-powershell-overview.md)

[Installing Teams PowerShell](teams-powershell-install.md)

[Managing Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Microsoft Teams cmdlet reference](/powershell/teams/?view=teams-ps)

[Skype for Business cmdlet reference](/powershell/skype/intro?view=skype-ps)
