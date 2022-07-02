---
title: Teams PowerShell Module - Supported Versions
author: pbafna03
ms.author: pbafna
ms.reviewer: pbafna
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

Microsoft Teams PowerShell Module (TPM) versions in the 4.x.x series or later are the only versions supported now. All earlier versions are fully retired since June 15, 2022 & will stop working (Message center post for reference - MC350371). 

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
  - Updates to Get-CsOnlineUser & Get-CsOnlineVoiceUser in TPM 3.x.x and later – more details in [Get-CsOnlineUser](/powershell/module/skype/get-csonlineuser) & [Get-CsOnlineVoiceUser](/powershell/module/skype/get-csonlinevoiceuser) (Message center post – MC340774).

  - Changes coming to Phone number assignment - more details in [Set-CsUser](/powershell/module/skype/set-csuser), [Set-CsOnlineVoiceUser](/powershell/module/skype/set-csonlinevoiceuser), [Set-CsOnlineApplicationInstance](/powershell/module/skype/set-csonlineapplicationinstance) & [Set-CsOnlineVoiceApplicationInstance](/powershell/module/skype/set-csonlinevoiceapplicationinstance) (Message center post – MC316139).

  - Parameter changes in Get-CsTenant - more details in [Get-CsTenant](/powershell/module/skype/get-cstenant) (Message center post – MC365397).
  
  - If your scripts use New/Set of Policy or Configuration cmdlets with PSListModifier type parameters, it’s recommended to use the latest version (4.2.0 or later).

- While using TPM 4.x.x or later, it's recommended to not use any of the deprecated or unsupported cmdlets mentioned [below](#deprecated-cmdlets).

## Deprecated cmdlets

- Some of the cmdlets that were deprecated recently are listed below. Details on the same can be found in the respective public documentations.
  - [Get-CsOnlineTelephoneNumber](/powershell/module/skype/get-csonlinetelephonenumber)
  - [Get-CsOnlineDialInConferencingUserInfo](/powershell/module/skype/get-csonlinedialinconferencinguserinfo), [Get-CsOnlineDialInConferencingUserState](/powershell/module/skype/get-csonlinedialinconferencinguserstate), [Enable-CsOnlineDialInConferencingUser](/powershell/module/skype/enable-csonlinedialinconferencinguser), [Disable-CsOnlineDialInConferencingUser](/powershell/module/skype/disable-csonlinedialinconferencinguser)
  - [Get-CsOnlineDirectoryTenant](/powershell/module/skype/get-csonlinedirectorytenant)
  - [New-CsOnlineAudioFile](/powershell/module/skype/new-csonlineaudiofile)
  - [Get-CsOnlineApplicationEndpoint](/powershell/module/skype/get-csonlineapplicationendpoint), [Set-CsOnlineApplicationEndpoint](/powershell/module/skype/set-csonlineapplicationendpoint), [New-CsOnlineApplicationEndpoint](/powershell/module/skype/new-csonlineapplicationendpoint), [Remove-CsOnlineApplicationEndpoint](/powershell/module/skype/remove-csonlineapplicationendpoint)
  - [Get-CsOnlineTelephoneNumberInventoryCities](/powershell/module/skype/get-csonlinetelephonenumberinventorycities), [Get-CsOnlineTelephoneNumberInventoryAreas](/powershell/module/skype/get-csonlinetelephonenumberinventoryareas), [Get-CsOnlineTelephoneNumberInventoryCountries](/powershell/module/skype/get-csonlinetelephonenumberinventorycountries), [Get-CsOnlineTelephoneNumberInventoryRegions](/powershell/module/skype/get-csonlinetelephonenumberinventoryregions), [Get-CsOnlineTelephoneNumberInventoryTypes](/powershell/module/skype/get-csonlinetelephonenumberinventorytypes), [Search-CsOnlineTelephoneNumberInventory](/powershell/module/skype/search-csonlinetelephonenumberinventory), [Select-CsOnlineTelephoneNumberInventory](/powershell/module/skype/select-csonlinetelephonenumberinventory), [Get-CsOnlineTelephoneNumberAvailableCount](/powershell/module/skype/get-csonlinetelephonenumberavailablecount), [Clear-CsOnlineTelephoneNumberReservation](/powershell/module/skype/clear-csonlinetelephonenumberreservation), [Get-CsOnlineTelephoneNumberReservationsInformation](/powershell/module/skype/get-csonlinetelephonenumberreservationsinformation), [Get-CsOnlineDirectoryTenantNumberCities](/powershell/module/skype/get-csonlinedirectorytenantnumbercities)
  - [Set-CsTeamsAppSetupPolicy](/powershell/module/skype/set-csteamsappsetuppolicy), [New-CsTeamsAppSetupPolicy](/powershell/module/skype/new-csteamsappsetuppolicy), [Set-CsTeamsAppPermissionPolicy](/powershell/module/skype/set-csteamsapppermissionpolicy), [New-CsTeamsAppPermissionPolicy](/powershell/module/skype/new-csteamsapppermissionpolicy)
  - [Test-CsOnlineLisCivicAddress](/powershell/module/skype/test-csonlineliscivicaddress)

- Cmdlets that aren't supported/relevant for Microsoft Teams scenarios are listed below.
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

## Related topics

[Teams PowerShell release notes](teams-powershell-release-notes.md)

[Install Microsoft Teams PowerShell](teams-powershell-install.md)

[Manage Teams with Teams PowerShell](teams-powershell-managing-teams.md)

[Microsoft Teams cmdlet reference](/powershell/module/teams)

[Skype for Business cmdlet reference](/powershell/module/skype)
