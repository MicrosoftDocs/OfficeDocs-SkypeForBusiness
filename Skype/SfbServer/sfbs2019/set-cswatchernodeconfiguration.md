---
title: "Set-CsWatcherNodeConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 001b49ab-de17-4161-9d0c-9d5d9626558f
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsWatcherNodeConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Modifies an existing collection of watcher node configuration settings. Watcher nodes are computers that periodically use Microsoft System Center Operations Manager and Lync Server 2013 synthetic transactions to verify that Lync Server components are working as expected. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsWatcherNodeConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The commands shown in Example 1 add a new audio conferencing provider test to the watcher node configuration settings applied to the pool atl-cs-001.litwareinc.com. To do this, the first command in the example uses the **New-CsExtendedTest** cmdlet to create the new test; this in-memory-only test is stored in a variable $x. In the second command, the **Set-CsWatcherNodeConfiguration** cmdlet adds the new test to the watcher node configuration settings; this is done by using the ExtendedTests parameter and the syntax @{Add=$x}. 
  
```
$x = New-CsExtendedTest -TestUsers "sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com" -Name "Audio Conferencing Test" -TestType "AudioConferencingProvider"
Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -ExtendedTests @{Add=$x}
```

### Example 2

The commands in Example 2 show how you can remove an extended test from a collection of watcher node configuration settings. To carry out this task, the first command in the example uses the **Get-CsWatcherNodeConfiguration** cmdlet to return an object reference to the watcher node settings for the pool atl-cs-001.litwareinc.com; this object reference is stored in a variable named $x. 
  
In the second command, the RemoveAt() method is used to remove the first extended test in the object reference $x. Extended tests are stored as items in an array, with the first item being given the index number 0, the second item being given the index number 1, and so on. The syntax RemoveAt(0) removes the item with the index number 0: the first item in the set of extended tests. To remove the second extended test, use the syntax RemoveAt(1).
  
After the object reference has been updated, the final command uses the **Set-CsWatcherNodeConfiguration** cmdlet and the Instance parameter to write the changes made to the object reference back to the actual watcher node settings for the pool atl-cs-001.litwareinc.com. 
  
```
$x = Get-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com"
$x.ExtendedTests.RemoveAt(0)
Set-CsWatcherNodeConfiguration -Instance $x
```

### Example 3

In Example 3, all the extended tests configured for the atl-cs-001.litwareinc.com watcher node are removed. This task is performed by including the ExtendedTests parameter and the parameter value $Null.
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -ExtendedTests $Null
```

## Detailed Description
<a name="DetailedDescription"> </a>

If you are using Microsoft System Center Operations Manager to monitor Lync Server 2013 then you have the option of setting up "watcher nodes": computers that periodically, and automatically, run synthetic transactions in order to verify that Lync Server is working as expected. Watcher nodes are assigned to pools, and are managed using the **CsWatcherNodeConfiguration** cmdlets. Note that you do not need to install watcher nodes if you are using System Center Operations Manager. You can still monitor your system without using watcher nodes; the only difference is that any synthetic transactions you want to run will need to be invoked manually rather than automatically invoked by Operations Manager. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsWatcherNodeConfiguration"}
  
 **Lync Server Control Panel:** The functions carried out by the **Set-CsWatcherNodeConfiguration** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Enables or disables the watcher node. The default value is True ($True).  <br/> |
| _ExtendedTests_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Object reference to one or more instances of the ExtendedTest object. These objects must be created using the **New-CsExtendedTest** cmdlet.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name of the pool associated with the watcher node configuration settings.  <br/> |
| _Instance_ <br/> |Optional  <br/> |PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _PortNumber_ <br/> |Optional  <br/> |System.UInt16  <br/> |SIP port used by the Registrar service.  <br/> |
| _Tests_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Synthetic transactions to be run by the watcher node. Allowed values are:  <br/> \* Registration  <br/> \* IM  <br/> \* GroupIM  <br/> \* P2PAV  <br/> \* AvConference  <br/> \* Presence  <br/> \* ABS  <br/> \* ABWQ  <br/> \* MCXP2PIM  <br/> \* ExumConnectivity  <br/> \* JoinLauncher  <br/> \* PersistentChatMessage  <br/> \* DataConference  <br/> \* XmppIM  <br/> \* UnifiedContactStore  <br/> \* AVEdgeConnectivity  <br/> To enable additional tests for a watcher node use syntax similar to this:  <br/> -Tests @{Add="ExumConnectivity","JoinLauncher","UnifiedContactStore"}  <br/> To disable one or more tests from a watcher node use syntax like this:  <br/> -Tests @{Remove="ABS","ABWQ"}  <br/> To disable all the tests for a watcher node, set the value of the Tests parameter to $Null:  <br/> -Tests $Null  <br/> |
| _TestUsers_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |SIP addresses of the test users employed by the watcher node. To add additional test users to the node use syntax similar to this:  <br/> -TestUsers @{Add="sip:aidan@litwareinc.com"}  <br/> To remove a test user from the watcher node user syntax like this:  <br/> -TestUsers @{Remove="sip:aidan@litwareinc.com"  <br/> To replace an existing user with a new user, use the Replace method. For example, this syntax replaces the user sip:pilar@litwareinc.com with the new user sip:aidan@litwareinc.com:  <br/> -TestUsers @{Replace="sip:pilar@litwareinc.com","sip:aidan@litwareinc.com"}  <br/> You must always have at least two test users per watcher node. If you have two users and try to remove one of those users (ostensibly leaving the node with just one test user) your command will fail.  <br/> |
| _UseInternalWebUrls_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True), instructs the watcher node to use the internal Web URLs rather than the external Web URLs. This provides a way to way to verify URL validity for users located behind the organization's firewall.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _XmppTestReceiverMailAddress_ <br/> |Optional  <br/> |System.String  <br/> |XMPP email address to be used when testing the XMPP gateway.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsWatcherNodeConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TargetPool#Decorated object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsWatcherNodeConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TargetPool#Decorated object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsWatcherNodeConfiguration](get-cswatchernodeconfiguration.md)
  
[New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)
  
[Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)
  
[Test-CsWatcherNodeConfiguration](test-cswatchernodeconfiguration.md)

