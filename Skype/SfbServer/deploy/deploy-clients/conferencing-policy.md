---
title: "Conferencing policy for Skype Room System accounts"
ms.author: v-lanac
author: lanachin
manager: serdars
ms.reviewer: davgroom
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 4dd8be28-5156-411b-8ccd-eff7f75cb897
description: "Read this topic to learn how to assign conferencing policies for Skype Room System accounts."
---

# Conferencing policy for Skype Room System accounts
 
Read this topic to learn how to assign conferencing policies for Skype Room System accounts.
  
## Conferencing policy features

The conferencing policy assigned to the Skype Room System account must have certain characteristics. Most of the time, the Skype Room System client joins a scheduled meeting, and therefore the conferencing policy of the meeting organizer will affect the conference. However, in Skype for Business Server, certain capabilities depend on the participant's configuration. For example, if the participant's policy allows a maximum video resolution of 1080p, the participants will experience this higher resolution video capability in the conference even if the organizer's policy doesn't allow it. The following table describes several such settings which you should be aware of when setting up conferencing policies for Skype Room System accounts in your organization. 
  
|Feature  <br/> |Value  <br/> |Comment  <br/> |
|:-----|:-----|:-----|
|AllowIPAudio  <br/> |TRUE  <br/> |Must be true for Skype Room System audio  <br/> |
|AllowIPVideo  <br/> |TRUE  <br/> |Must be true for Skype Room System audio to work in Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|AllowMultiView  <br/> |TRUE  <br/> |Allows Skype Room System to render multi-view, multiple video streams  <br/> |
|AllowParticipantControl  <br/> |TRUE  <br/> |Affects Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|AllowAnnotations  <br/> |TRUE  <br/> |Affects Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|DisablePowerPointAnnotations  <br/> |FALSE  <br/> |Affects Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|AllowUserToScheduleMeetingsWithAppSharing  <br/> |TRUE  <br/> |Affects Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|AllowNonEnterpriseVoiceUsersToDialOut  <br/> |FALSE  <br/> |Depends on whether the account is Enterprise Voice (EV) enabled (see the Enabling Skype Room System Accounts for Skype for Business section)  <br/> |
|AllowAnonymousUsersToDialOut  <br/> |FALSE  <br/> |Depends on whether the account is Enterprise Voice (EV) enabled  <br/> |
|AllowAnonymousParticipantsInMeetings  <br/> |TRUE  <br/> |Affects Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|AllowExternalUsersToSaveContent  <br/> |TRUE  <br/> |Affects Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|AllowExternalUserControl  <br/> |FALSE  <br/> |Affects Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|AllowExternalUsersToRecordMeeting  <br/> |FALSE  <br/> |Affects Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|AllowPolls  <br/> |TRUE  <br/> |N/A in Meet Now (ad hoc) meetings, but Skype Room System can respond to polls on the screen at the front of room  <br/> |
|AllowSharedNotes  <br/> |TRUE  <br/> |N/A in Meet Now (ad hoc) meetings, but Skype Room System can respond to polls on the screen at the front of room  <br/> |
|EnableDialInConferencing  <br/> |TRUE  <br/> |Affects Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|EnableAppDesktopSharing  <br/> |Desktop  <br/> |Affects Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|AllowConferenceRecording  <br/> |FALSE  <br/> |N/A for Skype Room System. If TRUE, a remote party could record  <br/> |
|EnableP2PRecording  <br/> |FALSE  <br/> |N/A for Skype Room System. If TRUE, a remote party could record  <br/> |
|EnableFileTransfer  <br/> |TRUE  <br/> |N/A  <br/> |
|EnableP2PFileTransfer  <br/> |TRUE  <br/> |N/A  <br/> |
|EnableP2PVideo  <br/> |TRUE  <br/> |Enables the Skype Room System client to participate in peer-to-peer video sessions  <br/> |
|AllowLargeMeetings  <br/> |FALSE  <br/> |N/A  <br/> |
|EnableDataCollaboration  <br/> |TRUE  <br/> |Affects Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|MaxVideoConferenceResolution  <br/> |VGA  <br/> |Ignored by Skype for Business Server, Skype Room System uses HD1080  <br/> |
|MaxMeetingSize  <br/> |250  <br/> |Affects Meet Now (ad hoc) whiteboard sessions in Skype Room System  <br/> |
|AudioBitRateKb  <br/> |200  <br/> |See note at the end of the table\*  <br/> |
|VideoBitRateKb  <br/> |5000  <br/> |This is the maximum outbound video bit rate allowed. Skype Room System can send one 1080 stream along with pano (if RoundTable is used) at this bit rate. \*  <br/> |
|AppSharingBitRateKb  <br/> |5000  <br/> |See note at the end of the table\*  <br/> |
|FileTransferBitRateKb  <br/> |5000  <br/> |N/A  <br/> |
|TotalReceiveVideoBitRateKb  <br/> |20000  <br/> |We recommend that you set this as high as possible. The effective bandwidth depends on network conditions at the time of conferences.\*  <br/> |
|EnableMultiViewJoin  <br/> |TRUE  <br/> |Must be TRUE for Skype Room System to ensure multi-view video streams  <br/> |
   
* For information about bandwidth planning, see [Network bandwidth requirements for media traffic](../../plan-your-deployment/network-requirements/network-requirements.md#network-bandwidth-requirements-for-media-traffic).
  
> [!NOTE]
> If the Skype Room System client tries to join a scheduled meeting organized by a user who is homed on a Lync Server 2010 pool, the meeting organizer's conferencing policy could prevent the Skype Room System client from performing collaboration. 
  
## Meeting authentication

Skype Room System prompts users for authentication when they use the meeting join link to join a restricted meeting; for example, a meeting for which meeting lobby options have been configured in Outlook. This setting is always on for customized meetings, and users are always prompted. However, for unrestricted meetings, users can join the meeting without authentication. 
  
The following command enables administrators to require authentication for all meetings, including unrestricted meetings: 
  
```
Set-CsMeetingConfiguration -RequireRoomSystemsAuthorization $TRUE
```

By default, RequireRoomSystemsAuthorization is FALSE. 
  

