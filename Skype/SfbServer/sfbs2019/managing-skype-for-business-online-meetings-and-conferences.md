---
title: "Managing Skype for Business Online meetings and conferences"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: a4d0c070-4df2-47df-a1e2-6ce62600a287

description: "The following cmdlets can be used to manage meeting and conferencing settings:"
---

# Managing Skype for Business Online meetings and conferences
[]
The following cmdlets can be used to manage meeting and conferencing settings:
  
|**Cmdlet**|**Description**|
|:-----|:-----|
|[Disable-CsMeetingRoom](disable-csmeetingroom.md)          [Enable-CsMeetingRoom](enable-csmeetingroom.md)          [Get-CsMeetingRoom](get-csmeetingroom.md)          [Set-CsMeetingRoom](set-csmeetingroom.md) <br/> |Manages endpoint devices for meeting rooms.  <br/> In Skype for Business Online, meeting rooms are self-contained computer appliances that are installed in conference rooms and supply advanced meeting capabilities. To manage these new endpoint devices you must, among other things, create and enable an Exchange resource mailbox account for the device, and then enable that resource account for Skype for Business Online.  <br/> |
|[Get-CsAudioConferencingProvider](get-csaudioconferencingprovider.md) <br/> |Returns information about the audio conferencing providers that your organization is contracted with.  <br/> An audio conferencing provider is a third-party company that provides organizations with conferencing services, including high-end services such as live translation, transcription, and live per-conference operator assistance.  <br/> |
|[Get-CsMeetingConfiguration](get-csmeetingconfiguration.md)          [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md) <br/> |Controls the type of meetings that users can create and determines how meetings deal with anonymous users and dial-in conferencing users.  <br/> Meetings (also called conferences) are an integral part of Skype for Business Online. With these cmdlets, for example, you can configure meetings so that dial-in users are not automatically admitted the meeting, but are instead routed to the meeting lobby. These dial-in users remain on hold in the lobby until a presenter admits them to the meeting.  <br/> |
   
You can also manage a small subset of meeting configuration properties by using the Skype for Business Online admin center:
  
![Lync admin center general options properties](media/LyncOnlinePowerShell_Meeting_Properties.png)
  
## See also

#### 

[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)
  
[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

