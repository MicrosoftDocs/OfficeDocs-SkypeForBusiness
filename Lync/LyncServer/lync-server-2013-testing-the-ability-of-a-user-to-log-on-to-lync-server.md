---
title: 'Lync Server 2013: Testing the ability of a user to log on to Lync Server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Testing the ability of a user to log on to Lync Server
ms:assetid: d9cd0f9b-6ef2-4050-a4ca-263c5afa93ee
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn743841(v=OCS.15)
ms:contentKeyID: 63969655
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing the ability of a user to log on to Lync Server 2013

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
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsRegistration&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The Test-CsRegistration cmdlet enables you to verify that users in your organization can log on to Lync Server. When you run Test-CsRegistration, the cmdlet attempts to sign in a test user to Lync Server and then, if it is successful, disconnects that test user from the system. All of this happens without any user interaction, and without affecting any actual users. For example, suppose that the test account sip:kenmyer@litwareinc.com corresponds to a real user who has a real Lync Server account. In that case, the test will be conducted without any disruption to the real Ken Myer. When the Ken Myer test account logs off from the system, Ken Myer the person will remain logged on.

</div>

<div>

## Running the test

The Test-CsRegistration cmdlet can be run using either a preconfigured test account (see Setting Up Test Accounts for Running Lync Server Tests) or the account of any user who is enabled for Lync Server. To run this check using a test account, you just have to specify the FQDN of the Lync Server Registrar pool being tested. For example:

    Test-CsRegistration -TargetFqdn "atl-cs-001.litwareinc.com"

To run this check using an actual user account, you must first create a Windows PowerShell credentials object that contains the account name and password. You must then include that credentials object and the SIP address assigned to the account when you call Test-CsRegistration:

    $credential = Get-Credential "litwareinc\kenmyer"
    Test-CsRegistration -TargetFqdn "atl-cs-001.litwareinc.com"-UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

For more information, see the Help documentation for the [Test-CsRegistration](https://docs.microsoft.com/powershell/module/skype/Test-CsRegistration) cmdlet.

</div>

<div>

## Determining success or failure

If the specified user can log on to (and then log off from) Lync Server, you'll receive output similar to this with the Result property marked as **Success:**

TargetFqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:06.8630376

Error :

Diagnosis :

If the specified user can't log in or log out, the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:

TargetFqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:00

Error : 404, Not Found

Diagnosis : ErrorCode=1003,source=atl-cs-001.litwareinc.com,Reason=User does

not exist

Microsoft.Rtc.Signaling.DiagnosticHeader

For example, the previous output states that the test failed because the specified user couldn't be found. You can determine whether or not a SIP address is valid (and whether the user assigned that SIP address is enabled for Lync Server) by running this command:

    Get-CsUser "sip:kenmyer@litwareinc.com"

If Test-CsRegistration fails, then you might want to rerun the test, this time including the Verbose parameter:

    Test-CsRegistration -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetFqdn "atl-cs-001.litwareinc.com" -Verbose

When the Verbose parameter is included, Test-CsRegistration will return a step-by-step account of each action it tried when it checked the ability of the specified user to log on to Lync Server. For example:

VERBOSE: 'Register' activity started.

Sending Registration request:

Target Fqdn = atl-cs-011.litwareinc.com

User Sip Address = sip:kenmyer@litwareinc.com

Registrar Port = 5061.

Auth Type 'Trusted' is selected.

An exception 'The endpoint is unable to register. See the ErrorCode for specific reason' occurred during Workflow Microsoft.Rtc.SyntheticTransactions.Workflow.STRegistrerWorkflow execution.

Exception Call Stack: at Microsoft.Rtc.Signaling.SipAsyncResult'1.ThrowIfFailed()

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why Test-CsRegistration might fail:

  - You specified an incorrect user account. You can verify that a user account exists by running a command similar to this:
    
        Get-CsUser "sip:kenmyer@litwareinc.com"

  - The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account is enabled for Lync Server, run a command similar to the following:
    
        Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
    
    If the Enabled property is set to False, that means that the user is currently not enabled for Lync Server.

  - You specified an incorrect Registrar pool. You can return the FQDNs of your Registrar pools by using this command:
    
        Get-CsService -Registrar | Select-Object PoolFqdn

  - The Registrar pool is currently not available. Try pinging the pool to see whether it responds:
    
        ping atl-cs-001.litwareinc.com

</div>

</div>

<span> </span>

</div>

</div>

</div>

