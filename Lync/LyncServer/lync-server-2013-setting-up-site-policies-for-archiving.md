---
title: 'Lync Server 2013: Setting up site policies for Archiving'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Setting up site policies for Archiving
ms:assetid: dc2ea206-8b9c-44dd-a479-efb217593c89
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205325(v=OCS.15)
ms:contentKeyID: 48185613
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Setting up site policies for Archiving in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-09_

You can enable or disable Archiving for specific sites by creating and configuring an Archiving policy for each of those sites. A site policy overrides the global policy, but user policies override site policies. Archiving policies only apply if you do not use Microsoft Exchange integration or, if you do use Microsoft Exchange integration, but have some users who are not homed on Exchange 2013 and have their mailboxes put on In-Place Hold.

For details about how Archiving policies work, including the hierarchy for global, site, and user policies, see [How Archiving works in Lync Server 2013](lync-server-2013-how-archiving-works.md) Planning documentation, Deployment documentation, or Operations documentation.

<div>


> [!NOTE]  
> If you enable Microsoft Exchange integration for your deployment, Exchange In-Place Hold policies control whether archiving is enabled for the users who are homed on Exchange 2013 and have their mailboxes put on In-Place Hold. For details, see <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Setting up policies for Archiving in Lync Server 2013 when using Exchange Server integration</A> in the Deployment documentation.<BR>You should specify all appropriate options in the Archiving configurations before enabling Archiving of internal or external communications in the Archiving policies. For details, see <A href="lync-server-2013-configuring-archiving-options.md">Configuring Archiving options in Lync Server 2013</A> in the Deployment documentation.



</div>

<div>

## To create an archiving policy for a site

1.  From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server 2013 Control Panel.

3.  In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.
    
    For details about how Archiving policies work, including the hierarchy for global, site, and user policies, see [How Archiving works in Lync Server 2013](lync-server-2013-how-archiving-works.md) Planning documentation, Deployment documentation, or Operations documentation.

4.  Click **New**, and then click **Site policy**.

5.  In **Select a site**, click the site to which the policy is to be applied.

6.  In **New Archiving Policy**, do the following:
    
      - In **Name**, specify the name for the site policy.
    
      - In **Description**, provide information about what the site policy is (for example, site policy for Redmond).
    
      - To control archiving of internal communications for the specified site, select or clear the **Archive internal communications** check box.
    
      - To control archiving of external communications for the specified site, select or clear the **Archive external communications** check box.

7.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

