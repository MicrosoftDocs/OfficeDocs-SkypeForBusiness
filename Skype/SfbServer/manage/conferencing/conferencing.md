---
title: "Manage conferencing in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 825e051c-83a5-420d-a5ef-f77afa368e2e
description: "Summary: Learn how to manage conferencing in Skype for Business Server."
---

# Manage conferencing in Skype for Business Server
 
**Summary:** Learn how to manage conferencing in Skype for Business Server.
  
This topic describes how to manage conferencing. For more information about how to plan and deploy conferencing, see [Plan for conferencing in Skype for Business Server](../../plan-your-deployment/conferencing/conferencing.md) and [Deploy conferencing in Skype for Business Server](../../deploy/deploy-conferencing/deploy-conferencing.md).
  
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
|[Get-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/get-csconferencingpolicy?view=skype-ps) <br/> |Returns information about the conferencing policies that have been configured for use in your organization. Conferencing policies determine the features and capabilities that can be used in a conference; this includes everything from whether or not the conference can include IP audio and video to the maximum number of people who can attend a meeting.  <br/> |
|[Grant-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csconferencingpolicy?view=skype-ps) <br/> |Assigns a conferencing policy at the per-user scope.  <br/> |
|[New-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/new-csconferencingpolicy?view=skype-ps) <br/> |Creates a new conferencing policy for use in your organization.  <br/> |
|[Remove-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/remove-csconferencingpolicy?view=skype-ps) <br/> |Removes the specified conferencing policy.  <br/> |
|[Set-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csconferencingpolicy?view=skype-ps) <br/> |Modifies an existing conferencing policy.  <br/> |
   
**Meeting configuration settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsMeetingConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csmeetingconfiguration?view=skype-ps) <br/> |Returns information about the meeting configuration settings currently in use in your organization. Meeting configuration settings help dictate the type of meetings that users can create, and control how (or even if) anonymous users and dial-in conferencing users can join these meetings.  <br/> |
|[New-CsMeetingConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csmeetingconfiguration?view=skype-ps) <br/> |Creates a new collection of meeting configuration settings at the site or service scope. Note that these settings only affect scheduled meetings; they do not affect ad-hoc meetings created by clicking the Meet Now option in Skype for Business.  <br/> |
|[Remove-CsMeetingConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-csmeetingconfiguration?view=skype-ps) <br/> |Deletes an existing collection of meeting configuration settings.  <br/> |
|[Set-CsMeetingConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csmeetingconfiguration?view=skype-ps) <br/> |Modifies the meeting configuration settings currently in use in your organization.  <br/> |
   
**Conferencing configuration settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csconferencingconfiguration?view=skype-ps) <br/> |Returns information about the conference configuration settings for your organization. Conference settings determine such things as the maximum-allowed size for conference content and handouts, the content grace period (that is, the amount of time content will be stored before being deleted), and the URLs for the internal and external downloads of the supported client.  <br/> |
|[New-CsConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csconferencingconfiguration?view=skype-ps) <br/> |Creates a new collection of conference configuration settings.  <br/> |
|[Remove-CsConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-csconferencingconfiguration?view=skype-ps) <br/> |Removes the specified collection of conference configuration settings.  <br/> |
|[Set-CsConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csconferencingconfiguration?view=skype-ps) <br/> |Modifies an existing collection of conferencing configuration settings.  <br/> |
   
**Dial-in configuration settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsConferenceDirectory](https://docs.microsoft.com/powershell/module/skype/get-csconferencedirectory?view=skype-ps) <br/> |Returns information about the conference directories configured for use in your organization. Conference directories are used to help dial-in conferencing users locate conference information.  <br/> |
|[Get-CsDialInConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csdialinconferencingconfiguration?view=skype-ps) <br/> |Retrieves information about how Skype for Business Server responds when users join or leave a dial-in conference.  <br/> |
|[Get-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/get-csdialinconferencingaccessnumber?view=skype-ps) <br/> |Returns information about all the dial-in conferencing access numbers configured for use in your organization.  <br/> |
|[Get-CsDialInConferencingDtmfConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csdialinconferencingdtmfconfiguration?view=skype-ps) <br/> |Returns the dual-tone multifrequency (DTMF) signaling settings used for dial-in conferencing. DTMF enables users who dial in to a conference to control conference settings (such as muting and unmuting themselves or locking and unlocking the conference) by using the keypad on their telephone.  <br/> |
|[Get-CsDialInConferencingLanguageList](https://docs.microsoft.com/powershell/module/skype/get-csdialinconferencinglanguagelist?view=skype-ps) <br/> |Returns a list of languages, including regional/minority languages, supported for use with Skype for Business Server dial-in conferences. These languages are used to relay audio messages and instructions to users participating in a conference by using a telephone.  <br/> |
|[Get-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/get-csdialplan?view=skype-ps) <br/> |Returns information about the dial plans used in your organization.  <br/> |
|[Grant-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/grant-csdialplan?view=skype-ps) <br/> |Assigns a dial plan to one or more users or groups.  <br/> |
|[Import-CsLegacyConferenceDirectory](https://docs.microsoft.com/powershell/module/skype/import-cslegacyconferencedirectory?view=skype-ps) <br/> |Imports conference directories from Microsoft Office Communications Server 2007 R2 to Skype for Business Server. This helps provide interoperability between Skype for Business Server and Office Communications Server 2007 R2.  <br/> |
|[Move-CsConferenceDirectory](https://docs.microsoft.com/powershell/module/skype/move-csconferencedirectory?view=skype-ps) <br/> |Moves an existing conference directory from one pool to another. Conference directories are used to help dial-in conferencing users locate conference information.  <br/> |
|[New-CsConferenceDirectory](https://docs.microsoft.com/powershell/module/skype/new-csconferencedirectory?view=skype-ps) <br/> |Creates a new conference directory for use in your organization. Conference directories are used to help dial-in conferencing users locate conference information.  <br/> |
|[New-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/new-csdialinconferencingaccessnumber?view=skype-ps) <br/> |Creates a new dial-in conferencing access number.  <br/> |
|[New-CsDialInConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csdialinconferencingconfiguration?view=skype-ps) <br/> |Creates a new collection of dial-in conferencing configuration settings. These settings determine how Skype for Business Server responds when users join or leave a dial-in conference. In particular, information is returned regarding whether or not participants are required to record their name when joining a conference, and how (or if) the system announces that someone has joined or left the call.  <br/> |
|[New-CsDialInConferencingDtmfConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csdialinconferencingdtmfconfiguration?view=skype-ps) <br/> |Creates a new collection of dual-tone multifrequency (DTMF) signaling settings used for dial-in conferencing.  <br/> |
|[New-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/new-csdialplan?view=skype-ps) <br/> |Creates a new dial plan.  <br/> |
|[Remove-CsConferenceDirectory](https://docs.microsoft.com/powershell/module/skype/remove-csconferencedirectory?view=skype-ps) <br/> |Removes an existing conference directory. Conference directories are used to help dial-in conferencing users locate conference information.  <br/> |
|[Remove-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/remove-csdialinconferencingaccessnumber?view=skype-ps) <br/> |Removes an existing dial-in conferencing access number.  <br/> |
|[Remove-CsDialInConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-csdialinconferencingconfiguration?view=skype-ps) <br/> |Removes one or more collections of dial-in conferencing configuration settings. These settings determine how Skype for Business Server responds when users join or leave a dial-in conference.  <br/> |
|[Remove-CsDialInConferencingDtmfConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-csdialinconferencingdtmfconfiguration?view=skype-ps) <br/> |Removes an existing collection of dual-tone multi-frequency (DTMF) signaling settings used for dial-in conferencing.  <br/> |
|[Set-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/set-csdialinconferencingaccessnumber?view=skype-ps) <br/> |Modifies the property values of an existing dial-in conferencing access number. Dial-in conferencing provides a way for users to use a "regular" telephone, mobile phone or other device on the public switched telephone network (PSTN) to join the audio portion of a conference.  <br/> |
|[Set-CsDialInConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csdialinconferencingconfiguration?view=skype-ps) <br/> |Modifies settings that determine how Skype for Business Server responds when users join or leave a dial-in conference.  <br/> |
|[Set-CsDialInConferencingDtmfConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csdialinconferencingdtmfconfiguration?view=skype-ps) <br/> |Modifies the dual-tone multifrequency (DTMF) signaling settings used for dial-in conferencing.  <br/> |
|[Set-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/set-csdialplan?view=skype-ps) <br/> |Modifies an existing dial plan.  <br/> |
   
**PIN policy settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/get-cspinpolicy?view=skype-ps) <br/> |Returns information about the client personal identification number (PIN) policies configured for use in your organization. PIN authentication enables users to access Skype for Business Server by providing a PIN instead of a user name and password.  <br/> |
|[Grant-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/grant-cspinpolicy?view=skype-ps) <br/> |Assigns a client personal identification number (PIN) policy to a user or group of users.  <br/> |
|[New-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/new-cspinpolicy?view=skype-ps) <br/> |Creates a new client personal identification number (PIN) policy.  <br/> |
|[Remove-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/remove-cspinpolicy?view=skype-ps) <br/> |Removes the specified personal identification number (PIN) policy.  <br/> |
|[Set-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/set-cspinpolicy?view=skype-ps) <br/> |Modifies one or more existing client personal identification number (PIN) policies.  <br/> |
   
**Other conferencing settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Disable-CsMeetingRoom](https://docs.microsoft.com/powershell/module/skype/disable-csmeetingroom?view=skype-ps) <br/> |Disables a Skype for Business Server meeting room. A meeting room is a conferencing device designed to address video conferencing and collaboration scenarios in small conference rooms. When you disable a meeting room object you remove all the Skype for Business Server-specific Active Directory attributes assigned to the user account that represents the meeting room. However, the Active Directory user account itself is not deleted.  <br/> |
|[Enable-CsMeetingRoom](https://docs.microsoft.com/powershell/module/skype/enable-csmeetingroom?view=skype-ps) <br/> |Enables a Skype for Business Server meeting room. To enable a meeting room you must first create an Active Directory user account that will represent that system. Note that, although meeting room objects are based on user accounts, these objects will not show up when you run the Get-CsUser cmdlet.  <br/> |
|[Get-CsConferenceDisclaimer](https://docs.microsoft.com/powershell/module/skype/get-csconferencedisclaimer?view=skype-ps) <br/> |Returns information about the conference disclaimer used in your organization. The conference disclaimer is a message that is displayed to users who join the conference by using a hyperlink (for example, users who paste a link to the conference into a browser such as Windows Internet Explorer).  <br/> |
|[Get-CsMeetingRoom](https://docs.microsoft.com/powershell/module/skype/get-csmeetingroom?view=skype-ps) <br/> |Returns information about all the Skype for Business Server meeting rooms configured for use in the organization.  <br/> |
|[Move-CsMeetingRoom](https://docs.microsoft.com/powershell/module/skype/move-csmeetingroom?view=skype-ps) <br/> |Moves a Skype for Business Server meeting room object from one Registrar pool to another.  <br/> |
|[Remove-CsConferenceDisclaimer](https://docs.microsoft.com/powershell/module/skype/remove-csconferencedisclaimer?view=skype-ps) <br/> |Clears the text from the header and body of the conference disclaimer used in your organization. The conference disclaimer is a message that is displayed to users who join the conference by using a hyperlink (for example, users who paste a link to the conference into a browser such as Windows Internet Explorer).  <br/> |
|[Set-CsMeetingRoom](https://docs.microsoft.com/powershell/module/skype/set-csmeetingroom?view=skype-ps) <br/> |Modifies the property values of an existing Skype for Business Server meeting room.  <br/> |
   
**Testing settings**

|**Cmdlet**|**Description**|
|:-----|:-----|
|[Test-CsASConference](https://docs.microsoft.com/powershell/module/skype/test-csasconference?view=skype-ps) <br/> |Tests the ability of a pair of users to take part in an application sharing conference.  <br/> |
|[Test-CsAudioConferencingProvider](https://docs.microsoft.com/powershell/module/skype/test-csaudioconferencingprovider?view=skype-ps) <br/> |Tests to see if a user can connect to his or her audio conferencing provider. An audio conferencing provider is a third-party company that provides organizations with conferencing services. Among other things, audio conferencing providers enable users located off site, and not connected to the corporate network or the Internet, to participate in the audio portion of a conference or meeting.  <br/> |
|[Test-CsAVConference](https://docs.microsoft.com/powershell/module/skype/test-csavconference?view=skype-ps) <br/> |Tests the ability of a pair of users to take part in an audio/video (A/V) conference.  <br/> |
|[Test-CsDataConference](https://docs.microsoft.com/powershell/module/skype/test-csdataconference?view=skype-ps) <br/> |Verifies whether or not a pair of users can participate in a Skype for Business Server web conference that includes activities such as sharing or viewing PowerPoint slides, whiteboards, or polls. The cmdlet also verifies that the Skype for Business Server web conferencing service can discover Office Web Apps Server and that a client can upload a PowerPoint file for broadcast by Office Web Apps Server.  <br/> |
|[Test-CsDialInConferencing](https://docs.microsoft.com/powershell/module/skype/test-csdialinconferencing?view=skype-ps) <br/> |Checks to see if a user can take part in a dial-in conferencing session.  <br/> |
|[Test-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/test-csdialplan?view=skype-ps) <br/> |Tests a telephone number against a dial plan (formerly known as a location profile) and returns the normalization rule that will be applied to the number as well as the translated number after the normalization rule has been applied.  <br/> |
|[Test-CsMcxConference](https://docs.microsoft.com/powershell/module/skype/test-csmcxconference?view=skype-ps) <br/> |Tests the ability of three users to participate in a Skype for Business Server Mobility Service conference. The Mobility Service enables users of mobile phones such as iPhones and Windows Phones to do such things as exchange instant messages and presence information; store and retrieve voice mail internally instead of with their wireless provider; and take advantage of Skype for Business Server capabilities such as Call via Work and dial-out conferencing.  <br/> **Note:** Clients that use MCX are not supported in Skype for Business Server 2019.|
|[Test-CsUcwaConference](https://docs.microsoft.com/powershell/module/skype/test-csucwaconference?view=skype-ps) <br/> |Tests the ability of a pair of users to schedule, join, and then conduct an online conference using the Unified Communications Web API (UCWA).  <br/> |
|[Debug-CsDataConference](https://docs.microsoft.com/powershell/module/skype/debug-csdataconference?view=skype-ps) <br/> |Returns diagnostic information for the data conferencing capabilities included in Skype for Business Server.  <br/> |
   

