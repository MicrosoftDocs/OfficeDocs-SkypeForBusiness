---
title: "Install and configure watcher nodes"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 11/20/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 7392e4f8-6e2d-447b-aaa3-878f73995f9d
description: "Summary: Install and configure watcher nodes for Skype for Business Server synthetic transactions."
---

# Install and configure watcher nodes
 
**Summary:** Install and configure watcher nodes for Skype for Business Server synthetic transactions.
  
Watcher nodes are computers that periodically run Skype for Business Server synthetic transactions. Synthetic transactions are Windows PowerShell cmdlets that verify that key user scenarios, such as the ability to sign in or to exchange instant messages, are working as expected. For Skype for Business Server 2015, System Center Operations Manager can run the synthetic transactions shown in the following table, which includes three synthetic transaction types:
  
- **Default** Synthetic transactions that a watcher node runs by default. When you create a new watcher node, you can specify which synthetic transactions that node will run. (That's the purpose of the Tests parameter used by the New-CsWatcherNodeConfiguration cmdlet.) If you do not use the Tests parameter when the watcher node is created, it will automatically run all the Default synthetic transactions and will not run any of the Non-default synthetic transactions. This means, for example, that the watcher node will be configured to run the Test-CsAddressBookService test, but will not be configured to run the Test-CsExumConnectivity test.
    
- **Non-default** Tests that watcher nodes do not run by default. (For details, see the description of the Default type.) However, the watcher node can be enabled to run any of the Non-default synthetic transactions. You can do this when you create the watcher node (by using the New-CsWatcherNodeConfiguration cmdlet), or any time after the watcher node has been created. Note that many of the Non-default synthetic transactions require extra setup steps. For more details about these steps, see [Special Setup Instructions for Synthetic Transactions](test-users-and-settings.md#special_synthetictrans).
    
- **Extended** A special type of Non-default synthetic transaction. Unlike other synthetic transactions, Extended tests can be run multiple times during each pass. This is useful when verifying behavior, such as multiple public switched telephone network (PSTN) voice routes for a pool. You can configure this simply by adding multiple instances of an extended test to a watcher node.
    
For details about the process for adding other synthetic transactions to a watcher node, see [Configure a Watcher Node to Run Synthetic Transactions](watcher-nodes.md#enable_synthetic_trans). You can also use Skype for Business Server Management Shell to remove synthetic transactions from a watcher node.
  
The synthetic transactions available to watcher nodes include the following:
  
|**Cmdlet Name (Test Name)**|**Description**|
|:-----|:-----|
|Test-CsAddressBookService (ABS)  <br/> |Confirms that users are able to look up users who aren't in their contact list.  <br/> |
|Test-CsAddressBookWebQuery (ABWQ)  <br/> |Confirms that users are able to look up users who aren't in their contact list via HTTP.  <br/> |
|Test-CsAVConference (AvConference)  <br/> |Confirms that users are able to create and participate in an audio/video conference.  <br/> |
|Test-CsGroupIM (IM Conferencing)  <br/> |Confirms that users are able to send instant messages in conferences and participate in instant message conversations with three or more people.  <br/> |
|Test-CsIM (P2P IM)  <br/> |Confirms that users are able to send peer-to-peer instant messages.  <br/> |
|Test-CsP2PAV (P2PAV)  <br/> |Confirms that users are able to place peer-to-peer audio calls (signaling only).  <br/> |
|Test-CsPresence (Presence)  <br/> |Confirms that users are able to view other users' presence.  <br/> |
|Test-CsRegistration (Registration)  <br/> |Confirms that users are able sign in to Skype for Business.  <br/> |
|Test-CsPstnPeerToPeerCall (PSTN)  <br/> |Confirms that users are able to place and receive calls with people outside of the enterprise (PSTN numbers).  <br/> |
|Test-CsASConference (ASConference)  <br/> |Confirms that users are able to create and participate in an application sharing conference.  <br/> |
|Test-CsAVEdgeConnectivity (AVEdgeConnectivity)  <br/> |Confirms that the Audio Video Edge servers are able to accept connections for peer-to- peer calls and conference calls.  <br/> |
|Test-CsDataConference (DataConference)  <br/> |Confirms that users can participate in a data collaboration conference (an online meeting that includes activities such as whiteboards and polls).  <br/> |
|Test-CsDialinConferencing (DialinConferencing)  <br/> |Confirms that users are able to dial phone numbers to join conferences.  <br/> |
|Test-CsDialinConferencing (DialinConferencing)  <br/> |Confirms that users are able to dial phone numbers to join conferences.  <br/> |
|Test-CsExumConnectivity (ExumConnectivity)  <br/> |Confirms that a user can connect to Exchange Unified Messaging (UM).  <br/> |
|Test-CsGroupIM -TestJoinLauncher (JoinLauncher)  <br/> |Confirms that users are able to create and join scheduled meetings (by a web address link).  <br/> |
|Test-CsMCXP2PIM (MCXP2PIM)  <br/> |Confirms that mobile device users are able to register and send instant messages.  <br/> |
|Test-CsP2PVideoInteropServerSipTrunkAV (P2PVideoInteropServerSipTrunkAV)  <br/> |Confirms that Video Interop Server is up and can handle incoming connections over a video SIP trunk.  <br/> **Note:** MCX support for legacy mobile clients is no longer available in Skype for Business Server 2019. |
|Test-CsPersistentChatMessage (PersistentChatMessage)  <br/> |Confirms that users can exchange messages by using the Persistent Chat service.  <br/> |
|Test-CsUcwaConference (UcwaConference)  <br/> |Confirms that users can join conferences via the web.  <br/> |
|Test-CsUnifiedContactStore (UnifiedContactStore)  <br/> |Confirms that a user's contacts can be accessed through the unified contact store. The unified contact store provides a way for users to maintain a single set of contacts that can be accessed by using Skype for Business Server 2015, Outlook messaging and collaboration client, and/or Outlook Web Access.  <br/> |
|Test-CsXmppIM (XmppIM)  <br/> |Confirms that an instant message can be sent across the Extensible Messaging and Presence Protocol (XMPP) gateway.  <br/> XMPP Gateways and proxies are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019.  |

You do not need to install watcher nodes to use System Center Operations Manager. If you do not install these nodes, you can still get real-time alerts from Skype for Business Server 2015 components whenever an issue occurs. (The Component and User Management Pack does not use watcher nodes.) However, watcher nodes are required if you want to monitor end-to-end scenarios by using the Active Monitoring Management pack.
  
> [!NOTE]
> Administrators can also run synthetic transactions manually, without using or installing Operations Manager. Depending on the size of your Skype for Business Server deployment, synthetic transactions can use a large amount of computer memory and processor time. Because of this, we recommend that you use a dedicated computer as a watcher node. For example, you should not configure a Skype for Business Server Front End Server to act as a watcher node. Watcher nodes should meet the same basic hardware requirements as any other computer in your Skype for Business Server topology. 
  
> [!NOTE]
> A legacy Lync Server 2013 watcher node cannot be collocated on the same machine as a Skype for Business Server 2015 watcher node because the core system files for Lync Server 2013 and Skype for Business Server 2015 cannot be installed on the same computer. However, Skype for Business Server 2015 watcher nodes can simultaneously monitor Skype for Business Server 2015 and Lync Server 2013. Default synthetic transactions are supported for both product versions. 
  
Lync Server 2013 watcher nodes may be deployed inside or outside an enterprise to help verify:
  
- Connectivity to pools for users inside the enterprise.
    
- Connectivity through perimeter networks for remote users working outside the enterprise.
    
- Connectivity to branch office appliances.
    
- Connectivity to Lync Server 2013 inside the enterprise and through perimeter networks.
    
To help simplify administration, different authentication options are available for inside and outside of the enterprise. For details, see [Configure a Watcher Node to Run Synthetic Transactions](watcher-nodes.md#enable_synthetic_trans).
  
To configure a computer to act as a watcher node, you must first complete the following prerequisites: 
  
- Install System Center Operations Manager and import the Skype for Business Server 2015 management packs. You must also first verify that the watcher node computer meets all prerequisites for installing Skype for Business Server 2015.
    
- Install the following items on the watcher node computer:
    
  - The full version of .NET Framework 4.5
    
  - Windows Identity Foundation
    
  - Windows PowerShell 3.0
    
After the prerequisites are met, you can configure the watcher node by following these steps:
  
1. Install the Skype for Business Server 2015 core files on the watcher node computer.
    
2. Install System Center Operations Manager agent on the watcher node computer.
    
3. Run the Watchernode.msi executable file.
    
4. Use the **New-CsWatcherNodeConfiguration** cmdlet to configure test user accounts to be employed by the watcher node.
    
## Install the Skype for Business Server 2015 Core Files and the RTCLocal Database

To install the Skype for Business Server 2015 core files on a computer, complete the following procedure. The RTCLocal database will automatically be installed when you install the core files. Note that you do not need to install SQL Server on the watcher nodes. SQL Server Express will be automatically installed.
  
To install the Skype for Business Server 2015 core files and the RTCLocal database:
  
1. On the watcher node computer, click Start, click All Programs, click Accessories, right-click Command Prompt, and then click Run as administrator.
    
2. In the console window, type the following command and press ENTER. Be sure to enter the appropriate path to your Skype for Business Server setup files: 
    D:\Setup.exe /BootstrapLocalMgmtTo verify that the core Skype for Business Server components are successfully installed, click **Start**, click **All Programs**, click **Skype for Business Server 2015**, and then click **Skype for Business Server Management Shell**. In the Skype for Business Server Management Shell, type the following Windows PowerShell command and press ENTER:
  
```
Get-CsWatcherNodeConfiguration
```

> [!NOTE]
> The first time you run this command, no data will be returned because you have not yet configured any watcher node computers. If the command runs without returning an error, you can assume that the Skype for Business Server setup completed successfully. 
  
If your watcher node computer is located inside your perimeter network, you can run the following command to verify the installation of Skype for Business Server 2015:
  
Get-CsPinPolicyYou will receive information similar to this, depending on the number of PIN policies configured for use in your organization:
  
Identity : Global
  
Description :
  
MinPasswordLength : 5
  
PINHistoryCount : 0
  
AllowCommonPatterns : False
  
PINLifetime : 0
  
MaximumLogonAttempts :
  
If you see information about your PIN policies, the core components have been successfully installed.
  
## Install the Operation Manager Agent Files on a Watcher Node

Similar to Skype for Business Server setup for reporting component alerts, a Skype for Business Server 2015 watcher node requires System Center Operations Manager agent files to be installed. This enables the synthetic transactions to be run and alerts to be reported to the System Center Operations Manager Root Management Server.
  
To install the agent files, follow the procedures listed in [Configure the Skype for Business Server computers that will be monitored](configure-computers-to-monitor.md).
  
## Configure a Watcher Node to Run Synthetic Transactions
<a name="enable_synthetic_trans"> </a>

After the System Center Operations Manager agent files have been installed, you must configure the watcher node itself. The steps you take to do this will vary, depending on whether your watcher node computer is inside your perimeter network or outside your perimeter network. 
  
When you configure a watcher node, you must also choose the type of authentication method to be employed by that node. Skype for Business Server 2015 enables you to choose one of two authentication methods: Trusted Server or Credential Authentication. The following table shows the differences between these two methods:
  
||**Description**|**Locations supported**|
|:-----|:-----|:-----|
|TrustedServer  <br/> |Uses a certificate to impersonate an internal server and bypass authentication challenges.  <br/> Useful for administrators who prefer to manage a single certificate, instead of many user passwords on each watcher node.  <br/> |Inside the enterprise.  <br/> With this method, the watcher node must be in the same domain as the pools being monitored. If the watcher node and the pools are in different domains, use Credential Authentication instead.  <br/> |
|Negotiate  <br/> |Stores user names and passwords securely in Windows Credential Manager on each watcher node.  <br/> This mode requires more password management, but is the only option for watcher nodes outside the enterprise. These watcher nodes cannot be treated as an endpoint trusted for authentication.  <br/> |Outside the enterprise.  <br/> Inside the enterprise.  <br/> |
   
## Configure a Watcher Node to Use Trusted Server Authentication
<a name="enable_synthetic_trans"> </a>

If your watcher node computer lies inside the perimeter network, using Trusted Server authentication can greatly reduce administration tasks by maintaining a single certificate, rather than using numerous user account passwords.
  
To configure Trusted Server authentication, you must first create a trusted application pool to host the watcher node computer. After you've created the trusted application pool, you must then configure synthetic transactions on that watcher node to run as trusted applications.
  
> [!NOTE]
> A trusted application is an application that is given trusted status to run as part of Skype for Business Server 2015, but is not a built-in part of the product. Trusted status means that the application will not be challenged for authentication each time it runs.
  
To create a trusted application pool, open the Skype for Business Server Management Shell and run a command similar to this:
  
```
New-CsTrustedApplicationPool -Identity atl-watcher-001.litwareinc.com -Registrar atl-cs-001.litwareinc.com -ThrottleAsServer $True -TreatAsAuthenticated $True -OutboundOnly $False -RequiresReplication $True -ComputerFqdn atl-watcher-001.litwareinc.com -Site Redmond
```

> [!NOTE]
> For details about the parameters in the preceding command, type the following from the Skype for Business Server Management Shell prompt: 
  
```
Get-Help New-CsTrustedApplicationPool -Full | more
```

After creating the trusted application pool, you can then configure the watcher node computer to run synthetic transactions as a trusted application by using the **New-CsTrustedApplication** cmdlet and a command similar to this:
  
```
New-CsTrustedApplication -ApplicationId STWatcherNode -TrustedApplicationPoolFqdn atl-watcher-001.litwareinc.com -Port 5061
```

When this command completes and the trusted application is created, you must then run the **Enable-CsTopology** cmdlet to make sure that the changes take effect:
  
```
Enable-CsTopology
```

After running Enable-CsTopology, restart the computer.
  
To verify that the new trusted application has been created, type the following at the Skype for Business Server Management Shell prompt:
  
```
Get-CsTrustedApplication -Identity "atl-watcher-001.litwareinc.com/urn:application:STWatcherNode"
```

## Configure a Default Certificate on the Watcher Node
<a name="enable_synthetic_trans"> </a>

Each watcher node that uses TrustedServer authentication must have a Default certificate assigned by using the Skype for Business Server Deployment wizard. 
  
To assign a Default certificate:
  
1. Click Start, click All Programs, click Skype for Business Server 2015, and then click Skype for Business Server Deployment Wizard. 
    
2. In the Skype for Business Server Deployment Wizard, click Install or Update Skype for Business Server System, and then click Run under the heading Request, Install, or Assign Certificate. 
    
> [!NOTE]
> If the Run button is disabled, you may need to first click Run under Install Local Configuration Store. 
  
Do one of the following:
  
- If you already have a certificate that can be used as the Default certificate, click Default in the Certificate wizard, and then click Assign. Follow the steps in the Certificate Assignment wizard to assign that certificate.
    
- If you need to request a certificate for use the Default certificate, click Request, and then follow the steps in the Certificate Request wizard to request that certificate. If you use the default values for the Web Server certificate, you get a certificate that you can assign as the Default certificate.
    
## Install and Configure a Watcher Node
<a name="enable_synthetic_trans"> </a>

After you have restarted the watcher node computer and configured a certificate, you must run the file Watchernode.msi. (You must run Watchernode.msi on any computer where both the Operations Manager agent files and the Skype for Business Server 2015 core components are installed.) 
  
To install and configure a watcher node:
  
1. Open the Skype for Business Server Management Shell by clicking Start, clicking All Programs, clicking Skype for Business Server 2015, and then clicking Skype for Business Server Management Shell. 
    
2. In the Management Shell, type the following command and then press ENTER (be sure and specify the actual path to your copy of Watchernode.msi):
    
```
C:\Tools\Watchernode.msi Authentication=TrustedServer
```

> [!NOTE]
> You can also run Watchernode.msi n from a command window. To open a command window, click Start, right-click Command Prompt, and then click Run as administrator. When the command window opens, type the same command shown in step 2, above. 
  
> [!IMPORTANT]
> In the preceding command, the name/value pair Authentication=TrustedServer is case-sensitive. It must be typed exactly as shown. For example, this command will fail because it does not use the correct letter casing: 
  
```
C:\Tools\Watchernode.msi authentication=trustedserver
```

TrustedServer mode can be used only with computers that lie inside the perimeter network. When a watcher node runs in TrustedServer mode, administrators do not have to maintain test user passwords on the computer.
  
## Configure a Watcher Node to Use Negotiate
<a name="enable_synthetic_trans"> </a>

If your watcher node computer lies outside the perimeter network then you must follow a slightly different procedure in order to configure that watcher node to run synthetic transactions: in particular, you should not create a trusted application pool or a trusted application. That means that you will need to complete the next two tasks.
  
### Update Membership in the RTC Local Read-Only Administrators Group

If your watcher node lies outside the perimeter network, you must add the Network Service account to the RTC Local Read-only Administrators group on the watcher node computer by completing the following procedure on the watcher node:
  
1. Click Start, right-click Computer, and then click Manage.
    
2. In Server Manager, expand Configuration, expand Local Users and Groups, and then click Groups.
    
3. In the Groups pane, double-click RTC Local Read-only Administrators.
    
4. In the RTC Local Read-only Administrators Properties dialog box, click Add.
    
5. In the Select Users, Computers, Service Accounts, or Groups dialog box, click Locations.
    
6. In the Locations dialog box, select the name of the watcher node computer, and then click OK.
    
7. In the Enter object names to select box, type Network Service, and then click OK.
    
8. In the RTC Local Read-only Administrators Properties dialog box, click OK, and then close Server Manager.
    
9. Restart the watcher node computer.
    
### Install the Watcher Node Configuration Files

Your next step is to run the file Watchernode.msi: 
  
1. Open the Microsoft Skype for Business Server 2015 Management Shell. Click Start, click All Programs, click Microsoft Skype for Business Server 2015, and then click Skype for Business Server Management Shell. 
    
2. In Skype for Business Server Management Shell, type the following command, and then press ENTER (be sure to specify the actual path to your copy of Watchernode.msi):
    
   ```
   c:\Tools\Watchernode.msi Authentication=Negotiate
   ```

> [!NOTE]
> As mentioned previously, Watchernode.msi can also be run from a command window. To open a command window, click **Start**, right-click **Command Prompt**, and then click **Run as administrator**. When the command window opens, type the same command shown in step 2, above. 
  
The Negotiate mode is used any time the watcher node cannot be set up as a trusted application pool. In this mode, administrators will need to manage test user passwords on the watcher node.
  

