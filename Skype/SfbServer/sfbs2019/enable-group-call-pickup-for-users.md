---
title: "Enable Group Call Pickup for users in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 20ec5f41-6ba2-4156-82ed-b91d05b62a6d
description: "Use the SEFAUtil resource kit tool to enable Group Call Pickup for users. Users must be assigned a group number with type GroupPickup in the call park orbit table to have Group Call Pickup enabled. You assign a call pickup group number and enable Group Call Pickup at the same time by using the /enablegrouppickup parameter when you run SEFAUtil.exe."
---

# Enable Group Call Pickup for users in Lync Server 2013
[]
Use the SEFAUtil resource kit tool to enable Group Call Pickup for users. Users must be assigned a group number with type GroupPickup in the call park orbit table to have Group Call Pickup enabled. You assign a call pickup group number and enable Group Call Pickup at the same time by using the /enablegrouppickup parameter when you run SEFAUtil.exe. 
  
### To enable Group Call Pickup for a user

1. Log on to the computer where you installed the SEFAUtil tool with administrator rights.
    
2. At the command line, run:
    
  ```
  SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /enablegrouppickup:<group number>
  ```

    For example:
    
  ```
  SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /enablegrouppickup:199
  ```

## See also

#### 

[Assign Group Call Pickup numbers to users in Lync Server 2013](assign-group-call-pickup-numbers-to-users.md)
  
[Disable Group Call Pickup for users in Lync Server 2013](disable-group-call-pickup-for-users.md)

