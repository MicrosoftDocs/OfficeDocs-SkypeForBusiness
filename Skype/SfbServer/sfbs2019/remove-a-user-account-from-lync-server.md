---
title: "Remove a user account from Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2f512aba-e358-45ae-af58-74312ee9c514
description: "You can use the following procedure to remove a previously added user account in Lync Server 2013."
---

# Remove a user account from Lync Server 2013
[]
You can use the following procedure to remove a previously added user account in Lync Server 2013. 
  
> [!NOTE]
> Removing a user will cause you to lose any settings you configured for the user account. If you would like to temporarily disable a user account instead, see the topic [Disable or re-enable user account for Lync Server 2013](disable-or-re-enable-user-account-for-lync-server.md). 
  
### To remove a user account by using Lync Server Management Shell

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Users**.
    
4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to disable or re-enable, and then click **Find**.
    
5. In the table, click the user account that you want to remove.
    
6. On the **Action** menu, select **Remove from Lync Server**, and a dialog box appears.
    
7. From the dialog box, select **OK** to remove the user. 
    
## Removing User Accounts by Using Windows PowerShell Cmdlets

You can remove user accounts by using the Disable-CsUser cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To remove a user account

- To remove a user account, use the Disable-CsUser cmdlet. For example:
    
  ```
  Disable-CsUser -Identity "Ken Myer"
  ```

    After this command has run there is no way to re-enable the account and its previous settings. Instead, you will need to use the Enable-CsUser cmdlet to create a brand-new account for Ken Myer.
    
For more information, see the help topic for the [Disable-CsUser](disable-csuser.md) cmdlet. 
  
## See also

#### 

[Disable or re-enable user account for Lync Server 2013](disable-or-re-enable-user-account-for-lync-server.md)
#### 

[Enabling and disabling users for Lync Server 2013](enabling-and-disabling-users-for-lync-server-2013.md)

