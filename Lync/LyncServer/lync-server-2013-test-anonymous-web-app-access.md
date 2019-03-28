---
title: 'Lync Server 2013: Test anonymous Web App access'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Test anonymous Web App access
ms:assetid: 92f691cd-e05e-4bab-beb5-251d4b837a19
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn767949(v=OCS.15)
ms:contentKeyID: 63969630
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test anonymous Web App access in Lync Server 2013

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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsWebAppAnonymous cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsWebAppAnonymous&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The Test-CsWebAppAnonymous cmdlet verifies that an anonymous user can join Lync Server conferences by using the Lync Web App. When you run the cmdlet, Test-CsWebAppAnonymous contacts the Web Ticket service to obtain a web ticket for the anonymous user. If the cmdlet succeeds in obtaining this ticket, Test-CsWebAppAnonymous will then contact Lync Server and attempt to establish separate conferences for instant messaging, application sharing, and data collaboration.

Note that Test-CsWebAppAnonymous only verifies the APIs and connections used to create these conferences. The cmdlet does not actually create and conduct any conferences.

</div>

<div>

## Running the test

The Test-CsWebAppAnonymous cmdlet can be run using either a pair of preconfigured test accounts or the accounts of any two users who are enabled for Lync Server. To run this check using test accounts, you just have to specify the fully qualified domain name of the Lync Server pool being tested. For example:

    Test-CsWebAppAnonymous -TargetFqdn atl-cs-001.litwareinc.com

To run this check using actual user accounts, you must create two Lync Server Management Shell credentials objects (objects that contain the account name and password) for each account. You must then include those credentials objects and the SIP addresses of the two accounts when you call Test-CsWebAppAnonymous:

    $cred1 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsWebApp -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred1

For more information, see the help topic for the Test-CsWebAppAnonymous cmdlet. Note that Test-CsWebAppAnonymous is deprecated for use on Lync Server 2013.

</div>

<div>

## Determining success or failure

If Test-CsWebAppAnonymous can join the anonymous user to his or her conferences, the cmdlet will return the test result Success:

Target Fqdn :

Result : Success

Latency : 00:00:00

Error Message :

Diagnosis :

If the anonymous user can't join the necessary conferences then the test result will be marked as Failure. Typically Test-CsWebAppAnonymous will also report back a detailed error message and diagnosis:

Target Fqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:05.9746266

Error Message : No response received for Web-Ticket service

Diagnosis : The HTTP request is unauthorized with client

authentication scheme 'Ntlm'. The authentication

header received from the server was 'Negotiate,NTLM'.

</div>

<div>

## Reasons why the test might have failed

Test-CsWebAppAnonymous failures usually revolve around user authentication errors: you must run the test using a valid user account even though the cmdlet is checking the ability of an anonymous user to connect to Lync Server. If Test-CsWebAppAnonymous fails, you should verify that the specified user has valid a Lync Server user account. You can retrieve Lync Server account information by using a command similar to this:

    Get-CsUser -Identity "sip:kenmyer@litwareinc.com" | Select-Object Enabled

If the Enabled property is not equal to True or if the command fails, that means that the user does not have a valid Lync Server account.

You should also verify that the password that you supplied when you run the cmdlet is a valid password.

Configuration problems with Office Web Apps Server can also cause Test-CsWebAppAnonymous to fail; that will often be the case if you receive the following diagnosis:

The HTTP request is unauthorized with client authentication scheme 'Ntlm'. The authentication header received from the server was 'Negotiate,NTLM'.

For more information on diagnosing and resolving Office Web Apps Server problems see the blog post [Office Web Apps Server 2013 - machines are always reported as Unhealthy](http://www.wictorwilen.se/office-web-apps-server-2013---machines-are-always-reported-as-unhealthy).

</div>

</div>

<span> </span>

</div>

</div>

</div>

