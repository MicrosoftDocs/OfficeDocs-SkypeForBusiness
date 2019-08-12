---
title: Deploy Lync Server 2013 clients
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deploy Lync Server 2013 clients
ms:assetid: 508e5dfa-588b-4289-81ce-2043c2d79e04
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204883(v=OCS.15)
ms:contentKeyID: 48184100
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploy Lync Server 2013 clients

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

After you migrate users to Lync Server 2013, do the following:

1.  Use the Client Version Filter on the new Lync Server 2013 server to only allow clients with the most current updates installed to sign in.

2.  If necessary, configure the Group Policy settings that are required for client bootstrapping. For details, see [Configuring client bootstrapping policies in Lync Server 2013](lync-server-2013-configuring-client-bootstrapping-policies.md) in the Deployment documentation. Configuration of these settings is only necessary if you want to change existing client bootstrapping policies or if you want to set new client bootstrapping policies. If you do not plan to configure client bootstrapping policies, or you want legacy client bootstrapping policies to remain in effect, no action is necessary.

3.  Configure other user and client policies for specific users or groups of users by using Lync Server 2013 Control Panel, Lync Server 2013 Management Shell, or both. For details, see [New and changed settings for Lync 2013](lync-server-2013-new-and-changed-settings-for-lync-2013.md) in the Planning documentation.

4.  Deploy the latest version of Lync Server 2013 clients along with the latest cumulative updates. For details, see [Deploying clients and devices in Lync Server 2013](lync-server-2013-deploying-clients-and-devices.md) in the Deployment documentation.

5.  (Optional) If your organization requires Lync Server 2013 enhanced presence privacy mode, after migration is complete, define a Client Version Policy Rule to prevent earlier client versions from signing in. Then, enable enhanced presence privacy mode.
    
    <div>
    

    > [!IMPORTANT]  
    > Do not enable Lync 2013 enhanced presence privacy mode until every user on a given server pool has the most current client versions installed.

    
    </div>

</div>

<span> </span>

</div>

</div>

</div>

