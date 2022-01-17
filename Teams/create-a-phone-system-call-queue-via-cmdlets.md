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
description: Learn how to setup call queues via cmdlets
---
# Create a call queue via cmdlets

## Assumptions
1)	Powershell is installed on your computer
a.	Set up your computer for [Windows PowerShell](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)

b.	MSTeams Module Installed (Install-Module -Name MicrosoftTeams -Force -AllowClobber)
c.	MSOnline module installed (Install-Module -Name MSOnline -Force -AllowClobber)
2)	You have tenant administration rights
3)	You have purchased Microsoft Teams Phone
4)	The agents and distribution lists have already been created
5)	The phone numbers have already been acquired and are available for use within the tenant

## Scenario

The following three call queues will be created:

•	Sales Call Queue information:
o	Language: English US
o	Greeting: None
o	Music on hold: Play an audio file (sales-hold-in-queue-music.wav)
o	Call Answering: Users (Bill and Mary)
o	Conference Mode: On
o	Routing method: Attendant
o	Presence-based routing: Off
o	Call agents can opt out of taking calls: Yes
o	Call agent alert time: 15
o	Call overflow handling: 200, redirect to Adele Vance
o	Call timeout handling: 120 seconds, redirect to Adele Vance

•	Support Call Queue information:
o	Language: English UK
o	Greeting: Play an audio file (support-greeting.wav)
o	Music on hold: Play an audio file (support-hold-in-queue-music.wav)
o	Call Answering: Support distribution list (Support)
o	Conference Mode: On
o	Routing method: Longest Idle
o	Presence-based routing: N/A – on by default due to Longest Idle
o	Call agents can opt out of taking calls: No
o	Call agent alert time: 15
o	Call overflow handling: 200, Support Shared Voicemail
	Play an audio file (support-shared-voicemail-greeting.wav)
	Transcription enabled
o	Call timeout handling: 45 minutes, Support Shared Voicemail
	Play an audio file (support-shared-voicemail-greeting.wav)
	Transcription enabled

•	After hours transfers to the Sales and Support shared voicemail should suppress the system greeting and transcription should be enabled.

•	Facilities Collaborative Calling Call Queue information:
o	Language: French FR
o	Greeting: TTS 
o	Music on hold: default
o	Call Answering: Channel: Facilities
o	Conference Mode: On
o	Routing method: Round Robin
o	Presence-based routing: On
o	Call agents can opt out of taking calls: No
o	Call agent alert time: 15
o	Call overflow handling: 200, Disconnect
o	Call timeout handling: 45 minutes, Disconnect

## Programming approach:

The call queues will be programmed from the bottom up, starting with any required assets (creating audio files, linking to users, distributions lists, channels and retrieving language codes), and finishing by assigning the resource accounts.

### Login
```
$credential = Get-Credential
Connect-MicrosoftTeams -Credential $credential
Connect-MsolService -Credential $credential
````

### Support Queue – Create audio files
````
$content = Get-Content “d:\support-greeting.wav” -Encoding byte -ReadCount 0
$audioFileSupportGreetingID = (Import-CsOnlineAudioFile -ApplicationID HuntGroup -FileName "support-greeting.wav" -Content $content).ID

$content = Get-Content “d:\support-hold-in-queue-music.wav” -Encoding byte -ReadCount 0
$audioFileSupportHoldInQueueMusicID = (Import-CsOnlineAudioFile -ApplicationID HuntGroup -FileName "support-hold-in-queue-music.wav" -Content $content).ID

$content = Get-Content “d:\support-shared-voicemail-greeting.wav” -Encoding byte -ReadCount 0
$audioFileSupportSharedVoicemailGreetingID = (Import-CsOnlineAudioFile -ApplicationID HuntGroup -FileName "support-shared-voicemail-greeting.wav" -Content $content).ID
````

### Support Queue – Get Support team group ID
````
$teamSupportID = (Get-Team -displayname "Support").GroupID
````

### Support Queue - Get list of supported languages


### Support Queue – Create Call Queue
````
New-CsCallQueue -Name “Support” -AgentAlertTime 15 -AllowOptOut $false -DistributionLists $teamSupportID -WelcomeMusicAudioFileID $audioFileSupportGreetingID -MusicOnHoldAudioFileID $audioFileSupportHoldInQueueMusicID -OverflowAction SharedVoicemail -OverflowActionTarget $teamSupportID -OverflowThreshold 200 -OverflowSharedVoicemailAudioFilePrompt $audioFileSupportSharedVoicemailGreetingID -EnableOverflowSharedVoicemailTranscription $true -TimeoutAction SharedVoicemail -TimeoutActionTarget $teamSupportID -TimeoutThreshold 2700 -TimeoutSharedVoicemailAudioFilePrompt $audioFileSupportSharedVoicemailGreetingID -EnableTimeoutSharedVoicemailTranscription $true -RoutingMethod LongestIdle -ConferenceMode $true -LanguageID “en-US”
````

### Support Queue – Create and Assign Resource Account
Note: Phone number not required here as call queue is front-ended by an Auto Attendant
#ApplicationID
#Auto Attendant: ce933385-9390-45d1-9512-c8d228074e07
#Call Queue: 11cd3e2e-fccb-42ad-ad00-878b93575e07
````
New-CsOnlineApplicationInstance -UserPrincipalName Support-RA@contoso.com -DisplayName "Support" -ApplicationID "11cd3e2e-fccb-42ad-ad00-878b93575e07"

Set-MsolUser -UserPrincipalName "Support-RA@contoso.com" -UsageLocation US

Set-MsolUserLicense -UserPrincipalName “Support-RA@contoso.com” -AddLicenses "contoso:PHONESYSTEM_VIRTUALUSER"

$applicationInstanceID = (Get-CsOnlineUser "Support-RA@contoso.com").ObjectID
$callQueueID = (Get-CsCallQueue -NameFilter "Support").Identity

New-CsOnlineApplicationInstanceAssociation -Identities @($applicationInstanceID) -ConfigurationID $callQueueID -ConfigurationType CallQueue
````

