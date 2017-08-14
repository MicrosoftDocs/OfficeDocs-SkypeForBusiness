---
title: New-CsConferencingPolicy
ms.prod: SKYPEFORBUSINESS
ms.assetid: f343bfcc-f296-4935-aa4c-94658dacace7
---



# New-CsConferencingPolicy
[]
Creates a new conferencing policy for use in your organization. Conferencing policies determine the features and capabilities that can be used in a conference; this includes everything from whether or not the conference can include IP audio and video to the maximum number of people who can attend a meeting. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsConferencingPolicy -Identity <XdsIdentity> [-AllowAnnotations <$true | $false>] [-AllowAnonymousParticipantsInMeetings <$true | $false>] [-AllowAnonymousUsersToDialOut <$true | $false>] [-AllowConferenceRecording <$true | $false>] [-AllowExternalUserControl <$true | $false>] [-AllowExternalUsersToRecordMeeting <$true | $false>] [-AllowExternalUsersToSaveContent <$true | $false>] [-AllowFederatedParticipantJoinAsSameEnterprise <$true | $false>] [-AllowIPAudio <$true | $false>] [-AllowIPVideo <$true | $false>] [-AllowLargeMeetings <$true | $false>] [-AllowMultiView <$true | $false>] [-AllowNonEnterpriseVoiceUsersToDialOut <$true | $false>] [-AllowOfficeContent <$true | $false>] [-AllowParticipantControl <$true | $false>] [-AllowPolls <$true | $false>] [-AllowQandA <$true | $false>] [-AllowSharedNotes <$true | $false>] [-AllowUserToScheduleMeetingsWithAppSharing <$true | $false>] [-ApplicationSharingMode <String>] [-AppSharingBitRateKb <Int64>] [-AudioBitRateKb <UInt32>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-DisablePowerPointAnnotations <$true | $false>] [-EnableAppDesktopSharing <None | SingleApplication | Desktop>] [-EnableDataCollaboration <$true | $false>] [-EnableDialInConferencing <$true | $false>] [-EnableFileTransfer <$true | $false>] [-EnableMultiViewJoin <$true | $false>] [-EnableOnlineMeetingPromptForLyncResources <$true | $false>] [-EnableP2PFileTransfer <$true | $false>] [-EnableP2PRecording <$true | $false>] [-EnableP2PVideo <$true | $false>] [-EnableReliableConferenceDeletion <$true | $false>] [-FileTransferBitRateKb <Int64>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaxMeetingSize <UInt32>] [-MaxVideoConferenceResolution <CIF | VGA>] [-Tenant <Guid>] [-TotalReceiveVideoBitRateKb <Int64>] [-VideoBitRateKb <Int64>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 uses the **New-CsConferencingPolicy** cmdlet to create a new conferencing policy with the Identity SalesConferencingPolicy. This policy will use all the default values for a conferencing policy except one: MaxMeetingSize; in this example, the maximum size for a meeting will be set to 50 instead of the default value of 250.
  
    
    

```

New-CsConferencingPolicy -Identity SalesConferencingPolicy -MaxMeetingSize 50
```


### EXAMPLE 2

In Example 2, the **New-CsConferencingPolicy** cmdlet is used to create a conferencing policy with the Identity site:Redmond. In this example two different property values are configured: MaxMeetingSize is set to 100 and AllowParticipantControl is set to False. All other policy properties will use the default values.
  
    
    

```
New-CsConferencingPolicy -Identity site:Redmond -MaxMeetingSize 100 -AllowParticipantControl $False
```


## Detailed Description

Conferencing is an important part of Skype for Business Server 2015: conferencing enables groups of users to come together online to view slides and video, share applications, exchange files, and otherwise communicate and collaborate. 
  
    
    
It's important for administrators to maintain control over conferences and conference settings. In some cases, there might be security concerns: by default, anyone, including unauthenticated users, can participate in meetings and save any of the slides or handouts distributed during those meetings. In other cases, there might be bandwidth concerns: having a multitude of simultaneous meetings, each involving hundreds of participants and each featuring video feeds and file sharing, has the potential to cause problems with your network. In addition, there might be occasional legal concerns. For example, by default meeting participants are allowed to make annotations on shared content; however, these annotations are not saved when the meeting is archived. If your organization is required to keep a record of all electronic communication, you might want to disable annotations.
  
    
    
Needing to manage conferencing settings is one thing; actually managing these settings is another. In Skype for Business Server 2015, conferences are managed by using conferencing policies. (In previous versions of the software, these were known as meeting policies.) As noted, conferencing policies determine the features and capabilities that can be used in a conference, including everything from whether or not the conference can include IP audio and video to the maximum number of people who can attend a meeting. Conferencing policies can be configured at the global scope; at the site scope; or at the per-user scope. This provides administrators with enormous flexibility when it comes to deciding which capabilities will be made available to which users. 
  
    
    
The **New-CsConferencingPolicy** cmdlet enables you to create new conferencing policies at either the site or the per-user scope. You cannot create a new global policy because the global policy already exists. However, you can modify the property values of the global policy by using the **Set-CsConferencingPolicy** cmdlet.
  
    
    

> [!NOTE]
>  Video conferencing resolution is version dependent. Video resolution parameters are applicable as follows.>  _TotalReceiveVideoBitRateKb_: Used in Lync Server 2013 and later versions. >  _VideoBitRateKb_: Used in Lync Server 2013 and later versions. >  _MaxVideoConferenceResolution_: Not supported for Lync Server 2013 or later clients, in Lync Server 2013 or later conferences. The  _MaxVideoConferenceResolution_ parameter determines the maximum resolution allowed for legacy clients in conferences organized by users who are homed on Lync Server 2013 or later.
  
    
    


## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the conferencing policy to be created. Conferencing policies can be created at the site or per-user scopes. To create a site policy, use syntax similar to this:  `-Identity site:Redmond`. To create a per-user policy, use syntax similar to this:  `-Identity SalesConferencingPolicy`.  <br/> |
| _AllowAnnotations_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not participants are allowed to make on-screen annotations on any content shared during the meeting; in addition, this setting determines whether or not whiteboarding is allowed in the conference. The default value is True.  <br/> Note that annotations are not archived along with other meeting content.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will include annotations. However, the user can participate in other conferences where annotations are allowed.  <br/> |
| _AllowAnonymousParticipantsInMeetings_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether anonymous users are allowed to participate in the meeting. If set to False then only authenticated users (that is, users logged on to your Active Directory Domain Services or the Active Directory of a federated partner) are allowed to attend the meeting. The default value is True.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow anonymous participants. However, the user can take part in other conferences where anonymous participants are allowed.  <br/> |
| _AllowAnonymousUsersToDialOut_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not anonymous users (unauthenticated users) are allowed to join a conference using dial-out phoning. With dial-out phoning, the conferencing server telephones the user; when the user answers the phone, he or she will be joined to the conference.  <br/> Note that dial-in conferencing is allowed even if this setting is False.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow anonymous participants to join the conference via dial-out phoning. However, the user can take part in other conferences where anonymous users can join via dial out.  <br/> The default value is False.  <br/> |
| _AllowConferenceRecording_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether users are allowed to record the meeting. The default value is False.  <br/> This setting applies to all users taking part in the conference.  <br/> |
| _AllowExternalUserControl_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether external users (either anonymous users or federated users) are allowed to take control of shared applications or desktops. The default value is False.  <br/> This setting is enforced at the per-user level, and for both conferences and peer-to-peer communication sessions. That means that some users in a session might be allowed to give up control of a shared application or desktop to an external user while other users might not be allowed to give up control.  <br/> |
| _AllowExternalUsersToRecordMeeting_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether external users (either anonymous users or federated users) are allowed to record the meeting. The default value is False.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow external users to record conferences. However, the user can take part in other conferences where external users are allowed to record meetings.  <br/> Note that this setting takes effect only if the AllowConferenceRecording property is set to True.  <br/> |
| _AllowExternalUsersToSaveContent_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether external users (that is, users not currently logged-on to your network) are allowed to save handouts, slides, and other meeting content. The default value is True.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow external users to save content. However, the user can take part in other conferences where external users are allowed to save content.  <br/> |
| _AllowFederatedParticipantJoinAsSameEnterprise_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True), allows federated meeting participants to join the meeting as though they were internal users rather than external users.  <br/> |
| _AllowIPAudio_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not computer audio is allowed in the meeting. The default value is True.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow IP audio. However, the user can take part in other conferences where IP audio is allowed.  <br/> |
| _AllowIPVideo_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not computer video is allowed in the meeting. The default value is True.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow IP video. However, the user can take part in other conferences where IP video is allowed.  <br/> |
| _AllowLargeMeetings_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, all online meetings are treated as "large meeting." With a large meeting, restrictions are placed on the number of notifications that are sent to participants as well as the size of the meeting roster that is transmitted by default.  <br/> The default value is False ($False).  <br/> |
| _AllowMultiView_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) enables users to schedule conferences that allow multiview; that is, clients can receive multiple video streams during a given conference. This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy can include multiview. However, the user can participate in other conferences where multiview is allowed.  <br/> |
| _AllowNonEnterpriseVoiceUsersToDialOut_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or users who have not been enabled for Enterprise Voice are allowed to join a conference using dial-out phoning. With dial-out phoning the conferencing server will telephone the user; when the user answers the phone, he or she will be joined to the conference.  <br/> Note that dial-in conferencing is allowed even when this setting is False.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow users who have not been enabled for Enterprise Voice to join the conference via dial-out phoning. However, the user can take part in other conferences where users who have not been enabled for Enterprise Voice can join via dial out.  <br/> The default value is False ($False).  <br/> |
| _AllowOfficeContent_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to False, prevents users from using Office content in their conferences.  <br/> |
| _AllowParticipantControl_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not meeting participants are allowed to take control of applications or desktops shared during the meeting. The default value is True.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow participant control. However, the user can take part in other conferences where participant control is allowed.  <br/> |
| _AllowPolls_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not users are allowed to conduct online polls during a meeting. The default value is True.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow polls. However, the user can take part in other conferences where polls are allowed.  <br/> |
| _AllowQandA_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) the user will be able to include the Questions and Answers Manager in any online conference that he or she organizes. When set to False, the user will be prohibited from including Questions and Answers Manager in any of his or her conferences.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow the use of the Questions and Answers Manager. However, the user can make use of the Questions and Answers Manager in other conferences where polls are allowed.  <br/> |
| _AllowSharedNotes_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) any open OneNote notebooks linked to the conference will automatically be updated with information such as conference participants and details about content shared during the conference.  <br/> |
| _AllowUserToScheduleMeetingsWithAppSharing_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not users are allowed to organize meetings that include application sharing. The default value is True.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow application sharing. However, the user can take part in other conferences where application sharing is allowed.  <br/> |
| _ApplicationSharingMode_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _AppSharingBitRateKb_ <br/> |Optional  <br/> |System.Int64  <br/> |Bit rate (in kilobits) used for application sharing. The default value is 50000.  <br/> |
| _AudioBitRateKb_ <br/> |Optional  <br/> |System.UInt32  <br/> |Bit rate (in kilobits) used for audio transmissions. The audio bit rate can be any whole number between 20 and 200, inclusive; the default value is 200.  <br/> This setting is enforced at the per-user level, and for both conferences and peer-to-peer communication sessions.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provider explanatory text about the conferencing policy. For example, the Description might indicate the users the policy should be assigned to.  <br/> |
| _DisablePowerPointAnnotations_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True) users will not be able to add annotations to PowerPoint slides used in a conference. However (depending on the value of the AllowAnnotations property), users will still have access to other whiteboarding features. The default value is False, meaning that PowerPoint annotations are allowed.  <br/> |
| _EnableAppDesktopSharing_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Policy.Meeting.EnableAppDesktopSharing  <br/> |Indicates whether participants are allowed to share applications (or their desktop) during the course of a meeting. Allowed values are:  <br/> Desktop. Users are allowed to share their entire desktop.  <br/> SingleApplication. Users are allowed to share a single application.  <br/> None. Users are not allowed to share applications or their desktop.  <br/> This setting is enforced at the per-user level. That means that some users in a conference might be allowed to share their desktop or applications while other users in the same conference might not be allowed to do so.  <br/> The default value is Desktop.  <br/> |
| _EnableDataCollaboration_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether users can organize meetings that include data collaboration activities such as whiteboarding and annotations.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow data collaboration. However, the user can take part in other conferences where data collaboration is allowed.  <br/> |
| _EnableDialInConferencing_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether users are able to join the meeting by dialing in with a public switched telephone network (PSTN) telephone. The default value is True.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow dial-in conferencing. However, the user can take part in other conferences where dial-in conferencing is allowed.  <br/> |
| _EnableFileTransfer_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether file transfers to all the meeting participants are allowed during the meeting. The default value is True.  <br/> This setting applies to the user who organizes the conference: if set to False, no conference created by a user affected by this policy will allow file transfers. However, the user can take part in other conferences where file transfers are allowed.  <br/> |
| _EnableMultiViewJoin_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) clients will attempt to join a conference using multiview (which allows the client to receive multiple video streams during the conference). This parameter will be ignored if multiview is not allowed in the conference being joined. This setting is enforced at the per-user level, and for both conferences and peer-to-peer communication sessions. That means that some users in a session might be allowed to have multiple video streams while other users in the same conference might not.  <br/> |
| _EnableOnlineMeetingPromptForLyncResources_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, users will be prompted any time they schedule a meeting in Outlook that includes invitees (such as a meeting room) that would benefit from having the meeting held online. The default value is False.  <br/> |
| _EnableP2PFileTransfer_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether peer-to-peer file transfers (that is, file transfers that do not involve all participants) are allowed during the meeting. The default value is True.  <br/> This setting is enforced at the per-user level. That means that one user in a peer-to-peer communication session might be allowed to transfer files while the other user is not.  <br/> |
| _EnableP2PRecording_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, users will be able to record peer-to-peer conferencing sessions. The default value is False.  <br/> This setting is enforced at the per-user level. That means that one user in a peer-to-peer communication session might be allowed to record the session while the other user is not.  <br/> |
| _EnableP2PVideo_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, users will be able to take part in peer-to-peer video conferencing sessions. The default value is False.  <br/> This setting is enforced at the per-user level. That means that one user in a peer-to-peer communication session might be allowed to use video the session while the other user is not.  <br/> |
| _EnableReliableConferenceDeletion_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _FileTransferBitRateKb_ <br/> |Optional  <br/> |System.Int64  <br/> |Bit rate (in kilobits) used for file transfers. The default value is 50000.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-<cmdlet>**. <br/> |
| _MaxMeetingSize_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum number of people who are allowed to attend a meeting. After the maximum number of participants has been reached, anyone else who tries to join the meeting will be turned away with the notice that the meeting is full.  <br/> Meeting sizes should be limited to a value between 2 and 250. You can't set it to less than 2 which means that everyone is at least allowed to initiate a peer-to-peer session but you should never set it higher than 250.  <br/> |
| _MaxVideoConferenceResolution_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Policy.Meeting.MaxVideoConferenceResolution  <br/> | This parameter specifies the maximum resolution allowed for legacy clients in conferences organized by users who are homed on Lync Server 2013 or later. <br/>  Allowed values are: <br/> **CIF**: Common Intermediate Format (CIF) has a resolution of 352 pixels by 288 pixels. <br/> **VGA**: VGA has a resolution of 640 pixels by 480 pixels. <br/>  The default value is VGA. <br/> > [!NOTE]>  Conference video resolution parameters and support are version dependent. See the note in Detailed description.          |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for whom the new conferencing policy is being created. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _TotalReceiveVideoBitRateKb_ <br/> |Optional  <br/> |System.Int64  <br/> |Indicates the maximum allowed bitrate (in kilobytes per second) for all the video used in a conference; that is, the combined total for all the video streams. The default value is 50000 kilobytes per second.  <br/> > [!NOTE]> Conference video resolution parameters and support are version dependent. See the note in Detailed description.           |
| _VideoBitRateKb_ <br/> |Optional  <br/> |System.Int64  <br/> |Bit rate (in kilobits) used for video transmissions. The default value is 50000.  <br/> This setting is enforced at the per-user level, and for both conferences and peer-to-peer communication sessions.  <br/> > [!NOTE]> Conference video resolution parameters and support are version dependent. See the note in Detailed description.           |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None. The **New-CsConferencingPolicy** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **New-CsConferencingPolicy** cmdlet creates a new instance of the Microsoft.Rtc.Management.WritableConfig.Policy.Meeting.MeetingPolicy object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsConferencingPolicy](get-csconferencingpolicy.md)
  
    
    
 [Grant-CsConferencingPolicy](grant-csconferencingpolicy.md)
  
    
    
 [Remove-CsConferencingPolicy](remove-csconferencingpolicy.md)
  
    
    
 [Set-CsConferencingPolicy](set-csconferencingpolicy.md)
