---
title: "Change simple URLs after migration [W14 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: addb0dc8-8324-42b1-9a00-f4bd14fdf5c0
description: "Lync Server supports three simple URLs:"
---

# Change simple URLs after migration [W14 to W15]
[]
Lync Server supports three simple URLs:
  
- **Meet** is used as the base URL for all conferences in the site or organization. With the Meet simple URL, links to join meetings are easy to comprehend, and easy to communicate and distribute. 
    
- **Dial-in** enables access to the Dial-in Conferencing Settings webpage. The Dial-in simple URL is included in all meeting invitations so that users who want to dial in to the meeting can access the necessary phone number and PIN information. 
    
- **Admin** enables quick access to the Lync Server Control Panel. The Admin simple URL is internal to your organization. 
    
After migrating to Lync Server 2013, you must be aware of how the change impacts your DNS records and certificates for simple URLs. If the legacy Lync Server 2010 Director remains in use in the topology, no changes to your simple URLs are required. If the Lync Server 2010 Director is removed from the topology after migration, the simple URL DNS records must be updated to point to one of the Lync Server 2013 pools. Whenever you change a simple URL name, however, you must run Enable-CsComputer on each Director and Front End Server to register the change.
  
## Changing Simple URLs after Migration

### To update the Meet simple URL

1. In Topology Builder, right-click the top node **Lync Server**, and then click **Edit Properties**.
    
2. Select **Simple URLs** in the left pane, then below **Meeting URLs:** select the Meet URL and then click **Edit URL**.
    
3. Update the URL to the value you want, and then click **OK** to save the edited URL. 
    
### To update the Admin simple URL

1. In Topology Builder, right-click the top node **Lync Server**, and then click **Edit Properties**.
    
2. Select **Simple URLs** in the left pane, then below **Administrative access URL** box, enter the simple URL you want for administrative access to Lync Server 2013 Control Panel, and then click **OK**.
    
    > [!TIP]
    > We recommend using the simplest possible URL for the Admin URL. The simplest option is https://admin. _\<domain\>_. 
  
## See also

#### 

<!-- [Planning for simple URLs in Lync Server 2013](../../planning/planning-for-manageability-and-virtualization/planning-for-simple-urls.md) -->

