---
title: "Search for Lync Server users in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3b9f6f55-d7a9-46ae-8e10-f221ba0d3bb5
description: "You can use the results of a search query to configure users for Lync Server 2013. You can search for users by display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI)."
---

# Search for Lync Server users in Lync Server 2013
[]
You can use the results of a search query to configure users for Lync Server 2013. You can search for users by display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI).
  
You can search for users by using the Lync Server Control Panel or the Active Directory Users and Computers snap-in. The following procedure describes how to use Lync Server Control Panel to search for users.
  
> [!NOTE]
> In an environment with a central forest topology, search results might not be accurate when you search for a user by the user's email address. Instead, you can search for users by specifying a SIP address prefix, for example, sip:name, add a search filter and select a SIP address that contains a partial email address, or use the **Get-CSUser** cmdlet. 
  
### To search for one or more users

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Users**.
    
4. In the **Search users** box, type all or the first portion of the display name, first name, last name, SAM account name, SIP address, or line URI of the user account that you want to search for, and then click **Find**.
    
5. (Optional) Specify additional search criteria to narrow the results:
    
1. Click the expand arrow button in the upper-right corner of the screen above **Search results**, and then click **Add Filter**.
    
2. Enter the user property by typing it or clicking the arrow in the drop-down list to select a user property.
    
3. In the **Equal to** list, click **Equal to** or **Not equal to**.
    
4. In the text box, type the search criteria you want to use to filter search results, and then click **Find**.
    
6. The search results appear under **Search Results**. You can select any or all of the users in the list and perform configuration tasks on the users you select.
    
## See also

#### 

[Viewing information about user accounts enabled for Lync Server 2013](viewing-information-about-user-accounts-enabled-for-lync-server-2013.md)
  
[Enabling and disabling users for Lync Server 2013](enabling-and-disabling-users-for-lync-server-2013.md)

