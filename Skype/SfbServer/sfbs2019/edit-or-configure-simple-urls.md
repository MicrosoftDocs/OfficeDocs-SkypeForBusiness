---
title: "Edit or configure simple URLs in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0008aeea-4ae9-4e36-83cd-ef7ff7b6e128
description: "This procedure does not require membership in a local administrator or privileged domain group. You should log on to a computer as a standard user."
---

# Edit or configure simple URLs in Lync Server 2013
[]
This procedure does not require membership in a local administrator or privileged domain group. You should log on to a computer as a standard user.
  
Lync Server 2013 uses simple URLs to direct internal and external calls to services on the Front End Server or on the Director, if one has been deployed. For more information about simple URLs, see [Planning for simple URLs in Lync Server 2013](planning-for-simple-urls.md) in the Planning documentation. You can select the format for your simple URLs from several options. For details about these options, see [DNS requirements for simple URLs in Lync Server 2013](dns-requirements-for-simple-urls.md) in the Planning documentation. 
  
By default, simple URLs will be configured in the form of (for example, the dial-in simple URL): https://dialin.\<SIP Domain\>
  
### To configure simple URLs

1. In Topology Builder, right-click the **Lync Server** node, and then click **Edit Properties**.
    
2. In the **Simple URLs** pane, select either **Phone access URLs:** (Dial-in) or **Meeting URLs:** (Meet) to edit, and then click **Edit URL**.
    
3. Update the URL to the value you want, and then click **OK** to save the edited URL. The example shown here has modified the Dial-in URL to https://pool01.contoso.net/dialin. 
    
4. Edit the Meet URL by using the same steps, if necessary.
    
### To define the optional Admin simple URL

1. In Topology Builder, right-click the **Lync Server** node, and then click **Edit Properties**.
    
2. In the **Administrative access URL** box, enter the simple URL you want for administrative access to Lync Server 2013 Control Panel, and then click **OK**.
    
    > [!TIP]
    > We recommend using the simplest possible URL for the Admin URL. The simplest option is https://admin. _\<domain\>_. 
  
    > [!IMPORTANT]
    > If you change a simple URL after initial deployment, you must be aware of what changes impact your Domain Name System (DNS) records and certificates for simple URLs. If the change impacts the base of a simple URL, then you must change the DNS records and certificates as well. For example, changing from https://lync.contoso.com/Meet to https://meet.contoso.com changes the base URL from lync.contoso.com to meet.contoso.com, so you would need to change the DNS records and certificates to refer to meet.contoso.com. If you changed the simple URL from https://lync.contoso.com/Meet to https://lync.contoso.com/Meetings, the base URL of lync.contoso.com stays the same, so no DNS or certificate changes are needed. Whenever you change a simple URL name, however, you must run the **Enable-CsComputer** cmdlet on each Director and Front End Server to register the change. 
  
## See also

#### 

[Planning for simple URLs in Lync Server 2013](planning-for-simple-urls.md)

