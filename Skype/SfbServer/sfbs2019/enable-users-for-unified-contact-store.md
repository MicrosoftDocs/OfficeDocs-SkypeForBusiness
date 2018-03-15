---
title: "Enable users for unified contact store in Lync Server 2013"
ms.author: tonysmit
author: tonysmit
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7b46a01f-beb5-4a33-adb0-35f0502b168d
description: "When you deploy Lync Server 2013 and publish the topology, unified contact store is enabled for all users by default. You do not need to take any additional action to enable unified contact store after you deploy Lync Server 2013. However, you can use the Set-CsUserServicesPolicy cmdlet to customize which users have unified contact store available. You can enable this feature globally, by site, by tenant, or by individuals or groups of individuals."
---

# Enable users for unified contact store in Lync Server 2013
[]
When you deploy Lync Server 2013 and publish the topology, unified contact store is enabled for all users by default. You do not need to take any additional action to enable unified contact store after you deploy Lync Server 2013. However, you can use the **Set-CsUserServicesPolicy** cmdlet to customize which users have unified contact store available. You can enable this feature globally, by site, by tenant, or by individuals or groups of individuals. 
  
### To enable users for unified contact store

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Do any of the following:
    
  - To enable unified contact store globally for all Lync Server users, at the command line, type:
    
  ```
  Set-CsUserServicesPolicy -Identity global -UcsAllowed $True
  ```

  - To enable unified contact store for the users at a specific site, at the command line, type:
    
  ```
  New-CsUserServicesPolicy -Identity site:<site name> -UcsAllowed $True
  ```

    For example:
    
  ```
  New-CsUserServicesPolicy -Identity site:Redmond -UcsAllowed $True
  ```

  - To enable unified contact store by tenant, at the command line, type:
    
  ```
  Set-CsUserServicesPolicy -Tenant <tenantId> -UcsAllowed $True
  ```

    For example:
    
  ```
  Set-CsUserServicesPolicy -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308" -UcsAllowed $True
  ```

  - To enable unified contact store for specific users, at the command line, type:
    
  ```
  New-CsUserServicesPolicy -Identity "<policy name>" -UcsAllowed $True
  Grant-CsUserServicesPolicy -Identity "<user display name>" -PolicyName <"policy name">
  
  ```

    > [!NOTE]
    > You can also use user alias or SIP URI instead of the user display name. 
  
    For example:
    
  ```
  New-CsUserServicesPolicy -Identity "UCS Enabled Users" -UcsAllowed $True
  Grant-CsUserServicesPolicy -Identity "Ken Myer" -PolicyName "UCS Enabled Users"
  
  ```

    > [!NOTE]
    > In the preceding example, the first command creates a new per-user policy named UCS Enabled Users with the UcsAllowed flag set to True. The second command assigns the policy to the user with the display name Ken Myer, which means that Ken Myer is now enabled for unified contact store. 
  

