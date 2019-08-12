---
title: 'Lync Server 2013: Edit or configure simple URLs'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Edit or configure simple URLs
ms:assetid: 0008aeea-4ae9-4e36-83cd-ef7ff7b6e128
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398063(v=OCS.15)
ms:contentKeyID: 48183216
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Edit or configure simple URLs in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-04_

This procedure does not require membership in a local administrator or privileged domain group. You should log on to a computer as a standard user.

Lync Server 2013 uses simple URLs to direct internal and external calls to services on the Front End Server or on the Director, if one has been deployed. For more information about simple URLs, see [Planning for simple URLs in Lync Server 2013](lync-server-2013-planning-for-simple-urls.md) in the Planning documentation. You can select the format for your simple URLs from several options. For details about these options, see [DNS requirements for simple URLs in Lync Server 2013](lync-server-2013-dns-requirements-for-simple-urls.md) in the Planning documentation.

By default, simple URLs will be configured in the form of (for example, the dial-in simple URL): https://dialin.\<SIP Domain\>

<div>

## To configure simple URLs

1.  In Topology Builder, right-click the **Lync Server** node, and then click **Edit Properties**.

2.  In the **Simple URLs** pane, select either **Phone access URLs:** (Dial-in) or **Meeting URLs:** (Meet) to edit, and then click **Edit URL**.

3.  Update the URL to the value you want, and then click **OK** to save the edited URL. The example shown here has modified the Dial-in URL to https://pool01.contoso.net/dialin.

4.  Edit the Meet URL by using the same steps, if necessary.

</div>

<div>

## To define the optional Admin simple URL

1.  In Topology Builder, right-click the **Lync Server** node, and then click **Edit Properties**.

2.  In the **Administrative access URL** box, enter the simple URL you want for administrative access to Lync Server 2013 Control Panel, and then click **OK**.
    
    <div>
    

    > [!TIP]  
    > We recommend using the simplest possible URL for the Admin URL. The simplest option is <STRONG>https://admin.</STRONG>&lt;domain&gt;.

    
    </div>
    
    <div>
    

    > [!IMPORTANT]  
    > If you change a simple URL after initial deployment, you must be aware of what changes impact your Domain Name System (DNS) records and certificates for simple URLs. If the change impacts the base of a simple URL, then you must change the DNS records and certificates as well. For example, changing from https://lync.contoso.com/Meet to https://meet.contoso.com changes the base URL from lync.contoso.com to meet.contoso.com, so you would need to change the DNS records and certificates to refer to meet.contoso.com. If you changed the simple URL from https://lync.contoso.com/Meet to https://lync.contoso.com/Meetings, the base URL of lync.contoso.com stays the same, so no DNS or certificate changes are needed. Whenever you change a simple URL name, however, you must run the <STRONG>Enable-CsComputer</STRONG> cmdlet on each Director and Front End Server to register the change.

    
    </div>

</div>

<div>

## See Also


[Planning for simple URLs in Lync Server 2013](lync-server-2013-planning-for-simple-urls.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

