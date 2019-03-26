---
title: "Configure watcher node test users and settings"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 2/13/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: ab2e0d93-cf52-4a4e-b5a4-fd545df7a1a9
description: "Summary: Configure test user accounts and watcher node settings for Skype for Business Server synthetic transactions."
---

# Configure watcher node test users and settings
 
**Summary:** Configure test user accounts and watcher node settings for Skype for Business Server synthetic transactions.
  
After configuring the computer that will act as a watcher node, you must:
  
1. [Configure Test User Accounts](test-users-and-settings.md#testuser) to be used by these watcher nodes. If you are using the Negotiate authentication method, you must also use the **Set-CsTestUserCredential** cmdlet to enable these test accounts for use on the watcher node.
    
2. Update the watcher node configuration settings.
    
## Configure Test User Accounts
<a name="testuser"> </a>

Test accounts do not need to represent actual people, but they must be valid Active Directory accounts. In addition, these accounts must be enabled for Skype for Business Server, they must have valid SIP addresses, and they should be enabled for Enterprise Voice (to use the Test-CsPstnPeerToPeerCall synthetic transaction). 
  
If you are using the TrustedServer authentication method, all you need to do is to make sure that these accounts exist and configure them as noted. You should assign at least two test users for each pool that you want to test. If you are using the Negotiate authentication method, you must also use the Set-CsTestUserCredential cmdlet and the Skype for Business Server Management Shell to enable these test accounts to work with the synthetic transactions. Do this by running a command similar to the following (these commands assume that the two Active Directory user accounts have been created and that these accounts are enabled for Skype for Business Server):
  
```
Set-CsTestUserCredential -SipAddress "sip:watcher1@litwareinc.com" -UserName "litwareinc\watcher1" -Password "P@ssw0rd"
Set-CsTestUserCredential -SipAddress "sip:watcher2@litwareinc.com" -UserName "litwareinc\watcher2" -Password "P@ssw0rd"
```

You must include not only the SIP address, but also the user name and password. If you do not include the password, the Set-CsTestUserCredential cmdlet will prompt you to enter that information. The user name can be specified by using the domain name\user name format shown in the preceding code block.
  
To verify that the test user credentials were created, run these commands from the Skype for Business Server Management Shell:
  
```
Get-CsTestUserCredential -SipAddress "sip:watcher1@litwareinc.com"
Get-CsTestUserCredential -SipAddress "sip:watcher2@litwareinc.com"
```

Information similar to this will be returned for each user:
  
|**UserName**|**Password**|
|:-----|:-----|
|Litwareinc\watcher1  <br/> |System.Security.SecureString  <br/> |
   
### Configure a Basic Watcher Node with the Default Synthetic Transactions

After the test users have been created, you can create a watcher node by using a command similar to this:
  
```
New-CsWatcherNodeConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers @{Add= "sip:watcher1@litwareinc.com","sip:watcher2@litwareinc.com"}
```

This command creates a new watcher node that uses the default settings and runs the default set of synthetic transactions. The new watcher node also uses the test users watcher1@litwareinc.com, and watcher2@litwareinc.com. If the watcher node uses TrustedServer authentication, the two test accounts can be any valid user accounts enabled for Active Directory and Skype for Business Server. If the watcher node uses the Negotiate authentication method, these user accounts must also be enabled for the watcher node by using the Set-CsTestUserCredential cmdlet.
  
To validate that automatic discovery of target pool to sign-in is configured correctly rather than targeting a pool directly use these steps instead:
  
```
New-CsWatcherNodeConfiguration -UseAutoDiscovery $true -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers @{Add= "sip:watcher1@litwareinc.com","sip:watcher2@litwareinc.com"}
```

### Configuring Extended Tests

If you want to enable the PSTN test, which verifies connectivity with the public switched telephone network, you need to do some additional configuration when setting up the watcher node. First, you must associate your test users with the PSTN test type by running a command similar to this from the Skype for Business Server Management Shell:
  
```
$pstnTest = New-CsExtendedTest -TestUsers "sip:watcher1@litwareinc.com", "sip:watcher2@litwareinc.com" -Name "Contoso Provider Test" -TestType PSTN
```

> [!NOTE]
> The results of this command must be stored in a variable. In this example, the variable is named $pstnTest. 
  
Next, you can use the **New-CsWatcherNodeConfiguration** cmdlet to associate the test type (stored in the variable $pstnTest) to a Skype for Business Server pool. For example, the following command creates a new watcher node configuration for the pool atl-cs-001.litwareinc.com, adding the two test users created previously, and adding the PSTN test type:
  
```
New-CsWatcherNodeConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers @{Add= "sip:watcher1@litwareinc.com","sip:watcher2@litwareinc.com"} -ExtendedTests @{Add=$pstnTest}
```

The preceding command will fail if you have not installed the Skype for Business Server core files and the RTCLocal database on the watcher node computer. 
  
To test multiple voice policies, you can create an extended test for each policy by using the **New-CsExtendedTest** cmdlet. The users provided should be configured with the desired voice policies. The extended tests are passed to the **New-CsWatcherNodeConfiguration** cmdlet by using comma-delimiters, such as:
  
-ExtendedTests @{Add=$pstnTest1,$pstnTest2,$pstnTest3}
  
Because the **New-CsWatcherNodeConfiguration** cmdlet was called without using the Tests parameter, only the Default synthetic transactions (and the specified extended synthetic transaction) will be enabled for the new watcher node. Therefore, the watcher node will test the following components:
  
- Registration
    
- IM
    
- GroupIM
    
- P2PAV (peer-to-peer audio/video sessions)
    
- AvConference (audio/conferencing)
    
- Presence
    
- ABS (Address Book service)
    
- ABWQ (Address Book web service)
    
The following components will not be tested by default:
  
- ASConference
    
- AVEdgeConnectivity
    
- DataConference
    
- DialinConferencing
    
- ExumConnectivity (Exchange Unified Messaging)
    
- JoinLauncher
    
- MCXP2PIM (legacy mobile device instant messaging)
    
- P2PVideoInteropServerSipTrunkAV
    
- PersistentChatMessage
    
- PSTN (PSTN gateway calls, specified as an extended test)
    
- UcwaConference
    
- UnifiedContactStore
    
- XmppIM
    
### Adding and Removing Synthetic Transactions

After a watcher node has been configured, you can use the Set-CsWatcherNodeConfiguration cmdlet to add or remove synthetic transactions from the node. For example, to add the PersistentChatMessage test to the watcher node, use the Add method and a command similar to this:
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Add="PersistentChatMessage"}
```

Multiple tests can be added by separating the test names by using commas. For example:
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Add="PersistentChatMessage","DataConference","UnifiedContactStore"}
```

An error will occur if one or more of these tests (for example, DataConference) has already been enabled on the watcher node. In this case, you will receive an error message similar to the following:
  
Set-CsWatcherNodeConfiguration : There is a duplicate key sequence 'DataConference' for the 'urn:schema:Microsoft.Rtc.Management.Settings.WatcherNode.2010:TestName' key or unique identity constraint.
  
When this error occurs, no changes will be applied. The command should be re-run with the duplicate test removed.
  
To remove a synthetic transaction from a watcher node, use the Remove method. For example, this command removes the ABWQ test from a watcher node:
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Remove="ABWQ"}
```

You can use the Replace method to replace all the currently-enabled tests with one or more new tests. For example, if you want a watcher node only to run the IM test, you can configure that by using this command:
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Replace="IM"}
```

When you run this command, all synthetic transactions on the specified watcher node will be disabled except for IM.
  
### Viewing and Testing the Watcher Node Configuration

If you want to view the tests that have been assigned to a watcher node, use a command similar to this:
  
```
Get-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" | Select-Object -ExpandProperty Tests
```

This command will return information similar to this, depending on the synthetic transactions that have been assigned to the node:
  
Registration IM GroupIM P2PAV AvConference Presence PersistentChatMessage DataConference
> [!TIP]
> To view the synthetic transactions in alphabetical order, use this command instead: 
  
```
Get-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" | Select-Object -ExpandProperty Tests | Sort-Object
```

To verify that a watcher node has been created, type the following command from the Skype for Business Server Management Shell:
  
```
Get-CsWatcherNodeConfiguration
```

You will get back information similar to this:
  
Identity : atl-cs-001.litwareinc.com <br/>
TestUsers : {sip:watcher1@litwareinc.com, sip:watcher2@litwareinc.com ...}<br/>
ExtendedTests : {TestUsers=IList<System.String>;Name=PSTN Test; Te...}<br/>
TargetFqdn : atl-cs-001.litwareinc.com<br/>
PortNumber : 5061<br/>

To verify that the watcher node has been configured correctly, type the following command from the Skype for Business Server Management Shell:
  
```
Test-CsWatcherNodeConfiguration
```

This command will test each watcher node in your deployment and confirm whether the following actions are completed:
  
- The required Registrar role is installed.
    
- The required registry key is created (completed when you ran the Set-CsWatcherNodeConfiguration cmdlet).
    
- Your servers are running the correct version of Skype for Business Server.
    
- Your ports are configured correctly.
    
- Your assigned test users have the required credentials.
    
## Managing Watcher Nodes
<a name="testuser"> </a>

In addition to modifying the synthetic transactions that are executed on a watcher node, you can also use the **Set-CsWatcherNodeConfiguration** cmdlet to carry out two other important tasks: enabling and disabling the watcher node, and configuring the watcher node to use either internal Web URLs or external Web URLs when running its tests.
  
By default, watcher nodes are designed to periodically run all their enabled synthetic transactions. At times, however, you may want to suspend those transactions. For example, if the watcher node is temporarily disconnected from the network, then there is no reason to run the synthetic transactions. Without network connectivity, those transactions will fail. To temporarily disable a watcher node, run a command similar to this from the Skype for Business Server Management Shell:
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -Enabled $False
```

This command will disable the execution of synthetic transactions on the watcher node atl watcher 001.litwareinc.com. To resume execution of the synthetic transactions, set the Enabled property back to True ($True):
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -Enabled $True
```

> [!NOTE]
> The Enabled property can be used to turn watcher nodes on or off. If you want to permanently delete a watcher node, use the **Remove-CsWatcherNodeConfiguration** cmdlet:
  
```
Remove-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com"
```

That command removes all the watcher node configuration settings from the specified computer, which prevents that computer from automatically running synthetic transactions. However, the command does not uninstall the System Center agent files or the Skype for Business Server system files.
  
By default, watcher nodes use an organization's external Web URLs when conducting tests. However, watcher nodes can also be configured to use the organization's internal Web URLs. This enables administrators to verify URL access for users located inside the perimeter network. To configure a watcher node to use internal URLs instead of external URLs, set the UseInternalWebURls property to True ($True):
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -UseInternalWebUrls $True
```

Resetting this property to the default value of False ($False) will cause the watcher to once again use the external URLs:
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -UseInternalWebUrls $False
```

## Special Setup Instructions for Synthetic Transactions
<a name="special_synthetictrans"> </a>

Most synthetic transactions can run on a watcher node as-is. In most cases, as soon as the synthetic transaction is added to the watcher node configuration settings, the watcher node can begin using that synthetic transaction during its test passes. However, there are some synthetic transactions that require special setup instructions, as discussed in the following sections.
  
### Data Conferencing Synthetic Transaction

If your watcher node computer is located outside your perimeter network, you will probably not be able to run the Data Conferencing Synthetic Transaction unless you first disable the Windows Internet Explorer® Internet browser proxy settings for the Network Service account by completing the following steps:
  
1. On the watcher node computer, click **Start**, click **All Programs**, click **Accessories**, right click **Command Prompt**, and then click **Run as administrator**.
    
2. In the console window, type the following command and then press ENTER. 
    
```
bitsadmin /util /SetIEProxy NetworkService NO_PROXY
```

You will see the following message displayed in the command window:
  
BITSAdmin is deprecated and is not guaranteed to be available in future versions of Windows. Administration tools for the BITS service are now provided by BITS PowerShell cmdlets.
  
Internet proxy settings for account NetworkService set to NO_PROXY. 
  
(connection = default)
  
This message indicates that you have disabled the Internet Explorer proxy settings for the Network Service account.
  
### Exchange Unified Messaging Synthetic Transaction

The Exchange Unified Messaging (UM) synthetic transaction verifies that test users can connect to voicemail accounts homed in Exchange.
  
The test users will need to be preconfigured with voicemail accounts. 
  
### Persistent Chat Synthetic Transaction

To use the Persistent Chat synthetic transaction, you must first create a channel and give the test users permissions to use it.
  
You can use the Persistent Chat synthetic transaction to configure this channel: 
  
```
$cred1 = Get-Credential "contoso\testUser1"
$cred2 = Get-Credential "contoso\testUser2"

Test-CsPersistentChatMessage -TargetFqdn pool0.contoso.com -SenderSipAddress sip:testUser1@contoso.com -SenderCredential $cred1 -ReceiverSipAddress sip:testUser2@contoso.com -ReceiverCredential $cred2 -TestUser1SipAddress sip:testUser1@contoso.com -TestUser2SipAddress sip:testUser2@contoso.com -Setup $true
```

You must run this setup task must be run from inside the enterprise:
  
- If run from a non-server machine, the user who executes the cmdlet must be a member of the CsPersistentChatAdministrators role for Role-Based Access Control (RBAC).
    
- If run from the server itself, the user who executes the cmdlet must be a member of the RTCUniversalServerAdmins group.
    
### PSTN Peer-to-Peer Call Synthetic Transaction

The Test-CsPstnPeerToPeerCall synthetic transaction verifies the ability to place and receive calls through a public switched telephone network (PSTN).
  
To run this synthetic transaction, you must configure:
  
- Two UC-enabled test users (a caller and a receiver).
    
- Direct Inward Dialing (DID) numbers for each user account.
    
- VoIP Policies and Voice routes that allow calls to the receiver's number to reach the PSTN gateway.
    
- A PSTN gateway that accepts call and media that will route calls back to a receiver's home pool, based on the number dialed.
    
### Unified Contact Store Synthetic Transaction

The Unified Contact Store synthetic transaction verifies the ability of Skype for Business Server to retrieve contacts on behalf of a user from Exchange.
  
To use this synthetic transaction, the following conditions must be met:
  
- Lyss-Exchange server to server authentication must be configured.
    
- Test users must have a valid Exchange mailbox.
    
After these conditions are met, you can run the following Windows PowerShell cmdlet to migrate the test users' contact lists to Exchange:
  
```
Test-CsUnifiedContactStore -TargetFqdn pool0.contoso.com -UserSipAddress sip:testUser1@contoso.com -RegistrarPort 5061 -Authentication TrustedServer -Setup
```

It may take some time for the test user contact lists to migrate to Exchange. To monitor the migration progress, the same command-line can be run without the -Setup flag:
  
```
Test-CsUnifiedContactStore -TargetFqdn pool0.contoso.com -UserSipAddress sip:testUser1@contoso.com -RegistrarPort 5061 -Authentication TrustedServer
```

This command line will succeed after migration is completed.
  
### XMPP Synthetic Transaction

The Extensible Messaging and Presence Protocol (XMPP) IM synthetic transaction requires that you configure the XMPP feature with one or more federated domains.
  
To enable the XMPP synthetic transaction, you must provide an XmppTestReceiverMailAddress parameter with a user account at a routable XMPP domain. For example:
  
```
Set-CsWatcherNodeConfiguration -Identity pool0.contoso.com -Tests @{Add="XmppIM"} -XmppTestReceiverMailAddress user1@litwareinc.com
```

In this example, a Skype for Business Server rule will need to exist to route messages for litwareinc.com to an XMPP gateway.

> [!NOTE]
> XMPP Gateways and proxies are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. See [Migrating XMPP federation](../../../SfBServer2019/migration/migrating-xmpp-federation.md) for more information. 
  
### Video Interop Server (VIS) Synthetic Transaction

The Video Interop Server (VIS) synthetic transaction requires that you download and install the synthetic transaction support files ([VISSTSupportPackage.msi](https://www.microsoft.com/en-us/download/details.aspx?id=46921)). 
  
To install VISSTSupportPackage.msi ensure the dependencies (under System Requirements) for the msi are already installed. Run VISSTSupportPackage.msi to do a simple installation. The .msi installs all the files in the following path: "%ProgramFiles%\VIS Synthetic Transaction Support Package".
  
For more details on how to run the VIS Synthetic Transaction refer to the documentation for the [Test-CsP2PVideoInteropServerSipTrunkAV](https://technet.microsoft.com/en-us/library/dn985894.aspx) cmdlet.
  
## Changing the Run Frequency for Synthetic Transactions
<a name="special_synthetictrans"> </a>

By default, synthetic transactions will run with the configured users every 15 minutes. Synthetic transactions are run sequentially within a set of users to avoid two synthetic transactions from conflicting with each other. A longer interval is needed to provide time for all synthetic transactions to complete.
  
If it is desirable to run synthetic transactions more frequently, the number of synthetic transactions run with a given set of users should be decreased so that the tests can complete in the desired time range with some buffer for occasional network delays. If running more synthetic transactions is desirable, create more user sets to run additional synthetic transactions.
  
To change the frequency at which synthetic transactions run, follow these steps:
  
1. Open System Center Operations Manager. Click Authoring section. Click Rules section (under Authoring).
    
2. In the Rules section, find the rule with the name "Main Synthetic Transaction Runner Performance Collection Rule".
    
3. Right click the rule, and select Overrides, select Override the Rule, and then select "For All objects of class: Pool Watcher".
    
4. In the Override Properties window, select Parameter Name "Frequency", and set the Override Value to the desired one.
    
5. In the same window, select the Management pack to which this override needs to be applied.
    
## Using Rich Logging for Synthetic Transactions
<a name="special_synthetictrans"> </a>

Synthetic transactions prove extremely useful in helping to identify issues with the system. For example, the Test-CsRegistration cmdlet could alert administrators to the fact that users were having difficulty registering with Skype for Business Server. However, additional details may be needed to determine the actual cause of a failure.
  
For this reason, synthetic transactions provide rich logging. With rich logging, for each activity that a synthetic transaction undertakes, the following information is recorded:
  
- The time that the activity started.
    
- The time that the activity finished.
    
- The action that was performed (for example, creating, joining, or leaving a conference; signing on to Skype for Business Server; sending an instant message).
    
- Informational, verbose, warning, or error messages generated when the activity ran.
    
- SIP registration messages.
    
- Exception records or diagnostic codes generated when the activity ran.
    
- The net result of running the activity.
    
This information is automatically generated each time a synthetic transaction is run, but is not automatically displayed or saved to a log file. If you are manually running a synthetic transaction, you can use the OutLoggerVariable parameter to specify a Windows PowerShell variable in which the information will be stored. From there, you have the option of using one of two methods to save and/or view error messages in the rich log in either XML or HTML format. 
  
To retrieve the troubleshooting information, specify the OutLoggerVariable parameter, followed by a variable name that you choose:
  
```
Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com -OutLoggerVariable RegistrationTest
```

> [!NOTE]
> Do not preface the variable name with the $ character. Use a variable name such as RegistrationTest (not $RegistrationTest). 
  
When you run this command, you will see output similar to this:
  
Target Fqdn : atl-cs-001.litwareinc.com Result : Failure Latency : 00:00:00 Error Message : This machine does not have any assigned certificates. Diagnosis :You can access much more detailed information for this failure than just the error message shown here.

To access this information in HTML format, use a command similar to this one to save the information stored in the variable RegistrationTest to an HTML file:
  
```
$RegistrationTest.ToHTML() | Out-File C:\Logs\Registration.html
```

Alternatively, you can use the ToXML() method to save the data to an XML file:
  
```
$RegistrationTest.ToXML() | Out-File C:\Logs\Registration.xml
```

You can view these files by using Windows Internet Explorer, Microsoft Visual Studio, or any other application capable of opening HTML/XML files.
  
Synthetic transactions run from inside of System Center Operations Manager will automatically generate these log files for failures. These logs will not be generated if the execution fails before Skype for Business Server PowerShell is able to load and run the synthetic transaction. 
  
> [!IMPORTANT]
> By default, Skype for Business Server saves log files to a folder that is not shared. To make these logs readily accessible, you should share this folder. For example: \\atl-watcher-001.litwareinc.com\WatcherNode. 
