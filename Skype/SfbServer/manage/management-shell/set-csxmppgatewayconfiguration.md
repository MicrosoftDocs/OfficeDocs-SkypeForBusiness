---
title: "Set-CsXmppGatewayConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2b90d563-a3fe-45bd-81da-210a7459411b
description: "Modifies the XMPP gateway configuration settings in use in the organization. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. XMPP gateways enable Skype for Business Server 2015 users to exchange instant message and presence information with users from IM and presence providers that employ XMPP. This cmdlet was introduced in Lync Server 2013."
---

# Set-CsXmppGatewayConfiguration
[]
Modifies the XMPP gateway configuration settings in use in the organization. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. XMPP gateways enable Skype for Business Server 2015 users to exchange instant message and presence information with users from IM and presence providers that employ XMPP. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsXmppGatewayConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

Example 1 modifies the ConnectionLimit property for the global collection of XMPP gateway settings.
  
```
Set-CsXmppGatewayConfiguration -Identity "global" -ConnectionLimit 1200
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Extensible Messaging and Presence Protocol (XMPP) is a standard communications protocol (based on XML) used for sending messages across the Internet. XMPP was originally named Jabber, and is supported by a number of Internet messaging and communication applications, including Google Talk and Facebook Chat.
  
The XMPP gateway that enables Skype for Business to communicate with users on an XMPP network was originally released as an add-on to Microsoft Lync Server 2010; in Skype for Business Server 2015, this functionality is built into the software. This means that your users can communicate with XMPP users provided that you:
  
> Configure the XMPP gateway settings.
    
> Configure the other XMPP network (for example, Google Talk) as an allowed XMPP partner.
    
Note that Skype for Business Server 2015 provides only a single, global set of XMPP configuration settings: you cannot selectively enable or disable XMPP for a given site or a given Registrar pool. In fact you cannot enable or disable XMPP at all: XMPP is always enabled. If you do not want users communicating with XMPP networks then you should remove all the allowed XMPP partners. Users can only communicate with an XMPP network if that network has been configured as an allowed partner.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Set-CsXmppGatewayConfiguration** cmdlet are not available in the Skype for Business Server Control Panel
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _ConnectionLimit_ <br/> |Optional  <br/> |System.UInt32  <br/> |Total number of simultaneous connections allowed for all XMPP partners. The default value is 1000.  <br/> |
| _DialbackPassphrase_ <br/> |Optional  <br/> |System.String  <br/> |Password used when connecting to an XMPP partner over a TCP dialback connection. With TCP dialback, the partner contacts the XMPP gateway and then hangs up. The XMPP gateway calls the partner back, and the communication session can then begin.  <br/> |
| _EnableLoggingAllMessageBodies_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, Skype for Business Server 2015 will log the actual content of all instant messages. For privacy reasons, message content is typically deleted and only information about the communicating endpoints is included in the log files.  <br/> The default value is False.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the XMPP gateway configuration settings to be modified. Because you can only have a single, global instance of these settings, you do not need to specify an Identity when calling the **Set-CsXmppGatewayConfiguration** cmdlet. If you prefer, however, you can use the following syntax to reference the global settings: <br/>  `-Identity global` <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _KeepAliveInterval_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum amount of time (in seconds) that can elapse before the partner must send a "keep alive" message. (A keep alive message simply verifies that the connection is still active.) If the time interval expires before a keep alive message is received, the connection will be closed. The default value is 300 seconds.  <br/> |
| _PartnerConnectionLimit_ <br/> |Optional  <br/> |System.UInt32  <br/> |Total number of simultaneous connections allowed for a single XMPP partner. The default value is 20.  <br/> |
| _StreamEstablishmentTimeout_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum amount of time (in seconds) allotted for the XMPP partner to establish an XMPP stream. If this timeout period is surpassed the connection will automatically be terminated. The default value is 60 seconds.  <br/> |
| _StreamInactivityTimeout_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum amount of time (in seconds) that an XMPP stream can be inactive before the connection is automatically terminated. The default value is 600 seconds (10 minutes).  <br/> |
| _SubscriptionRefreshInterval_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum amount of time (in seconds) that can elapse before the partner must refresh its presence subscription. The default value is 28800 seconds (8 hours).  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsXmppGatewayConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppGatewaySettings object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsXmppGatewayConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppGatewaySettings object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsXmppGatewayConfiguration](get-csxmppgatewayconfiguration.md)

