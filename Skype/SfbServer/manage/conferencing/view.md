---
title: "View conferencing policies in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c1c0976e-2bfb-475b-9255-ed6b093d8798
description: "Summary: Learn how to view conferencing policies in Skype for Business Server."
---

# View conferencing policies in Skype for Business Server
 
**Summary:** Learn how to view conferencing policies in Skype for Business Server.
  
You can view conferencing policies by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
## View conferencing policies by using Skype for Business Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **Conferencing Policy**.
    
4. On the **Conferencing Policy** page, double-click the conferencing policy that you would like to view.
    
5. In **Edit File Filter**, select the **Show Details** check box.
    
    **Edit Conferencing Policy - \<policy\>** opens displaying the settings for the selected policy.
    
    For details about configuring the settings, see [Create conferencing policies in Skype for Business Server](create-policies.md).
    
## View conferencing policies by using Skype for Business Server Management Shell

To view conferencing policies, use the **Get-CsConferencingPolicy** cmdlet:
  
```
Get-CsConferencingPolicy
```

The cmdlet returns information such as the following:
  
<pre>
Identity                                  : Global
AllowIPAudio                              : True
AllowIPVideo                              : True
AllowMultiView                            : True
Description                               :
AllowParticipantControl                   : True
AllowAnnotations                          : True
DisablePowerPointAnnotations              : False
AllowUserToScheduleMeetingsWithAppSharing : True
AllowNonEnterpriseVoiceUsersToDialOut     : False
AllowAnonymousUsersToDialOut              : False
AllowAnonymousParticipantsInMeetings      : True
AllowExternalUsersToSaveContent           : True
AllowExternalUserControl                  : False
AllowExternalUsersToRecordMeeting         : False
AllowPolls                                : True
AllowSharedNotes                          : True
EnableDialInConferencing                  : True
EnableAppDesktopSharing                   : Desktop
AllowConferenceRecording                  : False
EnableP2PRecording                        : False
EnableFileTransfer                        : True
EnableP2PFileTransfer                     : True
EnableP2PVideo                            : True
AllowLargeMeetings                        : False
EnableDataCollaboration                   : True
MaxVideoConferenceResolution              : VGA
MaxMeetingSize                            : 250
AudioBitRateKb                            : 200
VideoBitRateKb                            : 50000
AppSharingBitRateKb                       : 50000
FileTransferBitRateKb                     : 50000
TotalReceiveVideoBitRateKb                : 6000
EnableMultiViewJoin                       : True
</pre>

For more information, including a complete syntax description and list of parameters, see [Get-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/get-csconferencingpolicy?view=skype-ps).
  

