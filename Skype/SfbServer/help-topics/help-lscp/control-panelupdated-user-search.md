---
title: "Control Panel - updated User Search"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 5/21/2015
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.UserMain
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 50feb75f-92a1-4916-b92e-c039e1290c52
description: "You can use the results of a search query to configure users for Skype for Business Server. You can search for users by display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI). You can also search for users by using the Lync Server Control Panel or the Active Directory Users and Computers snap-in."
---

# Control Panel - updated: User Search

You can use the results of a search query to configure users for Skype for Business Server. You can search for users by display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI). You can also search for users by using the Lync Server Control Panel or the Active Directory Users and Computers snap-in.

## Tasks you can perform

You can perform the following tasks on the **User Search** Control Panel page:

- [Search for Lync Server 2010 Users](https://technet.microsoft.com/library/3b9f6f55-d7a9-46ae-8e10-f221ba0d3bb5.aspx)

- [Enable or Disable Users for Lync Server 2010](https://technet.microsoft.com/library/12497d00-f665-4a97-be68-854c5a8be4fc.aspx)

- [Move User](move-user.md)

- [Move All Users](move-all-users.md)

- [Assign Policies to Users](https://technet.microsoft.com/library/a4ed0120-d9e5-4eb2-acfd-8de2cb503652.aspx)

- [Enable users for Enterprise Voice in Skype for Business Server 2015](../../deploy/deploy-enterprise-voice/enable-users-for-enterprise-voice.md)

- [Configure Federation, Remote User Access, and Public IM Connectivity for Users](https://technet.microsoft.com/library/736fcaad-9f95-4896-b767-e199d86a00a4.aspx)

- [Configure Telephony for Users](https://technet.microsoft.com/library/4546432e-c839-4517-a2c5-bc0d4d8c6a03.aspx)

For details about the different procedures that you can perform by using the Skype for Business Server Control Panel, see [Manage Skype for Business Server 2015](../../manage/manage.md).

## UI Reference

The following lists describe the menus, command, fields, and properties on the **User Search** page.

### User Search

- **Search** Search for users by the first portion of the display name, first name, last name, SAM account name, SIP address, or line URI of the user account.

- **LDAP Search** Search for users by typing an LDAP expression.

- **Search users box** Type the user data or LDAP expression you want to seach for.

- **Find** Click to display the users that match the search values you entered in the **Search users** and box.

- **Open query** Click to open a saved search query.

- **Save query** Click to save a search query.

- **+ Add filter** Click to add additional search criteria.

- **Search filter fields** Select the field on which you want to filter search results, select an operator for the query, and then type the string you want to search on.

- **Maximum users to display** Type the number of search results you want to display, or use the up and down arrows to specify the number.

Add additional descriptive text, as appropriate.

### Search Results Menus

- **Enable users** Click to open the [Users: New Lync Server User](users-new-lync-server-user.md) dialog, where you can add a new user to Skype for Business Server.

    To add a new contact, click the down arrow and then select **Enable contacts** to open the [Users: New Contact Objects](users-new-contact-objects.md) dialog.

- **Edit** Click **Edit** and then click **Show details** to display the details of the selected user, or click **Select all search results** to select all users displayed in the results table.

- **Action** Click **Action**, and then select the action you want to perform for the selected users in the search results. The following actions are available:

  - **Re-enable for Lync Server** Enables the selected user account after it has been temporarily disabled.

  - **Temporarily disable for Lync Server** Disables the user account in Skype for Business Server until you re-enable it, without removing the user account.

  - **Assign Policies** Opens the [Users: Assign Policies](users-assign-policies.md) dialog, where you can configure the policies assigned to the user.

  - **View PIN status** Opens the [Users: View PIN Status](users-view-pin-status.md) dialog, which displays the PIN data for the selected user.

  - **Set PIN** Opens the [Set PIN](set-pin.md) dialog, where you can set the PIN for the selected user.

  - **Lock PIN** Locks the PIN for the user.

  - **Unlock PIN** Removes the lock on the user's PIN.

  - **Remove from Lync Server** Removes the user account from Skype for Business Server. The user is not removed from Active Directory.

  - **Remove user certificate** Removes all certificates granted to the user.

  - **Move selected users to pool** Opens the [Move User](move-user.md) dialog, where you can select a pool to move the selected user to.

  - **Move all users to pool** Opens the [Move User](move-user.md) dialog, where you can select a pool to move all selected users to.


