---
title: Create a custom meeting template in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: ralphmaamari
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
appliesto: 
  - Microsoft Teams
description: Learn how Microsoft Teams administrators can create a custom meeting template.
---

# Create a custom meeting template in Microsoft Teams

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]



For each option in the template, you can define the following:

- **Default value** - This is the value that is applied to a meeting when the template is used.
- **Visible** - This determines if the meeting organizer can see this setting in the meeting options. 
- **Lock status** - This determines if the meeting organizer can change the setting that was set by the template. If the setting is locked, the meeting organizer can't change it.

#### Security


|Setting|Description|
|:------|:----------|
|Sensitivity label|Specifies the meeting sensitivity label to be used for the meeting. Note that the sensitivity label may override certain settings in the template.|
|Who can bypass the lobby?|Specifies who can bypass the lobby and join the meeting directly.|
|People calling in by phone can bypass the lobby|Specifies if people calling in by phone can bypass the lobby and join the meeting directly.|
|Notify when callers join and leave|Specify if you want a sound to play when people calling in by phone join or leave the meeting.|
|Enable meeting end-to-end encrpytion|Specify if you want the meeting to use end-to-end encryption. Recording and transcription won't work if this is on.|



#### Audio and video

|Setting|Description|
|:------|:----------|
|Disable mic for attendees?|When **Off**, attendees can unmute.|
|Disable camera for attendees?|When **Off**, attendees can turn on their cameras.|


#### Recording and transcription

|Setting|Description|
|:------|:----------|
|Record meetings automatically|When **On** meetings are recorded automatically.|
|Who can record meetings?|Specifies whether meetings can be recorded by organizers only or by organizers and presenters.|
|Enable watermark for screenshare|Specifies if a watermark is overlaid on content that is shared on screen in the meeting.|
|Enable watermark for video|Specifies if a watermark is overlaid on attendees video feeds in the meeting.|



#### Meeting Engagement

|Setting|Description|
|:------|:----------|
|Attendees can chat|Specifies if the meeting chat is available. Can also be used to prevent chat before and after the meeting.|
|Attendees can use reactions|Specifies if attendees can use reactions in the meeting. This must be **On** for the raise hand feature to work.|
|Enable Q&A|Specifies if attendees can use the Q&A feature to ask questions during the meeting.|
|Manage what attendees see|When **On**, meeting organizers can preview and approve content being shared on screen before other meeting participants can see it.|






To create a custom meeting template

1. In the Teams admin center, expand **Meetings** and select **Meeting templates**.
1. Select **Add**
1. Type a name and description for the template.
1. Choose the settings that you want to use for this template.
1. To prevent the meeting organizer from changing a setting, select the setting and then select **lock**.
1. To prevent the meeting organizer from seeing a setting, select the setting and then select **Hide**.
1. Select **Save**.

## Related topics

[Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)

[Use Teams meeting templates, sensitivity labels, and admin policies together](meeting-templates-sensitivity-labels-policies.md)
