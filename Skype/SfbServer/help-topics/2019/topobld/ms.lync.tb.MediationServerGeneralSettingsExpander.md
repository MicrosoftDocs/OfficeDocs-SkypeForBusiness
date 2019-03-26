---
title: "Mediation Server General Settings Expander"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.MediationServerGeneralSettingsExpander
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0e0ad9f0-27d5-4975-ae88-0b8ff8a4c514
ROBOTS: NOINDEX, NOFOLLOW

---

# Mediation Server General Settings Expander
 


## General settings

Fully qualified domain name (FQDN) of the Mediation Server pool or Mediation Server. Edit the FQDN of the server to change the value. You must have a Domain Name System (DNS) host (A) record that coincides with the new value.
  
In the **Associations** section, you select an Edge Server or Edge Server pool to associate with the Mediation Server pool or Mediation Server. You select the Edge that the Mediation Server's media components will use for External user Enterprise Voice.
  
If you do not have an Edge Server currently defined and need to associate the Mediation Server with an Edge Server, click **New** and define the new Edge Server or Edge Server pool in the Define the New Edge pool wizard.
  
## Next hop settings

You specify the Mediation Server pool or Mediation Server next hop by selecting the defined Enterprise Edition Front End pool or Standard Edition Front End Server from the drop-down list. A Director or Director pool is not a valid selection for a Mediation Server pool or Mediation Server next hop, and will not appear in the list. Click **OK** to accept and save your changes. Click **Cancel** to discard your changes and exit the properties page.
  
## PSTN gateway settings

1. You define PSTN gateways that are associated with the Mediation Server pool or Mediation Server. If you have already defined gateways, they will be available to associate with the Mediation Server. If you enable the collocation of the Mediation Server, define the listening port range on the pool servers for Transport Layer Security (TLS). By default, this port is 5067. If you select **Enable TCP port**, you must define a Transmission Control Protocol (TCP) port for the collocated Mediation Server. This is an optional setting, and you should refer to the requirements of your gateway or PSTN requirements to determine if you need this. By default, the TCP port value is 5068.
    
2. Trunks that are associated with the collocated Mediation Server. If you have already defined trunks, they will be available to associate with the Mediation Server. 
    
3. If you have more than one trunk associated with a Mediation Server, you can specify a default trunk by selecting the trunk and then clicking **Make Default**. To unselect a gateway as the default, click **Unmake Default**. 
    

