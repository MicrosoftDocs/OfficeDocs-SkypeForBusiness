---
title: "Assign Group Call Pickup numbers to users in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b8e79275-8e7e-4799-b908-f34f61df22f0
description: "After you add Group Call Pickup group numbers to the call park orbit table, you can assign the groups to users. Use the secondary extension feature activation (SEFAUtil ) resource kit tool to assign call pickup groups to users."
---

# Assign Group Call Pickup numbers to users in Lync Server 2013
[]
After you add Group Call Pickup group numbers to the call park orbit table, you can assign the groups to users. Use the secondary extension feature activation (SEFAUtil ) resource kit tool to assign call pickup groups to users.
  
> [!NOTE]
> In a hybrid deployment, do not assign a Group Call Pickup group to users who are homed online. Users who are homed online cannot participate in Group Call Pickup. That is, their calls cannot be answered by other users, and they cannot answer calls to other users. 
  
### To assign a Group Call Pickup group to a user

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

[Enable Group Call Pickup for users in Lync Server 2013](enable-group-call-pickup-for-users.md)
  
[Disable Group Call Pickup for users in Lync Server 2013](disable-group-call-pickup-for-users.md)

