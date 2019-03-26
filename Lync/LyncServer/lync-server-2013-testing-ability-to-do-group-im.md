---
title: 'Lync Server 2013: Testing ability to do group IM'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Testing ability to do group IM
ms:assetid: ca5545bc-51ac-490f-b96b-917bb742ad04
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn743839(v=OCS.15)
ms:contentKeyID: 63969652
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing ability to do group IM in Lync Server 2013

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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsGroupIM cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsGroupIM&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The Test-CsGroupIM cmdlet verifies that users in your organization can conduct group instant messaging sessions. When you run Test-CsGroupIM, the cmdlet attempts to sign in a pair of test users to Lync Server. If successful, Test-CsGroupIM creates a new conference using the first test user, then invites the second user to join the conference. After an exchange of messages, both users are then disconnected from the system. Note that all of this happens without any user interaction, and without affecting any actual users. For example, suppose that the test account sip:kenmyer@litwareinc.com corresponds to a real user who has a real Lync Server account. In that case, the test will be conducted without any disruption to the real Ken Myer. For example, even when the Ken Myer test account logs off from the system, Ken Myer the person will remain logged on. Likewise, the real Ken Myer won't receive an invitation to join the conference. That invitation will be sent to, and accepted by, the test account.

For more information, see the Help documentation for the [Test-CsGroupIM](https://docs.microsoft.com/powershell/module/skype/Test-CsGroupIM) cmdlet.

</div>

<div>

## Running the test

The Test-CsGroupIM cmdlet can be run using either a pair of preconfigured test accounts (see Setting Up Test Accounts for Running Lync Server Tests) or the accounts of any two users who are enabled for Lync Server. To run this check using test accounts, you just have to specify the FQDN of the Lync Server pool being tested. For example:

    Test-CsGroupIM -TargetFqdn "atl-cs-001.litwareinc.com"

To run this check using actual user accounts, you must create two Lync Server Management Shell credentials objects (objects that contain the account name and password) for each account. You must then include those credentials objects and the SIP addresses of the two accounts when you call Test-CsGroupIM:

    $credential1 = Get-Credential "litwareinc\kenmyer"
    $credential2 = Get-Credential "litwareinc\davidlongmire"
    Test-CsGroupIm -TargetFqdn "atl-cs-001.litwareinc.com" -SenderSipAddress "sip:kenmyer@litwareinc.com" -SenderCredential $credential1 -ReceiverSipAddress "sip:davidlongmire@litwareinc.com" -ReceiverCredential $credential2

For more information, see the Help documentation for the [Test-CsGroupIM](https://docs.microsoft.com/powershell/module/skype/Test-CsGroupIM) cmdlet.

</div>

<div>

## Determining Success or Failure

If the two users can complete a group instant messaging session, you'll receive output similar to this with the Result property marked as **Success:**

TargetFqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:06.3812203

Error :

Diagnosis :

If the two users can't able to complete the instant messaging session, then the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:

TargetFqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:00

Error : 404, Not Found

Diagnosis : ErrorCode=4005,Source=atl-cs-001.litwareinc.com,

Reason=Destination URI either not enabled for SIP or does not

exist.

Microsoft.Rtc.Signaling.DiagnosticHeader

The previous output states that the test failed because at least one of the test accounts was not valid, either because the account does not exist or because the user has not been enabled for Lync Server. You can verify the account exists, and whether or not the account has been enabled for nm-ocs-14-3rd by running a command similar to this:

    "Ken Myer", "David Longmire" | Get-CsUser | Select-Object SipAddress, Enabled

If Test-CsGroupIM fails, then you might want to rerun the test, this time including the Verbose parameter:

    Test-CsGroupIM -TargetFqdn "atl-cs-001.litwareinc.com" -Verbose

When the Verbose parameter is included, Test-CsGroupIM will return a step-by-step account of each action it tried when it checked the ability of the specified users to participate in a group instant messaging sessions. For example, if your test fails and you are told that one or more of the user accounts is not valid, you can rerun the test using the Verbose parameter and determine which user account is not valid:

Sending Registration request:

 Target Fqdn      = atl-cs-001.litwareinc.com

 User SIP Address = sip:kenmyer@litwareinc.com

 Register Port    = 5061

Auth type 'IWA' is selected.

An exception 'The log on was denied. Check that the correct credentials are being used and the account is active'

As you can see, in this example the user who has the SIP address sip:kenmyer@litwareinc.com was not able to log on.

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why Test-CsGroupIM might fail:

  - You specified an incorrect user account. You can verify that a user account exists by running a command similar to this:
    
        Get-CsUser "sip:kenmyer@litwareinc.com"

  - The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account was enabled for Lync Server, run a command similar to the following:
    
    Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
    
    If the Enabled property is set to False, that means that the user is currently not enabled for Lync Server.

  - The instant messaging service might not be available. With Lync Server, you can configure the system so that instant messaging is not available if the archiving database cannot be accessed. You can verify that by running a command similar to the following:
    
        Get-CsArchivingConfiguration -Identity "atl-cs-001.litwareinc.com" | Select-Object BlockOnArchiveFailure
    
    If BlockOnArchiveFailure is set to True, then you should determine whether or not the archiving database is available. You can return the locations of your archiving databases by using the following command:
    
        Get-CsService -ArchivingDatabase

  - The Archiving Server might not be available. You can retrieve the FQDN of your Archiving Servers by using this command:
    
        Get-CsService -ArchivingServer
    
    You can then ping the appropriate server to verify that it is available. For example:
    
        ping atl-archiving-001.litwareinc.com

</div>

</div>

<span> </span>

</div>

</div>

</div>

