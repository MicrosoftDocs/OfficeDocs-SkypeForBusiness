---
title: New-CsWatcherNodeConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: c7f78c92-7965-4879-9efa-1b5adcd1881b
---


# New-CsWatcherNodeConfiguration
[]
Assigns a new collection of watcher node configuration settings to a pool. Watcher nodes are computers that periodically use Microsoft System Center Operations Manager and Skype for Business Server 2015 synthetic transactions to verify that Skype for Business Server 2015 components are working as expected. This cmdlet was introduced in Lync Server 2013.
  
    
    


> [!NOTE]
> The **New-CsWatcherNodeConfiguration** command should only be executed on the Trusted Application Server you are designating as a Watcher Node.
  
    
    


```

New-CsWatcherNodeConfiguration -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The commands shown in Example 1 create a new collection of watcher node configuration settings for the pool atl-cs-001.litwareinc.com. To do this, the first two commands in the example create a pair watcher node test users (sip:kenmyer@litwareinc.com and sip:pilar@litwareinc.com). After the test users have been created, the third command in the example creates a new extended PSTN test using the two newly-created users. This new test (which, at this point in time, exists only in memory) is stored in a variable named $x.
  
    
    
Finally, the fourth command in the example creates the watcher node configuration settings for atl-cs-001.litwareinc.com. These new settings use port 5061; the two new test users; and the extended test stored in the variable $x.
  
    
    



```

Set-CsTestUserCredential -SipAddress "sip:kenmyer@litwareinc.com" -UserName "litwareinc\\kenmyer" -Password "07Apples"

Set-CsTestUserCredential -SipAddress "sip:pilar@litwareinc.com" -UserName "litwareinc\\pilar" -Password "07Apples"

$x = New-CsExtendedTest -TestUsers "sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com" -Name "PSTN Test" -TestType "PSTN"

New-CsWatcherNodeConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers "sip:kenmyer@litwareinc.com","sip:pilar@litwareinc.com"} -ExtendedTests @{Add=$x}
```


## Detailed Description
<a name="DetailedDescription"> </a>

If you are using Microsoft System Center Operations Manager to monitor Skype for Business Server 2015 then you have the option of setting up "watcher nodes": computers that periodically, and automatically, run synthetic transactions in order to verify that Skype for Business Server 2015 is working as expected. Watcher nodes are assigned to pools, and are managed using the **CsWatcherNodeConfiguration** cmdlets. Note that you do not need to install watcher nodes if you are using System Center Operations Manager. You can still monitor your system without using watcher nodes; the only difference is that any synthetic transactions you want to run will need to be invoked manually rather than automatically invoked by Operations Manager.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **New-CsWatcherNodeConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name of the pool being associated with the watcher node configuration settings. You can use either the Identity parameter or the TargetFqdn parameter to specify the pool; however, you cannot use both these parameters in the same command.  <br/> |
| _PortNumber_ <br/> |Required  <br/> |System.UInt16  <br/> |SIP port used by the Registrar service.  <br/> |
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name of the pool being associated with the watcher node configuration settings. You can use either the TargetFqdn parameter or the Identity parameter to specify the pool; however, you cannot use both these parameters in the same command.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Enables or disables the watcher node. The default value is True ($True).  <br/> |
| _ExtendedTests_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |PSTN or Audio Conferencing Provider tests that can be assigned to a watcher node configuration. These tests must be created using the **New-CsExtendedTest** cmdlet and stored in a variable (for example, $x). The test can then be assigned to a watcher node by using syntax similar to this: <br/>  `-ExtendedTests @{Add=$x}` <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _Tests_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Synthetic transactions to be run by the watcher node. Allowed values are:  <br/> Registration  <br/> IM  <br/> GroupIM  <br/> P2PAV  <br/> AvConference  <br/> Presence  <br/> ABS  <br/> ABWQ  <br/> MCXP2PIM  <br/> ExumConnectivity  <br/> JoinLauncher  <br/> PersistentChatMessage  <br/> DataConference  <br/> XmppIM  <br/> UnifiedContactStore  <br/> AVEdgeConnectivity  <br/> To configure tests at the time you create a new watcher node, use the following syntax, separating the individual tests by using commas:  <br/>  `-Tests "ABS","ABWQ","IM","GroupIM","XmppIM"` <br/> |
| _TestUsers_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |SIP addresses of the test users to be assigned to the watcher node; these user accounts must have previously been configured by using the **Set-CsTestUserCredential** cmdlet. To add test users, use syntax similar to this, separating user addresses by using commas: <br/>  `-TestUsers "sip:kenmyer@litwareinc.com","sip:pilar@litwareinc.com"` <br/> |
| _UseAutoDiscovery_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True), Skype for Business Online watcher nodes will use the Autodiscover service to locate the target pool. When set to False (the default value) watcher nodes will use SRV records to locate the pool.  <br/> |
| _UseInternalWebUrls_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True), instructs the watcher node to use the internal Web URLs rather than the external Web URLs. This provides a way to way to verify URL validity for users located behind the organization's firewall.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _XmppTestReceiverMailAddress_ <br/> |Optional  <br/> |System.String  <br/> |XMPP email address to be used when testing the XMPP gateway.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **New-CsWatcherNodeConfiguration** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **New-CsWatcherNodeConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TargetPool#Decorated object.
  
    
    

