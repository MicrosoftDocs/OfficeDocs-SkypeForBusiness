---
title: 'Lync Server 2013: Test push notifications to smart phones'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Test push notifications to smart phones
ms:assetid: 8f5ca7d1-1ccb-4cb0-b417-730559e79b6e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn767948(v=OCS.15)
ms:contentKeyID: 63969626
ms.date: 03/15/2017
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test push notifications to smart phones in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2017-03-15_


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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsMcxPushNotification cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsMcxPushNotification&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The push notification service (Apple Push Notification Service and Microsoft Push Notification Service) can send notifications about events such as new instant messages or new voice mail to mobile devices such as iPhones and Windows Phones, even if the Lync client on those devices is currently suspended or running in the background. The push notification service is a cloud-based service that is running on Microsoft servers. In order to take advantage of push notifications, you must be able to connect to, and be authenticated by, the push notification clearinghouse. The Test-CsMcxPushNotification cmdlet enables administrators to verify that push notification requests can be routed through your Edge server to the push notification clearinghouse.

</div>

<div>

## Running the test

To test the push notification service, call the Test-CsMcxPushNotification cmdlet. Make sure that you specify the fully qualified domain name of your Edge server:

    Test-CsMcxPushNotification -AccessEdgeFqdn "atl-edge-001.litwareinc.com"

For more information, see the help topic for the [Test-CsMcxPushNotification](https://docs.microsoft.com/powershell/module/skype/Test-CsMcxPushNotification) cmdlet.

</div>

<div>

## Determining success or failure

If Test-CsMcxPushNotification succeeds the cmdlet will return the test result Success:

TargetFqdn : atl-cs-001.litwareinc.com

Result : Success

Latency : 00:00:00

Error :

Diagnosis :

If Test-CsMcxPushNotification is unable to connect to the push notification clearinghouse the cmdlet will typically not return a test result of Failure. Instead the command will usually fail completely. For example:

Test-CsMcxPushNotification : A 504 (Server time-out) response was received from the network and the operation failed. See the exception details for more information.

At line:1 char:27

\+ Test-CsMcxPushNotification \<\<\<\< -AccessEdgeFqdn lyncedge.mydomain.com

\+ CategoryInfo : OperationStopped: (:) \[Test-CsMcxPushNotification\], FailureResponseException

\+ FullyQualifiedErrorId : WorkflowNotCompleted,Microsoft.Rtc.Management.SyntheticTransactions.TestMcxPushNotificationCmdlet

</div>

<div>

## Reasons why the test might have failed

If the push notification service fails that usually indicates either problems communicating with your Edge server, or problems communicating with the Push Notification Clearing House. If you encounter problems when you run Test-CsMcxPushNotification, the first thing that you should do is verify that your Edge server is working correctly. One way to do that is to use the Test-CsAVEdgeConnectivity cmdlet:

    $credential = Get-Credential "litwareinc\kenmyer"
    
    Test-CsAVEdgeConnectivity -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

This check verifies that a specified user can connect to the Edge server.

If the Edge server seems to be working correctly, that often means that you are unable to connect to the push notification clearinghouse. In turn, that typically means that you either have not configured the clearinghouse URI correctly or that you do not have a DNS SRV record that points to this URL. You can verify that the URI is set to the correct value (sip:push@push.lync.com) by running this command:

    Get-CsMcxConfiguration

If the PushNotificationProxyUri property is set to anything other than sip:push@push.lync.com then you can correct that problem by using the Set-McxConfiguration cmdlet. For example, this command correctly sets the URI throughout your organization:

    Get-CsMcxConfiguration | Set-CsMcxConfiguration -PushNotificationProxyUri "sip:push@push.lync.com"

For more information, see the help topic for the [Set-CsMcxConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsMcxConfiguration) cmdlet.

If the URI is configured correctly, your next step should be to verify that you have a DNS SRV record that resolves to your SIP domain and your Edge server. For more information about how to configure these records, see the help topic DNS Requirements for Mobility. Note that the following error message usually indicates a problem with DNS records:

A 504 (Server time-out) response was received from the network and the operation failed. See the exception details for more information.

It’s also possible that Test-CsMcxConfiguration will fail with this error message:

Test-CsMcxPushNotification : Push Notification request was rejected.

At line:1 char:27

\+ Test-CsMcxPushNotification \<\<\<\<

\+ CategoryInfo : OperationStopped: (:) \[Test-CsMcxPushNotification\], SyntheticTransactionException

\+ FullyQualifiedErrorId : WorkflowNotCompleted,Microsoft.Rtc.Management.SyntheticTransactions.TestMcxPushNotificationCmdlet

The “Push notification request was rejected” message typically occurs if you have enabled URL filtering and are blocking the http: and https: prefixes. You can determine which prefixes are being blocked by using a command similar to the following:

``` 
 (Get-CsImFilterConfiguration -Identity Global).Prefixes
```

If http: or https: appear in the results, you must remove them from the blocked prefix list for push notifications to work. That can be done by using commands similar to these:

    Set-CsImFilterConfiguration -Identity site:Redmond -Prefixes @{remove="http:"}
    Set-CsImFilterConfiguration -Identity site:Redmond -Prefixes @{remove="https:"}

For more information, see the help topic for the [Set-CsImFilterConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsImFilterConfiguration)cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

