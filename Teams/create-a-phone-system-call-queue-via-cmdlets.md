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
1)	PowerShell is installed on your computer
- Set up your computer for [Windows PowerShell](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)
- MSTeams Module Installed
````  (Install-Module -Name MicrosoftTeams -Force -AllowClobber) ````
- MSOnline module installed
```` Install-Module -Name MSOnline -Force -AllowClobber ````
2)	You have tenant administration rights
3)	You have purchased Microsoft Teams Phone
4)	The agents, distribution lists and Teams channels referred to below have already been created

## Scenario

The following three call queues will be created:

Sales Call Queue information:
- Language: English US
- Greeting: None
- Music on hold: Play an audio file
- - Filename: sales-hold-in-queue-music.wav
- Call Answering: Users
- - Bill@contoso.com
- - Mary@contoso.com
- Conference Mode: On
- Routing method: Attendant
- Presence-based routing: Off
- Call agents can opt out of taking calls: Yes
- Call agent alert time: 15
- Call overflow handling: 200
- - Redirect to: Adele@contoso.com
- Call timeout handling: 120 seconds
- - Redirect to: Adele@contoso.com

Support Call Queue information:
-	Language: English UK
-	Greeting: Play an audio file
-	- Filename: support-greeting.wav
-	Music on hold: Play an audio file
-	- Filename: support-hold-in-queue-music.wav
-	Call Answering: Support distribution list
-	- Support@contoso.com
-	Conference Mode: On
-	Routing method: Longest Idle
-	Presence-based routing: N/A – on by default due to Longest Idle
-	Call agents can opt out of taking calls: No
-	Call agent alert time: 15
-	Call overflow handling: 200
-	- Redirect: Support Shared Voicemail
- - -	Play an audio file (support-shared-voicemail-greeting.wav)
- - -	Transcription enabled
-	Call timeout handling: 45 minutes
-	- Redirect: Support Shared Voicemail
- - - Play TTS "We're sorry to have kept you waiting and are now transferring your call to voicemail."
- - - Transcription enabled


Facilities Collaborative Calling Queue information:
-	Language: French FR
-	Greeting: None
-	Music on hold: default
-	Call Answering: Channel: Facilities
-	Conference Mode: On
-	Routing method: Round Robin
-	Presence-based routing: On
-	Call agents can opt out of taking calls: No
-	Call agent alert time: 15
-	Call overflow handling: 200
-	- Disconnect
-	Call timeout handling: 45 minutes
-	- Disconnect

## Methodology

The call queues will be programmed starting with any required assets (creating audio files, linking to users, distributions lists, channels, and retrieving language codes), and finishing by assigning the resource accounts.

## Login
You will be prompted to enter your Teams administrator credentials.
```
$credential = Get-Credential
Connect-MicrosoftTeams -Credential $credential
Connect-MsolService -Credential $credential
````

## Sales Queue
### Create Audio Files
Replace "d:\" with the path to where the wav files are stored on your computer.

````
$content = Get-Content “d:\sales-hold-in-queue-music.wav” -Encoding byte -ReadCount 0
$audioFileSalesHoldInQueueMusicID = (Import-CsOnlineAudioFile -ApplicationID HuntGroup -FileName "sales-hold-in-queue-music.wav" -Content $content).ID
````

### Get Users ID
Replace "contoso.com with the Teams domain name for your tenant.

````
$userAdeleID = (Get-CsOnlineUser -Identity “sip:adele@contoso.com”).ObjectID
$userSalesBillID = (Get-CsOnlineUser -Identity “sip:bill@contoso.com”).ObectID
$userSalesMaryID = (Get-CsOlineUser -Identity “sip:mary@contoso.com”).ObjectID
````

### Get list of supported languages
````
Get-CsAutoAttendantSupportedLanguage
````

### Create Call Queue
````
New-CsCallQueue -Name “Sales” -AgentAlertTime 15 -AllowOptOut $true -MusicOnHoldAudioFileID $audioFileSalesHoldInQueueMusicID -OverflowAction Forward -OverflowActionTarget $userAdeleID -OverflowThreshold 200 -TimeoutAction Forward -TimeoutActionTarget $userAdeleID -TimeoutThreshold 120 -RoutingMethod Attendant -ConferenceMode $true -User @($userSalesBillID, $userSalesMaryID) -LanguageID “en-US”
````

### Create and Assign Resource Account
Note: Phone number not required here as call queue is front ended by an Auto Attendant
#ApplicationID
#Auto Attendant: ce933385-9390-45d1-9512-c8d228074e07
#Call Queue: 11cd3e2e-fccb-42ad-ad00-878b93575e07

````
New-CsOnlineApplicationInstance -UserPrincipalName Sales-RA@contoso.com -DisplayName "Sales" -ApplicationID "11cd3e2e-fccb-42ad-ad00-878b93575e07"

Set-MsolUser -UserPrincipalName "Sales-RA@contoso.com" -UsageLocation US

Set-MsolUserLicense -UserPrincipalName “Sales-RA@contoso.com” -AddLicenses "contoso:PHONESYSTEM_VIRTUALUSER"

$applicationInstanceID = (Get-CsOnlineUser "Sales-RA@contoso.com").ObjectID
$callQueueID = (Get-CsCallQueue -NameFilter "Sales").Identity

New-CsOnlineApplicationInstanceAssociation -Identities @($applicationInstanceID) -ConfigurationID $callQueueID -ConfigurationType CallQueue
````

## Support Queue
### Create audio files
Replace "d:\" with the path to where the wav files are stored on your computer.

````
$content = Get-Content “d:\support-greeting.wav” -Encoding byte -ReadCount 0
$audioFileSupportGreetingID = (Import-CsOnlineAudioFile -ApplicationID HuntGroup -FileName "support-greeting.wav" -Content $content).ID

$content = Get-Content “d:\support-hold-in-queue-music.wav” -Encoding byte -ReadCount 0
$audioFileSupportHoldInQueueMusicID = (Import-CsOnlineAudioFile -ApplicationID HuntGroup -FileName "support-hold-in-queue-music.wav" -Content $content).ID

$content = Get-Content “d:\support-shared-voicemail-greeting.wav” -Encoding byte -ReadCount 0
$audioFileSupportSharedVoicemailGreetingID = (Import-CsOnlineAudioFile -ApplicationID HuntGroup -FileName "support-shared-voicemail-greeting.wav" -Content $content).ID
````

### Get Support team group ID
````
$teamSupportID = (Get-Team -displayname "Support").GroupID
````

### Get list of supported languages
````
Get-CsAutoAttendantSupportedLanguage
````

### Create Call Queue
````
New-CsCallQueue -Name “Support” -AgentAlertTime 15 -AllowOptOut $false -DistributionLists $teamSupportID -WelcomeMusicAudioFileID $audioFileSupportGreetingID -MusicOnHoldAudioFileID $audioFileSupportHoldInQueueMusicID -OverflowAction SharedVoicemail -OverflowActionTarget $teamSupportID -OverflowThreshold 200 -OverflowSharedVoicemailAudioFilePrompt $audioFileSupportSharedVoicemailGreetingID -EnableOverflowSharedVoicemailTranscription $true -TimeoutAction SharedVoicemail -TimeoutActionTarget $teamSupportID -TimeoutThreshold 2700 -TimeoutSharedVoicemailTextToSpeechPrompt "We're sorry to have kept you waiting and are now transferring your call to voicemail." -EnableTimeoutSharedVoicemailTranscription $true -RoutingMethod LongestIdle -ConferenceMode $true -LanguageID “en-US”
````

### Create and Assign Resource Account
Note: Phone number not required here as call queue is front-ended by an Auto Attendant
- ApplicationID
- - Auto Attendant: ce933385-9390-45d1-9512-c8d228074e07
- - Call Queue: 11cd3e2e-fccb-42ad-ad00-878b93575e07
````
New-CsOnlineApplicationInstance -UserPrincipalName Support-RA@contoso.com -DisplayName "Support" -ApplicationID "11cd3e2e-fccb-42ad-ad00-878b93575e07"

Set-MsolUser -UserPrincipalName "Support-RA@contoso.com" -UsageLocation US

Set-MsolUserLicense -UserPrincipalName “Support-RA@contoso.com” -AddLicenses "contoso:PHONESYSTEM_VIRTUALUSER"

$applicationInstanceID = (Get-CsOnlineUser "Support-RA@contoso.com").ObjectID
$callQueueID = (Get-CsCallQueue -NameFilter "Support").Identity

New-CsOnlineApplicationInstanceAssociation -Identities @($applicationInstanceID) -ConfigurationID $callQueueID -ConfigurationType CallQueue
````

