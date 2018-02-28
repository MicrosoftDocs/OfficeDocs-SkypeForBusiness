---
title: "Manage conferencing in Skype for Business Server 2015"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 825e051c-83a5-420d-a5ef-f77afa368e2e
description: "Summary: Learn how to manage conferencing in Skype for Business Server 2015."
---

# Manage conferencing in Skype for Business Server 2015
[]
 **Summary:** Learn how to manage conferencing in Skype for Business Server 2015.
  
This topic describes how to manage conferencing. For more information about how to plan and deploy conferencing, see [Plan for conferencing in Skype for Business Server 2015](../../plan-your-deployment/conferencing/conferencing.md) and[Deploy conferencing in Skype for Business Server 2015](../../deploy-1/deploy-conferencing/deploy-conferencing.md).
  
In Skype for Business Server, you manage the details of conferencing by specifying configuration and policy settings as follows. Note that the terms conferencing and meeting are sometimes used interchangeably. But, in general, you can think of a meeting as a specific instance of conferencing.
  
- **Conferencing policy settings** encompass a wide variety of scheduling and participation options, ranging from whether a meeting can include IP audio and video to the maximum number of people who can attend. You can use conferencing policies to manage security, bandwidth, and legal aspects of meetings.
    
    Note that conferencing policies are applied to the user or site and cannot be applied to a specific meeting. Therefore, the meeting invitation for the conference can be created some weeks in advance, but the restrictive conferencing policy should be applied to the Meeting Organizer's Skype for Business account just before the conference starts. 
    
    If a dedicated account is used for the Meeting Organizer role, the conferencing policy can remain assigned to that account. If the Meeting Organizer uses a general Skype for Business account, the policy must be removed after the conference is finished.
    
- **Meeting configuration settings** dictate the type of meetings that users can create, in addition to controlling how (or even if) anonymous users and dial-in conferencing users can join these meetings. Note that these settings only affect scheduled meetings. Meeting configurations are applied per pool, per site, or globally.
    
- **Conferencing configuration settings** determine such things as the maximum allowed size for meeting content and handouts; maximum amount of bandwidth for the Application Sharing Conferencing service; storage limits and expiration periods; the URLs for the internal and external downloads of the supported client; pointers to internal and external URLs where users can obtain conferencing help and resources; and the ports used for application sharing, client audio, file transfers, and media traffic.
    
    These settings allow you to manage the actual servers themselves. These settings can only be set by using Skype for Business Server Management Shell. 
    
- **Dial-in access settings** allow you to define information about whether and how users dial in from a phone. You specify some of the dial-in access information, such as access number, from the Control Panel Conferencing tab and some dial-in information--such as dial plan, voice policy, route, and PSTN usage--from the Control Panel Voice Routing tab.
    
- **PIN policy settings** allow you to name and define the PIN that participants use for dial-in access.
    
## Manage conferencing by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell

You can manage most conferencing policies and configuration settings by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell. Some configuration settings are available only by using Skype for Business Server Management Shell.
  
- To manage conferencing policy settings:
    
  - In Control Panel, select **Conferencing | Conferencing Policy**.
    
  - In PowerShell, search for the **-CsConferencingPolicy** cmdlets.
    
- To manage meeting configuration settings:
    
  - In Control Panel, select **Conferencing | Meeting configuration**.
    
  - In Skype for Business Server Management Shell, search for the **-CsMeetingConfiguration** cmdlets.
    
- To manage dial-in access number settings:
    
  - In Control Panel, select **Conferencing | Dial-in access number**.
    
  - In Skype for Business Server Management Shell, search for the **-CsDialInConferencing** cmdlets.
    
- To manage dial-in access information, such as dial plan, voice policy, route, and PSTN usage: 
    
  - In Control Panel, select **Conferencing | Voice routing**.
    
  - In Skype for Business Server Management Shell, search for the **-CsDialPlan** and **-CsVoice** cmdlets.
    
- To manage PIN policy settings:
    
  - In Control Panel, select **Conferencing | PIN policy**.
    
  - In Skype for Business Server Management Shell, search for the **-CsPinPolicy** cmdlets.
    
- To manage conferencing configuration settings, you must use the Skype for Business Server Management Shell. Search for **-CsConferencingConfiguration** cmdlets.
    
## Skype for Business Server Management Shell cmdlets

You can use the following Skype for Business Server Management Shell cmdlets to manage conferencing: 
  
**Conferencing policy settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsConferencingPolicy](../../manage/management-shell/get-csconferencingpolicy.md) <br/> |Returns information about the conferencing policies that have been configured for use in your organization. Conferencing policies determine the features and capabilities that can be used in a conference; this includes everything from whether or not the conference can include IP audio and video to the maximum number of people who can attend a meeting.  <br/> |
|[Grant-CsConferencingPolicy](../../manage/management-shell/grant-csconferencingpolicy.md) <br/> |Assigns a conferencing policy at the per-user scope.  <br/> |
|[New-CsConferencingPolicy](../../manage/management-shell/new-csconferencingpolicy.md) <br/> |Creates a new conferencing policy for use in your organization.  <br/> |
|[Remove-CsConferencingPolicy](../../manage/management-shell/remove-csconferencingpolicy.md) <br/> |Removes the specified conferencing policy.  <br/> |
|[Set-CsConferencingPolicy](../../manage/management-shell/set-csconferencingpolicy.md) <br/> |Modifies an existing conferencing policy.  <br/> |
   
**Meeting configuration settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsMeetingConfiguration](../../manage/management-shell/get-csmeetingconfiguration.md) <br/> |Returns information about the meeting configuration settings currently in use in your organization. Meeting configuration settings help dictate the type of meetings that users can create, and control how (or even if) anonymous users and dial-in conferencing users can join these meetings.  <br/> |
|[New-CsMeetingConfiguration](../../manage/management-shell/new-csmeetingconfiguration.md) <br/> |Creates a new collection of meeting configuration settings at the site or service scope. Note that these settings only affect scheduled meetings; they do not affect ad-hoc meetings created by clicking the Meet Now option in Skype for Business.  <br/> |
|[Remove-CsMeetingConfiguration](../../manage/management-shell/remove-csmeetingconfiguration.md) <br/> |Deletes an existing collection of meeting configuration settings.  <br/> |
|[Set-CsMeetingConfiguration](../../manage/management-shell/set-csmeetingconfiguration.md) <br/> |Modifies the meeting configuration settings currently in use in your organization.  <br/> |
   
**Conferencing configuration settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsConferencingConfiguration](../../manage/management-shell/get-csconferencingconfiguration.md) <br/> |Returns information about the conference configuration settings for your organization. Conference settings determine such things as the maximum-allowed size for conference content and handouts, the content grace period (that is, the amount of time content will be stored before being deleted), and the URLs for the internal and external downloads of the supported client.  <br/> |
|[New-CsConferencingConfiguration](../../manage/management-shell/new-csconferencingconfiguration.md) <br/> |Creates a new collection of conference configuration settings.  <br/> |
|[Remove-CsConferencingConfiguration](../../manage/management-shell/remove-csconferencingconfiguration.md) <br/> |Removes the specified collection of conference configuration settings.  <br/> |
|[Set-CsConferencingConfiguration](../../manage/management-shell/set-csconferencingconfiguration.md) <br/> |Modifies an existing collection of conferencing configuration settings.  <br/> |
   
**Dial-in configuration settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsConferenceDirectory](../../manage/management-shell/get-csconferencedirectory.md) <br/> |Returns information about the conference directories configured for use in your organization. Conference directories are used to help dial-in conferencing users locate conference information.  <br/> |
|[Get-CsDialInConferencingConfiguration](../../manage/management-shell/get-csdialinconferencingconfiguration.md) <br/> |Retrieves information about how Skype for Business Server responds when users join or leave a dial-in conference.  <br/> |
|[Get-CsDialInConferencingAccessNumber](../../manage/management-shell/get-csdialinconferencingaccessnumber.md) <br/> |Returns information about all the dial-in conferencing access numbers configured for use in your organization.  <br/> |
|[Get-CsDialInConferencingDtmfConfiguration](../../manage/management-shell/get-csdialinconferencingdtmfconfiguration.md) <br/> |Returns the dual-tone multifrequency (DTMF) signaling settings used for dial-in conferencing. DTMF enables users who dial in to a conference to control conference settings (such as muting and unmuting themselves or locking and unlocking the conference) by using the keypad on their telephone.  <br/> |
|[Get-CsDialInConferencingLanguageList](../../manage/management-shell/get-csdialinconferencinglanguagelist.md) <br/> |Returns a list of languages, including regional/minority languages, supported for use with Skype for Business Server dial-in conferences. These languages are used to relay audio messages and instructions to users participating in a conference by using a telephone.  <br/> |
|[Get-CsDialPlan](../../manage/management-shell/get-csdialplan.md) <br/> |Returns information about the dial plans used in your organization.  <br/> |
|[Grant-CsDialPlan](../../manage/management-shell/grant-csdialplan.md) <br/> |Assigns a dial plan to one or more users or groups.  <br/> |
|[Import-CsLegacyConferenceDirectory](../../manage/management-shell/import-cslegacyconferencedirectory.md) <br/> |Imports conference directories from Microsoft Office Communications Server 2007 R2 to Skype for Business Server. This helps provide interoperability between Skype for Business Server and Office Communications Server 2007 R2.  <br/> |
|[Move-CsConferenceDirectory](../../manage/management-shell/move-csconferencedirectory.md) <br/> |Moves an existing conference directory from one pool to another. Conference directories are used to help dial-in conferencing users locate conference information.  <br/> |
|[New-CsConferenceDirectory](../../manage/management-shell/new-csconferencedirectory.md) <br/> |Creates a new conference directory for use in your organization. Conference directories are used to help dial-in conferencing users locate conference information.  <br/> |
|[New-CsDialInConferencingAccessNumber](../../manage/management-shell/new-csdialinconferencingaccessnumber.md) <br/> |Creates a new dial-in conferencing access number.  <br/> |
|[New-CsDialInConferencingConfiguration](../../manage/management-shell/new-csdialinconferencingconfiguration.md) <br/> |Creates a new collection of dial-in conferencing configuration settings. These settings determine how Skype for Business Server responds when users join or leave a dial-in conference. In particular, information is returned regarding whether or not participants are required to record their name when joining a conference, and how (or if) the system announces that someone has joined or left the call.  <br/> |
|[New-CsDialInConferencingDtmfConfiguration](../../manage/management-shell/new-csdialinconferencingdtmfconfiguration.md) <br/> |Creates a new collection of dual-tone multifrequency (DTMF) signaling settings used for dial-in conferencing.  <br/> |
|[New-CsDialPlan](../../manage/management-shell/new-csdialplan.md) <br/> |Creates a new dial plan.  <br/> |
|[Remove-CsConferenceDirectory](../../manage/management-shell/remove-csconferencedirectory.md) <br/> |Removes an existing conference directory. Conference directories are used to help dial-in conferencing users locate conference information.  <br/> |
|[Remove-CsDialInConferencingAccessNumber](../../manage/management-shell/remove-csdialinconferencingaccessnumber.md) <br/> |Removes an existing dial-in conferencing access number.  <br/> |
|[Remove-CsDialInConferencingConfiguration](../../manage/management-shell/remove-csdialinconferencingconfiguration.md) <br/> |Removes one or more collections of dial-in conferencing configuration settings. These settings determine how Skype for Business Server responds when users join or leave a dial-in conference.  <br/> |
|[Remove-CsDialInConferencingDtmfConfiguration](../../manage/management-shell/remove-csdialinconferencingdtmfconfiguration.md) <br/> |Removes an existing collection of dual-tone multi-frequency (DTMF) signaling settings used for dial-in conferencing.  <br/> |
|[Set-CsDialInConferencingAccessNumber](../../manage/management-shell/set-csdialinconferencingaccessnumber.md) <br/> |Modifies the property values of an existing dial-in conferencing access number. Dial-in conferencing provides a way for users to use a "regular" telephone, mobile phone or other device on the public switched telephone network (PSTN) to join the audio portion of a conference.  <br/> |
|[Set-CsDialInConferencingConfiguration](../../manage/management-shell/set-csdialinconferencingconfiguration.md) <br/> |Modifies settings that determine how Skype for Business Server responds when users join or leave a dial-in conference.  <br/> |
|[Set-CsDialInConferencingDtmfConfiguration](../../manage/management-shell/set-csdialinconferencingdtmfconfiguration.md) <br/> |Modifies the dual-tone multifrequency (DTMF) signaling settings used for dial-in conferencing.  <br/> |
|[Set-CsDialPlan](../../manage/management-shell/set-csdialplan.md) <br/> |Modifies an existing dial plan.  <br/> |
   
**PIN policy settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsPinPolicy](../../manage/management-shell/get-cspinpolicy.md) <br/> |Returns information about the client personal identification number (PIN) policies configured for use in your organization. PIN authentication enables users to access Skype for Business Server by providing a PIN instead of a user name and password.  <br/> |
|[Grant-CsPinPolicy](../../manage/management-shell/grant-cspinpolicy.md) <br/> |Assigns a client personal identification number (PIN) policy to a user or group of users.  <br/> |
|[New-CsPinPolicy](../../manage/management-shell/new-cspinpolicy.md) <br/> |Creates a new client personal identification number (PIN) policy.  <br/> |
|[Remove-CsPinPolicy](../../manage/management-shell/remove-cspinpolicy.md) <br/> |Removes the specified personal identification number (PIN) policy.  <br/> |
|[Set-CsPinPolicy](../../manage/management-shell/set-cspinpolicy.md) <br/> |Modifies one or more existing client personal identification number (PIN) policies.  <br/> |
   
**Other conferencing settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Disable-CsMeetingRoom](../../manage/management-shell/disable-csmeetingroom.md) <br/> |Disables a Skype for Business Server meeting room. A meeting room is a conferencing device designed to address video conferencing and collaboration scenarios in small conference rooms. When you disable a meeting room object you remove all the Skype for Business Server-specific Active Directory attributes assigned to the user account that represents the meeting room. However, the Active Directory user account itself is not deleted.  <br/> |
|[Enable-CsMeetingRoom](../../manage/management-shell/enable-csmeetingroom.md) <br/> |Enables a Skype for Business Server meeting room. To enable a meeting room you must first create an Active Directory user account that will represent that system. Note that, although meeting room objects are based on user accounts, these objects will not show up when you run the Get-CsUser cmdlet.  <br/> |
|[Get-CsConferenceDisclaimer](../../manage/management-shell/get-csconferencedisclaimer.md) <br/> |Returns information about the conference disclaimer used in your organization. The conference disclaimer is a message that is displayed to users who join the conference by using a hyperlink (for example, users who paste a link to the conference into a browser such as Windows Internet Explorer).  <br/> |
|[Get-CsMeetingRoom](../../manage/management-shell/get-csmeetingroom.md) <br/> |Returns information about all the Skype for Business Server meeting rooms configured for use in the organization.  <br/> |
|[Move-CsMeetingRoom](../../manage/management-shell/move-csmeetingroom.md) <br/> |Moves a Skype for Business Server meeting room object from one Registrar pool to another.  <br/> |
|[Remove-CsConferenceDisclaimer](../../manage/management-shell/remove-csconferencedisclaimer.md) <br/> |Clears the text from the header and body of the conference disclaimer used in your organization. The conference disclaimer is a message that is displayed to users who join the conference by using a hyperlink (for example, users who paste a link to the conference into a browser such as Windows Internet Explorer).  <br/> |
|[Set-CsMeetingRoom](../../manage/management-shell/set-csmeetingroom.md) <br/> |Modifies the property values of an existing Skype for Business Server meeting room.  <br/> |
   
**Testing settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Test-CsASConference](../../manage/management-shell/test-csasconference.md) <br/> |Tests the ability of a pair of users to take part in an application sharing conference.  <br/> |
|[Test-CsAudioConferencingProvider](../../manage/management-shell/test-csaudioconferencingprovider.md) <br/> |Tests to see if a user can connect to his or her audio conferencing provider. An audio conferencing provider is a third-party company that provides organizations with conferencing services. Among other things, audio conferencing providers enable users located off site, and not connected to the corporate network or the Internet, to participate in the audio portion of a conference or meeting.  <br/> |
|[Test-CsAVConference](../../manage/management-shell/test-csavconference.md) <br/> |Tests the ability of a pair of users to take part in an audio/video (A/V) conference.  <br/> |
|[Test-CsDataConference](../../manage/management-shell/test-csdataconference.md) <br/> |Verifies whether or not a pair of users can participate in a Skype for Business Server web conference that includes activities such as sharing or viewing PowerPoint slides, whiteboards, or polls. The cmdlet also verifies that the Skype for Business Server web conferencing service can discover Office Web Apps Server and that a client can upload a PowerPoint file for broadcast by Office Web Apps Server.  <br/> |
|[Test-CsDialInConferencing](../../manage/management-shell/test-csdialinconferencing.md) <br/> |Checks to see if a user can take part in a dial-in conferencing session.  <br/> |
|[Test-CsDialPlan](../../manage/management-shell/test-csdialplan.md) <br/> |Tests a telephone number against a dial plan (formerly known as a location profile) and returns the normalization rule that will be applied to the number as well as the translated number after the normalization rule has been applied.  <br/> |
|[Test-CsMcxConference](../../manage/management-shell/test-csmcxconference.md) <br/> |Tests the ability of three users to participate in a Skype for Business Server Mobility Service conference. The Mobility Service enables users of mobile phones such as iPhones and Windows Phones to do such things as exchange instant messages and presence information; store and retrieve voice mail internally instead of with their wireless provider; and take advantage of Skype for Business Server capabilities such as Call via Work and dial-out conferencing.  <br/> |
|[Test-CsUcwaConference](../../manage/management-shell/test-csucwaconference.md) <br/> |Tests the ability of a pair of users to schedule, join, and then conduct an online conference using the Unified Communications Web API (UCWA).  <br/> |
|[Debug-CsDataConference](../../manage/management-shell/debug-csdataconference.md) <br/> |Returns diagnostic information for the data conferencing capabilities included in Skype for Business Server.  <br/> |
   

