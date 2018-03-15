---
title: "Failing over a mirrored database in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 70185476-e3d4-440a-9316-fa24b226343e
description: "If you have configured your back-end database to use synchronized mirroring with a witness, failover is automatic. If you have configured synchronized mirroring without a witness, you can use the following procedures to failover and failback your database. You can also use these procedures to manually failover and failback your databases even if you have configured a witness."
---

# Failing over a mirrored database in Lync Server 2013
[]
If you have configured your back-end database to use synchronized mirroring with a witness, failover is automatic. If you have configured synchronized mirroring without a witness, you can use the following procedures to failover and failback your database. You can also use these procedures to manually failover and failback your databases even if you have configured a witness.
  
## To fail over your back-end database

1. Before failing over, determine which back-end database is the principal and which is the mirror by typing the following cmdlet:
    
  ```
  Get-CsDatabaseMirrorState -PoolFqdn <poolFQDN> -DatabaseType User
  ```

2. If the Central Management store is hosted in this pool, type the following cmdlet to determine which is the principal and which is the mirror for the Central Management store:
    
  ```
  Get-CsDatabaseMirrorState -PoolFqdn <poolFQDN> -DatabaseType CentralMgmt
  ```

3. Perform the failover of the user database: 
    
  - If the primary has failed and you are failing over to the mirror, type:
    
  ```
  Invoke-CsDatabaseFailover -PoolFqdn <poolFQDN> -DatabaseType User -NewPrincipal mirror -Verbose
  ```

  - If the mirror has failed and you are failing over to the primary, type:
    
  ```
  Invoke-CsDatabaseFailover -PoolFqdn <poolFQDN> -DatabaseType User -NewPrincipal primary -Verbose
  ```

4. If the pool hosts the Central Management Server, perform the failover of the Central Management store. 
    
  - If the primary has failed and you are failing over to the mirror, type:
    
  ```
  Invoke-CsDatabaseFailover -PoolFqdn <poolFQDN> -DatabaseType CentralMgmt -NewPrincipal mirror -Verbose
  ```

  - If the mirror has failed and you are failing over to the primary, type:
    
  ```
  Invoke-CsDatabaseFailover -PoolFqdn <poolFQDN> -DatabaseType CentralMgmt -NewPrincipal primary -Verbose
  ```


