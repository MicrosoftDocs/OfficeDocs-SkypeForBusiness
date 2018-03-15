---
title: "Test-CsWatcherNodeConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 085507a1-17e8-4dfa-aa6a-062620584335
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsWatcherNodeConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Verifies the watcher node configuration settings in use in your organization. Watcher nodes are computers that periodically use Microsoft System Center Operations Manager and Lync Server 2013 synthetic transactions to verify that Lync Server components are working as expected. This cmdlet was introduced in Lync Server 2013.
  
```
Test-CsWatcherNodeConfiguration [-FileName <String>] [-ReadCredentialsFromCurrentUserStore <SwitchParameter>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 verifies the configuration settings for each watcher node in use in the organization.
  
```
Test-CsWatcherNodeConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

If you are using Microsoft System Center Operations Manager to monitor Lync Server 2013 then you have the option of setting up "watcher nodes": computers that periodically, and automatically, run synthetic transactions in order to verify that Lync Server is working as expected. Watcher nodes are assigned to pools, and are managed using the **CsWatcherNodeConfiguration** cmdlets. Note that you do not need to install watcher nodes if you are using System Center Operations Manager. You can still monitor your system without using watcher nodes; the only difference is that any synthetic transactions you want to run will need to be invoked manually rather than automatically invoked by Operations Manager. 
  
The **Test-CsWatcherNodeConfiguration** cmdlet provides a way for you to verify that a watcher node has been correctly configured and is assigned to a valid Lync Server 2013 pool. Note that the **Test-CsWatcherNodeConfiguration** cmdlet must be run on the watcher node itself; the cmdlet cannot be run against remote computers. 
  
 **Lync Server Control Panel:** The functions carried out by the **Test-CsWatcherNodeConfiguration** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FileName_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  <br/>  -Report "C:\Logs\WatcherNode.html"  <br/> |
| _ReadCredentialsFromCurrentUserStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, instructs the **Test-CsWatcherNodeConfiguration** cmdlet to retrieve the user credentials from the user's credentials store. By default, the **Test-CsWatcherNodeConfiguration** cmdlet looks for credentials in the network service account's credentials store.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Test-CsWatcherNodeConfiguration** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsWatcherNodeConfiguration** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsWatcherNodeConfiguration](get-cswatchernodeconfiguration.md)
  
[New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)
  
[Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)
  
[Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)

