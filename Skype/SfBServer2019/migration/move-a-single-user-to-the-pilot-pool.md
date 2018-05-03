---
title: "Move a single user to the pilot pool [W14 to W15 ]"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e9de81a8-40dd-4446-81e7-a2b810eaea50
description: "You can move a user from your Lync Server 2010 pool to your Lync Server 2013 pilot pool using Lync Server 2013 Control Panel or Lync Server 2013 Management Shell. In the example below, in the Registrar pool column, pool01.contoso.net is the Lync Server 2010 pool, and all six of these users are connected to this pool. Use the following procedures to move a user to your Lync Server 2013 pool using Lync Server 2013 Control Panel and Lync Server Management Shell."
---

# Move a single user to the pilot pool [W14 to W15 ]
[]
You can move a user from your Lync Server 2010 pool to your Lync Server 2013 pilot pool using Lync Server 2013 Control Panel or Lync Server 2013 Management Shell. In the example below, in the Registrar pool column, **pool01.contoso.net** is the Lync Server 2010 pool, and all six of these users are connected to this pool. Use the following procedures to move a user to your Lync Server 2013 pool using Lync Server 2013 Control Panel and Lync Server Management Shell. 
  
## To move a user by using the Lync Server 2013 Control Panel

**List of users in the Lync Server 2013 Control Panel**

![Lync Server Control Panel, Move User dialog](../../media/Migration_LyncServer_from_LyncServer2010_CPanelMoveUserDialog.jpg)
  
1. Log on to the Front End Server with an account that is a member of the RTCUniversalServerAdmins group or a member of the CsAdministrator or CsUserAdministrator administrative role.
    
2. Open **Lync Server Control Panel**.
    
3. Click **Users**, click Search, and then click **Find**.
    
4. Select a user that you want to move to the Lync Server 2013 pool. In this example, we will move user Sara Davis.
    
5. On the **Action** menu, select **Move selected users to pool**.
    
6. From the drop-down list, select the Lync Server 2013 pool.
    
7. Click **Action** and then click **Move selected users to pool**. Click **OK**.
    
     ![Move Users, destination registrar pool dialog box](../../media/Migration_LyncServer_from_LyncServer2010_CPanelMoveUserSelectPoolDialog.png)
  
8. Verify that the **Registrar pool** column for the user now contains the Lync Server 2013 pool, which indicates that the user has been successfully moved. 
    
## To move a user by using the Lync Server 2013 Management Shell

1. Open the Lync Server Management Shell.
    
2. At the command line, type the following: 
    
  ```
  Move-CsUser -Identity "David Pelton" -Target "pool02.contoso.net"
  ```

3. Next, at the command line, type the following: 
    
  ```
  Get-CsUser -Identity "David Pelton"
  ```

4. The **RegistrarPool** identity now points to the Lync Server 2013 pool. The presence of this identity confirms that the user has been successfully moved. 
    
     ![Output from Get-CsUser cmdlet with Identity filter](../../media/migration_lyncserver_w15_movesingleuser_getcsuser.JPG)
  
    > [!NOTE]
    > For details about the **Get-CsUser** cmdlet, run: **Get-Help Get-CsUser -Detailed**
  

