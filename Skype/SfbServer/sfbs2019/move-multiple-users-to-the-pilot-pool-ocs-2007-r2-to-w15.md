---
title: "Move multiple users to the pilot pool [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9492797f-2a26-4773-8ad2-97cb53fa68fc
description: "In this articleTo move multiple users by using the Lync Server 2013 Control PanelTo move multiple users by using the Lync Server 2013 Management ShellTo move all users at the same time by using the Lync Server 2013 Management Shell"
---

# Move multiple users to the pilot pool [OCS 2007 R2 to W15]
[]
 **In this article**
  
[To move multiple users by using the Lync Server 2013 Control Panel](#sectionSection0)
  
[To move multiple users by using the Lync Server 2013 Management Shell](#sectionSection1)
  
[To move all users at the same time by using the Lync Server 2013 Management Shell](#sectionSection2)
  
You can move multiple users from your Office Communications Server 2007 R2 pool to your Lync Server 2013 pilot pool using Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.
  
## To move multiple users by using the Lync Server 2013 Control Panel
<a name="sectionSection0"> </a>

1. Open **Lync Server Control Panel**.
    
2. From the **User Search** tab, click the **Search** button. 
    
3. Next, click **Add Filter**.
    
4. Create a filter where **Office Communications Server user** is equal to **True**. 
    
5. Click **Find** to search for legacy Office Communications Server 2007 R2 users. 
    
6. Select two users that you want to move to the Lync Server 2013 pool. In this example, we will move users Chen Yang and Claus Hansen.
    
     ![User list displayed from searching for OCS users](media/migration_lyncserver_w15_tb_twousersearch.JPG)
  
7. From the **Action** menu, select **Move selected users to pool**.
    
8. From the drop-down list, select the Lync Server 2013 pool.
    
9. Click **Action** and then click **Move selected users to pool**. Click OK.
    
     ![Move Users, destination registrar pool dialog box](media/Migration_LyncServer_from_LyncServer2010_CPanelMoveUserSelectPoolDialog.png)
  
10. Verify that the **Registrar pool** column for the users now contains the Lync Server 2013 pool, which indicates that the users have been successfully moved. 
    
## To move multiple users by using the Lync Server 2013 Management Shell
<a name="sectionSection1"> </a>

1. Open the Lync Server 2013 Management Shell. 
    
2.  At the command line, type the following and replace **User1** and **User2** with specific user names you want to move and replace **pool_FQDN** with the name of the destination pool. In this example we will move users Hao Chen and Katie Jordan. 
    
  ```
  Get-CsUser -Filter {DisplayName -eq "User1" -or DisplayName - eq "User2"} | Move-CsLegacyUser -Target "pool_FQDN"
  ```

     ![Example cmdlet to move a legacy user](media/migration_lyncserver_w15_movelegacyuser_w13.JPG)
  
3. At the command line, type the following 
    
  ```
  Get-CsUser -Identity "User1"
  ```

4. The **Registrar Pool** identity should now point to the pool you specified as **pool_FQDN** in the previous step. The presence of this identity confirms that the user has been successfully moved. Repeat step to verify **User2** has been moved. 
    
     ![Output of PowerShell Get-UsUser -Identity  cmdlet](media/Migration_LyncServer_from_LyncServer2010_showuser.jpg)
  
## To move all users at the same time by using the Lync Server 2013 Management Shell
<a name="sectionSection2"> </a>

In this example, all users have been returned to the Office Communications Server 2007 R2 pool (pool01.contoso.net). Using the Lync Server 2013 Management Shell, we will move all users at the same time to the Lync Server 2013 pool (pool02.contoso.net).
  
1. Open the **Lync Server 2013 Management Shell**.
    
2. At the command line, type the following: 
    
  ```
  Get-CsUser -OnOfficeCommunicationServer | Move-CsLegacyUser -Target "pool_FQDN"
  ```

     ![Example cmdlet to move all legacy users in a pool](media/migration_lyncserver_w15_movelegacyuser_w13_moveall.JPG)
  
3. Next, run **Get-CsUser** for one of the pilot users. 
    
  ```
  Get-CsUser -Identity "Hao Chen"
  ```

4. The **Registrar Pool** identity for each user now points to the pool you specified as "pool_FQDN" in the previous step. The presence of this identity confirms that the user has been successfully moved. 
    
5. Additionally, we can view the list of users in the Lync Server 2013 Control Panel and verify that the Registrar Pool value now points to the Lync Server 2013 pool.
    
     ![Lync Server 2013 Control Panel user list](media/Migration_LyncServer_CPanel_fromLyncServer2010_Move-CSUserVerifyHao.JPG)
  

