---
title: "Managing watcher nodes in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 66deaf49-a71f-4a6e-ada0-ea8b688ee921
description: "In addition to modifying the synthetic transactions that are executed on a watcher node, administrators can also use the Set-CsWatcherNodeConfiguration cmdlet to carry out two other important tasks: enabling and disabling the watcher node, and configuring the watcher node to use either internal URLs or external URLs when running its tests."
---

# Managing watcher nodes in Lync Server 2013
[]
In addition to modifying the synthetic transactions that are executed on a watcher node, administrators can also use the **Set-CsWatcherNodeConfiguration** cmdlet to carry out two other important tasks: enabling and disabling the watcher node, and configuring the watcher node to use either internal URLs or external URLs when running its tests. 
  
By default, watcher nodes are designed to periodically run all their enabled synthetic transactions. Sometimes, however, you may need to suspend those transactions. For example, if the watcher node is temporarily disconnected from the network, then there is no reason to run the synthetic transactions. Without network connectivity, those transactions are guaranteed to fail. If you want to temporarily disable a watcher node, run a command similar to this from the Lync Server Management Shell:
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -Enabled $False
```

This command will disable the execution of synthetic transactions on the watcher node atl-watcher- 001.litwareinc.com. To resume execution of the synthetic transactions, set the Enabled property back to True ($True):
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -Enabled $True
```

> [!NOTE]
> The Enabled property can be used to turn watcher nodes on or off. If you want to permanently delete a watcher node, use the **Remove-CsWatcherNodeConfiguration** cmdlet: > Remove-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" > That command removes all the watcher node configuration settings from the specified computer, which prevents the computer from automatically running synthetic transactions. However, the command does not uninstall the System Center agent files or the Lync Server 2013 system files. 
  
By default, watcher nodes use an organization's external URLs when conducting their tests. However, watcher nodes can also be configured to use the organization's internal URLs. This enables administrators to verify URL access for users located inside the perimeter network. To configure a watcher node to use internal URLs instead of external URLs, set the UseInternalWebUrls property to True ($True):
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -UseInternalWebUrls $True
```

If you reset this property to the default value of False ($False), the watcher will then use the external URLs:
  
```
Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -UseInternalWebUrls $False
```


