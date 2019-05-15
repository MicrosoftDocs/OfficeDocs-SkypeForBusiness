---
title: 'Configuring watcher node test users and configuration settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring watcher node test users and configuration settings
ms:assetid: ab00e9cb-f539-4aa6-bcb4-5533fbe7bc44
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205152(v=OCS.15)
ms:contentKeyID: 48185048
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring watcher node test users and configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-29_

After configuring the computer that will act as a watcher node, you must:

1.  Create the test accounts to be used by these watcher nodes. If you are using the Negotiate authentication method, you must also use the [Set-CsTestUserCredential](https://technet.microsoft.com/en-us/library/JJ205341(v=OCS.15)) cmdlet to enable these test accounts for use on the watcher node.

2.  Update the watcher node configuration settings.

This section covers:

  - Configuring Test User Accounts

  - Configuring a Basic Watcher Node with the Default Synthetic Transactions

  - Configuring Extended Tests

  - Adding and Removing Synthetic Transactions

  - Viewing and Testing the Watcher Node Configuration

<div>

## Configuring Test User Accounts

Test users do not need to represent actual people, but they must be valid Active Directory Domain Services accounts; in addition, these accounts must be enabled for Lync Server 2013, they must have valid SIP addresses, and they should be enabled for Enterprise Voice (to use the Test-CsPstnPeerToPeerCall synthetic transaction). If you use the TrustedServer authentication method, then all you need to do is to make sure that these accounts exist and have been configured as specified here. You should assign at least three test users for each pool that you want to test.

If you are using the Negotiate authentication method, you must also use the **Set-CsTestUserCredential** cmdlet and the Lync Server Management Shell to enable these test accounts to work with the synthetic transactions. You can do this by running a command similar to the following. (These commands assume that the three Active Directory user accounts have already been created and that those accounts have been enabled for Lync Server 2013.):

    Set-CsTestUserCredential -SipAddress "sip:watcher1@litwareinc.com" -UserName "litwareinc\watcher1" -Password "P@ssw0rd"
    Set-CsTestUserCredential -SipAddress "sip:watcher2@litwareinc.com" -UserName "litwareinc\watcher2" -Password "P@ssw0rd"
    Set-CsTestUserCredential -SipAddress "sip:watcher3@litwareinc.com" -UserName "litwareinc\watcher3" -Password "P@ssw0rd"

Note that you must include not only the SIP address but also the user name and password. If you do not include the password Set-CsTestUserCredential will prompt you to enter that information. The user name can be specified using the domain name\\user name format shown above, or by using the format user name@domain name; for example:

    -UserName "watcher3@litwareinc.com"

To verify that the test user credentials were created, run these commands from within the Lync Server Management Shell:

    Get-CsTestUserCredential -SipAddress "sip:watcher1@litwareinc.com"
    Get-CsTestUserCredential -SipAddress "sip:watcher2@litwareinc.com"
    Get-CsTestUserCredential -SipAddress "sip:watcher3@litwareinc.com"

Information similar to this should be returned for each user:

    UserName                        Password
    --------                        --------
    Litwareinc\watcher1              System.Security.SecureString

</div>

<div>

## Configuring a Basic Watcher Node with the Default Synthetic Transactions

After the test users have been created you can then create a watcher node by using a command similar to this:

    New-CsWatcherNodeConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers @{Add= "sip:watcher1@litwareinc.com","sip:watcher2@litwareinc.com", "sip:watcher3@litwareinc.com"}

This command creates a new watcher node that uses the default settings and runs the default set of synthetic transactions. The new watcher node also uses the test users watcher1@litwareinc.com, watcher2@litwareinc.com, and watcher3@litwareinc.com. If the watcher node is using TrustedServer authentication, the three test accounts can be any valid user accounts enabled for Active Directory and Lync Server. If the watcher node is using the Negotiate authentication method, you must also enable these user accounts for watcher node by using the **Set-CsTestUserCredential** cmdlet.

</div>

<div>

## Configuring Extended Tests

If you want to enable the public switched telephone network (PSTN test), which verifies connectivity with the public switched telephone network, you will need to do some additional configuration when setting up the watcher node. First, you need to associate your test users with the PSTN test type. To do that, run a command similar to this from within the Lync Server Management Shell:

    $pstnTest = New-CsExtendedTest -TestUsers "sip:watcher1@litwareinc.com", "sip:watcher2@litwareinc.com", "sip:watcher3@litwareinc.com"  -Name "Contoso Provider Test" -TestType PSTN

Note that the results of this command must be stored in a variable. In this example, that's a variable named $pstnTest.

At this point, you can use the **New-CsWatcherNodeConfiguration** cmdlet to associate the test type (stored in the variable $pstnTest) to a Lync Server 2013 pool. For example, the following command creates a new watcher node configuration for the pool atl-cs-001.litwareinc.com, adding the three test users that were created previously, and also adding the PSTN test type:

    New-CsWatcherNodeConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers @{Add= "sip:watcher1@litwareinc.com","sip:watcher2@litwareinc.com", "sip:watcher3@litwareinc.com"} -ExtendedTests @{Add=$pstnTest}

Note that the preceding command will fail if you have not installed the Lync Server core files and the RTCLocal database on the watcher node computer.

To test multiple voice policies, you need to create an extended test for each policy by using the **New-CsExtendedTest** cmdlet. The users assigned to this test should be configured with the desired voice policies. The extended tests are then passed to the **New-CsWatcherNodeConfiguration** cmdlet by using a command similar to the following:

    -ExtendedTests @{Add=$pstnTest1,$pstnTest2,$pstnTest3}

If New-CsWatcherNodeConfiguration is called without using the Tests parameter, that means that only the Default synthetic transactions (and the specified extended synthetic transaction) will be enabled for the new watcher node. This means that the watcher node will test the following components:

  - Registration

  - IM

  - GroupIM

  - P2PAV (peer-to-peer audio/video sessions)

  - AvConference (audio/conferencing)

  - Presence

  - ABS (Address Book service)

  - ABWQ (Address Book web service)

  - PSTN (PSTN gateway calls, specified as an extended test. By default, PSTN is disabled. The test is enabled in this case only because the command enabled PSTN by using the ExtendedTests parameter.)

This also means that the following components will not be tested by default:

  - AVEdgeConnectivity

  - MCXP2PIM (mobile device instant messaging)

  - ExumConnectivity (Exchange Unified Messaging)

  - JoinLauncher

  - PersistentChatMessage

  - DataConference

  - XmppIM

  - UnifiedContactStore

</div>

<div>

## Adding and Removing Synthetic Transactions

After a watcher node has been configured, you can use the **Set-CsWatcherNodeConfiguration** cmdlet to add or remove synthetic transactions from the node. For example, to add the PersistentChatMessage test to the watcher node, use the Add method and a command similar to this:

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Add="PersistentChatMessage"}

Multiple tests can be added by separating the test names by using commas. For example:

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Add="PersistentChatMessage","DataConference","UnifiedContactStore"}

Note that an error will occur if one or more of these tests (for example, DataConference) has already been enabled on the watcher node. In this case, you will receive an error message similar to the following:

    Set-CsWatcherNodeConfiguration : There is a duplicate key sequence 'DataConference' for the 'urn:schema:Microsoft.Rtc.Management.Settings.WatcherNode.2010:TestName' key or unique identity constraint.

When this error occurs, no changes will be applied. The command should be rerun with the duplicate test removed.

To remove a synthetic transaction from a watcher node, use the Remove method instead of the Add method. For example, this command removes the ABWQ test from a watcher node:

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Remove="ABWQ"}

You can also use the Replace method to replace all the currently-enabled tests with one or more new tests. For example, if you only want a watcher node to run the IM test, you can configure that by using this command:

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Replace="IM"}

When you run the preceding command, all synthetic transactions on the specified watcher node will be disabled except for IM.

</div>

<div>

## Viewing and Testing the Watcher Node Configuration

If you want to view the tests that have been assigned to a watcher node, use a command similar to this:

    Get-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" | Select-Object -ExpandProperty Tests

The preceding command will return information similar to this, depending on the synthetic transactions that have been assigned to the node:

    Registration
    IM
    GroupIM
    P2PAV
    AvConference
    Presence
    PersistentChatMessage
    DataConference

<div>


> [!TIP]
> To view the synthetic transactions in alphabetical order, use this command instead:<BR>Get-CsWatcherNodeConfiguration –Identity "atl-cs-001.litwareinc.com" | Select-Object –ExpandProperty Tests | Sort-Object



</div>

To verify that a watcher node has been created, type the following command from within the Lync Server Management Shell:

    Get-CsWatcherNodeConfiguration

You will receive information similar to this:

    Identity      : atl-cs-001.litwareinc.com
    TestUsers     : {sip:watcher1@litwareinc.com, sip:watcher2@litwareinc.com ...}
    ExtendedTests : {TestUsers=IList<System.String>;Name=PSTN Test; Te...}
    TargetFqdn    : atl-cs-001.litwareinc.com
    PortNumber    : 5061

To verify that the watcher node has been configured correctly, type the following command from within the Lync Server Management Shell:

    Test-CsWatcherNodeConfiguration

The preceding command will test each watcher node in your deployment and tell you information, such as whether:

  - The required Registrar role been installed.

  - The required registry key was created for you when you ran Set-CsWatcherNodeConfiguration.

  - Your servers are running the correct version of Lync Server.

  - Your ports been configured correctly.

  - Your assigned test users have the required credentials.

</div>

</div>

<span> </span>

</div>

</div>

</div>

