---
title: Enable remote call control
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Enable remote call control
ms:assetid: 0b91d418-e6ed-4556-97af-e8523e01f249
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204664(v=OCS.15)
ms:contentKeyID: 48183380
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable remote call control

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-02_

Remote call control enables users to control their desktop private branch exchange (PBX) phones by using Lync Server 2013. If you deployed remote call control in your legacy environment and want to migrate it Lync Server 2013, you need to perform the following tasks:

1.  Install a SIP/CSTA gateway and configure it to communicate with your PBX. You need to do this step when you deploy your Lync Server 2013 pilot pool.

2.  After you merge your topology and migrate your policies and settings, configure Lync Server 2013 to route CSTA requests to the SIP/CSTA gateway. This step is a manual step that follows the automated migration. To configure routing for CSTA requests, do the following:
    
      - Remove legacy authorized host entries (known as *trusted server entries* in Lync Server 2013). If you are migrating users from your legacy deployment, ensure that you remove all existing authorized host entries that you created for the SIP/CSTA gateway before you configure new trusted application entries on the Lync Server 2013 pilot pool. For details about how to remove legacy authorized host entries, see [Remove an authorized host entry](remove-an-authorized-host-entry.md).
    
      - Configure a static route for remote call control. You can configure a static route for individual pools that you want to support remote call control, or you can configure a global static route so that each pool that is not configured with a pool-level static route uses the global static route. For details about how to configure the static route, see [Configure a static route for remote call control in Lync Server 2013](lync-server-2013-configure-a-static-route-for-remote-call-control.md) in the Deployment documentation.
    
      - Configure a trusted application entry for remote call control on each pool for which you want to support remote call control. For details about how to configure a trusted application entry, see [Configure a trusted application entry for remote call control in Lync Server 2013](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md) in the Deployment documentation.

3.  If you deployed a SIP/CSTA gateway that uses Transmission Control Protocol (TCP) to connect to Lync Server 2013, define the IP address of the gateway in Topology Builder. For details about defining the IP address, see [Define a SIP/CSTA gateway IP address in Lync Server 2013](lync-server-2013-define-a-sip-csta-gateway-ip-address.md) in the Deployment documentation.

4.  Configure Lync 2013 users for remote call control by enabling remote call control and assigning a line server Uniform Resource Identifier (URI) and a line URI. When you migrate users from your legacy deployment to Lync Server 2013, the remote call control settings are migrated along with the other user settings.

5.  If you customized Address Book phone number normalization rules in your legacy deployment, you need to perform some manual tasks after the automated migration of policies and settings is complete to migrate the customized normalization rules. If you did not customize normalization rules, Address Book is migrated along with the rest of your topology. For details about manually migrating customized normalization rules, see [Migrate Address Book](migrate-address-book_1.md).

</div>

<span> </span>

</div>

</div>

</div>

