---
title: Move multiple users to the pilot pool
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Move multiple users to the pilot pool
ms:assetid: 9492797f-2a26-4773-8ad2-97cb53fa68fc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688143(v=OCS.15)
ms:contentKeyID: 49733745
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Move multiple users to the pilot pool

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-02_

You can move multiple users from your Office Communications Server 2007 R2 pool to your Lync Server 2013 pilot pool using Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.

<div>

## To move multiple users by using the Lync Server 2013 Control Panel

1.  Open **Lync Server Control Panel**.

2.  From the **User Search** tab, click the **Search** button.

3.  Next, click **Add Filter**.

4.  Create a filter where **Office Communications Server user** is equal to **True**.

5.  Click **Find** to search for legacy Office Communications Server 2007 R2 users.

6.  Select two users that you want to move to the Lync Server 2013 pool. In this example, we will move users Chen Yang and Claus Hansen.
    
    ![User list displayed from searching for OCS users](images/JJ688143.76beb4fa-72e0-41ef-b96e-3553e96645c0(OCS.15).jpg "User list displayed from searching for OCS users")  

7.  From the **Action** menu, select **Move selected users to pool**.

8.  From the drop-down list, select the Lync Server 2013 pool.

9.  Click **Action** and then click **Move selected users to pool**. Click OK.
    
    ![Move Users, destination registrar pool dialog box](images/JJ205401.8a375003-dc00-4541-b578-4d88f2010601(OCS.15).png "Move Users, destination registrar pool dialog box")  

10. Verify that the **Registrar pool** column for the users now contains the Lync Server 2013 pool, which indicates that the users have been successfully moved.

</div>

<div>

## To move multiple users by using the Lync Server 2013 Management Shell

1.  Open the Lync Server 2013 Management Shell.

2.  At the command line, type the following and replace **User1** and **User2** with specific user names you want to move and replace **pool\_FQDN** with the name of the destination pool. In this example we will move users Hao Chen and Katie Jordan.
    
        Get-CsUser -Filter {DisplayName -eq "User1" -or DisplayName - eq "User2"} | Move-CsLegacyUser -Target "pool_FQDN"
    
    ![Example cmdlet to move a legacy user](images/JJ688143.57cfc28e-3df5-459f-83ef-8b0edf182a25(OCS.15).jpg "Example cmdlet to move a legacy user")  

3.  At the command line, type the following
    
        Get-CsUser -Identity "User1"

4.  The **Registrar Pool** identity should now point to the pool you specified as **pool\_FQDN** in the previous step. The presence of this identity confirms that the user has been successfully moved. Repeat step to verify **User2** has been moved.
    
    ![Output of PowerShell Get-UsUser -Identity cmdlet](images/JJ205096.8ff04c67-37a0-4156-bfbc-28f9f7b137c8(OCS.15).jpg "Output of PowerShell Get-UsUser -Identity  cmdlet")  

</div>

<div>

## To move all users at the same time by using the Lync Server 2013 Management Shell

In this example, all users have been returned to the Office Communications Server 2007 R2 pool (pool01.contoso.net). Using the Lync Server 2013 Management Shell, we will move all users at the same time to the Lync Server 2013 pool (pool02.contoso.net).

1.  Open the **Lync Server 2013 Management Shell**.

2.  At the command line, type the following:
    
        Get-CsUser -OnOfficeCommunicationServer | Move-CsLegacyUser -Target "pool_FQDN"
    
    ![Example cmdlet to move all legacy users in a pool](images/JJ688143.e6a2d578-296e-476c-bd45-d757917ea853(OCS.15).jpg "Example cmdlet to move all legacy users in a pool")  

3.  Next, run **Get-CsUser** for one of the pilot users.
    
        Get-CsUser -Identity "Hao Chen"

4.  The **Registrar Pool** identity for each user now points to the pool you specified as “pool\_FQDN” in the previous step. The presence of this identity confirms that the user has been successfully moved.

5.  Additionally, we can view the list of users in the Lync Server 2013 Control Panel and verify that the Registrar Pool value now points to the Lync Server 2013 pool.
    
    ![Lync Server 2013 Control Panel user list](images/JJ205096.3f2e87a7-ec59-43c5-82cb-e770108bfb04(OCS.15).jpg "Lync Server 2013 Control Panel user list")  

</div>

</div>

<span> </span>

</div>

</div>

</div>

