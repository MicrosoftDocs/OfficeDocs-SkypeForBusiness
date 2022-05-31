---
title: "Create a call queue via cmdlets"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.assetid: 67ccda94-1210-43fb-a25b-7b9785f8a061
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.callqueues.overview"
  - Phone System
  - seo-marvel-apr2020
description: Learn how to configure call queues via cmdlets
---
# Create a call queue via cmdlets

## Assumptions

1. PowerShell is installed on your computer
   - Set up your computer for [Windows PowerShell](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)
   - MSTeams Module Installed

     ```powershell
     Install-Module -Name MicrosoftTeams -Force -AllowClobber
     ```

   - MSOnline module installed

     ```powershell
     Install-Module -Name MSOnline -Force -AllowClobber
     ```

2. You have tenant administration rights
3. You have purchased Microsoft Teams Phone
4. The agents, distribution lists, and Teams channels referred to below have already been created

Note: The Teams Channel cmdlet used below is part of the Public Preview version of Teams PowerShell Module.  For more information, see [Install Teams PowerShell public preview](teams-powershell-install.md) and also see [Microsoft Teams PowerShell Release Notes](teams-powershell-release-notes.md).

Users who already have the MicrosoftTeams module installed should `Update-Module MicrosoftTeams` to ensure the most up-to-date version is installed.

## Scenario

The following three call queues will be created:

Sales Call Queue information:

- Fronted by Auto Attendant: Yes
- Direct calling from PSTN: No
- Language: English US
- Greeting: None
- Music on hold: Play an audio file
  - Filename: sales-hold-in-queue-music.wav
- Call Answering: Users
  - Bill@contoso.com
  - Mary@contoso.com
- Conference Mode: On
- Routing method: Attendant
- Presence-based routing: Off
- Call agents can opt out of taking calls: Yes
- Call agent alert time: 15
- Call overflow handling: 200
  - Redirect to: Adele@contoso.com
- Call timeout handling: 120 seconds
  - Redirect to: Adele@contoso.com

Support Call Queue information:

- Fronted by Auto Attendant: Yes
- Direct calling from PSTN: No
- Language: English UK
- Greeting: Play an audio file
  - Filename: support-greeting.wav
- Music on hold: Play an audio file
  - Filename: support-hold-in-queue-music.wav
- Call Answering: Support distribution list
  - Support@contoso.com
- Conference Mode: On
- Routing method: Longest Idle
- Presence-based routing: N/A – on by default because of Longest Idle
- Call agents can opt out of taking calls: No
- Call agent alert time: 15
- Call overflow handling: 200
  - Redirect: Support Shared Voicemail
    - Play an audio file (support-shared-voicemail-greeting.wav)
    - Transcription enabled
- Call timeout handling: 45 minutes
  - Redirect: Support Shared Voicemail
    - TTS: "We're sorry to have kept you waiting and are now transferring your call to voicemail."
    - Transcription enabled

Facilities Collaborative Calling Queue information:

- Fronted by Auto Attendant: No
- Direct calling from PSTN: No (internal calling only)
- Language: French FR
- Greeting: None
- Music on hold: default
- Call Answering: Team: Facilities
- Call Answering Channel: Help Desk
  - Channel Owner: Fred@contoso.com
- Conference Mode: On
- Routing method: Round Robin
- Presence-based routing: On
- Call agents can opt out of taking calls: No
- Call agent alert time: 15
- Call overflow handling: 200
  - Disconnect
- Call timeout handling: 45 minutes
  - Disconnect

## Login

You will be prompted to enter your Teams administrator credentials.

```powershell
$credential = Get-Credential
Connect-MicrosoftTeams -Credential $credential
Connect-MsolService -Credential $credential
```

## Sales Queue

### Create Audio Files

Replace "d:\\" with the path to where the wav files are stored on your computer.

```powershell
$content = Get-Content "d:\sales-hold-in-queue-music.wav" -Encoding byte -ReadCount 0
$audioFileSalesHoldInQueueMusicID = (Import-CsOnlineAudioFile -ApplicationID HuntGroup -FileName "sales-hold-in-queue-music.wav" -Content $content).ID
```

### Get Users ID

```powershell
$userAdeleID = (Get-CsOnlineUser -Identity "sip:adele@contoso.com").Identity
$userSalesBillID = (Get-CsOnlineUser -Identity "sip:bill@contoso.com").Identity
$userSalesMaryID = (Get-CsOnlineUser -Identity "sip:mary@contoso.com").Identity
```

### Get list of supported languages

```powershell
Get-CsAutoAttendantSupportedLanguage
```

### Create Call Queue

```powershell
New-CsCallQueue -Name "Sales" -AgentAlertTime 15 -AllowOptOut $true -MusicOnHoldAudioFileID $audioFileSalesHoldInQueueMusicID -OverflowAction Forward -OverflowActionTarget $userAdeleID -OverflowThreshold 200 -TimeoutAction Forward -TimeoutActionTarget $userAdeleID -TimeoutThreshold 120 -RoutingMethod Attendant -ConferenceMode $true -User @($userSalesBillID, $userSalesMaryID) -LanguageID "en-US"
```

### Get license types

```powershell
Get-MsolAccountSku
```

### Create and Assign Resource Account

Note: Phone number not required here as call queue is front ended by an Auto Attendant

- ApplicationID
  - Auto Attendant: ce933385-9390-45d1-9512-c8d228074e07
  - Call Queue: 11cd3e2e-fccb-42ad-ad00-878b93575e07

Note: The license type shown below (PHONESYSTEM_VIRTUALUSER) must be one that is listed by the Get-MsolAccountSku cmdlet above.

```powershell
New-CsOnlineApplicationInstance -UserPrincipalName Sales-RA@contoso.com -DisplayName "Sales" -ApplicationID "11cd3e2e-fccb-42ad-ad00-878b93575e07"

Set-MsolUser -UserPrincipalName "Sales-RA@contoso.com" -UsageLocation US

Set-MsolUserLicense -UserPrincipalName "Sales-RA@contoso.com" -AddLicenses "contoso:PHONESYSTEM_VIRTUALUSER"

$applicationInstanceID = (Get-CsOnlineUser -Identity "Sales-RA@contoso.com").Identity
$callQueueID = (Get-CsCallQueue -NameFilter "Sales").Identity

New-CsOnlineApplicationInstanceAssociation -Identities @($applicationInstanceID) -ConfigurationID $callQueueID -ConfigurationType CallQueue
```

## Support Queue

### Create audio files

Replace "d:\\" with the path to where the wav files are stored on your computer.

```powershell
$content = Get-Content "d:\support-greeting.wav" -Encoding byte -ReadCount 0
$audioFileSupportGreetingID = (Import-CsOnlineAudioFile -ApplicationID HuntGroup -FileName "support-greeting.wav" -Content $content).ID

$content = Get-Content "d:\support-hold-in-queue-music.wav" -Encoding byte -ReadCount 0
$audioFileSupportHoldInQueueMusicID = (Import-CsOnlineAudioFile -ApplicationID HuntGroup -FileName "support-hold-in-queue-music.wav" -Content $content).ID

$content = Get-Content "d:\support-shared-voicemail-greeting.wav" -Encoding byte -ReadCount 0
$audioFileSupportSharedVoicemailGreetingID = (Import-CsOnlineAudioFile -ApplicationID HuntGroup -FileName "support-shared-voicemail-greeting.wav" -Content $content).ID
```

### Get Support team group ID

```powershell
$teamSupportID = (Get-Team -displayname "Support").GroupID
```

### Get list of supported languages

```powershell
Get-CsAutoAttendantSupportedLanguage
```

### Create Call Queue

```powershell
New-CsCallQueue -Name "Support" -AgentAlertTime 15 -AllowOptOut $false -DistributionLists $teamSupportID -WelcomeMusicAudioFileID $audioFileSupportGreetingID -MusicOnHoldAudioFileID $audioFileSupportHoldInQueueMusicID -OverflowAction SharedVoicemail -OverflowActionTarget $teamSupportID -OverflowThreshold 200 -OverflowSharedVoicemailAudioFilePrompt $audioFileSupportSharedVoicemailGreetingID -EnableOverflowSharedVoicemailTranscription $true -TimeoutAction SharedVoicemail -TimeoutActionTarget $teamSupportID -TimeoutThreshold 2700 -TimeoutSharedVoicemailTextToSpeechPrompt "We're sorry to have kept you waiting and are now transferring your call to voicemail." -EnableTimeoutSharedVoicemailTranscription $true -RoutingMethod LongestIdle -ConferenceMode $true -LanguageID "en-US"
```

### Get license types

```powershell
Get-MsolAccountSku
```

### Create and Assign Resource Account

Note: Phone number not required here as call queue is front-ended by an Auto Attendant

- ApplicationID
  - Auto Attendant: ce933385-9390-45d1-9512-c8d228074e07
  - Call Queue: 11cd3e2e-fccb-42ad-ad00-878b93575e07

Note: The license type shown below (PHONESYSTEM_VIRTUALUSER) must be one that is listed by the Get-MsolAccountSku cmdlet above.

```powershell
New-CsOnlineApplicationInstance -UserPrincipalName Support-RA@contoso.com -DisplayName "Support" -ApplicationID "11cd3e2e-fccb-42ad-ad00-878b93575e07"

Set-MsolUser -UserPrincipalName "Support-RA@contoso.com" -UsageLocation US

Set-MsolUserLicense -UserPrincipalName "Support-RA@contoso.com" -AddLicenses "contoso:PHONESYSTEM_VIRTUALUSER"

$applicationInstanceID = (Get-CsOnlineUser -Identity "Support-RA@contoso.com").Identity
$callQueueID = (Get-CsCallQueue -NameFilter "Support").Identity

New-CsOnlineApplicationInstanceAssociation -Identities @($applicationInstanceID) -ConfigurationID $callQueueID -ConfigurationType CallQueue
```

## Facilities Collaborative Calling Queue

### Get Facilities team group ID

```powershell
$teamFacilitiesGroupID = (Get-Team -DisplayName "Facilities").GroupID
```

### Get Facilities Help Desk team channel ID

```powershell
Get-TeamChannel -GroupId $teamFacilitiesGroupID
$teamFacilitiesHelpDeskChannelID = "{assign ID from output of above command}"
```

### Get Facilities Help Desk channel owner user ID

```powershell
$teamFacilitiesHelpDeskChannelUserID = (Get-TeamChannelUser -GroupId $teamFacilitiesGroupID -DisplayName "Help Desk" -Role Owner).UserId
```

### Get On Behalf Of Calling Resource Account ID

```powershell
$oboResourceAccountID = (Get-CsOnlineUser -Identity "MainAA-RA@contoso.com").Identity
```

### Get list of supported languages

```powershell
Get-CsAutoAttendantSupportedLanguage
```

### Create Call Queue

```powershell
New-CsCallQueue -Name "Facilities" -AgentAlertTime 15 -AllowOptOut $false -ChannelId $teamFacilitiesHelpDeskChannelID -ChannelUserObjectId $teamFacilitiesHelpDeskChannelUserID  -ConferenceMode $true -DistributionList $teamFacilitiesGroupID -LanguageID "fr-FR" -OboResourceAccountIds $oboResourceAccountID -OverflowAction DisconnectWithBusy -OverflowThreshold 200 -RoutingMethod RoundRobin -TimeoutAction Disconnect -TimeoutThreshold 2700 -UseDefaultMusicOnHold $true 
```

### Get license types

```powershell
Get-MsolAccountSku
```

### Create and Assign Resource Account

**Note**: Phone number not required here as call queue is front-ended by an Auto Attendant

- ApplicationID
  - Auto Attendant: ce933385-9390-45d1-9512-c8d228074e07
  - Call Queue: 11cd3e2e-fccb-42ad-ad00-878b93575e07

Note: The license type shown below (PHONESYSTEM_VIRTUALUSER) must be one that is listed by the Get-MsolAccountSku cmdlet above.

```powershell
New-CsOnlineApplicationInstance -UserPrincipalName Facilities-RA@contoso.com -DisplayName "Facilities" -ApplicationID "11cd3e2e-fccb-42ad-ad00-878b93575e07"

Set-MsolUser -UserPrincipalName "Facilities-RA@contoso.com" -UsageLocation US

Set-MsolUserLicense -UserPrincipalName "Facilities-RA@contoso.com" -AddLicenses "contoso:PHONESYSTEM_VIRTUALUSER"

$applicationInstanceID = (Get-CsOnlineUser -Identity "Facilities-RA@contoso.com").Identity
$callQueueID = (Get-CsCallQueue -NameFilter "Facilities").Identity

New-CsOnlineApplicationInstanceAssociation -Identities @($applicationInstanceID) -ConfigurationID $callQueueID -ConfigurationType CallQueue
```
