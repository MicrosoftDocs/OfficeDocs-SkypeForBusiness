---
title: "Set-CsApplicationServer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 74b3f941-df06-4fde-9487-eba081233723
description: "Enables you to modify configuration properties of one or more servers running the Application service. These servers (also known as Application Servers) host software programs, such as the Call Park application, that were developed using the Microsoft Unified Communications Managed API (UCMA) set. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsApplicationServer
 
Enables you to modify configuration properties of one or more servers running the Application service. These servers (also known as Application Servers) host software programs, such as the Call Park application, that were developed using the Microsoft Unified Communications Managed API (UCMA) set. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsApplicationServer [-Identity <XdsGlobalRelativeIdentity>] [-ApplicationDatabase <String>] [-AppSharingPortCount <UInt16>] [-AppSharingPortStart <UInt16>] [-AtsSipPort <UInt16>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-CaaSipPort <UInt16>] [-CasSipPort <UInt16>] [-Confirm [<SwitchParameter>]] [-CpsSipPort <UInt16>] [-Force <SwitchParameter>] [-PdpSipPort <UInt16>] [-PdpTurnPort <UInt16>] [-Registrar <String>] [-RgsSipPort <UInt16>] [-RgsWcfMtlsPort <UInt16>] [-VideoPortCount <UInt16>] [-VideoPortStart <UInt16>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 configures the SIP port for the Conferencing Announcement application on the Application Server ApplicationServer:atl-cs-001.litwareinc.com to 5074.
  
```
Set-CsApplicationServer -Identity "ApplicationServer:atl-cs-001.litwareinc.com" -CasSipPort 5074 
```

### EXAMPLE 2

Example 2 configures audio ports for the Application Server ApplicationServer:atl-cs-001.litwareinc.com. In this example, the starting audio port is set to 49500 and a total of 5500 ports are set aside for audio traffic.
  
```
Set-CsApplicationServer -Identity "ApplicationServer:atl-cs-001.litwareinc.com" -AudioPortStart 49500 -AudioPortCount 5500 
```

### EXAMPLE 3

In Example 3, the SIP port for the Conferencing Announcement application is set to 5074 for all of the Application Servers in the organization. To do this, the command first uses the **Get-CsService** cmdlet to return a collection of all the Application Servers currently in use. This collection is then piped to the **ForEach-Object** cmdlet, which takes each server in the collection, and uses the **Set-CsApplicationServer** cmdlet to set the Conferencing Announcement application SIP port to 5074.
  
```
Get-CsService -ApplicationServer | ForEach-Object {Set-CsApplicationServer -Identity $_.Identity -CasSipPort 5074} 
```

## Detailed Description

The Application service hosts a number of Skype for Business Server 2015 programs that are not part of the core server components; these programs include the Response Group application, the Conferencing Attendant application, and the Conferencing Announcement application. The Application service takes these programs and fully integrates them into the Skype for Business Server 2015 environment.
  
The **Set-CsApplicationServer** cmdlet enables administrators to modify the configuration settings for any (or all) of the Application Servers deployed in their organization. For example, you can modify the ports used for audio, video, or application sharing traffic, or assign new values to ports used by individual applications such as the Conferencing Attendant application or the Conferencing Announcement application. Note that any time you change ports you will then need to restart the corresponding service.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ApplicationDatabase_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Application database. For example:  `-ApplicationDatabase "ApplicationDatabase:atl-cs-001.litwareinc.com"`.  <br/> |
| _AppSharingPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |Total number of ports allocated for application sharing. The actual ports to be opened will start with the value configured for AppSharingPortStart and continue through the number of ports specified for AppSharingPortCount. For example, if the AppSharingPortStart is set to 60000 and the AppSharingPortCount is set to 100 then ports 60000 through 60099 will be used for application sharing.  <br/> |
| _AppSharingPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |First port in the range of ports allocated for application sharing. For example:  `-AppSharingPortStart 60000`.  <br/> |
| _AtsSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for the Audio Test service.  <br/> |
| _AudioPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |Total number of ports allocated for sending and receiving audio traffic. The actual ports to be opened will start with the value configured for AudioPortStart and continue through the number of ports specified for AudioPortCount. For example, if the AudioPortStart is set to 60000 and the AudioPortCount is set to 100, then ports 60000 through 60099 will be used for audio traffic.  <br/> |
| _AudioPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |First port in the range of ports allocated for sending and receiving audio traffic. For example:  `-AudioPortStart 60000`.  <br/> |
| _CaaSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |SIP port used by the Conferencing Attendant application, used when connecting users to a dial-in conference.  <br/> |
| _CasSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |SIP port used by the Conferencing Announcement application, used to play announcements (for example, "Ken Myer is now exiting") during a conference.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _CpsSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |SIP port used by the Call Park service. The Call Park service enables you to place a call on hold from one telephone, then have that call retrieved from a different phone.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Service location of the Application Server to be modified. For example:  `-Identity "ApplicationServer:atl-cs-001.litwareinc.com"`.  <br/> Note that you can leave off the prefix "ApplicationServer:" when specifying an Application server. For example:  `-Identity "atl-cs-001.litwareinc.com"`.  <br/> |
| _PdpSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |SIP port used by the Policy Decision Point Server. The Policy Decision Point Server is used for bandwidth management.  <br/> |
| _PdpTurnPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Turn traffic port used by the Policy Decision Point Server.  <br/> |
| _Registrar_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name of the Registrar associated with the Policy Decision Point Server.  <br/> |
| _RgsSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |SIP port used by the Response Group application. The Response Group application provides a way to direct incoming phone calls to a specific group of people, such as an organization's support team.  <br/> |
| _RgsWcfMtlsPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for Windows Communication Foundation (WCF) mutual TLS (MTLS) traffic used by the Response Group application.  <br/> |
| _VideoPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |Total number of ports allocated for sending and receiving video traffic. The actual ports to be opened will start with the value configured for VideoPortStart and continue through the number of ports specified for VideoPortCount. For example, if the VideoPortStart is set to 60000 and the VideoPortCount is set to 100, then ports 60000 through 60099 will be used for video traffic.  <br/> |
| _VideoPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |First port in the range of ports allocated for sending and receiving video traffic. For example  `-VideoPortStart 60000`.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Set-CsApplicationServer** cmdlet does not accept pipelined input.
  
## Return Types

The **Set-CsApplicationServer** cmdlet does not return any values or objects. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayApplicationServer object.
  
## See also

#### 

[Get-CsServerApplication](get-csserverapplication.md)

