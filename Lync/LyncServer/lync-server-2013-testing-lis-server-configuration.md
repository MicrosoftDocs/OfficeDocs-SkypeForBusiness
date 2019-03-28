---
title: 'Lync Server 2013: Testing LIS server configuration'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Testing LIS server configuration
ms:assetid: 6b06e7ab-522f-41a2-878b-e89cd4e3c6da
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn690129(v=OCS.15)
ms:contentKeyID: 63969614
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing LIS server configuration in Lync Server 2013

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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsLisConfiguration cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsLisConfiguration&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The Test-CsLisConfiguration cmdlet verifies your ability to contact the LIS web service. If the web service can be contacted, then the test will be considered a success, regardless of whether any specific locations can be found.

</div>

<div>

## Running the test

The Test-CsLisConfguration cmdlet can be run using either a preconfigured test account (see Setting Up Test Accounts for Running Lync Server Tests) or the account of any user who is enabled for Lync Server. To run this check using a test account, you just have to specify the FQDN of the Lync Server pool being tested. For example:

    Test-CsLisConfiguration -TargetFqdn "atl-cs-001.litwareinc.com"

To run this check using an actual user account, you must first create a Windows PowerShell credentials object that contains the account name and password. You must then include that credentials object and the SIP address assigned to the account when you call Test-CsLisConfiguration:

    $credential = Get-Credential "litwareinc\kenmyer"
    Test-CsLisConfiguration -TargetFqdn "atl-cs-001.litwareinc.com"-UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

For more information, see the Help documentation for the [Test-CsLisConfiguration](https://docs.microsoft.com/powershell/module/skype/Test-CsLisConfiguration) cmdlet.

</div>

<div>

## Determining success or failure

If the LIS is correctly configured, you'll receive output similar to this, with the Result property marked as **Success:**

TargetUri : https://atl-cs-001.litwareinc.com:443/locationinformation/

liservice.svc

TargetFqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:06.1616913

Error :

Diagnosis :

If the specified user can't log on or log off, the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:

TargetUri :

TargetFqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:00

Error : 11004, The requested name is valid but no data of the requested

type was found

Diagnosis :

Test-CsLisConfiguration : No matching cluster found in topology.

For example, the previous output includes the note “No matching cluster found in topology.” That typically indicates a problem with the Edge Server: the LIS using the Edge Server to connect to the service provider and validate addresses.

If Test-CsLisConfiguration fails then you might want to rerun the test, this time including the Verbose parameter:

    Test-CsLisConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -Verbose

When the Verbose parameter is included, Test-CsLisConfiguration will return a step-by-step account of each action it tried when it checked the ability of the specified user to log on to Lync Server. For example:

Calling Location Information Service.

Service Path = https://atl-cs-001.litwareinc.com:443/locationinformation/liservice.svc

Subnet =

BssId = 5

ChassisId =

PortId =

PortIdSubType = Undefined Type

Mac

An exception 'Location Information Web Service request has failed with a response code Item400.' occurred during Workflow Microsoft.Rtc.SyntheticTrsnactions.Workflows.STLisConfigurationWorkflow execution.

If you examine the previous output closely, you’ll see that the cmdlet failed after it tried to call the Location Information Service. One of the parameters that were used in that call was this:

BssId = 5

That’s not a valid value for the Basic Service Set Identifier (BssID). Instead, a BssID should resemble this:

12-34-56-78-90-ab

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why Test-CsLisConfiguration might fail:

  - An incorrect parameter value was supplied. As shown in the previous example, the optional parameters must be configured correctly or the test will fail. Rerun the command without the optional parameters and see whether that succeeds.

</div>

</div>

<span> </span>

</div>

</div>

</div>

