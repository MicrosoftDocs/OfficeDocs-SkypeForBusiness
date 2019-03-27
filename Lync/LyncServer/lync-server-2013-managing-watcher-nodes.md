---
title: 'Lync Server 2013: Managing watcher nodes'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Managing watcher nodes
ms:assetid: 66deaf49-a71f-4a6e-ada0-ea8b688ee921
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688078(v=OCS.15)
ms:contentKeyID: 49733674
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing watcher nodes in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-20_

In addition to modifying the synthetic transactions that are executed on a watcher node, administrators can also use the **Set-CsWatcherNodeConfiguration** cmdlet to carry out two other important tasks: enabling and disabling the watcher node, and configuring the watcher node to use either internal URLs or external URLs when running its tests.

By default, watcher nodes are designed to periodically run all their enabled synthetic transactions. Sometimes, however, you may need to suspend those transactions. For example, if the watcher node is temporarily disconnected from the network, then there is no reason to run the synthetic transactions. Without network connectivity, those transactions are guaranteed to fail. If you want to temporarily disable a watcher node, run a command similar to this from the Lync Server Management Shell:

    Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -Enabled $False

This command will disable the execution of synthetic transactions on the watcher node atl-watcher- 001.litwareinc.com. To resume execution of the synthetic transactions, set the Enabled property back to True ($True):

    Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -Enabled $True

<div>


> [!NOTE]  
> The Enabled property can be used to turn watcher nodes on or off. If you want to permanently delete a watcher node, use the <STRONG>Remove-CsWatcherNodeConfiguration</STRONG> cmdlet:<BR>Remove-CsWatcherNodeConfiguration –Identity "atl-watcher-001.litwareinc.com"<BR>That command removes all the watcher node configuration settings from the specified computer, which prevents the computer from automatically running synthetic transactions. However, the command does not uninstall the System Center agent files or the Lync Server 2013 system files.



</div>

By default, watcher nodes use an organization's external URLs when conducting their tests. However, watcher nodes can also be configured to use the organization's internal URLs. This enables administrators to verify URL access for users located inside the perimeter network. To configure a watcher node to use internal URLs instead of external URLs, set the UseInternalWebUrls property to True ($True):

    Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -UseInternalWebUrls $True

If you reset this property to the default value of False ($False), the watcher will then use the external URLs:

    Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -UseInternalWebUrls $False

</div>

<span> </span>

</div>

</div>

</div>

