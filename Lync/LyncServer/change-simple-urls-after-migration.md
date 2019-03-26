---
title: Change simple URLs after migration
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Change simple URLs after migration
ms:assetid: addb0dc8-8324-42b1-9a00-f4bd14fdf5c0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721844(v=OCS.15)
ms:contentKeyID: 49733777
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Change simple URLs after migration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-22_

Lync Server supports three simple URLs:

  - **Meet** is used as the base URL for all conferences in the site or organization. With the Meet simple URL, links to join meetings are easy to comprehend, and easy to communicate and distribute.

  - **Dial-in** enables access to the Dial-in Conferencing Settings webpage. The Dial-in simple URL is included in all meeting invitations so that users who want to dial in to the meeting can access the necessary phone number and PIN information.

  - **Admin** enables quick access to the Lync Server Control Panel. The Admin simple URL is internal to your organization.

After migrating to Lync Server 2013, you must be aware of how the change impacts your DNS records and certificates for simple URLs. If the legacy Lync Server 2010 Director remains in use in the topology, no changes to your simple URLs are required. If the Lync Server 2010 Director is removed from the topology after migration, the simple URL DNS records must be updated to point to one of the Lync Server 2013 pools. Whenever you change a simple URL name, however, you must run Enable-CsComputer on each Director and Front End Server to register the change.

<div>

## Changing Simple URLs after Migration

**To update the Meet simple URL**

1.  In Topology Builder, right-click the top node **Lync Server**, and then click **Edit Properties**.

2.  Select **Simple URLs** in the left pane, then below **Meeting URLs:** select the Meet URL and then click **Edit URL**.

3.  Update the URL to the value you want, and then click **OK** to save the edited URL.

**To update the Admin simple URL**

1.  In Topology Builder, right-click the top node **Lync Server**, and then click **Edit Properties**.

2.  Select **Simple URLs** in the left pane, then below **Administrative access URL** box, enter the simple URL you want for administrative access to Lync Server 2013 Control Panel, and then click **OK**.
    
    <div>
    

    > [!TIP]  
    > We recommend using the simplest possible URL for the Admin URL. The simplest option is <STRONG>https://admin.</STRONG>&lt;domain&gt;.

    
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

