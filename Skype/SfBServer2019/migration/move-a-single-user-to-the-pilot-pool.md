---
title: "Move a single user to the pilot pool"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You can move a user from your legacy pool to your Skype for Business Server 2019 pilot pool using Skype for Business Server 2019 Control Panel or Skype for Business Server 2019 Management Shell. In the example below, in the Registrar pool column, pool01.contoso.net is the legacy pool, and all six of these users are connected to this pool. Use the following procedures to move a user to your Skype for Business Server 2019 pool using Skype for Business Server 2019 Control Panel and Skype for Business Server Management Shell."
---

# Move a single user to the pilot pool

You can move a user from your legacy pool to your Skype for Business Server 2019 pilot pool using Skype for Business Server 2019 Control Panel or Skype for Business Server 2019 Management Shell. In the example below, in the **Registrar pool** column, **pool01.contoso.net** is the legacy pool, and all six of these users are connected to this pool. Use the following procedures to move a user to your Skype for Business Server 2019 pool using Skype for Business Server 2019 Control Panel and Skype for Business Server Management Shell. 
  
## To move a user by using the Skype for Business Server 2019 Control Panel
  
1. Log on to the Front End Server with an account that is a member of the RTCUniversalServerAdmins group or a member of the CsAdministrator or CsUserAdministrator administrative role.
    
2. Open **Skype for Business Server Control Panel**.
    
3. Click **Users**, click **Search**, and then click **Find**.
    
4. Select a user that you want to move to the Skype for Business Server 2019 pool. In this example, we will move user Sara Davis.
    
5. On the **Action** menu, select **Move selected users to pool**.
    
6. From the drop-down list, select the Skype for Business Server 2019 pool.
    
7. Click **Action**, and then click **Move selected users to pool**. Click **OK**.
  
8. Verify that the **Registrar pool** column for the user now contains the Skype for Business Server 2019 pool, which indicates that the user has been successfully moved. 
    
## To move a user by using the Skype for Business Server 2019 Management Shell

1. Open the Skype for Business Server Management Shell.
    
2. At the command line, type the following: 
    
   ```
   Move-CsUser -Identity "David Pelton" -Target "pool02.contoso.net"
   ```

3. Next, at the command line, type the following: 
    
   ```
   Get-CsUser -Identity "David Pelton"
   ```

4. The **RegistrarPool** identity now points to the Skype for Business Server 2019 pool. The presence of this identity confirms that the user has been successfully moved. 

    > [!NOTE]
    > For details about the **Get-CsUser** cmdlet, run: **Get-Help Get-CsUser -Detailed**
  

