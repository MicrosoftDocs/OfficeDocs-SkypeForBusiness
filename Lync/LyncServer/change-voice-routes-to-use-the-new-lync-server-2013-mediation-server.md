---
title: Change voice routes to use the new Lync Server 2013 Mediation Server
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Change voice routes to use the new Lync Server 2013 Mediation Server
ms:assetid: acd487b3-377c-46bf-9f71-fe6152002664
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205162(v=OCS.15)
ms:contentKeyID: 48185069
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Change voice routes to use the new Lync Server 2013 Mediation Server

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-28_

This procedure changes the voice routes to use the Lync Server 2013 Mediation Server, instead of the legacy Office Communications Server 2007 R2 Mediation Server.

<div>

## To change the voice routes to use the new Mediation Server

1.  Lync Server 2013 Control Panel

2.  In the left pane, select **Voice Routing** and then **Route**.

3.  Click **New** to create a New Voice Route.

4.  Fill in the following fields:
    
      - **Name**: Type a descriptive name of the voice route. For this document we will use **W15PSTNRoute**.
    
      - **Description**: Type a short description of the voice route.

5.  Skip all remaining sections until you reach **Associated gateways**. Click **Add**. Select the new default gateway and click **OK**.

6.  Under **Associated PSTN Usages**, click **Select**.

7.  From the **Select PSTN Usage Record** page, select a record name and then click **OK**.

8.  From the **New Voice Route** page, click **OK** to create the **Voice Route**.

9.  From the **Voice Routing** page, select **Route**.

10. Move the newly created route to the top of the list and then select **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

