---
title: 'Lync Server 2013: Testing peer to peer audio/video call'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Testing peer to peer audio/video call
ms:assetid: 95eb3693-b866-4652-bc45-9b75fdb40b49
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn743835(v=OCS.15)
ms:contentKeyID: 63969627
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing peer to peer audio/video call in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-05_


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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsP2PAV cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsP2PAV&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

Test-CsP2PAV is used to determine whether a pair of test users can participate in a peer-to-peer A/V conversation. To test this scenario, the cmdlet starts off by logging on the two users to Lync Server. Assuming that the two logons succeed, the first user then invites the second user to join an A/V call. The second user accepts the call, the connection between the two users is tested, and then the call is ended and the test users are logged off from the system.

Test-CsP2PAV does not actually conduct an A/V call. Multimedia information is not exchanged between the test users. Instead, the cmdlet merely verifies that the appropriate connections can be made and that the two users can conduct such a call.

For more information, see the Help documentation for the [Test-CsP2PAV](https://docs.microsoft.com/powershell/module/skype/Test-CsP2PAV) cmdlet.

</div>

<div>

## Running the test

The Test-CsP2PAV cmdlet can be run using either a pair of preconfigured test accounts (see Setting Up Test Accounts for Running Lync Server Tests) or the accounts of any two users who are enabled for Lync Server. To run this check using test accounts, you just have to specify the FQDN of the Lync Server pool being tested. For example:

    Test-CsP2PAV -TargetFqdn "atl-cs-001.litwareinc.com"

To run this check using actual user accounts, you must create two Lync Server credentials objects (objects that contain the account name and password) for each account. You must then include those credentials objects and the SIP addresses of the two accounts when you call Test-CsP2PAV:

    $credential1 = Get-Credential "litwareinc\kenmyer"
    $credential2 = Get-Credential "litwareinc\davidlongmire"
    Test-CsP2PAV -TargetFqdn "atl-cs-001.litwareinc.com" -SenderSipAddress "sip:kenmyer@litwareinc.com" -SenderCredential $credential1 -ReceiverSipAddress "sip:davidlongmire@litwareinc.com" -ReceiverCredential $credential2

</div>

<div>

## Determining success or failure

If the two test users can complete a peer-to-peer A/V call, then you'll receive output similar to this with the Result property marked as **Success:**

TargetFqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:06.8630376

Error :

Diagnosis :

If the test users can't complete the call, then the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:

TargetFqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:00

Error : 480, Temporarily Unavailable

Diagnosis : ErrorCode=15030,Source=atl-cs-001.litwareinc.com,Reason=Failed

to route to Exchange Server

Microsoft.Rtc.Signaling.DiagnosticHeader

For example, the previous output states that the test failed because the Microsoft Exchange Server couldn't be contacted. This error message typically indicates a problem the configuration of Exchange Unified Messaging.

If Test-CsP2PAV fails then you might want to rerun the test, this time including the Verbose parameter:

Test-CsP2PAV -TargetFqdn "atl-cs-001.litwareinc.com" -Verbose

When the Verbose parameter is included, Test-CsP2PAV will return a step-by-step account of each action it tried as it checked the ability of the specified user to log on to Lync Server. For example, suppose that your test failed with the following Diagnosis:

ErrorCode=6003,Source=atl-cs-001.litwareinc.com,Reason=Unsupported out of dialog request

If you rerun Test-CsP2PAV and include the Verbose parameter, you'll get output similar to this:

VERBOSE: 'Register' activity started.

Sending Registration request:

Target Fqdn = atl-cs-011.litwareinc.com

User Sip Address = sip:kenmyer@litwareinc.com

Registrar Port = 5062.

Auth Type 'IWA' is selected.

An exception 'The endpoint was unable to register. See the ErrorCode for specific reason.' occurred during workflow Microsoft.Rtc.SyntheticTransactions.Workflows.STP2PAVWorkflow execution.

Although it might not be immediately obvious, if you examine the output carefully you’ll see that an incorrect Registrar port (port 5062) was specified. In turn, that caused the test to fail.

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why Test-CsP2PAV might fail:

  - You specified a user account that is not valid. You can verify that a user account exists by running a command similar to this:
    
    Get-CsUser "sip:kenmyer@litwareinc.com"

  - The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account is enabled for Lync Server, run a command similar to the following:
    
        Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
    
    If the Enabled property is set to False, that means that the user is currently not enabled for Lync Server.

</div>

</div>

<span> </span>

</div>

</div>

</div>

