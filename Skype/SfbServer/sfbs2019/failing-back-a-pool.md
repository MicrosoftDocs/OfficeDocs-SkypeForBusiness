---
title: "Failing back a pool in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6232b644-ef57-4c9c-abec-14ff8ffc9fe7
description: "After the pool that experienced the disaster is back online (that is, Pool1 in this example), take the following steps to restore your deployment to regular working status."
---

# Failing back a pool in Lync Server 2013
[]
After the pool that experienced the disaster is back online (that is, Pool1 in this example), take the following steps to restore your deployment to regular working status.
  
Note that the failback process takes several minute to complete. For reference, it is expected to take up to 60 minutes for a pool of 20,000 users.
  
1. Fail back the users who were originally homed in Pool1 and have been failed over to Pool2 by typing the following cmdlet:
    
  ```
  Invoke-CsPoolFailback -PoolFQDN <Pool1 FQDN> -Verbose
  ```

No other steps are necessary. If you failed over the Central Management Server, you can leave it in Pool2.
  

