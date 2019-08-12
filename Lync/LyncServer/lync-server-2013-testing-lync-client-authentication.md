---
title: 'Lync Server 2013: Testing Lync Client authentication'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Testing Lync Client authentication
ms:assetid: e22114cb-4456-4e5f-93ab-51592c4a8209
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn689120(v=OCS.15)
ms:contentKeyID: 63969659
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing Lync Client authentication in Lync Server 2013

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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsClientAuth cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsClientAuth&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The Test-CsClientAuth cmdlet enables you to determine whether a user can log on to the Lync Server by using a client certificate, you can run the Test-CsClientAuth cmdlet. After calling Test-CsClientAuth, the cmdlet will contact the certificate provisioning service and download a copy of any client certificates for the specified user. If a client certificate can be found and downloaded, Test-CsClientAuth will then attempt to log on by using that certificate. If logon succeeds, Test-CsClientAuth will log off and report that the test succeeded. If a certificate cannot be found or downloaded, or if the cmdlet is unable to logon using that certificate, then Test-CsClientAuth will report that the test failed.

</div>

<div>

## Running the test

The Test-CsClientAuth cmdlet is run by using the account of any user who is enabled for Lync Server. To run this check using an actual user account, you must first create a Windows PowerShell credentials object that contains the account name and password. You must then include that credentials object and the SIP address assigned to the account when the system calls Test-CsClientAuth:

    $credential = Get-Credential "litwareinc\kenmyer"
    Test-CsClientAuth -TargetFqdn "atl-cs-001.litwareinc.com"-UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

For more information, see the Help documentation for the [Test-CsClientAuth](http://technet.microsoft.com/en-us/library/gg398712\(v=ocs.14\).aspx) cmdlet.

</div>

<div>

## Determining success or failure

If the specified user can log on to Lync Server by using a client certificate, you will receive output similar to this, with the Result property marked as **Success:**

TargetFqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:06.8630376

Error :

Diagnosis :

If the specified user can not log on, the Result will be shown as Failure and additional information will be recorded in the Error and Diagnosis properties:

TargetFqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:03.3645259

Error : Could not download a CS Certificate for the given user. Check if

provided uri and credentials are correct.

Diagnosis :

For example, the previous output states that the test failed because a valid client certificate couldn't be located for the specified user. You can return a list of the client certificates issued to a user by running a command as follows:

    Get-CsClientCertificate -Identity "sip:kenmyer@litwareinc.com"

If Test-CsClientAuth fails, then you might want to rerun the test, this time including the Verbose parameter:

    $credential = Get-Credential "litwareinc\kenmyer"
    Test-CsClientAuth -TargetFqdn "atl-cs-001.litwareinc.com"-UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential -Verbose

When the Verbose parameter is included, Test-CsClientAuth will return a step-by-step account of each action it tried when it checked the ability of the specified user to log on to Lync Server. For example:

Trying to download a CS certificate for User : kenmyer@litwareinc.com endpoint : STEpid

Web Service url : https://atl-cs-001.litwareinc.com:443/CertProv/CertprovisioningService.svc

Could not download a CS certificate from web service.

CHECK:

\- Web service url is valid and the web services are functional

\- If using PhoneNo\\\\Pin to authenticate, make sure they match the user uri

\- If using NTLM\\Kerberos auth, make sure you provided valid credentials

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why Test-CsClientAuth might fail:

  - You specified a user account that was not valid. You can verify that a user account exists by running a command similar to this:
    
        Get-CsUser "sip:kenmyer@litwareinc.com"

  - The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account is enabled for Lync Server, run a command similar to the following:
    
        Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
    
    If the Enabled property is set to False, that means that the user is currently not enabled for Lync Server.

  - The test user might not have a valid client certificate. You can return information about the client certificates assigned to a user by using a command similar to this:
    
        Get-CsClientCertificate -Identity "sip:kenmyer@litwareinc.com"

</div>

</div>

<span> </span>

</div>

</div>

</div>

