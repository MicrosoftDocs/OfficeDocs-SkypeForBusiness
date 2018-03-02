---
title: "Patch or update Front End Servers in Skype for Business Server 2015"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 4/4/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 20fa39ae-ecfb-4c72-9cc4-8e183d3c752f
description: "Summary: learn how to apply upgrades or patches to Front End Servers in Skype for Business Server."
---

# Patch or update Front End Servers in Skype for Business Server 2015
 
**Summary:** learn how to apply upgrades or patches to Front End Servers in Skype for Business Server.
  
When you patch the servers in a Front End pool, you do so one server at a time. 
  
### To apply an upgrade to the Front End servers in a pool

1. Type the following cmdlet:
    
  ```
  Get-CsPoolFabricState -PoolFqdn <PoolFQDN>
  ```

     If this cmdlet shows any missing replicas, then run the following cmdlet to recover the pool before you apply any patches.
    
  ```
  Reset-CsPoolRegistrarState -ResetType QuorumLossRecovery
  ```

2. On the first server you want to patch, run the following cmdlet:
    
  ```
  Invoke-CsComputerFailOver -ComputerName <Front End Server to be patched>
  ```

    This cmdlet moves all services to other Front End Servers in the pool, and takes this server offline.
    
3. Apply the upgrade or patch to this server.
    
4. On the upgraded server, run the following cmdlet:
    
  ```
  Invoke-CsComputerFailBack -ComputerName <Front End Server to be patched>
  ```

    The server is returned to service.
    
5. Repeat Steps 2-4 for each server that needs to be upgraded.
    

