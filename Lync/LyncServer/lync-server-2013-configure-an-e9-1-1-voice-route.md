---
title: 'Lync Server 2013: Configure an E9-1-1 voice route'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure an E9-1-1 voice route
ms:assetid: 6933b840-0e7b-4509-ae43-bc9065677547
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398496(v=OCS.15)
ms:contentKeyID: 48184384
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure an E9-1-1 voice route in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-17_

To deploy E9-1-1, you first need to configure an emergency call voice route. For details about creating voice routes, see [Create a voice route in Lync Server 2013](lync-server-2013-create-a-voice-route.md). You may define more than one route if, for example, your deployment includes a primary SIP trunk and a secondary SIP trunk.

<div>


> [!NOTE]  
> To include location information in an E9-1-1 INVITE, you need to configure the SIP trunk that connects to the E9-1-1 service provider to route emergency calls through the gateway. To do this, set the EnablePIDFLOSupport flag on the <STRONG>Set-CsTrunkConfiguration</STRONG> cmdlet to True. The default value for EnablePIDFLOSupport is False. For example: <CODE>Set-CsTrunkConfiguration Service:PstnGateway:192.168.0.241 -EnablePIDFLOSupport $true.</CODE><BR>It is not necessary to enable receiving locations for fallback public switched telephone network (PSTN) gateways and Emergency Location Identification Number (ELIN) gateways.



</div>

For details about working with voice routes, see the Lync Server Management Shell documentation for the following cmdlets:

  - **Set-CsPstnUsage**

  - **Get-CsPstnUsage**

  - **New-CsVoiceRoute**

  - **Get-CsVoiceRoute**

  - **Set-CsVoiceRoute**

  - **Remove-CsVoiceRoute**

<div>

## To configure an E9-1-1 voice route

1.  Log on to the computer with an account that is a member of the RTCUniversalServerAdmins groups, or a member of the CsVoiceAdministrator administrative role.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Run the following cmdlet to create a new PSTN usage record.
    
    This must be the same name that you will use for the **PSTN** setting in the location policy. Although your deployment will have multiple phone usage records, the following example adds "Emergency Usage" to the current list of available PSTN usages. For details, see [Configuring voice policies and PSTN usage records to authorize calling features and privileges in Lync Server 2013](lync-server-2013-configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features-and-privileges.md).
    
        Set-CsPstnUsage -Usage @{add='EmergencyUsage'}

4.  Run the following cmdlet to create a new voice route by using the PSTN usage record that you created in the previous step.
    
    The number pattern must be the same number pattern that is used in the **Emergency Dial String** setting in the location policy. A "+" sign is needed because Lync adds "+" to emergency calls. "Co1-pstngateway-1" is the SIP trunk service ID for the E9-1-1 service provider or for the ELIN gateway service ID. The following example uses "EmergencyRoute" as the name of the voice route.
    
        New-CsVoiceRoute -Name "EmergencyRoute" -NumberPattern "^\+911$" -PstnUsages @{add="EmergencyUsage"} -PstnGatewayList @{add="co1-pstngateway-1"}

5.  Optionally, for SIP trunk connections, we recommend that you run the following cmdlet to create a local route for calls that are not handled by the E9-1-1 service provider’s SIP trunk. This route will be used if the connection to the E9-1-1 service provider is not available.
    
    The following example assumes that user has "Local" usage in their voice policy.
    
        New-CsVoiceRoute -Name "LocalEmergencyRoute" -NumberPattern "^\+911$" -PstnUsages @{add="Local"} -PstnGatewayList @{add="co1-pstngateway-2"}

</div>

</div>

<span> </span>

</div>

</div>

</div>

