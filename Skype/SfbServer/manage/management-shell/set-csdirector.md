---
title: "Set-CsDirector"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 74eb6f17-812f-47df-84ee-fa6e42990f2e
description: "Modifies the properties of one or more Directors. Directors can be used to authenticate user requests, but do not host user accounts. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsDirector
 
Modifies the properties of one or more Directors. Directors can be used to authenticate user requests, but do not host user accounts. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsDirector [-Identity <XdsGlobalRelativeIdentity>] [-ArchivingServer <String>] [-Confirm [<SwitchParameter>]] [-EdgeServer <String>] [-Force <SwitchParameter>] [-MirrorMonitoringDatabase <String>] [-MonitoringDatabase <String>] [-MonitoringServer <String>] [-SipHealthPort <UInt16>] [-SipPort <UInt16>] [-SipServerTcpPort <UInt16>] [-WebPort <UInt16>] [-WebServer <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 changes the Archiving Server associated with the Director Director:atl-cs-001.litwareinc.com. In this example, the Archiving Server is switched to ArchivingServer:dublin-cs-001.litwareinc.com.
  
```
Set-CsDirector -Identity "Director:atl-cs-001.litwareinc.com" -ArchivingServer "ArchivingServer:dublin-cs-001.litwareinc.com"
```

### EXAMPLE 2

Example 2 changes the SIP port for all the Directors currently in use in the organization. To do this, the command first uses the **Get-CsService** cmdlet and the Director parameter to return a collection of all the Directors in the organization. That collection is then piped to the **ForEach-Object**. In turn, the **ForEach-Object** cmdlet runs the **Set-CsDirector** cmdlet against each site in the collection, changing the value of the SipPort property to 5072.
  
```
Get-CsService -Director | ForEach-Object {Set-CsDirector -Identity $_.Identity -SipPort 5072}
```

## Detailed Description

The Director authenticates users and responds to user requests without actually hosting user accounts. Directors are typically used for organizations that allow external access to the network through Edge Servers. In that scenario, Directors not only help alleviate the strain on Front End Servers (by handling authentication requests), but also help shield the internal network from denial-of-service attacks and other malicious traffic. Directors are also useful any time multiple Front End Servers are deployed in a central site. In that case, Directors receive all user requests and then channel those requests to the appropriate server pool. This, again, helps to ease the burden placed on the Front End Servers.
  
The **Set-CsDirector** cmdlet enables you to modify the property values for any of the Directors currently in use in your organization. This includes changing such things as the Archiving Server or Edge Server associated with the Director, or changing the port used for sending and receiving SIP traffic.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ArchivingServer_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Archiving Server to be associated with the Director. For example:  `-ArchivingServer "ArchivingServer:atl-cs-001.litwareinc.com"`.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EdgeServer_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Edge Server to be associated with the Director. For example:  `-EdgeServer "EdgeServer:atl-edge-001.litwareinc.com"` <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Service location of the Director to be modified. For example:  `-Identity "Director:atl-cs-001.litwareinc.com"`.  <br/> Note that you can leave off the prefix "Director:" when specifying a Director. For example:  `-Identity "atl-cs-001.litwareinc.com"`.  <br/> |
| _MirrorMonitoringDatabase_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the mirror monitoring database to be associated with the Director.  <br/> |
| _MonitoringDatabase_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the monitoring database to be associated with the Director.  <br/> |
| _MonitoringServer_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Monitoring Server to be associated with the Director. For example:  `-MonitoringServer "MonitoringServer:atl-cs-001.litwareinc.com"`.  <br/> |
| _SipHealthPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for monitoring server health.  <br/> |
| _SipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for Session Initiation Protocol (SIP) traffic.  <br/> |
| _SipServerTcpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |SIP listening port. The default value is 5060.  <br/> |
| _WebPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for communicating with Web Services.  <br/> |
| _WebServer_ <br/> |Optional  <br/> |System.String  <br/> |Web Services location of the server to be associated with the Director. For example:  `-WebServer "WebServer:atl-cs-001.litwareinc.com"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Set-CsDirector** cmdlet does not accept pipelined input.
  
## Return Types

The **Set-CsDirector** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayDirector object.
  
## See also

#### 

[Get-CsService](get-csservice.md)

