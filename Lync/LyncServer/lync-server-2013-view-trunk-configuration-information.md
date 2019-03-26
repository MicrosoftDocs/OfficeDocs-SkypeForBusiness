---
title: 'Lync Server 2013: View trunk configuration information'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: View trunk configuration information
ms:assetid: ebe10e14-08c2-4797-9254-9ed89516d5cd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721927(v=OCS.15)
ms:contentKeyID: 49733862
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# View trunk configuration information in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

SIP trunk configuration settings define the relationship and capabilities between a Mediation Server and the public switched telephone network (PSTN) gateway, an IP-public branch exchange (PBX), or a Session Border Controller (SBC) at the service provider. These settings do such things as specify:

  - Whether media bypass should be enabled on the trunks.

  - The conditions under which real-time transport control protocol (RTCP) packets are sent.

  - Whether or not secure real-time protocol (SRTP) encryption is required on each trunk.

When you install Microsoft Lync Server 2013, a global collection of SIP trunk configuration settings is created for you. In addition, administrators can create custom setting collections at the site scope or at the service scope (for the PSTN gateway service, only).

<div>

## To view SIP trunk configuration information by using Lync Server Control Panel

1.  In Lync Server Control Panel, click **Voice Routing** and then click **Trunk Configuration**.

2.  On the **Trunk Configuration** tab you will see a list of all your trunk configuration settings collection; for each collection you will see values for the **Name**, **Scope**, **State**, and **Media bypass** properties, along with the number of **PSTN usages**, **Calling number rules**, and **Called number rules** associated with the collection. To see additional details about a collection of trunk configuration settings, click the collection of interest, click **Edit**, and then click **Show details**. Note that you can view detailed information only for one collection of trunk configuration settings at a time.

</div>

<div>

## Viewing SIP Trunk Configuration Information by Using Windows PowerShell Cmdlets

SIP trunk configuration settings can be viewed by using Lync Server PowerShell and the Get-CsTrunkConfiguration cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To view SIP trunk configuration information

  - To view information about all your SIP trunk configuration settings, type the following command in the Lync Server Management Shell and then press ENTER:
    
        Get-CsTrunkConfiguration
    
    That will return information similar to this:
    
        Identity                                  : Global
        OutboundTranslationRulesList              : {}
        SipResponseCodeTranslationRulesList       : {}
        OutboundCallingNumberTranslationRulesList : {}
        PstnUsages                                : {}
        Description                               :
        ConcentratedTopology                      : True
        EnableBypass                              : False
        EnableMobileTrunkSupport                  : False
        EnableReferSupport                        : True
        EnableSessionTimer                        : False
        EnableSignalBoost                         : False
        MaxEarlyDialogs                           : 20
        RemovePlusFromUri                         : False
        RTCPActiveCalls                           : True
        RTCPCallsOnHold                           : True
        SRTPMode                                  : Required
        EnablePIDFLOSupport                       : False
        EnableRTPLatching                         : False
        EnableOnlineVoice                         : False
        ForwardCallHistory                        : False
        Enable3pccRefer                           : False
        ForwardPAI                                : False
        EnableFastFailoverTimer                   : True

</div>

For more information, see the help topic for the [Get-CsTrunkConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsTrunkConfiguration) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

