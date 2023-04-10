---
title: Predefined meeting templates included with Microsoft Teams Premium
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: ralphmaamari
ms.date: 04/10/2023
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365initiative-meetings
  - Tier2
appliesto: 
  - Microsoft Teams
description: See a list of meeting templates and their settings included with Microsoft Teams Premium.
---

# Predefined meeting templates included with Microsoft Teams Premium

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

The following predefined meeting templates are included with Teams Premium

<!---
Template
|Option|Default value|Visibility|Lock status|
|:-----|:------------|:---------|:----------|
|***Security***||||
|Apply sensitivity label||||
|Lobby||||
|People calling in by phone can bypass the lobby||||
|Enable meeting end-to-end encryption||||
|Enable watermark for screenshare||||
|Enable watermark for video||||
|***Audio and video***||||
|Enable mic for attendees||||
|Enable camera for attendees||||
|***Recording and transcription***||||
|Record meetings automatically||||
|Who can record meetings||||
|***Roles***||||
|Notify when callers join and leave||||
|***Meeting engagement***||||
|Allow meeting chat||||
|Allow reactions||||
|Enable Q&A||||
|Manage what attendees see||||
--->



## Virtual appointment

|Option|Default value|Visibility|Lock status|
|:-----|:------------|:---------|:----------|
|***Security***|None|Visible|Unlocked|
|Apply sensitivity label|Everyone|Visible|Unlocked|
|Lobby|Off|Visible|Unlocked|
|People calling in by phone can bypass the lobby|Off|Visible|Unlocked|
|Enable meeting end-to-end encryption|Off|Visible|Unlocked|
|Enable watermark for screenshare|Off|Visible|Unlocked|
|Enable watermark for video|Off|Visible|Unlocked|
|***Audio and video***||||
|Enable mic for attendees|On|Visible|Unlocked|
|Enable camera for attendees|On|Visible|Unlocked|
|***Recording and transcription***||||
|Record meetings automatically|Off|Visible|Unlocked|
|Who can record meetings|Only organizers and co-organizers|Visible|Unlocked|
|***Roles***||||
|Notify when callers join and leave|Off|Visible|Unlocked|
|***Meeting engagement***||||
|Allow meeting chat|On during the meeting only|Visible|Unlocked|
|Allow reactions|Off|Visible|Unlocked|
|Enable Q&A|Off|Visible|Unlocked|
|Manage what attendees see|Off|Visible|Unlocked|


#### Security

|Option|Default value|Visibility|Lock status|
|:-----|:------------|:---------|:----------|
|Apply sensitivity label||||
|Lobby||||
|People calling in by phone can bypass the lobby||||
|Enable meeting end-to-end encryption||||
|Enable watermark for screenshare||||
|Enable watermark for video||||

#### Audio and video

|Option|Default value|Visibility|Lock status|
|:-----|:------------|:---------|:----------|
|Enable mic for attendees||||
|Enable camera for attendees||||



#### Security

|Setting|Description|
|:------|:----------|
|Sensitivity label|Specifies the meeting sensitivity label to be used for the meeting. Note that the sensitivity label may override certain settings in the template.|
|Who can bypass the lobby?|Specifies who can bypass the lobby and join the meeting directly.|
|People dialing in can bypass the lobby|Specifies if people calling in by phone can bypass the lobby and join the meeting directly.|
|Enable meeting end-to-end encryption|Specify if you want the meeting to use end-to-end encryption. Recording and transcription won't work if this is on.|
|Apply a watermark to shared content|Specifies if a watermark is overlaid on content that is shared on screen in the meeting.|
|Apply a watermark to everyone's video feed|Specifies if a watermark is overlaid on attendees video feeds in the meeting.|

#### Audio and video

|Setting|Description|
|:------|:----------|
|Allow mic for attendees|When **On**, attendees can unmute.|
|Allow camera for attendees|When **On**, attendees can turn on their cameras.|

#### Recording and transcription

|Setting|Description|
|:------|:----------|
|Record meetings automatically|When **On** meetings are recorded automatically.|
|Who can record meetings?|Specifies whether meetings can be recorded by organizers only or by organizers and presenters.|

#### Roles

|Setting|Description|
|:------|:----------|
|Notify when callers join and leave|Specify if you want a sound to play when people calling in by phone join or leave the meeting.|

#### Meeting Engagement

|Setting|Description|
|:------|:----------|
|Attendees can chat|Specifies if the meeting chat is available. Can also be used to prevent chat before and after the meeting.|
|Attendees can use reactions|Specifies if attendees can use reactions in the meeting. This must be **On** for the raise hand feature to work.|
|Enable Q&A|Specifies if attendees can use the Q&A feature to ask questions during the meeting.|
|Manage what attendees see|When **On**, meeting organizers can preview and approve content being shared on screen before other meeting participants can see it.|

## Related topics

[Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)

[Use Teams meeting templates, sensitivity labels, and admin policies together](meeting-templates-sensitivity-labels-policies.md)

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)
