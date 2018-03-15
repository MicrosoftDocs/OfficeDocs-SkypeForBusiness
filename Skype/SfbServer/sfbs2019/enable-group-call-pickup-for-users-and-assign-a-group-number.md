---
title: "Enable Group Call Pickup for users in Lync Server 2013 and assign a group number"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c33bb6c2-d43b-4fb6-a0fa-6d82a7b09abe
description: "After you add call pickup group numbers to the call park orbit table, you assign the group numbers to users and enable Group Call Pickup for them. Use the secondary extension feature activation (SEFAUtil) resource kit tool to assign group numbers and enable Group Call Pickup."
---

# Enable Group Call Pickup for users in Lync Server 2013 and assign a group number
[]
After you add call pickup group numbers to the call park orbit table, you assign the group numbers to users and enable Group Call Pickup for them. Use the secondary extension feature activation (SEFAUtil) resource kit tool to assign group numbers and enable Group Call Pickup.
  
> [!NOTE]
> In a hybrid deployment, do not assign a Group Call Pickup group to users who are homed online. Users who are homed online cannot participate in Group Call Pickup. That is, their calls cannot be answered by other users, and they cannot answer calls to other users. 
  
### To assign a group number and enable Group Call Pickup for a user

1. Log on to the computer where you installed the SEFAUtil tool with administrator rights.
    
2. At the command line, run:
    
  ```
  SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /enablegrouppickup:<group number>
  ```

    For example, to assign group number 199 to a user:
    
  ```
  SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /enablegrouppickup:199 
  ```

## See also

#### 

[Disable Group Call Pickup for users in Lync Server 2013](disable-group-call-pickup-for-users.md)

