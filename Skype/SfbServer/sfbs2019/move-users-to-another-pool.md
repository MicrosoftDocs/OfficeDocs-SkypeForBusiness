---
title: "Move users to another pool in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 2/9/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e7b4968c-0e9d-4d56-b5f1-9edf0f7206f8
description: "You can use Lync Server Control Panel to assign users to a specific server or pool."
---

# Move users to another pool in Lync Server 2013
[]
You can use Lync Server Control Panel to assign users to a specific server or pool.
  
> [!TIP]
> Moving all existing users from a source pool that is running Lync Server 2010 or earlier to a Lync Server 2013 destination pool in a complex Active Directory environment might result in slower Active Directory replication. To avoid this, you can use search filters to move users from pools that are running Lync Server 2010 or earlier separately, or you can use Lync Server Management Shell to move users with cmdlets. Also, the filter functionality works with Lync Server 2013 users. 
  
### To move selected users to a different server or pool

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Users**.
    
4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want, and then click **Find**. 
    
5. In the table, select a specific user or users in the list. 
    
6. On the **Action** menu, click **Move selected users to pool**.
    
7. In **Move Users**, select the pool that you want to move the users to in **Destination registrar pool**.
    
8. (Optional) If the destination server or pool is unavailable, select the **Force** check box. 
    
    > [!CAUTION]
    > If you select **Force**, the user account is moved, but associated user data such scheduled conferences and contacts is not moved. 
  
### To move all users from one server or pool to a different server or pool

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Users**.
    
4. On the **Action** menu, click **Move all users to pool**.
    
5. In **Move Users**, select the pool that contains the user accounts that you want to move in **Source registrar pool**.
    
6. In **Destination registrar pool**, select the pool that you want to move the users to.
    
7. (Optional) If the destination server or pool is unavailable, select the **Force** check box. 
    
    > [!CAUTION]
    > If you select **Force**, the user account is moved, but associated user data such scheduled conferences and contacts is not moved. 
  
### To move users from one pool to a different pool by using a filter

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Users**.
    
4. In **User Search**, click **Search**, and then click **Add Filter**.
    
5. In the Search criteria, select **Registrar Pool**, select **Equal to**, select **Current Pool FQDN**, and then click **Find**.
    
6. On the **Action** menu, click **Move all users to pool**.
    
    > [!NOTE]
    > When a filter is applied to an existing set of users, the option **Move all users to pool** is in the context of the filtered subset of users, not **all** possible users. 
  
7. In **Move Users**, select the pool that contains the user accounts that you want to move in **Source registrar pool**.
    
8. In **Destination registrar pool**, select the pool where you want to move the users.
    
9. (Optional) If the destination server or pool is unavailable, select the **Force** check box. 
    
    > [!CAUTION]
    > If you select **Force**, the user account is moved, but associated user data such scheduled conferences and contacts is not moved. 
  
### To move users from one pool to another using Windows PowerShell cmdlets

1. Depending on how you run Windows PowerShell commands (that is, locally or remotely), you need to log on as a member of the correct Lync Server 2013 administrative roles as follows:
    
1. If you are running the commands on the local machine (for example, you log on directly to a Front End Server): Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. If you are running the commands remotely on another computer (for example, you log on to your computer and run the commands remotely on a Standard Edition Front End Server): From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. To move single users, use the Move-CsUser cmdlet as follows:
    
  ```
  Move-CsUser -Identity "Pilar Ackerman" -Target "pool01.contoso.net"
  ```

    Where the user to move is the user Pilar Ackerman, and the user will be moved from their currently assigned home pool to the pool pool01.contoso.net
    
4. To move a large number of users, use filters with the **Get-CsUser** cmdlet and pass the resulting set of users to **Move-CsUser**: 
    
  ```
  Get-CsUser -Filter {RegistrarPool -eq "CurrentPoolFqdn"} | Move-CsUser -Target "TargetPoolFQDN"
  ```

    The combined commands of the **Get-CsUser** and **Move-CsUser** might result in this: 
    
  ```
  Get-CsUser -Filter {RegistrarPool -eq "pool02.contoso.net"} | Move-CsUser -Target "pool01.contoso.net"
  ```

## See also

#### 

[Modifying user account properties in Lync Server 2013](modifying-user-account-properties.md)

