---
title: 'Lync Server 2013: Test Web App access'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Test Web App access
ms:assetid: 17d67ea3-f74d-4952-ac2b-92c0dacc8014
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn767944(v=OCS.15)
ms:contentKeyID: 63969584
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test Web App access in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-07_


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Verification schedule</p></td>
<td><p>Monthly</p></td>
</tr>
<tr class="even">
<td><p>Testing tool</p></td>
<td><p>Windows PowerShell</p></td>
</tr>
<tr class="odd">
<td><p>Permissions required</p></td>
<td><p>When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.</p>
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsWebApp cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsWebApp&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The Test-CsWebApp cmdlet verifies that authenticated users can join Lync Server conferences by using the Lync Web App. When you run the cmdlet, Test-CsWebApp contacts the Web Ticket service to obtain web tickets for the specified users. These tickets effectively act as ‘admission tickets” to the Lync Server conference. If the tickets can be retrieved, and if the users can be authenticated, Test-CsWebApp will then contact Lync Server and attempt to establish separate conferences for instant messaging, application sharing, and data collaboration.

Note that Test-CsWebApp just verifies the APIs and connections used to create these conferences. The cmdlet is designed to verify that Lync Web App could be used to create and join conferences. However,, it does not actually create and conduct a conference.

</div>

<div>

## Running the test

The Test-CsWebApp cmdlet can be run using either a pair of preconfigured test accounts or the accounts of any two users who are enabled for Lync Server. To run this check using test accounts, you just have to specify the fully qualified domain name of the Lync Server pool being tested. For example:

    Test-CsWebApp -TargetFqdn "atl-cs-001.litwareinc.com"

To run this check using actual user accounts, you must create two Windows PowerShell credentials objects (objects that contain the account name and password) for each account. You must then include those credentials objects and the SIP addresses of the two accounts when you call Test-CsWebApp:

    $cred1 = Get-Credential "litwareinc\kenmyer"
    $cred2 = Get-Credential "litwareinc\pilar"
    
    Test-CsWebApp -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred1 -User2SipAddress "sip:pilar@litwareinc.com" -User2Credential $cred2

For more information, see the help topic for the [Test-CsWebApp](https://docs.microsoft.com/powershell/module/skype/Test-CsWebApp) cmdlet. Note that Test-CsWebApp was deprecated for use on Lync Server 2013.

</div>

<div>

## Determining success or failure

If Test-CsWebApp can join the users to their conferences, the cmdlet will return the test result Success:

Target Fqdn :

Result : Success

Latency : 00:00:00

Error Message :

Diagnosis :

If the users cannot join the necessary conferences then the test result will be marked as Failure. Typically Test-CsWebApp will also report back a detailed error message and diagnosis:

Target Fqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:00

Error Message : No response received for Web-Ticket service

Diagnosis : The HTTP request is unauthorized with client

authentication scheme 'Ntlm'. The authentication

header received from the server was 'Negotiate,NTLM'.

</div>

<div>

## Reasons why the test might have failed

Test-CsWebApp failures typically involve user authentication errors. If Test-CsWebApp fails, you should first verify that the specified users have valid user accounts and are enabled for Lync Server. You can retrieve account information by using a command similar to this:

    Get-CsUser -Identity "sip:kenmyer@litwareinc.com" | Select-Object Enabled

If the Enabled property is not equal to True or if the command fails, that means that the user does not have a valid Lync Server account.You should also verify that the passwords that you supplied to the cmdlet are valid.

</div>

</div>

<span> </span>

</div>

</div>

</div>

