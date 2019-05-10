---
title: "Edit Edge Settings Expander for Lync Server 2010"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.EdgeSettingsExpander2010
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 74a66817-7092-4b2f-a2af-bc1a2c9e5fed
description: "You edit the settings for the Edge Server or Edge pool by configuring the following properties:"
---

# Edit Edge Settings Expander for Lync Server 2010
 
You edit the settings for the Edge Server or Edge pool by configuring the following properties: 
  
 **General**
  
- **Internal pool FQDN**: The internal pool fully qualified domain name is the identity of the Edge Server or Edge pool as defined in the domain name system (DNS) host (A or AAAA for IPv6) record.
    
- Select **Enable federation for this Edge pool (port 5061)** if you want to enable the Edge Server or Edge pool for federation with other session initiation protocol partners.
    
    > [!IMPORTANT]
    > You can only define one Edge Server or Edge pool actively for federation. The configuration shown in the associated screen shot indicates that another Edge Server or Edge pool is already configured for federation. The external DNS SRV record for federation (_sipfederationtls._tcp.\<external domain name\>) will point to the Edge Server or Edge pool for federation. 
  
- The **Internal Configuration Replication Port (HTTPS)**, by default at TCP port 4443, is the port that the local (that is, local to the Edge Servers) copy of the Central Management store is replicated over. The local copy of the Central Management store is in the **RTCLOCAL** database in the SQL Server on each computer. The replication is one-way, initiated from the Central Management Server (or, the Front End Server or Front End pool that holds the Central Management Server role) to the Edge Servers and is an internal interface port.
    
  **Next hop selection**
  
- Select for the list your **Next hop pool**. You define either a Director, Director pool, Front End Server or Front End pool to assume this role. The next hop pool is the server or server pool that will accept inbound SIP messages from the Edge Server or Edge pool internal interface and send outbound SIP to the Edge internal interface.
    
    > [!NOTE]
    > The Director is an optional role and if you decide not to deploy Directors, the Front End Servers (single computer or pool) will assume the Director role. 
  
  **External settings**
  
This section of the properties allows you to edit properties for the external settings of the Edge Server or Edge pool. The following properties are available to edit:
  
- Select the **Enable separate FQDN and IP address for web conferencing and A/V** check box if you want to assign distinct IP addresses and fully qualified domain names to each Edge Server service.
    
    > [!NOTE]
    > If you choose to not select the check box, you must use separate ports for each Edge service. Each Edge service will share the FQDN defined for the Access Edge service, and will therefore use the same IP address. Each Edge service must be uniquely identified by either a distinct IP address and same port, or the same IP address and unique port values. 
  
- Select **A/V Edge service is NAT enabled** if you want to configure the A/V Edge service to use a private address or other address that will be hidden behind a network address translation (NAT) device.
    
- To edit the **Access Edge service**, you define the **Pool FQDN** for the Access Edge service as defined in DNS by host (A, and AAAA if IPv6 is used) records and a port value
    
- To edit the **Web Conferencing Edge service**, you define a **Pool FQDN** for the Web Conferencing Edge service as defined in DNS by host (A, and AAAA if IPv6 is used) records and a port value
    
- To edit the **A/V Edge service**, you define a **Pool FQDN** for the A/V Edge service as defined in DNS by host (A, and AAAA if IPv6 is used) records and a port value
    
    > [!IMPORTANT]
    > If you have selected the **Enable separate FQDN and IP address for web conferencing and A/V** check box, only the Access Edge service Pool FQDN will be available for editing. Assign distinct ports for each of the three Edge services.
  
  **OK** Accepts and commits changes to the dialog.
  
  **Cancel** Discards changes and closes the dialog.
  
  **Help** Displays this help screen.
  

