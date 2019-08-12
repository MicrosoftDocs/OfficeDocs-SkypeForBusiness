---
title: 'Lync Server 2013: Search for Lync Server users'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Search for Lync Server users
ms:assetid: 3b9f6f55-d7a9-46ae-8e10-f221ba0d3bb5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg429701(v=OCS.15)
ms:contentKeyID: 48183871
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Search for Lync Server users in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-14_

You can use the results of a search query to configure users for Lync Server 2013. You can search for users by display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI).

You can search for users by using the Lync Server Control Panel or the Active Directory Users and Computers snap-in. The following procedure describes how to use Lync Server Control Panel to search for users.

<div>


> [!NOTE]  
> In an environment with a central forest topology, search results might not be accurate when you search for a user by the user’s email address. Instead, you can search for users by specifying a SIP address prefix, for example, sip:name, add a search filter and select a SIP address that contains a partial email address, or use the <STRONG>Get-CSUser</STRONG> cmdlet.



</div>

<div>

## To search for one or more users

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Users**.

4.  In the **Search users** box, type all or the first portion of the display name, first name, last name, SAM account name, SIP address, or line URI of the user account that you want to search for, and then click **Find**.

5.  (Optional) Specify additional search criteria to narrow the results:
    
    1.  Click the expand arrow button in the upper-right corner of the screen above **Search results**, and then click **Add Filter**.
    
    2.  Enter the user property by typing it or clicking the arrow in the drop-down list to select a user property.
    
    3.  In the **Equal to** list, click **Equal to** or **Not equal to**.
    
    4.  In the text box, type the search criteria you want to use to filter search results, and then click **Find**.

6.  The search results appear under **Search Results**. You can select any or all of the users in the list and perform configuration tasks on the users you select.

</div>

<div>

## See Also


[Viewing information about user accounts enabled for Lync Server 2013](lync-server-2013-viewing-information-about-user-accounts-enabled-for-lync-server.md)  
[Enabling and disabling users for Lync Server 2013](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

