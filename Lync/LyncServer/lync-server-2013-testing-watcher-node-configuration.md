---
title: 'Lync Server 2013: Testing watcher node configuration'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Testing watcher node configuration
ms:assetid: f9ecd85c-0ae9-4906-b786-6b002b5a77c6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn751537(v=OCS.15)
ms:contentKeyID: 63969667
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing watcher node configuration in Lync Server 2013

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
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the <strong>Test-CsWatcherNodeConfiguration</strong> cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot; Test-CsWatcherNodeConfiguration&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

If you are using Microsoft System Center Operations Manager to monitor Lync Server 2013 then you have the option of setting up "watcher nodes": computers that periodically, and automatically, run synthetic transactions to verify that Lync Server is working as expected. Watcher nodes are assigned to pools, and are managed by using the **CsWatcherNodeConfiguration** cmdlets. Note that you do not need to install watcher nodes if you are using System Center Operations Manager. You can still monitor your system without using watcher nodes. The only difference is that any synthetic transactions that you want to run must be invoked manually instead of automatically invoked by Operations Manager.

The **Test-CsWatcherNodeConfiguration** cmdlet enables you to verify that a watcher node was configured correctly and is assigned to a valid Lync Server 2013 pool. Note that the **Test-CsWatcherNodeConfiguration** cmdlet must be run on the watcher node itself. The cmdlet cannot be run against remote computers.

</div>

<div>

## Running the test

The following command verifies the configuration settings for each watcher node that is being used in the organization.

    Test-CsWatcherNodeConfiguration

</div>

<div>

## Determining success or failure

The following successful sample output shows a system with four edge servers.

Validating target pool atl-cs-001.litwareinc.com against topology.

Success: Target pool atl-cs-001.litwareinc.com exists in topology.

Success: Target pool atl-cs-001.litwareinc.com has Registrar role installed.

Success: Target pool atl-cs-001.litwareinc.com is supported version.

Success: Port number for 5061 Target pool atl-cs-001.litwareinc.com is correct.

Checking for missing pools in watcher node configuration is started. If any error is detected, it will be printed.

Checking for missing pools in watcher node configuration is finished.

Checking for watcher node registry keys created by watcher node installation, is started. If any error is detected, it will be printed.

Checking for watcher node registry keys created by watcher node installation, is finished. Detected authentication type is Negotiate.

Successfully validated existence of test user’s credential sip:user1@ atl-cs-001.litwareinc.com in credential management store.

Successfully validated existence of test user’s credential sip:user2@ atl-cs-001.litwareinc.com in credential management store.

Checking for missing pools in watcher node configuration is started. If any error is detected, it will be printed.

WARNING: Pool atl-cs-001.litwareinc.com has Registrar

role installed, but there are no test users configured for it.

Checking for missing pools in watcher node configuration is finished.

Checking for watcher node registry keys created by watcher node installation, is

started. If any error is detected, it will be printed.

Test-CsWatcherNodeConfiguration : Cannot find Health registry key in

Software\\Microsoft\\Real-Time Communications. Make sure watcher node .msi is

installed properly.

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why **Test-CsWatcherNodeConfiguration** might fail:

  - Watcher node is not correctly installed.

  - No test users are configured.

</div>

<div>

## See Also


[Get-CsWatcherNodeConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsWatcherNodeConfiguration)  
[New-CsWatcherNodeConfiguration](https://docs.microsoft.com/powershell/module/skype/New-CsWatcherNodeConfiguration)  
[Remove-CsWatcherNodeConfiguration](https://docs.microsoft.com/powershell/module/skype/Remove-CsWatcherNodeConfiguration)  
[Set-CsWatcherNodeConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsWatcherNodeConfiguration)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

