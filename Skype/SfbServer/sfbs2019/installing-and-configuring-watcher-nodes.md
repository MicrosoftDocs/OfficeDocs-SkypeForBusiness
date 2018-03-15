---
title: "Installing and configuring watcher nodes in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 61f6deea-e3ef-4468-9be8-a65705815ebb
description: "Watcher nodes are computers that periodically run Lync Server synthetic transactions. Synthetic transactions are Windows PowerShell cmdlets that verify that key end user scenarios—such as the ability to sign in to the system, or the ability to exchange instant messages—are working as expected. For Lync Server 2013, System Center Operations Manager can run the synthetic transactions shown in the following table. There are three different synthetic transaction types shown in the table:"
---

# Installing and configuring watcher nodes in Lync Server 2013
[]
Watcher nodes are computers that periodically run Lync Server synthetic transactions. Synthetic transactions are Windows PowerShell cmdlets that verify that key end user scenarios—such as the ability to sign in to the system, or the ability to exchange instant messages—are working as expected. For Lync Server 2013, System Center Operations Manager can run the synthetic transactions shown in the following table. There are three different synthetic transaction types shown in the table: 
  
- **Default**. These are the synthetic transactions that a watcher node will run by default. When you create a new watcher node, you have the option of specifying which synthetic transactions that node will run. (That's the purpose of the Tests parameter used by the **New-CsWatcherNodeConfiguration** cmdlet.) If you do not use the Tests parameter when the watcher node is created, it will automatically run all the Default synthetic transactions and will not run any of the Non-default synthetic transactions. That means, for example, that the watcher node will be configured to run the Test-CsAddressBookService test, but will not be configured to run the Test-CsExumConnectivity test. 
    
- **Non-default**. As the name implies, Non-default synthetic transactions are tests that watcher nodes do not run by default. However, the watcher node can be enabled to run any of the Non-default synthetic transactions. You can do this when you create the watcher node (by using the **New-CsWatcherNodeConfiguration** cmdlet), or at any time after that. Many of the Non-default synthetic transactions require extra setup steps. For details, see [Special setup instructions for synthetic transactions in Lync Server 2013](special-setup-instructions-for-synthetic-transactions.md).
    
- **Extended**. Extended tests are a special type of Non-default synthetic transaction. Unlike other synthetic transactions, Extended tests can be run multiple times during each pass. This can be useful when verifying behavior such as multiple public switched telephone network (PSTN) voice routes for a pool. This can be configured simply by adding multiple instances of an Extended test to a watcher node. 
    
For details about the process of adding other synthetic transactions to a watcher node, see [Managing watcher nodes in Lync Server 2013](managing-watcher-nodes.md). You can use the Lync Server Management Shell to remove synthetic transactions from a watcher node.
  
The synthetic transactions available to watcher nodes include the following:
  
|**Cmdlet Name (Test Name)**|**Description**|**Synthetic Transaction Type**|
|:-----|:-----|:-----|
|Test-CsAddressBookService (ABS)  <br/> |Confirms that users are able to look up users that aren't in their contact list.  <br/> |Default  <br/> |
|Test-CsAddressBookWebQuery (ABWQ)  <br/> |Confirms that users are able to look up users that aren't in their contact list via HTTP.  <br/> |Default  <br/> |
|Test-CsIM (IM)  <br/> |Confirms that users are able to send peer-to-peer instant messages.  <br/> |Default  <br/> |
|Test-CsP2PAV (P2PAV)  <br/> |Confirms that users are able to place peer-to-peer audio calls (signaling only).  <br/> |Default  <br/> |
|Test-CsPresence (Presence)  <br/> |Confirms that users are able to view other users' presence.  <br/> |Default  <br/> |
|Test-CsRegistration (Registration)  <br/> |Confirms that users are able sign in to Lync.  <br/> |Default  <br/> |
|Test-CsAudioConferencingProvider (ACP)  <br/> |Not used with the on-premises version of Lync Server 2013  <br/> |Extended  <br/> |
|Test-CsPstnPeerToPeerCall (PSTN)  <br/> |Confirms that users are able to place and receive calls with people outside of the enterprise (PSTN numbers).  <br/> |Non-default, Extended  <br/> |
|Test-CsAVConference (AvConference)  <br/> |Confirms that users are able to create and participate in an audio/video conference.  <br/> |Default  <br/> |
|Test-CsAVEdgeConnectivity (AVEdgeConnectivity)  <br/> |Confirms that the A/V Edge servers are able to accept connections for peer-to-peer calls and conference calls.  <br/> |Non-default  <br/> |
|Test-CsDataConference (DataConference)  <br/> |Confirms that users can participate in a data collaboration conference, an online meeting that includes activities such as whiteboards and polls.  <br/> |Non-default  <br/> |
|Test-CsExumConnectivity (ExumConnectivity)  <br/> |Confirms that a user can connect to Exchange Unified Messaging (UM).  <br/> |Non-default  <br/> |
|Test-CsGroupIM (GroupIM)  <br/> |Confirms that users are able to send instant messages in conferences and participate in instant message conversations with three or more people.  <br/> |Default  <br/> |
|Test-CsGroupIM -TestJoinLauncher (JoinLauncher)  <br/> |Confirms that users are able to create and join scheduled meetings via a web address link.  <br/> |Non-default  <br/> |
|Test-CsMCXP2PIM (MCXP2PIM)  <br/> |Confirms that mobile device users are able to register and send instant messages.  <br/> |Non-default  <br/> |
|Test-CsPersistentChatMessage (PersistentChatMessage)  <br/> |Confirms that users can exchange messages by using the Persistent Chat service.  <br/> |Non-default  <br/> |
|Test-CsUnifiedContactStore (UnifiedContactStore)  <br/> |Confirms that a user's contacts can be accessed through the unified contact store. The unified contact store provides a way for users to maintain a single set of contacts that can be accessed by using Lync 2013, Outlook, and/or Outlook Web Access.  <br/> |Non-default  <br/> |
|Test-CsXmppIM (XmppIM)  <br/> |Confirms that an instant message can be sent across the XMPP (Extensible Messaging and Presence Protocol) gateway.  <br/> |Non-default  <br/> |
   
You do not need to install watcher nodes in order to use System Center Operations Manager. If you do not install these nodes, you can still get real-time alerts from Lync Server 2013 components when an issue occurs. (The Component and User Management Pack does not use watcher nodes.) However, watcher nodes are required if you want to monitor end-to-end scenarios by using the Active Monitoring Management pack.
  
> [!NOTE]
> Administrators can also run synthetic transactions manually, without needing to use, or install, Operations Manager. For details about the various Test-Cs cmdlets, see the [Lync Server 2013 cmdlets index](lync-server-2013-cmdlets-index.md). 
  
Depending on the size of your deployment, synthetic transactions may use a large amount of computer memory and processor time. For this reason, we recommend that you use a dedicated computer as a watcher node. For example, you should not configure a Front End Server to act as a watcher node. Watcher nodes should meet the following hardware specifications:
  
> [!NOTE]
> A legacy Microsoft Lync Server 2010 watcher node cannot be collocated on the same machine with a Lync Server 2013 watcher node. This is because the core system files for Lync Server 2010 and Lync Server 2013 cannot be installed on the same computer. > However, Lync Server 2013 watcher nodes can simultaneously monitor both Lync Server 2013 and Lync Server 2010. The Default synthetic transactions are supported on both product versions. 
  
Lync Server 2013 watcher nodes may be deployed inside or outside of an enterprise to help verify:
  
> Connectivity to pools for users inside the enterprise.
    
> Connectivity through perimeter networks for remote users who work outside the enterprise.
    
> Connectivity to branch office appliances.
    
> Connectivity to Lync Server 2010 inside the enterprise and through perimeter networks.
    
Different authentication options are available for inside and outside of the enterprise to help simplify administration. For details, see [Configuring a watcher node to run synthetic transactions in Lync Server 2013](configuring-a-watcher-node-to-run-synthetic-transactions.md).
  
To configure a computer to act as a watcher node, you must complete the following steps after you have installed System Center Operations Manager and imported the Lync Server 2013 management packs.
  
Before you install the Lync Server 2013 core files and the System Center agent files, you should also make sure that the watcher node computer meets all the prerequisites for installing Lync Server 2013. In addition, the watcher node computer should also have the following items installed:
  
|**Hardware component**|**Minimum requirement**|
|:-----|:-----|
|CPU  <br/> | One of the following:  <br/>  64-bit processor, quad-core, 2.33 GHz or higher  <br/>  64-bit 2-way processor, dual-core, 2.33 GHz or higher  <br/> |
|Memory  <br/> |8 GB  <br/> |
|Network operating system  <br/> | 1 network adapter 1 Gbps  <br/>  Windows Server 2008 R2, Windows Server 2012, or  <br/>  Windows Server 2012 R2  <br/> |
   
- The full version of .NET Framework 4.5. 
    
- Windows Identity Foundation.
    
- Windows PowerShell 3.0.
    
As soon as all these prerequisites have been met, you can configure the watcher node by:
  
- Installing the Lync Server 2013 core files on the watcher node computer.
    
- Installing System Center Operations Manager agent on the watcher node computer.
    
- Running the Watchernode.msi executable file.
    
- Using the **CsWatcherNodeConfiguration** cmdlets to configure test users to be employed by the watcher node. 
    

