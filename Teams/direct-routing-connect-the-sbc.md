---
title: "Connect your Session Border Controller (SBC) to Direct Routing"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: "Learn how to configure Microsoft Phone System Direct Routing."
---

# Connect your Session Border Controller (SBC) to Direct Routing 

This article describes how to connect your Session Border Controller (SBC) to Phone System Direct Routing.  This is step 1 of the following steps for configuring Direct Routing:

- **Step 1. Connect your SBC with Phone System and validate the connection** (This article)
- Step 2. [Enable users for Direct Routing](direct-routing-enable-users.md)
- Step 3. [Configure call routing](direct-routing-voice-routing.md)
- Step 4. [Translate numbers to an alternate format](direct-routing-translate-numbers.md) 

For information on all the steps required for setting up Direct Routing, see [Configure Direct Routing](direct-routing-configure.md).

To connect your SBC to Direct Routing, you'll need to: 

1. Connect to **Skype for Business Online** admin center by using PowerShell.            
2. Connect the SBC to the tenant.
3. Validate the connection. 

## Connect to Skype for Business Online by using PowerShell 

You can use a PowerShell session connected to the tenant to pair the SBC to the Direct Routing interface. To open a PowerShell session, follow the steps outlined in [Set up your computer for Windows PowerShell](https://docs.microsoft.com/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell). 
 
After you establish a remote PowerShell session, validate that you can see the commands to manage the SBC. To validate the commands, type or copy and paste the following command in the PowerShell session and press Enter: 

```PowerShell
Get-Command *onlinePSTNGateway*
```

The command returns the four functions shown here that will let you manage the SBC. 

<pre>
CommandType    Name                       Version    Source 
-----------    ----                       -------    ------ 
Function       Get-CsOnlinePSTNGateway    1.0        tmp_v5fiu1no.wxt 
Function       New-CsOnlinePSTNGateway    1.0        tmp_v5fiu1no.wxt 
Function       Remove-CsOnlinePSTNGateway 1.0        tmp_v5fiu1no.wxt 
Function       Set-CsOnlinePSTNGateway    1.0        tmp_v5fiu1no.wxt
</pre>   


## Connect the SBC to the tenant 

To connect the SBC to the tenant, in the PowerShell session type the following and press Enter: 

```PowerShell
New-CsOnlinePSTNGateway -Fqdn <SBC FQDN> -SipSignalingPort <SBC SIP Port> -MaxConcurrentSessions <Max Concurrent Sessions the SBC can handle> -Enabled $true 
```
  > [!NOTE]
  > 1. Microsoft recommends setting a maximum call limit in the SBC, using information that can be found in the SBC documentation. The limit will trigger a notification if the SBC is at the capacity level.
  > 2. You can only pair the SBC if the domain portion of its FQDN matches one of the domains registered in your tenant, except \*.onmicrosoft.com. Using \*.onmicrosoft.com domain names is not supported for the SBC FQDN name. For example, if you have two domain names:<br/><br/>
  > **contoso**.com<br/>**contoso**.onmicrosoft.com<br/><br/>
  > For the SBC name, you can use the name sbc.contoso.com. If you try to pair the SBC with a name sbc.contoso.abc, the system will not let you, as the domain is not owned by this tenant.<br/>
  > In addition to the domain registered in your tenant, it is important that there is a user with that domain and an assigned E3 or E5 license. If not, you will receive the following error:<br/>
  `Can not use the “sbc.contoso.com” domain as it was not configured for this tenant`.

```PowerShell
New-CsOnlinePSTNGateway -Identity sbc.contoso.com -Enabled $true -SipSignalingPort 5067 -MaxConcurrentSessions 100 
```
Returns:
<pre>
Identity              : sbc.contoso.com 
Fqdn                  : sbc.contoso.com 
SipSignalingPort     : 5067 
FailoverTimeSeconds   : 10 
ForwardCallHistory    : False 
ForwardPai            : False 
SendSipOptions        : True 
MaxConcurrentSessions : 100 
Enabled               : True   
</pre>
There are additional options that can be set during the connection process. In the previous example, however, only the minimum required parameters are shown. 
 
The following table lists the additional parameters that you can use in setting parameters for ```New-CsOnlinePstnGateway```.

|Required?|Name|Description|Default|Possible values|Type and restrictions|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Yes|FQDN|The FQDN name of the SBC |None|NoneFQDN name, limit 63 characters|String, list of allowed and disallowed characters on [Naming conventions in Active Directory for computers, domains, sites, and OUs](https://support.microsoft.com/help/909264)|
|No|MediaBypass |Parameter indicated of the SBC supports Media Bypass and the administrator wants to use it.|None|True<br/>False|Boolean|
|Yes|SipSignalingPort |Listening port used for communicating with Direct Routing services by using the Transport Layer Security (TLS) protocol.|None|Any port|0 to 65535 |
|No|FailoverTimeSeconds |When set to 10 (default value), outbound calls that are not answered by the gateway within 10 seconds are routed to the next available trunk; if there are no additional trunks, then the call is automatically dropped. In an organization with slow networks and gateway responses, that could potentially result in calls being dropped unnecessarily. The default value is 10.|10|Number|Int|
|No|ForwardCallHistory |Indicates whether call history information will be forwarded through the trunk. If enabled, the Office 365 PSTN Proxy sends two headers: History-info and Referred-By. The default value is **False** ($False). |False|True<br/>False|Boolean|
|No|ForwardPAI|Indicates whether the P-Asserted-Identity (PAI) header will be forwarded along with the call. The PAI header provides a way to verify the identity of the caller. If enabled the Privacy:ID header will also be sent. The default value is **False** ($False).|False|True<br/>False|Boolean|
|No|SendSIPOptions |Defines if an SBC will or will not send the SIP options. If disabled, the SBC will be excluded from Monitoring and Alerting system. We highly recommend that you enable SIP options. Default value is **True**. |True|True<br/>False|Boolean|
|No|MaxConcurrentSessions |Used by alerting system. When any value is set, the alerting system will generate an alert to the tenant administrator when the number of concurrent sessions is 90% or higher than this value. If the parameter is not set, the alerts are not generated. However, the monitoring system will report number of concurrent sessions every 24 hours. |Null|Null<br/>1 to 100,000 ||
|No|MediaRelayRoutingLocationOverride |Allows selecting path for media manually. Direct Routing assigns a datacenter for media path based on the public IP of the SBC. We always select closest to the SBC datacenter. However, in some cases a public IP from, for example, a US range can be assigned to an SBC located in Europe. In this case, we will be using not optimal media path. This parameter allows manually set the preferred region for media traffic. Microsoft only recommends setting this parameter if the call logs clearly indicate that automatic assignment of the datacenter for media path does not assign the closest to the SBC datacenter. |None|Country codes in ISO format||
|No|Enabled|Used to enable this SBC for outbound calls. Can be used to temporarily remove the SBC while it is being updated or during maintenance. |False|True<br/>False|Boolean|
 
## Verify the SBC connection 

To verify the connection: 
- Check if the SBC is on the list of paired SBCs. 
- Validate SIP Options. 
 
### Check if the SBC is on the list of paired SBCs 

After you connect the SBC, validate that the SBC is present in the list of paired SBCs by running the following command in a remote PowerShell session: 

```PowerShell
Get-CsOnlinePSTNGateway -Identity sbc.contoso.com  
```

The paired gateway should appear in the list as shown in the example below, and the **Enabled** parameter should display a value of **True**. 


Which returns:
<pre>
Identity              : sbc.contoso.com  
Fqdn                  : sbc.contoso.com 
SipSignalingPort     : 5067 
CodecPriority         : SILKWB,SILKNB,PCMU,PCMA 
ExcludedCodecs        :  
FailoverTimeSeconds   : 10 
ForwardCallHistory    : False 
ForwardPai            : False 
SendSipOptions        : True 
MaxConcurrentSessions : 100 
Enabled               : True 
</pre>

### Validate SIP Options flow 

To validate the pairing using outgoing SIP Options, use the SBC management interface and confirm that the SBC receives 200 OK responses to its outgoing OPTIONS messages.

When Direct Routing sees incoming OPTIONS, it will start sending outgoing SIP Options messages to the SBC FQDN configured in the Contact header field in the incoming OPTIONS message. 

To validate the pairing using incoming SIP Options, use the SBC management interface and see that the SBC sends a reply to the OPTIONS messages coming in from Direct Routing and that the response code it sends is 200 OK.


## See also

[Plan Direct Routing](direct-routing-plan.md)

[Configure Direct Routing](direct-routing-configure.md)
