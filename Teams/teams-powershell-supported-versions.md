---
title: Teams PowerShell Module - Supported Versions
author: pbafna03
ms.author: pbafna
ms.reviewer: pbafna
ms.date: 01/08/2022
manager: sshastri
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.collection:
  - M365-collaboration
description: Learn about versions supported of the Teams PowerShell Module, used for administration of Microsoft Teams.
appliesto:
  - Microsoft Teams
---

# Teams PowerShell Module - Supported Versions

Microsoft Teams PowerShell Module (TPM) versions in the 4.x.x series or later are the only versions supported now. All earlier versions are fully retired. 

It’s recommended to update to the latest Teams PowerShell Module version.


## Important notes

- Release notes for all the Teams PowerShell Module versions can be found at [Teams PowerShell release notes](teams-powershell-release-notes.md).

- To update any PowerShell module, you should use the same method used to install the module. For example, if you originally used Install-Module, then you should use [Update-Module](/powershell/module/powershellget/update-module) to get the latest version.

  ```powershell
  Update-Module MicrosoftTeams
  ```

- If updating from Teams PowerShell Module version 1.1.6, update your scripts to use `Connect-MicrosoftTeams` instead of `New-CsOnlineSession`.

- During the update, it's suggested to not use TPM 4.x.x/3.x.x alongside versions earlier than 3.0.0. For example, using versions 4.x.x & 2.6.0 together for different admin operations in the same organization isn't recommended.

- Related changes
  - Updates to Get-CsOnlineUser & Get-CsOnlineVoiceUser in TPM 3.x.x and later – more details in [Get-CsOnlineUser](/powershell/module/teams/get-csonlineuser) & [Get-CsOnlineVoiceUser](/powershell/module/teams/get-csonlinevoiceuser) (Message center post – MC340774/MC511150).

  - Changes coming to Phone number assignment - more details in [Set-CsUser](/powershell/module/teams/set-csuser), [Set-CsOnlineVoiceUser](/powershell/module/teams/set-csonlinevoiceuser), [Set-CsOnlineApplicationInstance](/powershell/module/teams/set-csonlineapplicationinstance) & [Set-CsOnlineVoiceApplicationInstance](/powershell/module/teams/set-csonlinevoiceapplicationinstance) (Message center post – MC316139).

  - Parameter changes in Get-CsTenant - more details in [Get-CsTenant](/powershell/module/teams/get-cstenant) (Message center post – MC365397).
  
  - If your scripts use New/Set of Policy or Configuration cmdlets with PSListModifier type parameters, it’s recommended to use the latest version (4.2.0 or later). Message center post for reference - MC397428.

  - [New|Get]-CsCloudCallDataConnection cmdlets are now supported from versions 4.6.0 or later (Message center post - MC408993).
  
  - [New|Remove]-CsHybridTelephoneNumber cmdlets are now supported from versions 4.5.0 or later in GCC High and DoD environments.


- While using TPM 4.x.x or later, it's recommended to not use any of the [deprecated or unsupported](#deprecated-cmdlets) cmdlets.

## Deprecated cmdlets

- Some of the cmdlets that were deprecated recently are listed below. Details on the same can be found in the respective public documentations.
  - [Get-CsOnlineVoiceUser](/powershell/module/teams/get-csonlinevoiceuser) (deprecated only in commercial & GCC environments currently)
  - [Get-CsOnlineTelephoneNumber](/powershell/module/teams/get-csonlinetelephonenumber)
  - [Get-CsOnlineDialInConferencingUserInfo](/powershell/module/teams/get-csonlinedialinconferencinguserinfo), [Get-CsOnlineDialInConferencingUserState](/powershell/module/teams/get-csonlinedialinconferencinguserstate), [Enable-CsOnlineDialInConferencingUser](/powershell/module/teams/enable-csonlinedialinconferencinguser), [Disable-CsOnlineDialInConferencingUser](/powershell/module/teams/disable-csonlinedialinconferencinguser)
  - [Get-CsOnlineDirectoryTenant](/powershell/module/teams/get-csonlinedirectorytenant)
  - [New-CsOnlineAudioFile](/powershell/module/teams/new-csonlineaudiofile)
  - [Get-CsOnlineApplicationEndpoint](/powershell/module/teams/get-csonlineapplicationendpoint), [Set-CsOnlineApplicationEndpoint](/powershell/module/teams/set-csonlineapplicationendpoint), [New-CsOnlineApplicationEndpoint](/powershell/module/teams/new-csonlineapplicationendpoint), [Remove-CsOnlineApplicationEndpoint](/powershell/module/teams/remove-csonlineapplicationendpoint), Switch-CsOnlineApplicationEndpoint
  - [Get-CsOnlineTelephoneNumberInventoryCities](/powershell/module/teams/get-csonlinetelephonenumberinventorycities), [Get-CsOnlineTelephoneNumberInventoryAreas](/powershell/module/teams/get-csonlinetelephonenumberinventoryareas), [Get-CsOnlineTelephoneNumberInventoryCountries](/powershell/module/teams/get-csonlinetelephonenumberinventorycountries), [Get-CsOnlineTelephoneNumberInventoryRegions](/powershell/module/teams/get-csonlinetelephonenumberinventoryregions), [Get-CsOnlineTelephoneNumberInventoryTypes](/powershell/module/teams/get-csonlinetelephonenumberinventorytypes), [Search-CsOnlineTelephoneNumberInventory](/powershell/module/teams/search-csonlinetelephonenumberinventory), [Select-CsOnlineTelephoneNumberInventory](/powershell/module/teams/select-csonlinetelephonenumberinventory), [Get-CsOnlineTelephoneNumberAvailableCount](/powershell/module/teams/get-csonlinetelephonenumberavailablecount), [Clear-CsOnlineTelephoneNumberReservation](/powershell/module/teams/clear-csonlinetelephonenumberreservation), [Get-CsOnlineTelephoneNumberReservationsInformation](/powershell/module/teams/get-csonlinetelephonenumberreservationsinformation), [Get-CsOnlineDirectoryTenantNumberCities](/powershell/module/teams/get-csonlinedirectorytenantnumbercities)
  - [Set-CsTeamsAppSetupPolicy](/powershell/module/teams/set-csteamsappsetuppolicy), [New-CsTeamsAppSetupPolicy](/powershell/module/teams/new-csteamsappsetuppolicy), [Set-CsTeamsAppPermissionPolicy](/powershell/module/teams/set-csteamsapppermissionpolicy), [New-CsTeamsAppPermissionPolicy](/powershell/module/teams/new-csteamsapppermissionpolicy)
  - [Test-CsOnlineLisCivicAddress](/powershell/module/teams/test-csonlineliscivicaddress)

- Cmdlets that aren't supported/relevant for Microsoft Teams scenarios.
  - [Get|Set]-CsUserPstnSettings
  - [Get|Set|Enable|Disable]-CsMeetingRoom
  - [Grant|Get|Set|New|Remove]-CsConferencingPolicy
  - [Grant|Get|Set|New|Remove]-CsClientPolicy
  - [Grant|Get]-CsHostedVoicemailPolicy
  - [Grant|Get|Set|New|Remove]-CsMobilityPolicy
  - [Grant|Get]-CsVoiceRoutingPolicy
  - [Grant|Get]-CsBroadcastMeetingPolicy
  - [Grant|Get]-CsCloudMeetingPolicy
  - [Grant|Get]-CsGraphPolicy
  - [Grant|Get|Set|New|Remove]-CsExternalUserCommunicationPolicy
  - [Grant|Get|Set]-CsIPPhonePolicy
  - Get-CsUserServicesPolicy
  - [Get|Set]-CsBroadcastMeetingConfiguration
  - [Get|Set]-CsOAuthConfiguration
  - [Get|Set]-CsMeetingConfiguration
  - [Get|Set]-CsTenantHybridConfiguration
  - [Get|Set]-CsPushNotificationConfiguration
  - [Get|Set]-CsUCPhoneConfiguration
  - Get-CsImFilterConfiguration
  - Get-CsAudioConferencingProvider
  - [Get|Set]-CsTenantPublicProvider
  - Get-CsHostingProvider
  - [Get|Set|Register|Unregister]-CsHybridPSTNAppliance
  - [Get|Set|New|Remove]-CsHybridPSTNSite
  - [Get|Set]-CsHybridMediationServer
  - [Get|Set|New|Remove]-CsTenantUpdateTimeWindow
  - Get-CsUserLocationStatus
  - Invoke-CsUcsRollback
  - [Get|Set|New|Remove]-CsTeamsPinnedApp
  - [Get|Set|New|Remove]-CsTenantCatalogApp
  - [Get|Set|New|Remove]-CsGlobalCatalogApp
  - [Get|Set|New|Remove]-CsDefaultCatalogApp
  - [Get|Set|New|Remove]-CsTeamsAppPreset
  - Invoke-CsUserPreferredDataLocationSync
  - [Get|Set]-CsTeamsUpgradeStatus
  - Grant-CsPolicy
  - Set-CsOnlineDirectoryUser

## Related topics

[Teams PowerShell release notes](teams-powershell-release-notes.md)

[Install Microsoft Teams PowerShell](teams-powershell-install.md)

[Manage Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Microsoft Teams cmdlet reference](/powershell/module/teams)

[Skype for Business cmdlet reference](/powershell/module/teams)
