---
title: "Mediation Server General Settings Expander"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 4/14/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.MediationServerGeneralSettingsExpander
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.assetid: 0e0ad9f0-27d5-4975-ae88-0b8ff8a4c514
description: "Mediation Server helps to mediate traffic between internal Skype for Business Server and Public Switched telephone Network gateways."

---

# Mediation Server General Settings Expander

## General settings

Fully qualified domain name (FQDN) of the Mediation Server pool or Mediation Server. Edit the FQDN of the server to change the value. You must have a Domain Name System (DNS) host (A) record that coincides with the new value.
  
In the **Associations** section, you select a Microsoft Edge Server or Microsoft Edge Server pool to associate with the Mediation Server pool or Mediation Server. You select the Microsoft Edge that the Mediation Server's media components use for External user Enterprise Voice.
  
If you don't have a Microsoft Edge Server currently defined and need to associate the Mediation Server with a Microsoft Edge Server, select **New** and define the new Microsoft Edge Server or Microsoft Edge Server pool in the Define the New Microsoft Edge pool wizard.
  
## Next hop settings

You specify the Mediation Server pool or Mediation Server next hop by selecting the defined Enterprise Edition Front End pool or Standard Edition Front End Server from the drop-down list. A Director or Director pool isn't a valid selection for a Mediation Server pool or Mediation Server next hop, and won't appear in the list. Select **OK** to accept and save your changes. Select **Cancel** to discard your changes and exit the properties page.
  
## PSTN gateway settings

1. You define PSTN gateways that are associated with the Mediation Server pool or Mediation Server. If you define gateways, they're available to associate with the Mediation Server. If you enable the collocation of the Mediation Server, define the listening port range on the pool servers for Transport Layer Security (TLS). By default, this port is 5067. If you select **Enable TCP port**, you must define a Transmission Control Protocol (TCP) port for the collocated Mediation Server. Enabling the TCP port is an optional setting. You must refer to the requirements of your gateway or PSTN to determine if you need it. By default, the TCP port value is 5068.
    
2. Trunks that are associated with the collocated Mediation Server. If you define trunks, they're available to associate with the Mediation Server. 
    
3. If you have more than one trunk associated with a Mediation Server, you can specify a default trunk by selecting the trunk and then clicking **Make Default**. To unselect a gateway as the default, select **Unmake Default**. 
    

