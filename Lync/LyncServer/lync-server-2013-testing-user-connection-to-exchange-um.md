---
title: 'Lync Server 2013: Testing user connection to Exchange UM'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Testing user connection to Exchange UM
ms:assetid: 0b83fbf4-e124-4efd-a0a9-202eb849af82
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn727300(v=OCS.15)
ms:contentKeyID: 63969573
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing user connection to Exchange UM in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-11-01_


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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the <strong>Test-CsExUMConnectivity</strong> cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsExUMConnectivity&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The **Test-CsExUMConnectivity** cmdlet verifies that the specified user can connect to the Microsoft Exchange Server 2013 unified messaging service. Note that this cmdlet only verifies that a connection can be made to the service. It does not test the service itself. To test the unified messaging service (by running a synthetic transaction cmdlet that actually leaves a voice mail message in a user's mailbox) use the Test-CsExUMVoiceMail cmdlet.

</div>

<div>

## Running the test

The following example tests Exchange Unified Messaging connectivity for the pool atl-cs-001.litwareinc.com. This command will work only if test users were defined for the pool atl-cs-001.litwareinc.com. If they have, then the command will determine whether the first test user can connect to Unified Messaging. If test users were not configured for the pool then the command will fail.

    Test-CsExUMConnectivity -TargetFqdn "atl-cs-001.litwareinc.com" 

The commands shown in the following example test Exchange Unified Messaging connectivity for the user litwareinc\\kenmyer. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credentials object for the user litwareinc\\kenmyer. Note that you must supply the password for this account to create a valid credentials object and to ensure that the **Test-CsExUMConnectivity** cmdlet can run its check.

The second command in the example uses the supplied credentials object ($x) and the SIP address of the user litwareinc\\kenmyer to determine whether or this user can connect to Exchange Unified Messaging.

    $credential = Get-Credential "litwareinc\kenmyer" 
    Test-CsExUMConnectivity -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

The command shown in the next example is a variation of the command just shown. In this case, the OutLoggerVariable parameter is included to generate a detailed log of every step done by the **Test-CsExUMConnectivity** cmdletand the success or failure of each of those steps. To do this, the OutLoggerVariable parameter is added together with the parameter value ExumText; that causes detailed logging information to be stored in a variable named $ExumTest. In the final command in the example, the ToXML() method is used to convert the log information to XML format. That XML data is then written to a file that is named C:\\Logs\\ExumTest.xml by using the Out-File cmdlet.

    $credential = Get-Credential "litwareinc\kenmyer" 
    Test-CsExUMConnectivity -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential -OutLoggerVariable ExumTest 
    $ExumTest.ToXML() | Out-File C:\Logs\ExumTest.xml 

</div>

<div>

## Determining success or failure

If Exchange integration is correctly configured, you'll receive output similar to this, with the Result property marked as **Success**:

Target Fqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:00

Error Message :

Diagnosis :

If the specified user can't receive notifications, the Result will be shown as **Failure**, and additional information will be recorded in the Error and Diagnosis properties:

Target Fqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:00

Error Message : 10060, A connection attempt failed because the connected party

did not properly respond after a period of time, or

established connection failed because connected host has

failed to respond 10.188.116.96:5061

Inner Exception:A connection attempt failed because the

connected party did not properly respond after a period of

time, or established connection failed because connected host

has failed to respond 10.188.116.96:5061

Diagnosis :

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why **Test-CsExUMConnectivity** might fail:

  - An incorrect parameter value was supplied. If used, the optional parameters must be configured correctly or the test will fail. Rerun the command without the optional parameters and see whether that succeeds.

  - This command will fail if the Exchange Server is misconfigured or not yet deployed.

  - This command will fail if the Exchange Server is not reachable over your network.

</div>

<div>

## See Also


[Test-CsExUMVoiceMail](https://docs.microsoft.com/powershell/module/skype/Test-CsExUMVoiceMail)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

