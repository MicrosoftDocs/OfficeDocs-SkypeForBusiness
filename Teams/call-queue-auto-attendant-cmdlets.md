---
title: PowerShell cmdlet reference for Auto attendants and Call queues
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.date: 12/05/2023
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

- [New-CsAutoAttendant](/powershell/module/teams/new-csautoattendant)  
- [Get-CsAutoAttendant](/powershell/module/teams/get-csautoattendant)
- [Set-CsAutoAttendant](/powershell/module/teams/set-csautoattendant)
- [Update-CsAutoAttendant](/powershell/module/teams/update-csautoattendant)
- [Remove-CsAutoAttendant](/powershell/module/teams/remove-csautoattendant)
- [New-CsOnlineTimeRange](/powershell/module/teams/new-csonlinetimerange)
- [New-CsOnlineDateTimeRange](/powershell/module/teams/new-csonlinedatetimerange)
- [New-CsOnlineSchedule](/powershell/module/teams/New-CsOnlineSchedule)
- [Get-CsAutoAttendantHolidays](/powershell/module/teams/get-csautoattendantholidays)
- [Import-CsAutoAttendantHolidays](/powershell/module/teams/import-csautoattendantholidays)
- [Export-CsAutoAttendantHolidays](/powershell/module/teams/export-csautoattendantholidays)
- [New-CsAutoAttendantDialScope](/powershell/module/teams/New-CsAutoAttendantDialScope)
- [New-CsAutoAttendantPrompt](/powershell/module/teams/New-CsAutoAttendantPrompt)
- [New-CsAutoAttendantCallableEntity](/powershell/module/teams/New-CsAutoAttendantCallableEntity)
- [New-CsAutoAttendantMenuOption](/powershell/module/teams/New-CsAutoAttendantMenuOption)
- [New-CsAutoAttendantMenu](/powershell/module/teams/new-csautoattendantmenu)
- [New-CsAutoAttendantCallFlow](/powershell/module/teams/New-CsAutoAttendantCallFlow)
- [New-CsAutoAttendantCallHandlingAssociation](/powershell/module/teams/New-CsAutoAttendantCallHandlingAssociation)
- [Get-CsAutoAttendantStatus](/powershell/module/teams/Get-CsAutoAttendantStatus)
- [Get-CsAutoAttendantTenantInformation](/powershell/module/teams/Get-CsAutoAttendantTenantInformation)

For a step-by-step guide to creating Auto attendants with PowerShell, see [Creating Auto attendants with PowerShell cmdlets](create-a-phone-system-auto-attendant-via-cmdlets.md)

## Call queue cmdlets

The following cmdlets allow you to manage a Call queue:

- [New-CsCallQueue](/powershell/module/teams/New-CsCallQueue)
- [Get-CsCallQueue](/powershell/module/teams/Get-CsCallQueue)
- [Set-CsCallQueue](/powershell/module/teams/Set-CsCallQueue)
- [Remove-CsCallQueue](/powershell/module/teams/Remove-CsCallQueue)

For a step-by-step guide to creating Call queues with PowerShell, see [Creating Call queues with PowerShell cmdlets](create-a-phone-system-call-queue-via-cmdlets.md)

## Common cmdlets used by both Auto attendants and Call queues

The following cmdlets are also required to manage the users, resource accounts, Microsoft Teams Phone licenses, phone numbers, audio files, and supported languages that are used with Auto attendants:

### Users and Teams

- Users
  - [Get-CsOnlineUser](/powershell/module/teams/Get-CsOnlineUser)

- Teams:
  - [Get-Team](/powershell/module/teams/Get-Team)
  - [Get-TeamChannel](/powershell/module/teams/Get-TeamChannel)

### Resource accounts

- [New-CsOnlineApplicationInstance](/powershell/module/teams/New-CsOnlineApplicationInstance)
- [Find-CsOnlineApplicationInstance](/powershell/module/teams/Find-CsOnlineApplicationInstance)
- [Get-CsOnlineApplicationInstance](/powershell/module/teams/Get-CsOnlineApplicationInstance)
- [Set-CsOnlineApplicationInstance](/powershell/module/teams/Set-CsOnlineApplicationInstance)
- [New-CsOnlineApplicationInstanceAssociation](/powershell/module/teams/New-CsOnlineApplicationInstanceAssociation)
- [Get-CsOnlineApplicationInstanceAssociation](/powershell/module/teams/Get-CsOnlineApplicationInstanceAssociation)
- [Remove-CsOnlineApplicationInstanceAssociation](/powershell/module/teams/Remove-CsOnlineApplicationInstanceAssociation)
- [Get-CsOnlineApplicationInstanceAssociationStatus](/powershell/module/teams/Get-CsOnlineApplicationInstanceAssociationStatus)

### Teams Phone Resource Account licenses

- [Get-MgSubscribedSku](/powershell/module/microsoft.graph.identity.directorymanagement/get-mgsubscribedsku)
- [Set-MgUserLicense](/powershell/module/microsoft.graph.users.actions/set-mguserlicense)

### Phone number assignment

- [Get-CsPhoneNumberAssignment](/powershell/module/teams/Get-CsPhoneNumberAssignment)
- [Set-CsPhoneNumberAssignment](/powershell/module/teams/Set-CsPhoneNumberAssignment)

### Audio Files

- [Get-CsOnlineAudioFile](/powershell/module/teams/Get-CsOnlineAudioFile)
- [Import-CsOnlineAudioFile](/powershell/module/teams/Import-CsOnlineAudioFile)
- [Export-CsOnlineAudioFile](/powershell/module/teams/Export-CsOnlineAudioFile)
- [Remove-CsOnlineAudioFile](/powershell/module/teams/Remove-CsOnlineAudioFile)

### Support Languages and Time zones

- [Get-CsAutoAttendantSupportedLanguage](/powershell/module/teams/Get-CsAutoAttendantSupportedLanguage)
- [Get-CsAutoAttendantSupportedTimeZone](/powershell/module/teams/Get-CsAutoAttendantSupportedTimeZone)

### Voice applications policies

- [Get-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/Get-CsTeamsVoiceApplicationsPolicy)
- [Grant-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/Grant-CsTeamsVoiceApplicationsPolicy)
- [New-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/New-CsTeamsVoiceApplicationsPolicy)
- [Remove-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/Remove-CsTeamsVoiceApplicationsPolicy)
- [Set-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/Set-CsTeamsVoiceApplicationsPolicy)
