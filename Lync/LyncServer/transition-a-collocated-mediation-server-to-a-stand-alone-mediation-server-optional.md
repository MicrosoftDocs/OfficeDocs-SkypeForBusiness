---
title: Transition a collocated Mediation Server to a stand-alone Mediation Server (optional)
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Transition a collocated Mediation Server to a stand-alone Mediation Server (optional)
ms:assetid: 7c3c2fb4-4ff2-47b1-aab3-0aa91472eadb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205026(v=OCS.15)
ms:contentKeyID: 48184602
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Transition a collocated Mediation Server to a stand-alone Mediation Server (optional)

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

Use the procedure that follows to transition your Mediation Server, collocated on your Standard Edition server or Front End pool, to a stand-alone Mediation Server for a single-site deployment.

<div>

## To transition a collocated Mediation Server to a stand-alone Mediation Server

1.  Open an existing topology from Topology Builder.

2.  In the left pane, navigate to **Mediation pools**.

3.  Right-click **Mediation pools** and select **New Mediation Server**.

4.  On the **Define New Mediation Pool** page, provide the FQDN of the new Mediation Server pool. Also, select whether this pool will be a single-server or multiple-server pool, and then click **Next**.

5.  Select the next hop Front End server pool to which the new Mediation Server will route inbound calls, and then click **Next**.

6.  Select the Edge pool to be used by the Mediation Server and then click **Next**.

7.  On the **Specify PSTN gateways** page, associate the previous PSTN gateway with the Mediation Server. Select the gateway and then click **Add**.

8.  Click **Finish** to close the **Define New Mediation Pool** wizard.

9.  From **Topology Builder**, select the top node **Lync Server 2013**.

10. From the **Actions** pane, select **Publish Topology** and complete the wizard.

11. Follow the steps in [Install the files for Mediation Server in Lync Server 2013](lync-server-2013-install-the-files-for-mediation-server.md) in the Deployment documentation to install the files on the new Mediation Server.

12. After the files are installed on the Mediation Server, return to Topology Builder, and in the left pane navigate to the pool.

13. Right-click the pool and select **Edit Properties**.

14. Under **Mediation Server**, clear the check box **Collocated Mediation Server enabled** and then click **OK**.

15. From **Topology Builder**, select the top node **Lync Server 2013**.

16. From the **Action** menu, select **Publish Topology** and complete the wizard.

</div>

</div>

<span> </span>

</div>

</div>

</div>

