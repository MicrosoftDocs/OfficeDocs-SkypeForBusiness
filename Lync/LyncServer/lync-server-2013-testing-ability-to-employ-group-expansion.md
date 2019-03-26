---
title: 'Lync Server 2013: Testing ability to employ group expansion'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Testing ability to employ group expansion
ms:assetid: 9b0fc954-6f9c-411a-ab32-94ebabc42de2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn743836(v=OCS.15)
ms:contentKeyID: 63969634
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing ability to employ group expansion in Lync Server 2013

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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsGroupExpansion cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsGroupExpansion&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The Test-CsGroupExpansion cmdlet lets you determine whether group expansion is working within your organization. When group expansion is enabled, users configure distribution groups as a contact. That means that those users can then send the same instant message to all the group members by addressing the message to the group instead of to individual members of that group. Group expansion enables you to quickly and easily view all the group members and their current status.

With the Test-CsGroupExpansion cmdlet, you specify an Active Directory distribution group by using the group’s email address. Test-CsGroupExpansion then uses group expansion to retrieve the group membership and compare the retrieved list to the membership of the group email address that you supplied. If the two lists match, then group expansion is working correctly. Note that you can test group expansion in two ways: by testing the service itself or by testing the associated web service.

For more information, see the Help documentation for the [Test-CsGroupExpansion](https://docs.microsoft.com/powershell/module/skype/Test-CsGroupExpansion) cmdlet.

</div>

<div>

## Running the test

The Test-CsGroupExpansion cmdlet can be run using either a preconfigured test account (see Setting Up Test Accounts for Running Lync Server Tests) or the account of any user who was enabled for Lync Server. To run this check using a test account, you just have to specify the FQDN of the Lync Server pool being tested and the email address for a valid distribution group. For example:

    Test-CsGroupExpansion -TargetFqdn "atl-cs-001.litwareinc.com" -GroupEmailAddress "Sales@litwareinc.com"

To run this check using an actual user account, you must first create a Lync Server credentials object that contains the account name and password. You must then include that credentials object and the SIP address assigned to the account when the system calls Test-CsGroupExpansion:

    $credential = Get-Credential "litwareinc\kenmyer"
    Test-CsGroupExpansion -TargetFqdn "atl-cs-001.litwareinc.com" -GroupEmailAddress "Sales@litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

For more information, see the Help documentation for the [Test-CsGroupExpansion](https://docs.microsoft.com/powershell/module/skype/Test-CsGroupExpansion) cmdlet.

</div>

<div>

## Determining success or failure

If the specified user can use group expansion, you'll receive output similar to this with the Result property marked as **Success:**

TargetUri : https://atl-cs-001.litwareinc.com:443/groupexpansion/service.svc

TargetFqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:01.1234976

Error :

Diagnosis :

If the specified user can't use group expansion, then the Result will be shown as Failure and additional information will be recorded in the Error and Diagnosis properties:

TargetUri : https://atl-cs-001.litwareinc.com:443/groupexpansion/service.svc

TargetFqdn : atl-cs-001.litwareinc.com

Result : Failure

Latency : 00:00:00

Error :

Diagnosis :

Test-CsGroupExpansion : The endpoint was unable to register. See the ErrorCode for specific reason.

The previous output states that the test failed because the specified user was unable to register with Lync Server. This will typically occur if the test account does not exist or has not enabled for Lync Server. You can verify that the account exists, and determine whether or not the account has been enabled for nm-ocs-14-3rd by running a command similar to the following:

    Get-CsUser -Identity "sip:kenmyer@litwareinc.com" | Select-Object SipAddress, Enabled

If Test-CsGroupExpansion fails, then you might want to rerun the test, this time including the Verbose parameter:

    Test-CsGroupExpansion -TargetFqdn "atl-cs-001.litwareinc.com" -GroupEmailAddress "Sales@litwareinc.com" -Verbose

When the Verbose parameter is included Test-CsGroupExpansion will return a step-by-step account of each action it tried when it checked the ability of the specified user to log on to Lync Server. For example, this output indicates that the specified distribution group couldn't be found:

Trying to get web ticket.

Web Service url : https://atl-cs-001.litwareinc.com:443/WebTicket/WebTicketService.svc

Using NTLM/Kerb auth.

GetWebTicketActivity completed.

'VerifyDistributionList' activity started.

DLX Web Service Response Status is: NotFound.

'VerifyDistributionList' activity completed in '0.2597923' secs.

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why Test-CsGroupExpansion might fail:

  - You specified an invalid user account. You can verify that a user account exists by running a command similar to this:
    
        Get-CsUser "sip:kenmyer@litwareinc.com"

  - The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account was enabled for Lync Server, run a command similar to the following:
    
        Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
    
    If the Enabled property is set to False, that means that the user is currently not enabled for Lync Server.

  - Group expansion might be disabled. It is possible to turn off group expansion. If group expansion was disabled then the Test-CsGroupExpansion cmdlet will fail. To determine whether group expansion is enabled, use a command similar to this:
    
        Get-CsWebServiceConfiguration | Select-Object Identity, EnableGroupExpansion

</div>

</div>

<span> </span>

</div>

</div>

</div>

