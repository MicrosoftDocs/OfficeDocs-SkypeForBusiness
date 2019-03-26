---
title: Remove an authorized host entry
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Remove an authorized host entry
ms:assetid: 56a04140-347e-4eef-bede-0e858534f71e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204902(v=OCS.15)
ms:contentKeyID: 48184177
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove an authorized host entry

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-26_

This topic describes how to remove a legacy authorized host entry (known as a *trusted application entry* in Lync Server 2013). You must remove existing authorized host entries for any SIP/CSTA gateways in your Office Communications Server 2007 R2 deployment when you migrate remote call control to a Lync Server 2013 deployment. You must use the administrative tools included with Office Communications Server 2007 R2 to remove the existing authorized host entries.

<div>

## To remove an authorized host entry in an Office Communications Server 2007 R2 deployment

1.  Open the Office Communications Server 2007 R2 administrative console.

2.  Expand the tree and right-click the pool where the authorized host was created.

3.  Click **Properties**, and then click **Front End Properties**.

4.  Click the **Host Authorization** tab.

5.  Select a server, and then click **Remove**.

6.  In **Properties**, click **OK**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

