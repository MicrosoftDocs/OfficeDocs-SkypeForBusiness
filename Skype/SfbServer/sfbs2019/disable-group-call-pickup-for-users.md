---
title: "Disable Group Call Pickup for users in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 91b06f9e-2840-45a2-bbb3-6a29179b9a9f
description: "Use the following procedure to disable Group Call Pickup for a user."
---

# Disable Group Call Pickup for users in Lync Server 2013
[]
Use the following procedure to disable Group Call Pickup for a user.
  
> [!NOTE]
> When you disable Group Call Pickup for a user, the call pickup group number that was assigned to the user is not retained. If you subsequently want to re-enable Group Call Pickup for that user, you must assign the call pickup group number again with the /enablegrouppickup parameter. 
  
### To disable Group Call Pickup for a user

1. Log on to the computer where you installed the SEFAUtil tool with administrator rights.
    
2. At the command line, run:
    
  ```
  SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /disablegrouppickup
  ```

    For example:
    
  ```
  SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /disablegrouppickup
  ```

## See also

#### 

[Assign Group Call Pickup numbers to users in Lync Server 2013](assign-group-call-pickup-numbers-to-users.md)
  
[Enable Group Call Pickup for users in Lync Server 2013](enable-group-call-pickup-for-users.md)

