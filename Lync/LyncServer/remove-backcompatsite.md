---
title: Remove BackCompatSite
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Remove BackCompatSite
ms:assetid: 039650e3-541b-45c2-a682-c4fa08423118
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204637(v=OCS.15)
ms:contentKeyID: 48183265
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove BackCompatSite

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-28_

After all pools are deactivated and all Edge Servers have been uninstalled, run the Topology Builder Merge wizard to remove the **BackCompatSite**.

<div>

## To remove BackCompat site from Topology Builder

1.  Open an existing deployment from Topology Builder.

2.  In the **Action** menu, click **Merge 2007 R2 Topology**.

3.  Click **Next** to continue.

4.  On the **Specify Legacy Edge** page, ensure that list of Edge Servers is empty. If the list is not empty, use the **Remove** button to remove all the legacy Edge Servers, and then click **Next**.
    
    ![Merge Topology Wizard, Specify Edge Setup page](images/JJ204637.fb35a59a-711e-4259-b177-7311df1fed3c(OCS.15).jpg "Merge Topology Wizard, Specify Edge Setup page")  

5.  On the **Specify Internal SIP port setting** page, click **Next**.

6.  On the **Summary** page, click **Next** to begin merging the topologies to remove the legacy site.

7.  In the **Status** column, verify that the value is **Success** and then click **Finish** to close the wizard.

8.  In the left pane of Topology Builder, expand the BackCompatSite and ensure no servers are listed.

9.  Right-click the **BackCompatSite**, and then click **Delete**.

10. In **Topology Builder**, select the top-most node **Lync Server**.

11. From the **Action** menu, select **Publish Topology** and then click **Next**.

12. When the **Publishing wizard** completes, click **Finish** to close the wizard.

</div>

</div>

<span> </span>

</div>

</div>

</div>

