---
title: Download topology from existing deployment
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Download topology from existing deployment
ms:assetid: e39065a2-d4b0-4f27-8c49-f56be78fa55b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721913(v=OCS.15)
ms:contentKeyID: 49733847
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Download topology from existing deployment

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-29_

When creating a Lync Server 2013 pool, you will use the Central Management Store that is associated with Lync Server 2010. When you start Topology Builder on first use and subsequent edit sessions, you are prompted for the location where you want Topology Builder to load the current configuration document. Because you already have a Lync Server 2010 topology defined and have established the Central Management store, you should choose to download a topology from an existing deployment. Topology Builder will read the database and retrieve the current definition.

**To download a topology from an existing deployment**

1.  Open the **Lync Server Deployment Wizard**.

2.  From the **Lync Server 2013 – Deployment Wizard** page, click **Install Administrative Tools**.

3.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013** , and then click **Lync Server Topology Builder**.

4.  Select **Download Topology from existing deployment**.
    
    ![Deployment Wizard Topology Builder settings](images/JJ721913.d5b39fd9-3c13-422e-a06c-25d2568fe781(OCS.15).jpg "Deployment Wizard Topology Builder settings")

5.  Choose a file name and save the topology with the default .tbxml file type.

6.  Expand the Lync Server node, as shown, to reveal the various server roles in the deployment.
    
    ![Topology Builder server role general properties](images/JJ721913.af99ead3-676b-47fd-8369-5a5f9717383f(OCS.15).jpg "Topology Builder server role general properties")

</div>

<span> </span>

</div>

</div>

</div>

