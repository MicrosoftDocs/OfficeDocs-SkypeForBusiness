---
title: 'Lync Server 2013: Testing ability to IM between two users'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Testing ability to IM between two users
ms:assetid: a0f3f5c6-f115-4c3f-90ac-5fdc932b417e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn743838(v=OCS.15)
ms:contentKeyID: 63969635
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing ability to IM between two users in Lync Server 2013

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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsIM cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsIM&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The Test-CsIM cmdlet verifies that a pair of test users can exchange instant messages. When called, the Test-CsIM cmdlet starts off by trying to log on a pair of test users to Lync Server. Assuming the two logons are successful, the cmdlet then starts an IM session between the two test users. (User 1 invites User 2 to an IM session, and User 2 accepts the invitation.) After verifying that messages can be exchanged between the two users, Test-CsIM then ends the IM session and logs both users off the system.

For more information, see the Help documentation for the [Test-CsIM](https://docs.microsoft.com/powershell/module/skype/Test-CsIM) cmdlet.

</div>

<div>

## Running the Test

The Test-CsIM cmdlet can be run using either a pair of preconfigured test accounts (see Setting Up Test Accounts for Running Lync Server Tests) or the accounts of any two users who are enabled for Lync Server. To run this check using test accounts, you just have to specify the FQDN of the Lync Server pool being tested. For example:

    Test-CsIM -TargetFqdn "atl-cs-001.litwareinc.com"

To run this check using actual user accounts, you must create two Windows PowerShell credentials objects (objects that contain the account name and password) for each account. You must then include those credentials objects and the SIP addresses of the two accounts when you call Test-CsIM:

    $credential1 = Get-Credential "litwareinc\kenmyer"
    $credential2 = Get-Credential "litwareinc\davidlongmire"
    Test-CsIm -TargetFqdn "atl-cs-001.litwareinc.com" -SenderSipAddress "sip:kenmyer@litwareinc.com" -SenderCredential $credential1 -ReceiverSipAddress "sip:davidlongmire@litwareinc.com" -ReceiverCredential $credential2

For more information, see the Help documentation for the [Test-CsIM](https://docs.microsoft.com/powershell/module/skype/Test-CsIM) cmdlet.

</div>

<div>

## Determining Success or Failure

If the two users can complete an instant messaging session, you'll receive output similar to this, with the Result property marked as **Success:**

TargetFqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:06.6630911

Error :

Diagnosis :

If the test users can't complete the session, the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:

TargetFqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:00

Error : 504, Server time-out

Diagnosis : ErrorCode=2, Source=atl-cs-001.litwareinc.com,Reason=See

response code and reason phrase.

Microsoft.Rtc.Signaling.DiagnosticHeader

For example, the previous output states that the test failed because the specified user couldn't be found. You can determine whether a SIP address is valid (and whether the user assigned that SIP address was enabled for Lync Server) by running this command:

    Get-CsUser "Ken Myer" | Select-Object SipAddress, Enabled

If Test-CsIM fails, then you might want to rerun the test, this time including the Verbose parameter:

    Test-CsIM -TargetFqdn "atl-cs-001.litwareinc.com" -Verbose

When the Verbose parameter is included, Test-CsIM will return a step-by-step account of each action it tried when it checked the ability of the two test users to take part in an IM session. For example, here’s sample output that occurs when an incorrect set of user credentials (in this case, an incorrect password) is supplied to Test-CsIM:

Sending Registration request :

Target Fqdn = atl-cs-011.litwareinc.com

User Sip Address = sip:kenmyer@litwareinc.com

Registrar Port = 5061

Auth Type 'IWA' is selected.

Registration hit against sip/atl-cs-001.litwareinc.com

'Register' activity completed in '0.0601795' secs.

An exception 'The log on was denied. Check that the correct credentials are being used and the account is active.' occurred during the Workflow.

</div>

<div>

## Reasons Why the Test Might Have Failed

Here are some common reasons why Test-CsIM might fail:

  - You specified a user account that is not valid. You can verify that a user account exists by running a command similar to this:
    
        Get-CsUser "sip:kenmyer@litwareinc.com"

  - The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account is enabled for Lync Server, run a command similar to the following:
    
        Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
    
    If the Enabled property is set to False that means that the user is currently not enabled for Lync Server.

  - The instant messaging service might not be available. With Lync Server, you can configure the system so that IM is not available if the archiving database cannot be accessed. You can verify that by running a command similar to the following:
    
        Get-CsArchivingConfiguration -Identity "atl-cs-001.litwareinc.com" | Select-Object BlockOnArchiveFailure
    
    If BlockOnArchiveFailure is set to True, then you should determine whether or not the archiving database is available. You can return the locations of your archiving databases by using the following command:
    
        Get-CsService -ArchivingDatabase

  - The Archiving server might not be available. You can retrieve the FQDN of your Archiving servers by using this command:
    
        Get-CsService -ArchivingServer
    
    You can then ping the appropriate server to verify that it is available. For example:
    
        ping atl-archiving-001.litwareinc.com

</div>

</div>

<span> </span>

</div>

</div>

</div>

