---
title: 'Lync Server 2013: Configuring the meeting invitation'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring the meeting invitation
ms:assetid: 7faa4797-0344-418b-9fa3-59dfb9c2baf7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398638(v=OCS.15)
ms:contentKeyID: 48184641
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring the meeting invitation in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-16_

You can customize meeting invitations sent by the Online Meeting Add-in for Lync 2013 by including the following optional items in the body of the meeting invitation:

  - **Your organization’s logo** Add your organization’s logo to meeting invitations by using the Logo URL option. If meeting invitations will be sent to people external to your organization, the image should be located at a publicly available URL. The supported image formats are GIF and JPG. Although Lync Server 2013 stores the URL with no size restrictions on the image, for best results, the maximum size of the image should be 30 pixels high by 188 pixels wide.

  - **A Custom Help or Support Link** Add a URL for your organization’s help or support team website. If meeting invitations will be sent to people external to your organization, the URL should be publicly available. The maximum URL length is 1 KB.

  - **Legal disclaimer text** Add a URL for legal text or a disclaimer that will be displayed in all meeting invitations. If meeting invitations will be sent to people external to your organization, the URL should be publicly available. The maximum URL length is 1 KB.

  - **Custom footer text** Add text that will be rendered as a custom footer in the invitation. The maximum length of text that can be added is 2 KB.

You can configure these options by using either Lync Server Control Panel or Lync Server Management Shell.

<div>


**To Customize the Meeting Invitation by using Lync Server Control Panel**

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Conferencing** and then click **Meeting Configuration**.

4.  On the **Meeting Configuration** page, click **New**, and then do one of the following:
    
      - To create a site-level policy, click **Site configuration**. In the **Select a Site** search field, type all or part of the name of the site for which you want to define meeting join settings. In the resulting list of sites, click the site you want, and then click **OK**.
    
      - To create a pool-level policy, click **Pool configuration**. In the **Select a Service** search field, type all or part of the name of the pool service for which you want to define meeting join settings. In the resulting list of services, click the pool you want, and then click **OK**.

5.  Do any of the following:
    
      - In the **Logo URL** field, type the URL for your organization’s logo image.
    
      - In the **Help URL** field, type the URL to your organization’s help or support site.
    
      - In the **Legal text** field, type the URL to the legal text or disclaimer that you want to include in meeting invitations.
    
      - In the **Custom footer text** field, type footer text, up to 2 KB.

**To Customize the Meeting Invitation by using Lync Server Management Shell**

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the **New-CsMeetingConfiguration** or **Set-CsMeetingConfiguration** cmdlet to create or configure the meeting invitation options. For example, run:
    
        New-CsMeetingConfiguration -Identity site:Redmond -LogoURL "http://www.contoso.com/logo/contosobanner.gif" -HelpURL "http://www.contoso.com/support" -LegalURL "http://www.contoso.com/disclaimer" -CustomFooterText "Communications may be monitored or recorded."

</div>

</div>

<span> </span>

</div>

</div>

</div>

