---
title: PowerShell cmdlet reference for Auto attendants and Call queues
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.reviewer: colongma
ms.date: 06/09/2022
ms.topic: article
ms.assetid: 67ccda94-1210-43fb-a25b-7b9785f8a061
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom:
  - Phone System
  - seo-marvel-apr2020
  - has-azure-ad-ps-ref
  - azure-ad-ref-level-one-done
description: Reference this article for PowerShell cmdlets to create and manage Auto attendants and Call queues in Microsoft Teams.
---

# PowerShell cmdlet reference for Auto attendants and Call queues

The following cmdlet references are for Microsoft Teams Auto attendants and Call queues.

## Auto attendant cmdlets

The following cmdlets allow you to manage Auto attendants:

- [New-CsAutoAttendant](/powershell/module/skype/new-csautoattendant)  
- [Get-CsAutoAttendant](/powershell/module/skype/get-csautoattendant)
- [Set-CsAutoAttendant](/powershell/module/skype/set-csautoattendant)
- [Update-CsAutoAttendant](/powershell/module/skype/update-csautoattendant)
- [Remove-CsAutoAttendant](/powershell/module/skype/remove-csautoattendant)
- [New-CsOnlineTimeRange](/powershell/module/skype/new-csonlinetimerange)
- [New-CsOnlineDateTimeRange](/powershell/module/skype/new-csonlinedatetimerange)
- [New-CsOnlineSchedule](/powershell/module/skype/New-CsOnlineSchedule)
- [Get-CsAutoAttendantHolidays](/powershell/module/skype/get-csautoattendantholidays)
- [Import-CsAutoAttendantHolidays](/powershell/module/skype/import-csautoattendantholidays)
- [Export-CsAutoAttendantHolidays](/powershell/module/skype/export-csautoattendantholidays)
- [New-CsAutoAttendantDialScope](/powershell/module/skype/New-CsAutoAttendantDialScope)
- [New-CsAutoAttendantPrompt](/powershell/module/skype/New-CsAutoAttendantPrompt)
- [New-CsAutoAttendantCallableEntity](/powershell/module/skype/New-CsAutoAttendantCallableEntity)
- [New-CsAutoAttendantMenuOption](/powershell/module/skype/New-CsAutoAttendantMenuOption)
- [New-CsAutoAttendantMenu](/powershell/module/skype/new-csautoattendantmenu)
- [New-CsAutoAttendantCallFlow](/powershell/module/skype/New-CsAutoAttendantCallFlow)
- [New-CsAutoAttendantCallHandlingAssociation](/powershell/module/skype/New-CsAutoAttendantCallHandlingAssociation)
- [Get-CsAutoAttendantStatus](/powershell/module/skype/Get-CsAutoAttendantStatus)
- [Get-CsAutoAttendantTenantInformation](/powershell/module/skype/Get-CsAutoAttendantTenantInformation)

For a step-by-step guide to creating Auto attendants with PowerShell, see [Creating Auto attendants with PowerShell cmdlets](create-a-phone-system-auto-attendant-via-cmdlets.md)

## Call queue cmdlets

The following cmdlets allow you to manage a Call queue:

- [New-CsCallQueue](/powershell/module/skype/New-CsCallQueue)
- [Get-CsCallQueue](/powershell/module/skype/Get-CsCallQueue)
- [Set-CsCallQueue](/powershell/module/skype/Set-CsCallQueue)
- [Remove-CsCallQueue](/powershell/module/skype/Remove-CsCallQueue)

For a step-by-step guide to creating Call queues with PowerShell, see [Creating Call queues with PowerShell cmdlets](create-a-phone-system-call-queue-via-cmdlets.md)

## Common cmdlets used by both Auto attendants and Call queues

The following cmdlets are also required to manage the users, resource accounts, Microsoft Teams Phone licenses, phone numbers, audio files, and supported languages that are used with Auto attendants:

### Users and Teams

- Users
  - [Get-CsOnlineUser](/powershell/module/skype/Get-CsOnlineUser)

- Teams:
  - [Get-Team](/powershell/module/teams/Get-Team)
  - [Get-TeamChannel](/powershell/module/teams/Get-TeamChannel)

### Resource accounts

- [New-CsOnlineApplicationInstance](/powershell/module/skype/New-CsOnlineApplicationInstance)
- [Find-CsOnlineApplicationInstance](/powershell/module/skype/Find-CsOnlineApplicationInstance)
- [Get-CsOnlineApplicationInstance](/powershell/module/skype/Get-CsOnlineApplicationInstance)
- [Set-CsOnlineApplicationInstance](/powershell/module/skype/Set-CsOnlineApplicationInstance)
- [New-CsOnlineApplicationInstanceAssociation](/powershell/module/skype/New-CsOnlineApplicationInstanceAssociation)
- [Get-CsOnlineApplicationInstanceAssociation](/powershell/module/skype/Get-CsOnlineApplicationInstanceAssociation)
- [Remove-CsOnlineApplicationInstanceAssociation](/powershell/module/skype/Remove-CsOnlineApplicationInstanceAssociation)
- [Get-CsOnlineApplicationInstanceAssociationStatus](/powershell/module/skype/Get-CsOnlineApplicationInstanceAssociationStatus)

### Teams Phone Resource Account licenses

- [Get-MgSubscribedSku](/powershell/module/microsoft.graph.identity.directorymanagement/get-mgsubscribedsku)
- [Set-MgUserLicense](/powershell/module/microsoft.graph.users.actions/set-mguserlicense)

### Phone number assignment

- [Get-CsPhoneNumberAssignment](/powershell/module/teams/Get-CsPhoneNumberAssignment)
- [Set-CsPhoneNumberAssignment](/powershell/module/teams/Set-CsPhoneNumberAssignment)

### Audio Files

- [Get-CsOnlineAudioFile](/powershell/module/skype/Get-CsOnlineAudioFile)
- [Import-CsOnlineAudioFile](/powershell/module/skype/Import-CsOnlineAudioFile)
- [Export-CsOnlineAudioFile](/powershell/module/skype/Export-CsOnlineAudioFile)
- [Remove-CsOnlineAudioFile](/powershell/module/skype/Remove-CsOnlineAudioFile)

### Support Languages and Time zones

- [Get-CsAutoAttendantSupportedLanguage](/powershell/module/skype/Get-CsAutoAttendantSupportedLanguage)
- [Get-CsAutoAttendantSupportedTimeZone](/powershell/module/skype/Get-CsAutoAttendantSupportedTimeZone)

### Voice applications policies

- [Get-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/Get-CsTeamsVoiceApplicationsPolicy)
- [Grant-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/Grant-CsTeamsVoiceApplicationsPolicy)
- [New-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/New-CsTeamsVoiceApplicationsPolicy)
- [Remove-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/Remove-CsTeamsVoiceApplicationsPolicy)
- [Set-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/Set-CsTeamsVoiceApplicationsPolicy)
