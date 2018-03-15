---
title: "Set-CsWebServer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 95a7be5b-9e53-40b9-b7b8-3a4bae9c946c
description: "Modifies one or more of the Web Server services used by Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsWebServer
 
Modifies one or more of the Web Server services used by Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsWebServer [-Identity <XdsGlobalRelativeIdentity>] [-AppSharingPortCount <UInt16>] [-AppSharingPortStart <UInt16>] [-Confirm [<SwitchParameter>]] [-ExternalFqdn <Fqdn>] [-ExternalHttpPort <UInt16>] [-ExternalHttpsPort <UInt16>] [-Force <SwitchParameter>] [-InternalFqdn <Fqdn>] [-McxSipExternalListeningPort <UInt16>] [-McxSipPrimaryListeningPort <UInt16>] [-MeetingRoomAdminPortalExternalListeningPort <UInt16>] [-MeetingRoomAdminPortalInternalListeningPort <UInt16>] [-PrimaryHttpPort <UInt16>] [-PrimaryHttpsPort <UInt16>] [-PublishedExternalHttpPort <UInt16>] [-PublishedExternalHttpsPort <UInt16>] [-PublishedPrimaryHttpPort <UInt16>] [-PublishedPrimaryHttpsPort <UInt16>] [-ReachExternalPsomServerPort <UInt16>] [-ReachPrimaryPsomServerPort <UInt16>] [-RmWebSipExternalListeningPort <UInt16>] [-RmWebSipPrimaryListeningPort <UInt16>] [-SupportConferenceConsoleSipExternalListeningPort <UInt16>] [-SupportConferenceConsoleSipPrimaryListeningPort <UInt16>] [-UcapSipPrimaryListeningPort <UInt16>] [-UcwaSipExternalListeningPort <UInt16>] [-UcwaSipPrimaryListeningPort <UInt16>] [-UserServer <String>] [-VxmlSipPrimaryListeningPort <UInt16>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 changes the PrimaryHttpPort for a single Web Service pool: the pool with the Identity WebServer:atl-cs-001.litwareinc.com. In this example, the port is changed to port number 89.
  
```
Set-CsWebServer -Identity "WebServer:atl-cs-001.litwareinc.com" -PrimaryHttpPort 89
```

### EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In this case, the PrimaryHttpPort is modified for all the Web Service pools in the organization. To do this, the command starts off by using the **Get-CsService** cmdlet and the WebServer parameter to return a collection of all the Web Services pools currently in use. This collection is then piped to the **ForEach-Object** cmdlet, which takes each pool in the collection and sets the PrimaryHttpPort to port 89. The data must be piped to the **ForEach-Object** cmdlet because the **Set-CsWebServer** cmdlet cannot accept pipelined data itself.
  
```
Get-CsService -WebServer | ForEach-Object {Set-CsWebServer -Identity $_.Identity -PrimaryHttpPort 89}
```

## Detailed Description

Skype for Business Server 2015 makes extensive use of Web servers and web services. For example, Address Book queries can be conducted using web services (the Address Book Query Web service). Skype for Business Server 2015 also hosts webpages that enable users to do such things as configure their dial-in conferencing personal identification number (PINs). Considering the important role played by Web servers and web services, it is critical that administrators know how these servers and services are configured. That information that can be returned using the following command:
  
 `Get-CsService -WebServer`
  
There are also times where it is critical that administrators be able to change the way their Web servers are configured. For example, you might need to modify the port used for external HTTP or HTTPS connections. Port changes like these (and other modifications) can be made using the **Set-CsWebServer** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AppSharingPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |Total number of ports allocated for application sharing. The actual ports to be opened will start with the value configured for AppSharingPortStart and continue through the number of ports specified for AppSharingPortCount. For example, if the AppSharingPortStart is set to 60000 and the AppSharingPortCount is set to 100 then ports 60000 through 60099 will be used for application sharing. The default value is 16383.  <br/> |
| _AppSharingPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |First port in the range of ports allocated for application sharing. The default value is 49152.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _ExternalFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) used by people connecting to the Web Services pool from outside the internal network. For example:  <br/>  `-ExternalFqdn "www.litwareinc.com"` <br/> |
| _ExternalHttpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port number for external web connections made using the HTTP protocol. The default value is port 8080.  <br/> |
| _ExternalHttpsPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port number for external web connections made using the HTTPS protocol. The default value is port 4443.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the Web Services pool. For example:  <br/>  `-Identity "WebServer:atl-cs-001.litwareinc.com"` <br/> Note that you can leave off the prefix "WebServer:" when specifying a Web server. For example:  <br/>  `-Identity "atl-cs-001.litwareinc.com"` <br/> |
| _InternalFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name for the Mobility Services. The InternalFqdn should only be accessible from inside the organization's firewall.  <br/> |
| _McxSipExternalListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |External listening port for the Mobility service.  <br/> |
| _McxSipPrimaryListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Internal listening port for the Mobility service.  <br/> |
| _MeetingRoomAdminPortalExternalListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |External listening port for the Skype for Business Meeting Room Admin Portal. The Admin Portal is a web-based utility that makes it easy for administrator to manage meeting rooms.  <br/> |
| _MeetingRoomAdminPortalInternalListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Internal listening port for the Skype for Business Meeting Room Admin Portal. The Admin Portal is a web-based utility that makes it easy for administrator to manage meeting rooms.  <br/> |
| _PrimaryHttpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port number for internal web connections made using the HTTP protocol. The default value is port 80.  <br/> |
| _PrimaryHttpsPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port number for internal web connections made using the HTTPS protocol. The default value is port 443.  <br/> |
| _PublishedExternalHttpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port number for the published external HTTP port.  <br/> |
| _PublishedExternalHttpsPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |External port for the Mobility service.  <br/> |
| _PublishedPrimaryHttpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port number for the published primary HTTP port.  <br/> |
| _PublishedPrimaryHttpsPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Internal port for the Mobility service.  <br/> |
| _ReachExternalPsomServerPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |External port number for the Persistent Shared Object Model Protocol, a Microsoft protocol used for conferences. The default port number is 8061.  <br/> |
| _ReachPrimaryPsomServerPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Primary port number for the Persistent Shared Object Model (PSOM) Protocol, a Microsoft protocol used for conferences. The default port number is 8060.  <br/> |
| _RmWebSipExternalListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |External listening port for the Persistent Chat Room Management Web App. This application is available only if you have installed and configured Persistent Chat.  <br/> |
| _RmWebSipPrimaryListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Primary listening port for the Persistent Chat Room Management Web App. This application is available only if you have installed and configured Persistent Chat.  <br/> |
| _SupportConferenceConsoleSipExternalListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Listening port for the Support Conferencing Console. The default value is 6007.  <br/> |
| _SupportConferenceConsoleSipPrimaryListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used by the Office 365 Support Conference Console. This console is used by support personnel to troubleshoot problems with conferences and online meetings.  <br/> |
| _UcapSipPrimaryListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Primary listening port for the UCAP (Unified Communication Application Platform).  <br/> |
| _UcwaSipExternalListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |External SIP listening port for the Unified Communications Web API (UCWA). The default value is 5088.  <br/> |
| _UcwaSipPrimaryListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Internal SIP listening port for the Unified Communications Web API (UCWA). The default value is 5089.  <br/> |
| _UserServer_ <br/> |Optional  <br/> |System.String  <br/> |Service ID for the User Services pool associated with the Web Services pool. For example:  <br/>  `-UserServer "UserServer:atl-cs-001.litwareinc.com"` <br/> |
| _VxmlSipPrimaryListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |This parameter is not currently used with Skype for Business Server 2015.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Set-CsWebServer** cmdlet does not accept pipelined input.
  
## Return Types

None. Instead, the **Set-CsWebServer** cmdlet modifies instances of the Microsoft.Rtc.Management.Xds.DisplayWebServer object.
  
## See also

#### 

[Get-CsService](get-csservice.md)

