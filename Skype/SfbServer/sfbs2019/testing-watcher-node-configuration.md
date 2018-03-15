---
title: "Testing watcher node configuration in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f9ecd85c-0ae9-4906-b786-6b002b5a77c6

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing watcher node configuration in Lync Server 2013
[]
 **In this article**
  
[Description](#sectionSection0)
  
[Running the test](#sectionSection1)
  
[Determining success or failure](#sectionSection2)
  
[Reasons why the test might have failed](#sectionSection3)
  
****

|||
|:-----|:-----|
|Verification schedule  <br/> |Daily  <br/> |
|Testing tool  <br/> |Windows PowerShell  <br/> |
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the **Test-CsWatcherNodeConfiguration** cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match " Test-CsWatcherNodeConfiguration"}```|
   
## Description
<a name="sectionSection0"> </a>

If you are using Microsoft System Center Operations Manager to monitor Lync Server 2013 then you have the option of setting up "watcher nodes": computers that periodically, and automatically, run synthetic transactions to verify that Lync Server is working as expected. Watcher nodes are assigned to pools, and are managed by using the **CsWatcherNodeConfiguration** cmdlets. Note that you do not need to install watcher nodes if you are using System Center Operations Manager. You can still monitor your system without using watcher nodes. The only difference is that any synthetic transactions that you want to run must be invoked manually instead of automatically invoked by Operations Manager. 
  
The **Test-CsWatcherNodeConfiguration** cmdlet enables you to verify that a watcher node was configured correctly and is assigned to a valid Lync Server 2013 pool. Note that the **Test-CsWatcherNodeConfiguration** cmdlet must be run on the watcher node itself. The cmdlet cannot be run against remote computers. 
  
## Running the test
<a name="sectionSection1"> </a>

The following command verifies the configuration settings for each watcher node that is being used in the organization.
  
```
Test-CsWatcherNodeConfiguration
```

## Determining success or failure
<a name="sectionSection2"> </a>

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
  
 Successfully validated existence of test user's credential sip:user1@ atl-cs-001.litwareinc.com in credential management store. 
  
 Successfully validated existence of test user's credential sip:user2@ atl-cs-001.litwareinc.com in credential management store. 
  
Checking for missing pools in watcher node configuration is started. If any error is detected, it will be printed.
  
WARNING: Pool atl-cs-001.litwareinc.com has Registrar
  
role installed, but there are no test users configured for it.
  
Checking for missing pools in watcher node configuration is finished.
  
Checking for watcher node registry keys created by watcher node installation, is
  
 started. If any error is detected, it will be printed. 
  
Test-CsWatcherNodeConfiguration : Cannot find Health registry key in
  
Software\Microsoft\Real-Time Communications. Make sure watcher node .msi is
  
installed properly.
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why **Test-CsWatcherNodeConfiguration** might fail: 
  
- Watcher node is not correctly installed. 
    
- No test users are configured. 
    
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsWatcherNodeConfiguration](get-cswatchernodeconfiguration.md)
  
[New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)
  
[Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)
  
[Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)

