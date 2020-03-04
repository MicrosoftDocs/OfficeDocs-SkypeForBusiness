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
description: "Learn how to configure and connect your SBC to Phone System Direct Routing."
---

# Connect your Session Border Controller (SBC) to Direct Routing

This article describes how to configure a Session Border Controller (SBC) and connect it to Phone System Direct Routing.  This is step 1 of the following steps to configure Direct Routing:

- **Step 1. Connect your SBC with Phone System and validate the connection** (This article)
- Step 2. [Enable users for Direct Routing](direct-routing-enable-users.md)
- Step 3. [Configure call routing](direct-routing-voice-routing.md)
- Step 4. [Translate numbers to an alternate format](direct-routing-translate-numbers.md) 

For information on all the steps required to set up Direct Routing, see [Configure Direct Routing](direct-routing-configure.md).

You can use the Microsoft Teams admin center or PowerShell to configure and connect an SBC to Direct Routing.

## Using the Microsoft Teams admin center

1. In the left navigation, go to **Voice** > **Direct Routing**, and then click the **SBCs** tab.
2. Click **Add**.
3. Enter a FQDN for the SBC. <br><br>Make sure the domain name portion of the FQDN matches a domain that's registered in your tenant and keep in mind that the `*.onmicrosoft.com` domain name isn't supported for the SBC FQDN domain name. For example, if you have two domain names, \*contoso.com and \*contoso.on.microsoft.com, use \*sbc.contoso.com as the SBC name.
4. Configure the following settings for the SBC, based on your organization's needs.

    ![Screenshot of add SBC page in the Microsoft Teams admin center](media/direct-routing-add-sbc.png)

    - **Enabled**: Turn on or turn off the SBC for outbound calls. For example, you may have to temporarily turn off the SBC while it's being updated or during maintenance.
    - **SIP signaling port**: Specify an SIP signaling port between 1 and 65535. This is the listening port that's used to communicate with Direct Routing by using the Transport Layer (TLS) protocol.
    - **Send SIP options**: Set whether the SBC will send SIP options messages. We highly recommend that you turn on this setting. When this setting is off, the SBC is excluded from the Monitoring and Alert system.
    - **Forward call history**: Set whether call history information is forwarded to the SBC. When you turn this on, the Office 365 proxy sends a History-info and Referred-by header.
    - **Forward P-Asserted-identity (PAI) header**: Set whether the PAI header, which provides a way to verify the identify of the caller, is forwarded along with the call.
    - **Concurrent call capacity**: When you set a value, the alerting system will notify you when the number of concurrent sessions is 90 percent or higher than tis value. If you don't set a value, alerts aren't generated. However, the monitoring system will report the number of concurrent sessions every 24 hours.
    - **Failover response codes**: If Direct Routing receives any 4xx or 6xx SIP error code in response to an outgoing Invite, the call is considered completed by default. Outgoing means a call from a Teams client to the PSTN with traffic flow: Teams client -> Direct Routing -> SBC -> telephony network). When you specify a failover response code, this forces Direct Routing to try another SBC (if another SBC exists in the voice routing policy of the user) when it receives the specified codes if the SBC can't make a call because of network or other issues. To learn more, see [Failover of specific SIP codes received from the Session Border Controller (SBC)](direct-routing-trunk-failover-on-outbound-call.md#failover-of-specific-sip-codes-received-from-the-session-border-controller-sbc).
    - **Failover time (seconds)**: When you set this value, outbound calls that aren't answered by the gateway within the time that you set are routed to the next available trunk. If there are no additional trunks, the call is automatically dropped. The default value is 10 seconds. In an organization with slow networks and gateway responses, this could potentially result in calls being dropped unnecessarily.
    - **Preferred country or region for media traffic**: Use to manually set your preferred country or region for media traffic. We recommend that you set this only if the call logs clearly indicate that the default assignment of the datacenter for the media path doesn't use the path closest to the SBC datacenter. <br>By default, Direct Routing assigns a datacenter based on the public IP address of the SBC, and always selects the path closest to the SBC datacenter. However, in some cases, the default path might not be the optimal path. This parameter allows you to manually set the preferred region for media traffic. 
    - **SBC supports PIDF/LO for emergency calls**: Specify whether the SBC supports Presence Information Data Format Location Object (PIDF/LO) for emergency calls.
    - **Ring phone while trying to find the user**: Set whether an audio signal is played to the caller to indicate that Teams is in the process of establishing the call. This setting only applies to Direct Routing in non-media bypass mode. Sometimes inbound calls from the PSTN to Teams clients can take longer than expected to be established. When this happens, the caller might not hear anything, the Teams client doesn't ring, and the call might be canceled by some telecommunications providers. This setting helps to avoid unexpected silences that can occur in these scenarios.
5. When you're done, click **Save**.

## Using PowerShell

To connect your SBC to Direct Routing, you'll need to:

1. [Connect to Skype for Business Online by using PowerShell](#connect-to-skype-for-business-online-by-using-powershell).
2. [Connect the SBC to the tenant](#connect-the-sbc-to-the-tenant).
3. [Verify the SBC connection](#verify-the-sbc-connection).

### Connect to Skype for Business Online by using PowerShell

You can use a PowerShell session connected to the tenant to pair the SBC to the Direct Routing interface. To open a PowerShell session, follow the steps outlined in [Set up your computer for Windows PowerShell](https://docs.microsoft.com/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).
 
After you establish a remote PowerShell session, verify that you can see the commands to manage the SBC. To verify the commands, type or copy and paste the following command in the PowerShell session, and then press Enter: 

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

### Connect the SBC to the tenant 

Use the [New-CsOnlinePSTNGateway](https://docs.microsoft.com/powershell/module/skype/new-csonlinepstngateway) cmdlet to connect the SBC to the tenant. In a PowerShell session, type the following, and then press Enter:

```PowerShell
New-CsOnlinePSTNGateway -Fqdn <SBC FQDN> -SipSignalingPort <SBC SIP Port> -MaxConcurrentSessions <Max Concurrent Sessions the SBC can handle> -Enabled $true
```

  > [!NOTE]
  > 1. We recommend that you set a maximum call limit in the SBC using information that can be found in the SBC documentation. The limit will trigger a notification if the SBC is at the capacity level.
  > 2. You can only connect the SBC if the domain portion of its FQDN matches one of the domains registered in your tenant, except \*.onmicrosoft.com. Using \*.onmicrosoft.com domain names is not supported for the SBC FQDN name. For example, if you have two domain names, **contoso**.com and **contoso**.onmicrosoft.com, you can use sbc.contoso.con for the SBC name. If you try to connect the SBC with a name such as sbc.contoso.abc, the system won't let you, as the domain is not owned by this tenant.<br/>
  > In addition to the domain registered in your tenant, it's important that there's a user with that domain and an assigned E3 or E5 license. If not, you'll receive the following error:<br/>
  `Can not use the “sbc.contoso.com” domain as it was not configured for this tenant`.

Here's an example:

```PowerShell
New-CsOnlinePSTNGateway -Identity sbc.contoso.com -Enabled $true -SipSignalingPort 5067 -MaxConcurrentSessions 100 
```

Which returns:

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

There are additional options that you can set during the connection process. In the previous example, only the minimum required parameters are shown. The following table lists the parameters that you can use for the [New-CsOnlinePSTNGateway](https://docs.microsoft.com/powershell/module/skype/new-csonlinepstngateway) cmdlet.

|Required?|Name|Description|Default|Possible values|Type and restrictions|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Yes|FQDN|The FQDN name of the SBC |None|FQDN name, limit 63 characters|String, see the list of allowed and disallowed characters at [Naming conventions in Active Directory for computers, domains, sites, and OUs](https://support.microsoft.com/help/909264)|
|No|Enabled|Used to enable this SBC for outbound calls. Can be used to temporarily remove the SBC while it's being updated or during maintenance. |False|True<br/>False|Boolean|
|Yes|SipSignalingPort |Listening port used for communicating with Direct Routing services by using the Transport Layer Security (TLS) protocol.|None|Any port|0 to 65535 |
|No|SendSIPOptions |Defines if an SBC will or won't send the SIP options. If disabled, the SBC will be excluded from Monitoring and Alerting system. We highly recommend that you enable SIP options.|True|True<br/>False|Boolean|
|No|ForwardCallHistory |Indicates whether call history information will be forwarded through the trunk. If enabled, the Office 365 PSTN Proxy sends two headers: History-info and Referred-By. |False|True<br/>False|Boolean|
|No|ForwardPAI|Indicates whether the P-Asserted-Identity (PAI) header will be forwarded along with the call. The PAI header provides a way to verify the identity of the caller. If enabled the Privacy:ID header will also be sent.|False|True<br/>False|Boolean|
|No|MaxConcurrentSessions |Used by alerting system. When any value is set, the alerting system will generate an alert to the tenant administrator when the number of concurrent sessions is 90% or higher than this value. If the parameter is not set, the alerts are not generated. However, the monitoring system will report number of concurrent sessions every 24 hours. |Null|Null<br/>1 to 100,000 ||
|No|**FailoverResponseCodes**<br>**ADDED**|If Direct Routing receives any 4xx or 6xx SIP error code in response to an outgoing Invite, the call is considered completed by default. Outgoing means a call from a Teams client to the PSTN with traffic flow: Teams client -> Direct Routing -> SBC -> telephony network). When you specify a failover response code, this forces Direct Routing to try another SBC (if another SBC exists in the voice routing policy of the user) when it receives the specified codes if the SBC can't make a call because of network or other issues. To learn more, see [Failover of specific SIP codes received from the Session Border Controller (SBC)](direct-routing-trunk-failover-on-outbound-call.md).|408, 503, 504||Int|
|No|FailoverTimeSeconds |When set to 10 (default value), outbound calls that are not answered by the gateway within 10 seconds are routed to the next available trunk; if there are no additional trunks, then the call is automatically dropped. In an organization with slow networks and gateway responses, that could potentially result in calls being dropped unnecessarily. |10|Number|Int|
|No|MediaRelayRoutingLocationOverride |Allows selecting path for media manually. Direct Routing assigns a datacenter for media path based on the public IP of the SBC. We always select closest to the SBC datacenter. However, in some cases a public IP from, for example, a US range can be assigned to an SBC located in Europe. In this case, we will be using not optimal media path. This parameter allows manually set the preferred region for media traffic. Microsoft only recommends setting this parameter if the call logs clearly indicate that automatic assignment of the datacenter for media path does not assign the closest to the SBC datacenter. |None|Country codes in ISO format||
|No|**PLACEHOLDER for PIDF/LO parameter**<br>**ADDED**|||||
|No|**GenerateRingingWhileLocatingUser**<br>**ADDED**|Set whether an audio signal is played to the caller to indicate that Teams is in the process of establishing the call. This setting only applies to Direct Routing in non-media bypass mode. Sometimes inbound calls from the PSTN to Teams clients can take longer than expected to be established. When this happens, the caller might not hear anything, the Teams client doesn't ring, and the call might be canceled by some telecommunications providers. This setting helps to avoid unexpected silences that can occur in these scenarios.|True|True<br/>False|Boolean|
|No|**MediaBypass**<br>**INCLUDE**?|This setting indicates whether the SBC supports media bypass and whether you want to use it for the SBC.|None|True<br/>False|Boolean||No|Enabled|Used to enable this SBC for outbound calls. Can be used to temporarily remove the SBC while it's being updated or during maintenance. |False|True<br/>False|Boolean|
 
### Verify the SBC connection

To verify the connection:

- [Check whether the SBC is on the list of paired SBCs](#check-whether-the-sbc-is-on-the-list-of-paired-sbcs).
- [Validate SIP options](#validate-sip-options).
 
#### Check whether the SBC is on the list of paired SBCs

After you connect the SBC, use the [Get-CsOnlinePSTNGateway](https://docs.microsoft.com/powershell/module/skype/get-csonlinepstngateway) cmdlet to verify that the SBC is present in the list of paired SBCs. Type the following in a remote PowerShell session, and then press Enter:

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

#### Validate SIP options

To validate the pairing using outgoing SIP options, use the SBC management interface and confirm that the SBC receives 200 OK responses to its outgoing OPTIONS messages.

When Direct Routing sees incoming OPTIONS, it will start sending outgoing SIP Options messages to the SBC FQDN configured in the Contact header field in the incoming OPTIONS message. 

To validate the pairing using incoming SIP options, use the SBC management interface and see that the SBC sends a reply to the OPTIONS messages coming in from Direct Routing and that the response code it sends is 200 OK.

## See also

[Plan Direct Routing](direct-routing-plan.md)

[Configure Direct Routing](direct-routing-configure.md)

[Teams PowerShell overview](teams-powershell-overview.md)
