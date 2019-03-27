---
title: 'Lync Server 2013: Hosted Exchange user management'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Hosted Exchange user management
ms:assetid: e8723af5-0604-4d7d-bad2-463a9832efb4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399037(v=OCS.15)
ms:contentKeyID: 48185887
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Hosted Exchange user management in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-18_

To provide voice mail services for Lync Server 2013 users whose mailboxes are located on a hosted Exchange service, you must enable their user accounts for hosted voice mail.

<div>


> [!NOTE]  
> Before a Lync Server 2013 user can be enabled for hosted voice mail, a hosted voice mail policy that applies to the corresponding user account must be deployed. The policy can be global, site, or per-user in scope, as long as it applies to the user whom you want to enable. For details, see <A href="lync-server-2013-hosted-voice-mail-policies.md">Hosted voice mail policies in Lync Server 2013</A>.



</div>

<div>

## The msExchUCVoiceMailSettings Attribute

Lync Server 2013 introduces a new user attribute named **msExchUCVoiceMailSettings**, which is created as part of the Lync Server 2013 Active Directory schema preparation. This multivalued attribute holds voice mail settings that are shared by Lync Server 2013 and the hosted Exchange service.

The hosted Exchange service may in some cases set the value of the msExchUCVoiceMailSettings attribute in the process of enabling Exchange UM, or during the process of transferring mailboxes to a hosted Exchange Server. If this attribute is not set by Exchange, the Lync Server 2013 administrator must set it by running the Set-CsUser cmdlet, as described earlier in this topic.

The attribute’s key/value pairs and their authors are shown in the following table.

### The msExchUCVoiceMailSettings Attribute Key/Value Pairs

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Value</th>
<th>Author</th>
<th>Meaning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ExchangeHostedVoiceMail=1</p></td>
<td><p>Exchange</p></td>
<td><p>User has been enabled for hosted UM access by Exchange Server. The Exchange UM Routing application will check the user’s hosted voice mail policy for routing details.</p></td>
</tr>
<tr class="even">
<td><p>ExchangeHostedVoiceMail=0</p></td>
<td><p>Exchange</p></td>
<td><p>User has been disabled for hosted UM access by Exchange Server.</p></td>
</tr>
<tr class="odd">
<td><p>CsHostedVoiceMail=1</p></td>
<td><p>Lync Server</p></td>
<td><p>User has been enabled for hosted UM access by Lync Server 2013. The Lync Server 2013 ExUM Routing application will check the user’s hosted voice mail policy for routing details.</p></td>
</tr>
<tr class="even">
<td><p>CsHostedVoiceMail=0</p></td>
<td><p>Lync Server</p></td>
<td><p>User has been disabled for hosted UM access by Lync Server 2013.</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> If the attribute already has values other than one of the Lync Server 2013 key/value pairs (CSHostedVoiceMail=0 or CSHostedVoiceMail=1), a warning will indicate that the attribute may be managed by a different application. For example, a warning is displayed if the key/value pair ExchangeHostedVoiceMail=0 or ExchangeHostedVoiceMail=1 is already present. In that case, you can change the value by editing it the Active Directory, or run the following cmdlet to set the value to null:<BR>Set-CsUser –identity user –HostedVoicemail $null



</div>

</div>

<div>

## Enabling Users for Hosted Voice Mail

To enable a user’s voice mail calls to be routed to hosted Exchange UM, you must run the Set-CsUser cmdlet to set the value of the *HostedVoiceMail* parameter. This parameter also signals Lync Server 2013 to light up the “call voice mail” indicator.

  - The following example enables Pilar Ackerman’s user account for hosted voice mail:
    
        Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $True
    
    The cmdlet verifies that a hosted voice mail policy (global, site-level or per-user) applies to this user. If no policy applies, the cmdlet fails.

  - The following example disables Pilar Ackerman’s user account for hosted voice mail:
    
        Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $False
    
    The cmdlet verifies that no hosted voice mail policy (global, site-level or per-user) applies to this user. If a policy does apply, the cmdlet fails.

For details about using the Set-CsUser cmdlet, see the Lync Server Management Shell documentation.

</div>

</div>

<span> </span>

</div>

</div>

</div>

