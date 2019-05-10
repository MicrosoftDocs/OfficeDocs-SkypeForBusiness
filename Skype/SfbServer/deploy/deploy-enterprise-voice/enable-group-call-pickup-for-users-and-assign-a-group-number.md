---
title: "Enable Group Call Pickup for users and assign a group number in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: c33bb6c2-d43b-4fb6-a0fa-6d82a7b09abe
description: "Enable users for Group Call Pickup in Skype for Business Server Enterprise Voice, and assign a group number."
---

# Enable Group Call Pickup for users and assign a group number in Skype for Business

Enable users for Group Call Pickup in Skype for Business Server Enterprise Voice, and assign a group number.

After you add call pickup group numbers to the call park orbit table, you use the SEFAUtil tool to assign the group numbers to users and enable Group Call Pickup for them.

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

[Disable Group Pickup for Users](https://technet.microsoft.com/library/91b06f9e-2840-45a2-bbb3-6a29179b9a9f.aspx)

