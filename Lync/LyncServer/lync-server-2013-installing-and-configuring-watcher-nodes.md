---
title: 'Lync Server 2013: Installing and configuring watcher nodes'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Installing and configuring watcher nodes
ms:assetid: 61f6deea-e3ef-4468-9be8-a65705815ebb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204943(v=OCS.15)
ms:contentKeyID: 48184284
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Installing and configuring watcher nodes in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-07_

*Watcher nodes* are computers that periodically run Lync Server synthetic transactions. *Synthetic transactions* are Windows PowerShell cmdlets that verify that key end user scenarios—such as the ability to sign in to the system, or the ability to exchange instant messages—are working as expected. For Lync Server 2013, System Center Operations Manager can run the synthetic transactions shown in the following table. There are three different synthetic transaction types shown in the table:

  - **Default**. These are the synthetic transactions that a watcher node will run by default. When you create a new watcher node, you have the option of specifying which synthetic transactions that node will run. (That's the purpose of the Tests parameter used by the **New-CsWatcherNodeConfiguration** cmdlet.) If you do not use the Tests parameter when the watcher node is created, it will automatically run all the Default synthetic transactions and will not run any of the Non-default synthetic transactions. That means, for example, that the watcher node will be configured to run the Test-CsAddressBookService test, but will not be configured to run the Test-CsExumConnectivity test.

  - **Non-default**. As the name implies, Non-default synthetic transactions are tests that watcher nodes do not run by default. However, the watcher node can be enabled to run any of the Non-default synthetic transactions. You can do this when you create the watcher node (by using the **New-CsWatcherNodeConfiguration** cmdlet), or at any time after that. Many of the Non-default synthetic transactions require extra setup steps. For details, see [Special setup instructions for synthetic transactions in Lync Server 2013](lync-server-2013-special-setup-instructions-for-synthetic-transactions.md).

  - **Extended**. Extended tests are a special type of Non-default synthetic transaction. Unlike other synthetic transactions, Extended tests can be run multiple times during each pass. This can be useful when verifying behavior such as multiple public switched telephone network (PSTN) voice routes for a pool. This can be configured simply by adding multiple instances of an Extended test to a watcher node.

For details about the process of adding other synthetic transactions to a watcher node, see [Managing watcher nodes in Lync Server 2013](lync-server-2013-managing-watcher-nodes.md). You can use the Lync Server Management Shell to remove synthetic transactions from a watcher node.

The synthetic transactions available to watcher nodes include the following:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet Name (Test Name)</th>
<th>Description</th>
<th>Synthetic Transaction Type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Test-CsAddressBookService (ABS)</p></td>
<td><p>Confirms that users are able to look up users that aren’t in their contact list.</p></td>
<td><p>Default</p></td>
</tr>
<tr class="even">
<td><p>Test-CsAddressBookWebQuery (ABWQ)</p></td>
<td><p>Confirms that users are able to look up users that aren’t in their contact list via HTTP.</p></td>
<td><p>Default</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsIM (IM)</p></td>
<td><p>Confirms that users are able to send peer-to-peer instant messages.</p></td>
<td><p>Default</p></td>
</tr>
<tr class="even">
<td><p>Test-CsP2PAV (P2PAV)</p></td>
<td><p>Confirms that users are able to place peer-to-peer audio calls (signaling only).</p></td>
<td><p>Default</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsPresence (Presence)</p></td>
<td><p>Confirms that users are able to view other users’ presence.</p></td>
<td><p>Default</p></td>
</tr>
<tr class="even">
<td><p>Test-CsRegistration (Registration)</p></td>
<td><p>Confirms that users are able sign in to Lync.</p></td>
<td><p>Default</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsAudioConferencingProvider (ACP)</p></td>
<td><p>Not used with the on-premises version of Lync Server 2013</p></td>
<td><p>Extended</p></td>
</tr>
<tr class="even">
<td><p>Test-CsPstnPeerToPeerCall (PSTN)</p></td>
<td><p>Confirms that users are able to place and receive calls with people outside of the enterprise (PSTN numbers).</p></td>
<td><p>Non-default, Extended</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsAVConference (AvConference)</p></td>
<td><p>Confirms that users are able to create and participate in an audio/video conference.</p></td>
<td><p>Default</p></td>
</tr>
<tr class="even">
<td><p>Test-CsAVEdgeConnectivity (AVEdgeConnectivity)</p></td>
<td><p>Confirms that the A/V Edge servers are able to accept connections for peer-to-peer calls and conference calls.</p></td>
<td><p>Non-default</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsDataConference (DataConference)</p></td>
<td><p>Confirms that users can participate in a data collaboration conference, an online meeting that includes activities such as whiteboards and polls.</p></td>
<td><p>Non-default</p></td>
</tr>
<tr class="even">
<td><p>Test-CsExumConnectivity (ExumConnectivity)</p></td>
<td><p>Confirms that a user can connect to Exchange Unified Messaging (UM).</p></td>
<td><p>Non-default</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsGroupIM (GroupIM)</p></td>
<td><p>Confirms that users are able to send instant messages in conferences and participate in instant message conversations with three or more people.</p></td>
<td><p>Default</p></td>
</tr>
<tr class="even">
<td><p>Test-CsGroupIM –TestJoinLauncher (JoinLauncher)</p></td>
<td><p>Confirms that users are able to create and join scheduled meetings via a web address link.</p></td>
<td><p>Non-default</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsMCXP2PIM (MCXP2PIM)</p></td>
<td><p>Confirms that mobile device users are able to register and send instant messages.</p></td>
<td><p>Non-default</p></td>
</tr>
<tr class="even">
<td><p>Test-CsPersistentChatMessage (PersistentChatMessage)</p></td>
<td><p>Confirms that users can exchange messages by using the Persistent Chat service.</p></td>
<td><p>Non-default</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsUnifiedContactStore (UnifiedContactStore)</p></td>
<td><p>Confirms that a user's contacts can be accessed through the unified contact store. The unified contact store provides a way for users to maintain a single set of contacts that can be accessed by using Lync 2013, Outlook, and/or Outlook Web Access.</p></td>
<td><p>Non-default</p></td>
</tr>
<tr class="even">
<td><p>Test-CsXmppIM (XmppIM)</p></td>
<td><p>Confirms that an instant message can be sent across the XMPP (Extensible Messaging and Presence Protocol) gateway.</p></td>
<td><p>Non-default</p></td>
</tr>
</tbody>
</table>


You do not need to install watcher nodes in order to use System Center Operations Manager. If you do not install these nodes, you can still get real-time alerts from Lync Server 2013 components when an issue occurs. (The Component and User Management Pack does not use watcher nodes.) However, watcher nodes are required if you want to monitor end-to-end scenarios by using the Active Monitoring Management pack.

<div>


> [!NOTE]  
> Administrators can also run synthetic transactions manually, without needing to use, or install, Operations Manager. For details about the various Test-Cs cmdlets, see the <A href="https://docs.microsoft.com/powershell/module/skype/?view=skype-ps">Lync Server 2013 cmdlets index</A>.



</div>

Depending on the size of your deployment, synthetic transactions may use a large amount of computer memory and processor time. For this reason, we recommend that you use a dedicated computer as a watcher node. For example, you should not configure a Front End Server to act as a watcher node. Watcher nodes should meet the following hardware specifications:

<div>


> [!NOTE]  
> A legacy Microsoft Lync Server 2010 watcher node cannot be collocated on the same machine with a Lync Server 2013 watcher node. This is because the core system files for Lync Server 2010 and Lync Server 2013 cannot be installed on the same computer.<BR>However, Lync Server 2013 watcher nodes can simultaneously monitor both Lync Server 2013 and Lync Server 2010. The Default synthetic transactions are supported on both product versions.



</div>

Lync Server 2013 watcher nodes may be deployed inside or outside of an enterprise to help verify:

  - <span></span>  
    Connectivity to pools for users inside the enterprise.

  - <span></span>  
    Connectivity through perimeter networks for remote users who work outside the enterprise.

  - <span></span>  
    Connectivity to branch office appliances.

  - <span></span>  
    Connectivity to Lync Server 2010 inside the enterprise and through perimeter networks.

Different authentication options are available for inside and outside of the enterprise to help simplify administration. For details, see [Configuring a watcher node to run synthetic transactions in Lync Server 2013](lync-server-2013-configuring-a-watcher-node-to-run-synthetic-transactions.md).

To configure a computer to act as a watcher node, you must complete the following steps after you have installed System Center Operations Manager and imported the Lync Server 2013 management packs.

Before you install the Lync Server 2013 core files and the System Center agent files, you should also make sure that the watcher node computer meets all the prerequisites for installing Lync Server 2013. In addition, the watcher node computer should also have the following items installed:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Hardware component</th>
<th>Minimum requirement</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>One of the following:</p>
<ul>
<li><p>64-bit processor, quad-core, 2.33 GHz or higher</p></li>
<li><p>64-bit 2-way processor, dual-core, 2.33 GHz or higher</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Memory</p></td>
<td><p>8 GB</p></td>
</tr>
<tr class="odd">
<td><p>Network operating system</p></td>
<td><ul>
<li><p>1 network adapter 1 Gbps</p></li>
<li><p>Windows Server 2008 R2, Windows Server 2012, or</p>
<p>Windows Server 2012 R2</p></li>
</ul></td>
</tr>
</tbody>
</table>


  - The full version of .NET Framework 4.5.

  - Windows Identity Foundation.

  - Windows PowerShell 3.0.

As soon as all these prerequisites have been met, you can configure the watcher node by:

  - Installing the Lync Server 2013 core files on the watcher node computer.

  - Installing System Center Operations Manager agent on the watcher node computer.

  - Running the Watchernode.msi executable file.

  - Using the **CsWatcherNodeConfiguration** cmdlets to configure test users to be employed by the watcher node.

</div>

<span> </span>

</div>

</div>

</div>

