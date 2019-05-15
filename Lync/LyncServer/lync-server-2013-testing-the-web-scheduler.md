---
title: 'Lync Server 2013: Testing the Web scheduler'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Testing the Web scheduler
ms:assetid: 58e34058-1afa-42e3-9096-c4ea1954c237
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn727304(v=OCS.15)
ms:contentKeyID: 63969603
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing the Web scheduler in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-11-03_


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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the <strong>Test-CsWebScheduler</strong> cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsWebScheduler&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The **Test-CsWebScheduler** cmdlet enables you to determine whether a specific user can schedule a meeting using the Web Scheduler. The Web Scheduler enables users who are not running Outlook to schedule online meetings. Among other things, this new feature (which incorporates the functionality found in the Web Scheduler tool that was included with the Microsoft Lync Server 2010 resource kit) enables users to:

  - Schedule a new online meeting.

  - List all meetings that he or she has scheduled.

  - View/modify an existing meeting.

  - Delete an existing meeting.

  - Send an email invitation to meeting participants by using a preconfigured SMTP mail server.

  - Join an existing conference.

</div>

<div>

## Running the test

The following example verifies the Web Scheduler for the pool atl-cs-001.litwareinc.com. This command will work only if test users are defined for the pool atl-cs-001.litwareinc.com. If they have, then the command will determine whether the first test user can schedule an online meeting using the Web Scheduler.

If test users are not defined, then the command will fail because it won't know which user to log on as. If you have not defined test users for a pool, then you must include the UserSipAddress parameter and the credentials of the user the command should use when trying to log on.

    Test-CsWebScheduler -TargetFqdn "atl-cs-001.litwareinc.com"

The commands shown in the next example test the ability of a specific user (litwareinc\\kenmeyer) to schedule an online meeting using the Web scheduler. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credential object that contains the name and password of the user Ken Meyer. (Because the logon name litwareinc\\kenmeyer is included as a parameter, the Windows PowerShell Credential Request dialog box only requires the administrator to enter the password for the Ken Meyer account.) The resulting credential object is then stored in a variable named $cred1.

The second command then checks whether this user can log on to the pool atl-cs-001.litwareinc.com and schedule an online meeting. To run this task, the **Test-CsWebScheduler** cmdlet is called, together with three parameters: TargetFqdn (the FQDN of the Registrar pool); UserCredential (the Windows PowerShell object that contains Pilar Ackerman’s user credentials); and UserSipAddress (the SIP address that corresponds to the supplied user credentials).

    $credential = Get-Credential "litwareinc\kenmyer"
    
    Test-CsWebScheduler -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

</div>

<div>

## Determining success or failure

If the web scheduler is configured correctly , you'll receive output similar to this, with the Result property marked as **Success**:

Target Fqdn : atl-cs-001.litwareinc.com

Target Uri : https:// atl-cs-001.litwareinc.com.

litwareinc.com:443/Scheduler

Result : Success

Latency : 00:00:00

Error Message :

Diagnosis :

If the web scheduler is not configured correctly, the Result will be shown as **Failure**, and additional information will be recorded in the Error and Diagnosis properties:

WARNING: Failed to read Registrar port number for the given fully qualified

domain name (FQDN). Using default Registrar port number. Exception:

System.InvalidOperationException: No matching cluster found in topology.

at

Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction.TryRetri

eveRegistrarPortFromTopology(Int32& registrarPortNumber)

Target Fqdn : atl-cs-001.litwareinc.com

Target Uri :

Result : Failure

Latency : 00:00:00

Error Message : No matching cluster found in topology.

Diagnosis :

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why **Test-CsWebScheduler** might fail:

  - An incorrect parameter value was supplied. If used, the optional parameters must be configured correctly or the test will fail. Rerun the command without the optional parameters and see whether that succeeds.

  - This command will fail if the Web Scheduler is misconfigured or not yet deployed.

</div>

<div>

## See Also


[Set-CsWebServer](https://docs.microsoft.com/powershell/module/skype/Set-CsWebServer)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

