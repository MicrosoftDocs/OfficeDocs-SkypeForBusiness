---
title: 'Lync Server 2013: Testing PSTN phone call'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Testing PSTN phone call
ms:assetid: dc7d319d-a627-45b6-a978-6111901251e3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn690133(v=OCS.15)
ms:contentKeyID: 63969656
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing PSTN phone call in Lync Server 2013

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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsRegistration cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsPstnOutboundCall&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The Test-CsPstnOutboundCall cmdlet tests the ability of a user to make a call to a phone number located on the PSTN. When you run Test-CsPstnOutboundCall, the cmdlet first attempts to log the test user on to Lync Server. If the logon succeeds, the cmdlet will then try to make a phone call across the PSTN gateway. This phone call will be made using the dial plan, voice policy, and other policies and settings assigned to the test account. When the call is answered, the cmdlet sends dual-tone multi-frequency (DTMF) codes over the network to verify media connectivity.

When conducting its test, Test-CsPstnOutboundCall will make an actual phone call: the target phone will ring and must be answered for the test to succeed. This call must also be manually ended by the administrator.

</div>

<div>

## Running the test

The Test-CsPstnOutboundCall cmdlet can be run using either a preconfigured test account (see Setting Up Test Accounts for Running Lync Server Tests) or the account of any user who is enabled for Lync Server. To run this check using a test account, you just have to specify the FQDN of the Lync Server pool being tested and the PSTN phone number being called. For example:

    Test-CsPstnOutboundCall -TargetFqdn "atl-cs-001.litwareinc.com" -TargetPstnPhoneNumber "+12065551219"

To run this check using an actual user account, you must first create a Windows PowerShell credentials object that contains the account name and password. You must then include that credentials object and the SIP address assigned to the account when you call Test-CsPstnOutboundCall:

    $credential = Get-Credential "litwareinc\kenmyer"
    Test-CsPstnOutboundCall -TargetFqdn "atl-cs-001.litwareinc.com" -TargetPstnPhoneNumber "+12065551219" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

For more information, see the Help documentation for the [Test-CsPstnOutboundCall](https://docs.microsoft.com/powershell/module/skype/Test-CsPstnOutboundCall) cmdlet.

</div>

<div>

## Determining success or failure

If the specified user can make the call, and if the call is answered, you'll receive output similar to this, with the Result property marked as **Success:**

TargetFqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:06.8630376

Error :

Diagnosis :

If the specified user can't make the call or if the call is not answered, then the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:

TargetFqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:0987365

Error : 403, Forbidden

Diagnosis : ErrorCode=12001,Source=atl-cs-001.litwareinc.com,Reason=User

Policy does not contain phone route usage

The previous output states that the test failed because the voice policy assigned to the specified user does not include a phone usage. (Phone usages tie voice policies to voice routes. Without both a voice policy and a corresponding voice route you can't make calls over the PSTN.)

If Test-CsPstnOutboundCall fails then you might want to rerun the test, this time including the Verbose parameter:

    Test-CsPstnOutboundCall -TargetFqdn "atl-cs-001.litwareinc.com" -TargetPstnPhoneNumber "+12065551219" -Verbose

When the Verbose parameter is included, Test-CsPstnOutboundCall will return a step-by-step account of each action it tried when it checked the ability of the specified user to log on to Lync Server. For example, this output indicates that network problems are preventing a connection with the PSTN:

Establishing Audio Video call to 'sip:+12065551219@litwareinc.com;user=phone'.

An exception 'A 404 (Not Found) response was received from the network and the operation failed.

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why Test-CsPstnOutboundCall might fail:

  - You specified an invalid user account. You can verify that a user account exists by running a command similar to this:
    
        Get-CsUser "sip:kenmyer@litwareinc.com"

  - The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account is enabled for Lync Server, run a command similar to the following:
    
        Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
    
    If the Enabled property is set to False that means that the user is currently not enabled for Lync Server.

  - The voice policy assigned to the specified user does not have a valid PSTN usage. You can determine the voice policy that is assigned to a user by using a command similar to this:
    
        Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object VoicePolicy
    
    And then you can determine the PSTN usages (if any) that are assigned to that policy by using a command similar to the following, which retrieves information about the per-user voice policy RedmondVoicePolicy:
    
        Get-CsVoicePolicy -Identity "RedmondVoicePolicy"

</div>

</div>

<span> </span>

</div>

</div>

</div>

