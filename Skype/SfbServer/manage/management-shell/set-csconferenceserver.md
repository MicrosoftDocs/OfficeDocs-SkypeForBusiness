---
title: "Set-CsConferenceServer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 90f9f1f1-0029-4f97-a8f4-719523cfad56
description: "Modifies the properties of an A/V Conferencing Server (also known as a Conference Server). The Conference Server provides audio and video (A/V) capabilities to your conferences. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsConferenceServer
 
Modifies the properties of an A/V Conferencing Server (also known as a Conference Server). The Conference Server provides audio and video (A/V) capabilities to your conferences. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsConferenceServer [-Identity <XdsGlobalRelativeIdentity>] [-AppSharingPortCount <UInt16>] [-AppSharingPortStart <UInt16>] [-AppSharingSipPort <UInt16>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-AudioVideoSipPort <UInt16>] [-Confirm [<SwitchParameter>]] [-DataPsomPort <UInt16>] [-EdgeServer <String>] [-Force <SwitchParameter>] [-ImSipPort <UInt16>] [-MeetingPsomPort <UInt16>] [-PhoneSipPort <UInt16>] [-VideoPortCount <UInt16>] [-VideoPortStart <UInt16>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 modifies the instant messaging SIP port for the Conference Server ConferencingServer:atl-cs-001.litwareinc.com. In this example, the port is changed to 5075.
  
```
Set-CsConferenceServer -Identity "ConferencingServer:atl-cs-001.litwareinc.com" -ImSipPort 5075
```

### EXAMPLE 2

Example 2 is a variation of the command shown in Example 1; in this case, however, the instant messaging SIP port is changed for all the Conference Servers in the organization. To do this, the command first uses the **Get-CsService** cmdlet and the ConferencingServer parameter to return a collection of all the Conferencing Servers currently in use. That collection is then piped to the **ForEach-Object** cmdlet, which runs the **Set-CsConferenceServer** cmdlet against each server in the collection, setting the ImSipPort to 5075.
  
```
Get-CsService -ConferencingServer | ForEach-Object {Set-CsConferenceServer -Identity $_.Identity -ImSipPort 5075}
```

## Detailed Description

Conference Servers (also known as A/V Conferencing Servers) are used to provide audio and video capabilities to conferences. In turn, the **Set-CsConferenceServer** cmdlet can be used to modify the properties of these servers; in particular, you can specify which ports are used for such things as audio traffic, video traffic, and application sharing. You can also use the **Set-CsConferenceServer** cmdlet to associate a given server with a Edge Server or Archiving Server.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AppSharingPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |Total number of ports allocated for application sharing. The actual ports to be opened will start with the value configured for AppSharingPortStart and continue through the number of ports specified for AppSharingPortCount. For example, if the AppSharingPortStart is set to 60000 and the AppSharingPortCount is set to 100, then ports 60000 through 60099 will be used for application sharing.  <br/> |
| _AppSharingPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |First port in the range of media ports allocated for application sharing. For example:  `-AppSharingPortStart 60000`.  <br/> |
| _AppSharingSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |SIP port used to listen for requests for application sharing. The ports actually used for application sharing are configured using AppSharingPortStart and AppSharingPortCount.  <br/> |
| _AudioPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |Total number of ports allocated for sending and receiving audio traffic. The actual ports to be opened will start with the value configured for AudioPortStart and continue through the number of ports specified for AudioPortCount. For example, if the AudioPortStart is set to 60000 and the AudioPortCount is set to 100, then ports 60000 through 60099 will be used for audio traffic.  <br/> |
| _AudioPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |First port in the range of media ports allocated for sending and receiving audio traffic. For example:  `-AudioPortStart 60000`.  <br/> |
| _AudioVideoSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |SIP port used to listen for incoming requests for audio and video service. The ports actually used for audio and video traffic are configured using AudioPortCount, AudioPortStart, VideoPortCount, and VideoPortStart.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DataPsomPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Data port used by the Persistent Shared Object Model (PSOM) protocol.  <br/> |
| _EdgeServer_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Edge Server to be associated with the Conference Server. For example:  `-EdgeServer "EdgeServer:atl-edge-001.litwareinc.com"`.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Service location of the Conference Server to be modified. For example:  `-Identity "ConferencingServer:atl-cs-001.litwareinc.com"`.  <br/> Note that you can leave off the prefix "ConferencingServer:" when specifying a Conference Server. For example:  `-Identity "atl-cs-001.litwareinc.com"`.  <br/> |
| _ImSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for instant messaging traffic.  <br/> |
| _MeetingPsomPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for the Persistent Shared Object Model (PSOM) protocol, a Microsoft protocol used for conferences.  <br/> |
| _PhoneSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for telephony traffic.  <br/> |
| _VideoPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |Total number of ports allocated for sending and receiving video traffic. The actual ports to be opened will start with the value configured for VideoPortStart and continue through the number of ports specified for VideoPortCount. For example, if the VideoPortStart is set to 60000 and the VideoPortCount is set to 100, then ports 60000 through 60099 will be used for video traffic.  <br/> |
| _VideoPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |First port in the range of ports allocated for sending and receiving video traffic. For example:  `-VideoPortStart 60000`.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Set-CsConferenceServer** cmdlet does not accept pipelined input.
  
## Return Types

The **Set-CsConferenceServer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayConferenceServer object.
  
## See also

#### 

[Get-CsConferencingConfiguration](get-csconferencingconfiguration.md)
  
[Get-CsService](get-csservice.md)

