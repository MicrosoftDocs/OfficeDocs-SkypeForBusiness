---
title: "Manage user accounts for Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 2fe7e3a7-bc75-4d4b-94af-a8818722b0d3
description: "The sections in this article describe how to enable, temporarily disable, or remove Active Directory users from Skype for Business Server."
---

# Manage user accounts for Skype for Business Server

The sections in this article describe how to enable, temporarily disable, or remove Active Directory users from Skype for Business Server.

For information on how to enable an Active Directory user, see [Create a New User Account](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732336(v=ws.11)). For information on how to delete an Active Directory user, see [Delete a User Account](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).

These procedures should be performed during a maintenance window, when Skype for Business usage is lowest. Whether this is done on a daily or weekly schedule will be determined by the needs of your organization.

This article contains the following procedures:

- [Search for one or more users](#search-for-one-or-more-users)

- [Add and enable a new Skype for Business Server user](#add-and-enable-a-new-skype-for-business-server-user)

- [Disable or re-enable a user account for Skype for Business Server](#disable-or-re-enable-a-user-account-for-skype-for-business-server)

- [Disable a user for Enterprise Voice](#disable-a-user-for-enterprise-voice)

- [Remove a user account with the Skype for Business Server Management Shell](#remove-a-user-account-with-the-skype-for-business-server-management-shell)

## Search for one or more users

You can use the results of a search query to configure Active Directory users for Skype for Business Server. You can search for users by display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI).

You can search for users by using the Skype for Business Server Control Panel or the Active Directory Users and Computers snap-in. The following procedure describes how to use Skype for Business Server Control Panel to search for users.

> [!NOTE]
> In an environment with a central forest topology, search results might not be accurate when you search for a user by the user's email address. Instead, you can search for users by specifying a SIP address prefix, for example, sip:name, add a search filter and select a SIP address that contains a partial email address, or use the **Get-CSUser** cmdlet.

### Search for users using the new Control Panel 

1. Open a browser window and enter the Admin URL to open the Skype for Business Server Control Panel.
 
2. Log in using a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role.

3. In the left pane, select **Users**.

4. On the **Users** page, in the **Search** box, type all or the first portion of the display name that you want to search for and press **Enter**.

5. (Optional) Specify additional search criteria to narrow the results:

    1. Click the filter button next to the **Search** box.

    2. In the **Filter** panel that appears, select the required user property by clicking the arrow in the dropdown list.

    3. Click the arrow in the dropdown operator list, to select the required operator.

    4. In the text box, type the search criteria you want to use to filter search results, and then click **OK**.

6. The search results appear on the **Users** page. You can select any or all of the users in the list and perform configuration tasks on the users you select.

> [!NOTE]
> The new Control Panel is not available for Skype for Business Server 2015.

### Search for users using the legacy Control Panel 

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left pane, select **Users**.

4. In the **Search users** box, type all or the first portion of the display name, first name, last name, SAM account name, SIP address, or line URI of the user account that you want to search for, and then click **Find**.

5. (Optional) Specify additional search criteria to narrow the results:

    1. Click the expand arrow button in the upper-right corner of the screen above **Search results**, and then click **Add Filter**.

    2. Enter the user property by typing it or clicking the arrow in the dropdown list to select a user property.

    3. In the **Equal to** list, select **Equal to** or **Not equal to**.

    4. In the text box, type the search criteria you want to use to filter search results, and then click **Find**.

6. The search results appear under **Search Results**. You can select any or all of the users in the list and perform configuration tasks on the users you select.

## Add and enable a new Skype for Business Server user

After enabling a user account in Active Directory Users and Computers, you can use Skype for Business Server Control Panel to create and enable new Skype for Business Server user accounts by adding an Active Directory user to Skype for Business Server.

You can also use a cmdlet, specifically [Enable-CsUser](/powershell/module/skype/enable-csuser).

### Add a user using the new Control Panel 

1. Open a browser window and enter the Admin URL to open the Skype for Business Server Control Panel.
 
2. Log in using a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role.

3. Navigate to **Users** > **Enable Users**, and click **Add**.

4. In the **Search** box, type all or the first portion of the display name and click **Find**.

5. (Optional) To specify additional user criteria, click **+ Add filter**, select the required user property, select the operator, and enter the value. Click **Find**.

6. In the table, select the account you want to add to Skype for Business Server, and then click **OK**.

7. Assign the user to a pool, specify any additional details, and assign the required policies to the user, and then click **Enable**.

> [!NOTE]
> The new Control Panel is not available for Skype for Business Server 2015.

### Add a user using the legacy Control Panel 

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. Navigate to **Users** > **Enable users** > **New Lync Server User**, and click **Add.**

6. In the **Search users** box, type all or the first portion of the name, display name, first name, last name, Security Accounts Manager (SAM) account name, email address, User Principal Name (UPN), or phone number of the Active Directory user account that you want, and then click **Find**.

7. In the table, select the account you want to add to Skype for Business Server, and then click **OK**.

8. Assign the user to a pool, specify any additional details, and assign the policies to the user you want, and then click **Enable**.

## Disable or re-enable a user account for Skype for Business Server

You can use the following procedure to disable a previously enabled user account in Skype for Business Server without losing the Skype for Business Server settings that you configured for the user account. Because you do not lose the Skype for Business Server user account settings, you can re-enable a previously enabled user account again without having to reconfigure the user account.

### Disable or re-enable a user account using the new Control Panel

1. Open a browser window and enter the Admin URL to open the Skype for Business Server Control Panel.
 
2. Log in using a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role.

3. In the left pane, select **Users**.

4. On the **Users** page, in the **Search** box, type all or the first portion of the display name and press **Enter**.

5. In the table, double-click the user account that you want to disable or re-enable.
    1. In the panel that appears, to temporarily disable the user account for Skype for Business Server, select **Disable User**. In the panel that appears, click **Save**.
    2. To re-enable the user account for Skype for Business Server, in the panel, select **Re-enable User**. In the next panel that appears, click **Save**.

> [!NOTE]
> The new Control Panel is not available for Skype for Business Server 2015.

### Disable or re-enable a user account using the legacy Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left pane, select **Users**.

4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to disable or re-enable, and then click **Find**.

5. In the table, click the user account that you want to disable or re-enable.

6. On the **Action** menu, do one of the following:
   1. To temporarily disable the user account for Skype for Business Server, select **Temporarily disable for Lync Server**.
   2. To enable the user account for Skype for Business Server, select **Re-enable for Lync Server**.
  
### Disable or re-enable user accounts using Windows PowerShell

User accounts can be temporarily disabled, and then later re-enabled, by using the **Set-CsUser** cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see [Microsoft Lync Remote PowerShell Administration](https://blog.insideo365.com/2011/08/remote-lync-powershell-administration/). The process is the same in Skype for Business Server.

### To disable a user account using Windows PowerShell

- To temporarily disable a user account, set the value of the enabled property to False ($False). For example:

  ```PowerShell
  Set-CsUser -Identity "Ken Myer" -Enabled $False
  ```

### To re-enable a user account using Windows PowerShell

- To re-enable a disabled user account, set the value of the enabled property to True ($True). For example:

  ```PowerShell
  Set-CsUser -Identity "Ken Myer" -Enabled $True
  ```

For more information, see the help topic for the [Set-CsUser](/powershell/module/skype/set-csuser) cmdlet.

## Disable a user for Enterprise Voice

Use the following procedure to disable Enterprise Voice for a user account that is enabled for Skype for Business Server.

### Disable a user for Enterprise Voice using new Control Panel

1. Open a browser window and enter the Admin URL to open the Skype for Business Server Control Panel.
 
2. Log in using a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role.

3. In the left pane, click **Users**.

4. In the **Search** box, type all or the first portion of the display name and click **Find**.

5. In the table, double-click the user account that you want to disable for Enterprise Voice.

6. In the panel that appears, click the pencil icon next to **Assigned Policies**.

7. In the **Assigned Policies** panel, under **Telephony**, click any option except **Enterprise Voice** in the dropdown list.

8. Click **Save**.

    > [!NOTE]
    > To restrict a user from making audio or video calls, under **Telephony**, click **Audio/Video disabled**.

The user is now unable to use the Enterprise Voice feature. 

> [!NOTE]
> The new Control Panel is not available for Skype for Business Server 2015.

### Disable a user account for Enterprise Voice using legacy Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left pane, click **Users**.

4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to enable, and then click **Find**.

5. In the table, click the user account that you want to enable for Enterprise Voice.

6. On the **Edit** menu, click **Show details**.

7. On the **Edit Lync Server User** page, under **Telephony**, click any option except **Enterprise Voice**.

    > [!NOTE]
    > To restrict a user from making audio or video calls by using Lync, under **Telephony**, click **Audio/video disabled**.

8. Click **Commit**.

The user is now unable to use the Enterprise Voice feature.

Related information: <br/>[Enterprise Voice and mobility](/previous-versions/office/lync-server-2013/lync-server-2013-managing-enterprise-voice-for-users)<br/> [Enable users for Enterprise Voice in Skype for Business Server](../../deploy/deploy-enterprise-voice/enable-users-for-enterprise-voice.md)<br/> [Skype for Business Server Management Shell](../management-shell.md)

## Remove a user account with the Skype for Business Server Management Shell

You can use the following procedure to remove a previously added user account in Skype for Business Server.

> [!NOTE]
> Removing a user will cause you to lose any settings you configured for the user account. If you would like to temporarily disable a user account instead, see [Disable or re-enable a user account previously enabled for Skype for Business Server](#disable-or-re-enable-a-user-account-for-skype-for-business-server).

### Remove a user using the new Control Panel

1. Open a browser window and enter the Admin URL to open the Skype for Business Server Control Panel.
 
2. Log in using a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role.

3. In the left pane, select **Users**.

4. In the **Search** box, type all or the first portion of the display name and click **Find**.

5. In the table, double-click the user account that you want to remove.

6. In the panel that appears, click **Remove User**. In the next panel that appears, click **OK**.

> [!NOTE]
> The new Control Panel is not available for Skype for Business Server 2015.

### Remove a user using the legacy Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left pane, select **Users**.

4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to remove, and then click **Find**.

5. In the table, click the user account that you want to remove.

6. On the **Action** menu, select **Remove from Lync Server**, and a dialog box appears.

7. From the dialog box, select **OK** to remove the user.

### Remove user accounts with Windows PowerShell cmdlets

You can remove user accounts by using the Disable-CsUser cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see [Microsoft Lync Remote PowerShell Administration](https://blog.insideo365.com/2011/08/remote-lync-powershell-administration/). The process is the same in Skype for Business Server.

To remove a user account, use the Disable-CsUser cmdlet. For example:

  ```PowerShell
  Disable-CsUser -Identity "Ken Myer"
  ```

After this command has run there is no way to re-enable the account and its previous settings. Instead, you will need to use the Enable-CsUser cmdlet to create a brand-new account for Ken Myer.

For more information, see the help topic for the [Disable-CsUser](/powershell/module/skype/disable-csuser) cmdlet.

## See also

[Enable-CsUser](/powershell/module/skype/enable-csuser)

[Disable-CsUser](/powershell/module/skype/disable-csuser)
