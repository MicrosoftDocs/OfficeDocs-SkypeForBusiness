---
title: 'Lync Server 2013: Testing Exchange to Lync notifications'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Testing Exchange to Lync notifications
ms:assetid: ed2d6325-3cf5-4450-9951-03092bcb0a7c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn727315(v=OCS.15)
ms:contentKeyID: 63969665
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing Exchange to Lync notifications in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-11-01_


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Verification schedule</p></td>
<td><p>Daily</p></td>
</tr>
<tr class="even">
<td><p>Testing tool</p></td>
<td><p>Windows PowerShell</p></td>
</tr>
<tr class="odd">
<td><p>Permissions required</p></td>
<td><p>When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.</p>
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the <strong>Test-CsExStorageNotification</strong> cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsExStorageNotification&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The **Test-CsExStorageNotification** cmdlet is used to verify that the Microsoft Exchange Server 2013 notification service can notify Lync Server 2013 any time updates are made to a user's Contact List. This cmdlet is valid only if you are using the unified contact store.

</div>

<div>

## Running the test

The command shown in Example 1 tests to see whether the Lync Server Storage Service can connect to the Microsoft Exchange Server mailbox notification service for the user sip:kenmyer@litwareinc.com. In this example, NetNamedPipe is used as the WCF binding.

    Test-CsExStorageNotification -SipUri "sip:kenmyer@litwareinc.com" -Binding "NetNamedPipe"

</div>

<div>

## Determining success or failure

If Exchange integration is configured correctly , you'll receive output similar to this, with the Result property marked as **Success**:

Target Fqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:00

Error Message :

Diagnosis :

If the specified user can't receive notifications, the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:

Target Fqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:00

Error Message : 10060, A connection attempt failed because the connected party

did not properly respond after a period of time, or

established connection failed because connected host has

failed to respond 10.188.116.96:5061

Inner Exception:A connection attempt failed because the

connected party did not properly respond after a period of

time, or established connection failed because connected host

has failed to respond 10.188.116.96:5061

Diagnosis :

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why **Test-CsExStorageNotification** might fail:

  - An incorrect parameter value was supplied. If used, the optional parameters must be configured correctly or the test will fail. Rerun the command without the optional parameters and see whether that succeeds.

  - This command will fail if the Microsoft Exchange Server is misconfigured or not yet deployed.

</div>

<div>

## See Also


[Test-CsExStorageConnectivity](https://docs.microsoft.com/powershell/module/skype/Test-CsExStorageConnectivity)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

