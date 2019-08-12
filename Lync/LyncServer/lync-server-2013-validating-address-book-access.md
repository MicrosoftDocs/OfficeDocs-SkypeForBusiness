---
title: 'Lync Server 2013: Validating address book access'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Validating address book access
ms:assetid: 630682c6-9262-46c5-9af1-6193db70374b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720916(v=OCS.15)
ms:contentKeyID: 63969611
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Validating address book access in Lync Server 2013

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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsAddressBookService cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsAddressBookService&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The Test-CsAddressBookService cmdlet provides a way for you to verify that a user can connect to the Address Book Download Web service. When you run the cmdlet, Test-CsAddressBookService connects to the Address Book Download Web service on the specified pool and requests the location of the Address Book files. If the Address Book Download Web service supplies that location, the test is considered successful. If the request is denied, then the test is considered a failure.

</div>

<div>

## Running the test

The Test-CsAddressBookService cmdlet can be run using either a preconfigured test account (see Setting Up Test Accounts for Running Lync Server Tests) or the account of any user who has been enabled for Lync Server. To run this check using a test account, all you need to do is specify the fully qualified domain name (FQDN) of the Lync Server pool being tested. For example:

    Test-CsAddressBookService -TargetFqdn "atl-cs-001.litwareinc.com"

To run this check using an actual user account, you must first create a Windows PowerShell credentials object that contains the account name and password. You must then include that credentials object and the SIP address assigned to the account when calling Test-CsAddressBookService:

    $credential = Get-Credential "litwareinc\kenmyer"
    Test-CsAddressBookService -TargetFqdn "atl-cs-001.litwareinc.com"-UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

For more information, see the Help documentation for the [Test-CsAddressBookService](https://docs.microsoft.com/powershell/module/skype/Test-CsAddressBookService) cmdlet.

</div>

<div>

## Determining success or failure

If the specified user is able to connect to the Address Book Service you will get back output similar to this, with the Result property marked as **Success**:

TargetUri : https://lync-se.fabrikam.com:443/abs/handler

TargetFqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:06.2260399

Error :

Diagnosis :

If the specified user is not able to make this connection, the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:

TargetUri :

TargetFqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:00

Diagnosis : ErrorCode=4005,Source=atl-cs-001.litwareinc.com,

Reason=Destination URI either not enabled for SIP or does not

exist.

Microsoft.Rtc.Signaling.DiagnosticHeader

For example, the preceding output states that the test failed because the specified user (that is, the “Destination URI”) either does not exist or has not been enabled for Lync Server. You can verify whether or not a user account is valid, and verify that you supplied the correct SIP address, by running a command like this one:

Get-CsUser -Identity "sip:kenmyer@litwareinc.com" | Select-Object SipAddress, Enabled

If Test-CsAddressBookService fails then you might want to rerun the test, this time including the Verbose parameter:

Test-CsAddressBookService -TargetFqdn "atl-cs-001.litwareinc.com" -Verbose

When the Verbose parameter is included Test-CsAddressBookService will return a step-by-step account of each action it attempted when checking the ability of the specified user to log on to Lync Server. For example, this sample output shows that Test-CsAddressBookService, at least in this example, was able to download the Address Book file:

Sending Http GET Request.

File Path = https://atl-cs-001.litwareinc.com:443/abs/handler/f-1299.lsabs

Attempt Number = 1

TimeOut (msec) = 60000

Successfully Downloaded the ABS file https://atl-cs-001.litwareinc.com:443/abs/handler/f-1299.lsabs

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why Test-CsAddressBookService might fail:

  - You specified an invalid user account. You can verify that a user account exists by running a command similar to this:
    
        Get-CsUser "sip:kenmyer@litwareinc.com"

  - The user account is valid, but the account is not currently enabled for Lync Server. To verify that a user account has been enabled for Lync Server, run a command similar to the following:
    
        Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
    
    If the Enabled property is set to False that means that the user is not currently enabled for Lync Server.

</div>

<div>

## See Also


[Test-CsAddressBookService](https://docs.microsoft.com/powershell/module/skype/Test-CsAddressBookService)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

