---
title: "Manage user accounts for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 2fe7e3a7-bc75-4d4b-94af-a8818722b0d3
description: "The sections in this article describe how to enable, temporarily disable, or remove Active Directory users from Skype for Business Server."
---

# Manage user accounts for Skype for Business Server

The sections in this article describe how to enable, temporarily disable, or remove Active Directory users from Skype for Business Server.

For information on how to enable an Active Directory user, see [Create a New User Account](https://technet.microsoft.com/en-us/library/cc732336%28v=ws.11%29.aspx). For information on how to delete an Active Directory user, see [Delete a User Account](https://technet.microsoft.com/en-us/library/cc753730%28v=ws.11%29.aspx).

These procedures should be performed during a maintenance window, when Skype for Business usage is lowest. Whether this is done on a daily or weekly schedule will be determined by the needs of your organization.

This article contains the following procedures:

- [To search for one or more users](user-accounts.md#Search)

- [Add and enable a new Skype for Business Server user](user-accounts.md#Add)

- [Disable or re-enable a user account previously enabled for Skype for Business Server](user-accounts.md#Disable)

- [Disable a user for Enterprise Voice](user-accounts.md#Disable_EV)

- [Remove a user account with the Skype for Business Server Management Shell](user-accounts.md#Remove)

## To search for one or more users
<a name="Search"> </a>

You can use the results of a search query to configure Active Directory users for Skype for Business Server. You can search for users by display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI).

You can search for users by using the Skype for Business Server Control Panel or the Active Directory Users and Computers snap-in. The following procedure describes how to use Skype for Business Server Control Panel to search for users.

> [!NOTE]
> In an environment with a central forest topology, search results might not be accurate when you search for a user by the user's email address. Instead, you can search for users by specifying a SIP address prefix, for example, sip:name, add a search filter and select a SIP address that contains a partial email address, or use the **Get-CSUser** cmdlet.

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left navigation bar, click **Users**.

4. In the **Search users** box, type all or the first portion of the display name, first name, last name, SAM account name, SIP address, or line URI of the user account that you want to search for, and then click **Find**.

5. (Optional) Specify additional search criteria to narrow the results:

   a. Click the expand arrow button in the upper-right corner of the screen above **Search results**, and then click **Add Filter**.

   b. Enter the user property by typing it or clicking the arrow in the drop-down list to select a user property.

   c. In the **Equal to** list, click **Equal to** or **Not equal to**.

   d. In the text box, type the search criteria you want to use to filter search results, and then click **Find**.

6. The search results appear under **Search Results**. You can select any or all of the users in the list and perform configuration tasks on the users you select.

## Add and enable a new Skype for Business Server user
<a name="Add"> </a>

After enabling a user account in Active Directory Users and Computers, you can use Skype for Business Server Control Panel to create and enable new Skype for Business Server user accounts by adding an Active Directory user to Skype for Business Server.

You can also use a cmdlet, specifically [Enable-CsUser](https://docs.microsoft.com/powershell/module/skype/enable-csuser?view=skype-ps).

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left navigation bar, click **Users**.

4. Click **Enable users**.

5. On the **New Lync Server User** dialog, click **Add**.

6. In the **Search users** box, type all or the first portion of the name, display name, first name, last name, Security Accounts Manager (SAM) account name, email address, User Principal Name (UPN), or phone number of the Active Directory user account that you want, and then click **Find**.

7. In the table, select the account you want to add to Skype for Business Server, and then click **OK**.

8. Assign the user to a pool, specify any additional details, and assign the policies to the user you want, and then click **Enable**.

## Disable or re-enable a user account previously enabled for Skype for Business Server
<a name="Disable"> </a>

You can use the following procedure to disable a previously enabled user account in Skype for Business Server without losing the Skype for Business Server settings that you configured for the user account. Because you do not lose the Skype for Business Server user account settings, you can re-enable a previously enabled user account again without having to reconfigure the user account.

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left navigation bar, click **Users**.

4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to disable or re-enable, and then click **Find**.

5. In the table, click the user account that you want to disable or re-enable.

6. On the **Action** menu, do one of the following:

   - To temporarily disable the user account for Skype for Business Server, click **Temporarily disable for Lync Server**.

   - To enable the user account for Skype for Business Server, click **Re-enable for Lync Server**.

### Use Windows Powershell to Disable or Re-enable User Accounts

User accounts can be temporarily disabled, and then later re-enabled, by using the **Set-CsUser** cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.

### To disable a user account

- To temporarily disable a user account, set the value of the Enabled property to False ($False). For example:

  ```
  Set-CsUser -Identity "Ken Myer" -Enabled $False
  ```

### To re-enable a user account

- To re-enable a disabled user account, set the value of the Enabled property to True ($True). For example:

  ```
  Set-CsUser -Identity "Ken Myer" -Enabled $True
  ```

For more information, see the help topic for the [Set-CsUser](https://docs.microsoft.com/powershell/module/skype/set-csuser?view=skype-ps) cmdlet.

## Disable a user for Enterprise Voice
<a name="Disable_EV"> </a>

Use the following procedure to disable Enterprise Voice for a user account that is enabled for Skype for Business Server.

### To disable a user account for Enterprise Voice

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left navigation bar, click **Users**.

4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to enable, and then click **Find**.

5. In the table, click the user account that you want to enable for Enterprise Voice.

6. On the **Edit** menu, click **Show details**.

7. On the **Edit Lync Server User** page, under **Telephony**, click any option except **Enterprise Voice**.

    > [!NOTE]
    > To restrict a user from making audio or video calls by using Lync, under **Telephony**, click **Audio/video disabled**.

8. Click **Commit**.

The user is now unable to use the Enterprise Voice feature. Related information: <br/>[Enterprise Voice and mobility](https://technet.microsoft.com/library/72cbe2f5-1a01-4a6f-84a5-01f3212a8992.aspx)<br/> [Enable users for Enterprise Voice in Skype for Business Server](../../deploy/deploy-enterprise-voice/enable-users-for-enterprise-voice.md)<br/> [Skype for Business Server Management Shell](../management-shell.md)
## Remove a user account with the Skype for Business Server Management Shell
<a name="Remove"> </a>

You can use the following procedure to remove a previously added user account in Skype for Business Server.

> [!NOTE]
> Removing a user will cause you to lose any settings you configured for the user account. If you would like to temporarily disable a user account instead, see [Disable or re-enable a user account previously enabled for Skype for Business Server](user-accounts.md#Disable).

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3. In the left navigation bar, click **Users**.

4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to disable or re-enable, and then click **Find**.

5. In the table, click the user account that you want to remove.

6. On the **Action** menu, select **Remove from Lync Server**, and a dialog box appears.

7. From the dialog box, select **OK** to remove the user.

### Remove user accounts with Windows Powershell cmdlets

You can remove user accounts by using the Disable-CsUser cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.

### To remove a user account
To remove a user account, use the Disable-CsUser cmdlet. For example:

  ```
  Disable-CsUser -Identity "Ken Myer"
  ```

    After this command has run there is no way to re-enable the account and its previous settings. Instead, you will need to use the Enable-CsUser cmdlet to create a brand-new account for Ken Myer.

For more information, see the help topic for the [Disable-CsUser](https://docs.microsoft.com/powershell/module/skype/disable-csuser?view=skype-ps) cmdlet.

## See also
<a name="Remove"> </a>

[Enable-CsUser](https://docs.microsoft.com/powershell/module/skype/enable-csuser?view=skype-ps)

[Disable-CsUser](https://docs.microsoft.com/powershell/module/skype/disable-csuser?view=skype-ps)
