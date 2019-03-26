---
title: 'Lync Server 2013: Authenticated user permissions are removed'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Authenticated user permissions are removed
ms:assetid: 5fcd70a5-813a-4076-9bb6-5b0d47505038
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398425(v=OCS.15)
ms:contentKeyID: 48184304
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Authenticated user permissions are removed in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

In a locked-down Active Directory environment, authenticated user access control entries (ACEs) are removed from the default Active Directory containers, including the Users, Configuration or System, and organizational units (OUs) where User and Computer objects are stored. Removing authenticated user ACEs prevents read access to Active Directory information. However, removing the ACEs creates issues for Lync Server 2013 because it depends on read permissions to these containers to allow users to run domain preparation.

In this situation, membership in the Domain Admins group, which is required to run domain preparation, server activation, and pool creation, no longer grants read access to Active Directory information stored in the default containers. You must manually grant read-access permissions on various containers in the forest root domain to check that the prerequisite forest preparation procedure is complete.

To enable a user to run domain preparation, server activation, or pool creation on any non-forest root domain, you have the following options:

  - Use an account that is a member of the Enterprise Admins group to run domain preparation.

  - Use an account that is a member of the Domain Admins group and grant this account read-access permissions on each of the following containers in the forest root domain:
    
      - Domain
    
      - Configuration or System

If you do not want to use an account that is a member of the Enterprise Admins group to run domain preparation or other Setup tasks, explicitly grant the account you want to use read access on the relevant containers in the forest root.

<div>

## To give users read-access permissions on containers in the forest root domain

1.  Log on to the computer joined to the forest root domain with an account that is a member of the Domain Admins group for the forest root domain.

2.  Run adsiedit.msc for the forest root domain.
    
    If authenticated user ACEs were removed from the Domain, Configuration, or System container, you must grant read-only permissions to the container, as described in the following steps.

3.  Right-click the container, and then click **Properties**.

4.  Click the **Security** tab.

5.  Click **Advanced**.

6.  On the **Permissions** tab, click **Add**.

7.  Type the name of the user or group receiving permissions by using the following format: `domain\account name`, and then click **OK**.

8.  On the **Objects** tab, in **Applies To**, click **This Object Only**.

9.  In **Permissions**, select the following Allow ACEs by clicking the **Allow** column: **List Content**, **Read All Properties**, and **Read Permissions**.

10. Click **OK** twice.

11. Repeat these steps for any of the relevant containers listed in Step 2.

</div>

</div>

<span> </span>

</div>

</div>

</div>

