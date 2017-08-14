---
title: Set-CsEdgeServer
ms.prod: SKYPEFORBUSINESS
ms.assetid: cbe140a4-8ce6-4e20-913b-b1ffb58e6698
---


# Set-CsEdgeServer
[]
Modifies the property values for one or more Edge Servers. Edge Servers are used to provide connectivity between your internal network and the Internet. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsEdgeServer [-Identity <XdsGlobalRelativeIdentity>] [-AccessEdgeClientSipPort <UInt16>] [-AccessEdgeExternalSipPort <UInt16>] [-AccessEdgeInternalSipPort <UInt16>] [-Confirm [<SwitchParameter>]] [-DataPsomClientPort <UInt16>] [-DataPsomServerPort <UInt16>] [-Force <SwitchParameter>] [-MediaCommunicationPortCount <UInt16>] [-MediaCommunicationPortStart <UInt16>] [-MediaRelayAuthEdgePort <UInt16>] [-MediaRelayExternalTurnTcpPort <UInt16>] [-MediaRelayExternalTurnUdpPort <UInt16>] [-MediaRelayInternalTurnTcpPort <UInt16>] [-MediaRelayInternalTurnUdpPort <UInt16>] [-Registrar <String>] [-SkypeSearchProxyPort <UInt16>] [-WhatIf [<SwitchParameter>]] [-XmppInternalPort <UInt16>] [-XmppListeningPort <UInt16>]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 modifies the internal and external SIP ports for the Edge Server "EdgeServer:atl-edge-001.litwareinc.com".
  
    
    

```

Set-CsEdgeServer -Identity "EdgeServer:atl-edge-001.litwareinc.com" -AccessEdgeInternalSipPort 5062 -AccessEdgeExternalSipPort 5062
```


### EXAMPLE 2

Example 2 modifies the internal and external SIP ports for all the Edge Servers located in the Redmond site. To do this, the command first uses the **Get-CsService** cmdlet and the EdgeServer parameter to return a collection of all the Edge Servers currently in use in the organization. That collection is then piped to the **Where-Object** cmdlet, which selects only those Edge servers from the Redmond site; that is, servers where the SiteId property is equal to site:Redmond. This filtered collection is then piped to the **For-Each-Object** cmdlet. That cmdlet runs the **Set-CsEdgeServer** cmdlet against each server in the collection, changing the values assigned to the AccessInternalSipPort and AccessExternalSipPort properties.
  
    
    

```
Get-CsService -EdgeServer | Where-Object {$_.SiteId -eq "site:Redmond"} | ForEach-Object {Set-CsEdgeServer -Identity $_.Identity -AccessEdgeInternalSipPort 5062 -AccessEdgeExternalSipPort 5062}
```


## Detailed Description

Connectivity with the outside world (that is, with the Internet) is an important aspect of Skype for Business Server 2015. Without this connectivity, users would have to log on to the internal network in order to access Skype for Business Server 2015. This would make it difficult for users working off-site to use the software, and preclude the ability of users who do not have accounts in your domain from being able to participate in conferences. Likewise, without connectivity outside of the organization users would be unable to exchange instant messages with federated partners or with people who have accounts on a public instant messaging system such as Yahoo!, AOL, or MSN.
  
    
    
Edge Servers are used to help provide connectivity between your internal network and the Internet. The **Set-CsEdgeServer** cmdlet enables you to modify configuration settings for your Edge Servers, a task that primarily involves changing the port numbers used for transmitting network traffic.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AccessEdgeClientSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for SIP communications between the Edge Server and client devices. The initial value is set in Topology Builder but can be changed by specifying a new value for this parameter.  <br/> |
| _AccessEdgeExternalSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for external SIP traffic. The default value is 5061.  <br/> |
| _AccessEdgeInternalSipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for internal SIP traffic. The default value is 5061.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DataPsomClientPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for Persistent Shared Object Model (PSOM) communications between the Edge Server and client devices. The initial value is set in Topology Builder but can be changed by specifying a new value for this parameter.  <br/> |
| _DataPsomServerPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for PSOM communications between the Edge Server and other servers.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Service location of the Edge Server to be modified. For example:  `-Identity "EdgeServer:atl-edge-001.litwareinc.com"`.  <br/> Note that you can leave off the prefix "EdgeServer:" when specifying an Edge server. For example:  `-Identity "atl-cs-001.litwareinc.com"`.  <br/> |
| _MediaCommunicationPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |Total number of ports allocated on the external Edge for media communications. The default value is 10000.  <br/> |
| _MediaCommunicationPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |Starting port number on the external Edge for media communications. The default value is 50000.  <br/> |
| _MediaRelayAuthEdgePort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for media relay authentication. The default value is 5062.  <br/> |
| _MediaRelayExternalTurnTcpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for external media relay traffic using the Transmission Control Protocol (TCP). The default value is 444 if your Edge server has a single IP address. If your Edge server has multiple IP addresses then the default value is 443. These values are initially set in Topology Builder but can be changed by specifying a new value for this parameter.  <br/> |
| _MediaRelayExternalTurnUdpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for external media relay traffic using the User Datagram Protocol (UDP). The default value is 3478.  <br/> |
| _MediaRelayInternalTurnTcpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for internal media relay traffic using TCP. The default value is 443.  <br/> |
| _MediaRelayInternalTurnUdpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for internal media relay traffic using UDP. The default value is 3478.  <br/> |
| _Registrar_ <br/> |Optional  <br/> |System.String  <br/> |Service location of the Registrar to be associated with the Edge Server. For example:  `-Registrar "Registrar:atl-cs-001.litwareinc.com"`.  <br/> |
| _SkypeSearchProxyPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |PARAMVALUE: UInt16  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _XmppInternalPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for internal XMPP traffic. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. An allowed partner is an IM and presence provider whose users are allowed to exchange instant messages and presence information with your Skype for Business Server 2015 users. The default value is 5098.  <br/> |
| _XmppListeningPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Listening port for XMPP traffic.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None. The **Set-CsEdgeServer** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **Set-CsEdgeServer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayEdgeServer object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsService](get-csservice.md)
