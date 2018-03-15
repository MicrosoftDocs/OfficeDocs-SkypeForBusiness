---
title: "View conferencing policy information in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e99fdc4d-926a-4e36-ac99-ab5035568847
description: "In Lync Server 2013 Control Panel, you use conferencing policies to control how conferencing is implemented in your deployment. This includes the following conferencing policies:"
---

# View conferencing policy information in Lync Server 2013
[]
In Lync Server 2013 Control Panel, you use conferencing policies to control how conferencing is implemented in your deployment. This includes the following conferencing policies:
  
- A global policy that is created by default when you deploy Lync Server 2013.
    
- Optional site-level and user-level policy that you can create and use to specify how conferencing is implemented for specific sites or users.
    
### To view conferencing policy settings

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Conferencing** and then click **Conferencing Policy**.
    
4. On the **Conferencing Policy** page, double-click the conferencing policy that you would like to view. 
    
5. In **Edit File Filter**, select the **Show Details…** check box. 
    
    **Edit Conferencing Policy - \<policy\>** opens displaying the settings for the selected policy. For details about configuring the settings, see [Create or modify a conferencing policy in Lync Server 2013](create-or-modify-a-conferencing-policy.md).
    
## Viewing Conferencing Policies by Using Windows PowerShell Cmdlets

Conferencing policies can be viewed by using Windows PowerShell and the Get-CsConferencingPolicy cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view conferencing policies

- To view information about all your conferencing policies, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsConferencingPolicy
  ```

    That will return information similar to this:
    
  ```
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
  
  ```

For more information, see the help topic for the [Get-CsConferencingPolicy](get-csconferencingpolicy.md) cmdlet. 
  

