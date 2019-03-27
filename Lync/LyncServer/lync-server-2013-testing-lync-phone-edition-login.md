---
title: 'Lync Server 2013: Testing Lync Phone Edition login'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Testing Lync Phone Edition login
ms:assetid: 1ccde6bf-9a2d-4fcf-b81f-1bc9fee2cfbb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn690128(v=OCS.15)
ms:contentKeyID: 63969583
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing Lync Phone Edition login in Lync Server 2013

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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsPhoneBootstrap cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsPhoneBootstrap&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The Test-CsPhoneBootstrap cmdlet enables administrators to verify that a given user—using the phone number and PIN assigned to him or her—can log on to the system from a Lync 2013 Phone Edition-compatible device. (No device is actually needed to run the test.)

In order for Test-CsPhoneBootstrap to make its check, the Registrar pool that hosts the user account being tested must be discoverable using DHCP. To determine whether a Registrar is discoverable in this manner, use the cmdlet Get-CsRegistrarConfiguration and check the value of the EnableDHCPServer property. If this property is set to False, you must use Set-CsRegistrarConfiguration to set the property value to True and make the Registrar discoverable using DHCP. This can also be done by using Enterprise DHCP Server and configuring the Lync Server-specific options.

</div>

<div>

## Running the test

To run the Test-CsPhoneBootstrap cmdlet, you must, at a minimum, supply the phone number and client personal identification number (PIN) for a valid Lync Server user. For example, this command tests the logon ability for the user who has the phone number 12065551219 and the PIN 0712:

    Test-CsPhoneBootstrap -PhoneOrExt "+12065551219" -Pin "0712"

For a more comprehensive check, you can also include the user’s SIP address. In that case, the phone number, client PIN, and SIP address must all be valid for the test to succeed:

    Test-CsPhoneBootstrap -PhoneOrExt "+12065551219" -Pin "0712" -UserSipAddress "sip:kenmyer@litwareinc.com"

For more information, see the Help documentation for the [Test-CsPhoneBootstrap](https://docs.microsoft.com/powershell/module/skype/Test-CsPhoneBootstrap) cmdlet.

</div>

<div>

## Determining success or failure

If the specified user was able to connect to Lync Server, you'll receive output similar to this, with the Result property marked as **Success:**

TargetUri : https://atl-cs-001.litwareinc.com:443/CertProv/

CertProvisioningService.svc

TargetFqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:06.3981276

Error :

Diagnosis :

If the specified user was not able to make a connection, then the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:

TargetFqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:04.1993845

Error : ERROR - No response received for Web-Ticket service.

Diagnosis :

The previous output states that the test failed because the Web Ticket service did not respond. This could be due to a problem with the service itself, or it might be due to the SIP address, phone number, or client PIN passed to Test-CsPhoneBootstrap. You can verify the user’s SIP address and phone number by using a command similar to this one:

    Get-CsUser -Identity "sip:kenmyer@litwareinc.com" | Select-Object SipAddress, LineUri

And you can verify that the user has a valid PIN by using a command as follows:

    Get-CsClientPinInfo -Identity "sip:kenmyer@litwareinc.com" 

If Test-CsPhoneBootstrap fails, then you might want to rerun the test, this time including the Verbose parameter:

    Test-CsPhoneBootstrap -PhoneOrExt "+12065551219" -Pin "0712" -Verbose

When the Verbose parameter is included, Test-CsPhoneBootstrap will return a step-by-step account of each action it tried when it checked the ability of the specified user to log on to Lync Server. For example, here is a portion of the output for an unsuccessful logon, a session in which an incorrect PIN was included:

Using PIN auth with Phone\\Ext : 12065551219 Pin : 0712

Could not get web ticket

CHECK :

\- Web service url is valid and the web services are functional

\- If using PhoneNo\\PIN to authenticate, make sure they match the user uri

\- If using NTLM\\Kerberos auth, make sure you provided valid credentials

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why Test-CsPhoneBootstrap might fail:

  - You might have specified a SIP address that is not valid. You can verify that a SIP address is correct by using a command such as this one:
    
        Get-CsUser -Identity "sip:kenmyer@litwareinc.com"

  - You might have specified a PIN that is not valid. Although you can't retrieve the user’s PIN number, you can verify that the user at least has a PIN number by using a command similar to this:
    
        Get-CsClientPinInfo -Identity "sip:kenmyer@litwareinc.com"

  - You might have specified a phone number that is not valid. You can verify a user’s phone by using a command similar to the following:
    
        Get-CsUser -Identity "sip:kenmyer@litwareinc.com" | Select-Object LineUri

  - The Registrar pool is not DHCP-enabled. To determine whether your Registrar pool is enabled for DHCP, run the Get-CsRegistrarConfiguration cmdlet and check the value of the EnableDHCPServer property. For example:
    
        Get-CsRegistrarConfiguration -Identity "global"

</div>

</div>

<span> </span>

</div>

</div>

</div>

