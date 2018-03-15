---
title: "User Search"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.UserMain
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 50feb75f-92a1-4916-b92e-c039e1290c52
description: "You can use the results of a search query to configure users for Microsoft Lync Server 2010. You can search for users by display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI). You can search for users by using the Lync Server Control Panel or the Active Directory Users and Computers snap-in."
---

# User Search
[]
You can use the results of a search query to configure users for Microsoft Lync Server 2010. You can search for users by display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI). You can search for users by using the Lync Server Control Panel or the Active Directory Users and Computers snap-in.
  
## Tasks you can perform

You can perform the following tasks on the **User Search** page: 
  
- [Search for Lync Server users in Lync Server 2013](search-for-lync-server-users.md)
    
- [Disable or re-enable user account for Lync Server 2013](disable-or-re-enable-user-account-for-lync-server.md)
    
- [Move User](move-user.md)
    
- [Move All Users](move-all-users.md)
    
- [Assigning per-user policies in Lync Server 2013](assigning-per-user-policies.md)
    
- [Enable users for Enterprise Voice in Lync Server 2013](enable-users-for-enterprise-voice.md)
    
- [Assign an external user access policy to a Lync enabled user in Lync Server 2013](assign-an-external-user-access-policy-to-a-lync-enabled-user.md)
    
- [Configure telephony for a user in Lync Server 2013](configure-telephony-for-a-user.md)
    
For details about the different procedures that you can perform by using the Lync Server 2013 Control Panel, see [Operations in Lync Server 2013](operations.md).
  
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

- **Enable users** Click to open the [Users: New Lync Server User](users-new-lync-server-user.md) dialog, where you can add a new user to Lync Server. 
    
    To add a new contact, click the down arrow and then select **Enable contacts** to open the [Users: New Contact Objects](users-new-contact-objects.md) dialog. 
    
- **Edit** Click **Edit** and then click **Show details** to display the details of the selected user, or click **Select all search results** to select all users displayed in the results table. 
    
- **Action** Click **Action**, and then select the action you want to perform for the selected users in the search results. The following actions are available:
    
  - **Re-enable for Lync Server** Enables the selected user account after it has been temporarily disabled. 
    
  - **Temporarily disable for Lync Server** Disables the user on Lync Server until you re-enable it, without removing the user from Lync Server. 
    
  - **Assign Policies** Opens the [Users: Assign Policies](users-assign-policies.md) dialog, where you can configure the policies assigned to the user. 
    
  - **View PIN status** Opens the [Users: View PIN Status](users-view-pin-status.md) dialog, which displays the PIN data for the selected user. 
    
  - **Set PIN** Opens the [Set PIN](set-pin.md) dialog, where you can set the PIN for the selected user. 
    
  - **Lock PIN** Locks the PIN for the user. 
    
  - **Unlock PIN** Removes the lock on the user's PIN. 
    
  - **Remove from Lync Server** Removes the user account from Lync Server. The user is not removed from Active Directory. 
    
  - **Remove user certificate** Removes all certificates granted to the user. 
    
  - **Move selected users to pool** Opens the [Move User](move-user.md) dialog, where you can select a pool to move the selected user to. 
    
  - **Move all users to pool** Opens the [Move User](move-user.md) dialog, where you can select a pool to move all selected users to. 
    

