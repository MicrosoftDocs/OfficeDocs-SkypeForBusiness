---
title: "Move multiple users to the pilot pool"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You can move multiple users from your legacy pool to your Skype for Business Server 2019 pilot pool using Skype for Business Server 2019 Control Panel or Skype for Business Server 2019 Management Shell."
---

# Move multiple users to the pilot pool

You can move multiple users from your legacy pool to your Skype for Business Server 2019 pilot pool using Skype for Business Server 2019 Control Panel or Skype for Business Server 2019 Management Shell.

 **In this article**
  
[To move multiple users by using the Skype for Business Server 2019 Control Panel](#sectionSection0)
  
[To move multiple users by using the Skype for Business Server 2019 Management Shell](#sectionSection1)
  
[To move all users at the same time by using the Skype for Business Server 2019 Management Shell](#sectionSection2)
  
  
## To move multiple users by using the Skype for Business Server 2019 Control Panel
<a name="sectionSection0"> </a>

1. Open Skype for Business Server Control Panel.
    
2. Click **Users**, click **Search**, and then click **Find**.
    
3. Select two users that you want to move to the Skype for Business Server 2019 pool. In this example, we will move users Chen Yang and Claus Hansen.
    
     ![Move users to specific register pool](../media/Migration_LyncServer_CPanel_fromLyncServer2010_MoveMultipleUsersList.JPG)
  
4. From the **Action** menu, select **Move selected users to pool**.
    
5. From the drop-down list, select the Skype for Business Server 2019 pool.
    
6. Click **Action**, and then click **Move selected users to pool**. Click **OK**.
    
     ![Move Users, destination registrar pool dialog box](../media/Migration_LyncServer_from_LyncServer2010_CPanelMoveUserSelectPoolDialog.png)
  
7. Verify that the **Registrar pool** column for the users now contains the Skype for Business Server 2019 pool, which indicates that the users have been successfully moved. 
    
## To move multiple users by using the Skype for Business Server 2019 Management Shell
<a name="sectionSection1"> </a>

1. Open the Skype for Business Server 2019 Management Shell. 
    
2. At the command line, type the following and replace **User1** and **User2** with specific user names you want to move, and replace **pool_FQDN** with the name of the destination pool. In this example we will move users Hao Chen and Katie Jordan. 
    
   ```
   Get-CsUser -Filter {DisplayName -eq "User1" -or DisplayName - eq "User2"} | Move-CsUser -Target "pool_FQDN"
   ```

    ![Example of PowerShell Get-CsUser cmdlet](../media/Migration_LyncServer_from_LyncServer2010_move2users.jpg)
  
3. At the command line, type the following: 
    
   ```
   Get-CsUser -Identity "User1"
   ```

4. The **Registrar Pool** identity should now point to the pool you specified as **pool_FQDN** in the previous step. The presence of this identity confirms that the user has been successfully moved. Repeat step to verify that **User2** has been moved. 
    
     ![Output of PowerShell Get-UsUser -Identity  cmdlet](../media/Migration_LyncServer_from_LyncServer2010_showuser.jpg)
  
## To move all users at the same time by using the Skype for Business Server 2019 Management Shell
<a name="sectionSection2"> </a>

In this example, all users have been returned to the legacy pool (pool01.contoso.net). Using the Skype for Business Server 2019 Management Shell, we will move all users at the same time to the Skype for Business Server 2019 pool (pool02.contoso.net).
  
1. Open the Skype for Business Server 2019 Management Shell.
    
2. At the command line, type the following: 
    
   ```
   Get-CsUser -OnLyncServer | Move-CsUser -Target "pool_FQDN"
   ```

     ![PowerShell cmdlet and results in Management Shell](../media/Migration_LyncServer_CPanel_fromLyncServer2010_Move-CSUserMultipleAll.png)
  
3. Run **Get-CsUser** for one of the pilot users. 
    
   ```
   Get-CsUser -Identity "Hao Chen"
   ```

4. The **Registrar Pool** identity for each user now points to the pool you specified as **pool_FQDN** in the previous step. The presence of this identity confirms that the user has been successfully moved. 
    
5. Additionally, we can view the list of users in the Skype for Business Server 2019 Control Panel and verify that the Registrar Pool value now points to the Skype for Business Server 2019 pool.
    
     ![Skype for Business Server 2019 Control Panel user list](../media/Migration_LyncServer_CPanel_fromLyncServer2010_Move-CSUserVerifyHao.JPG)
  

