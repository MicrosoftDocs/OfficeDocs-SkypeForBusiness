---
title: "Update DNS SRV records"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "To successfully complete this procedure, you should be logged on to the server or domain as a member of the Domain Admins group or a member of the DnsAdmins group."
---

# Update DNS SRV records

To successfully complete this procedure, you should be logged on to the server or domain as a member of the Domain Admins group or a member of the DnsAdmins group.
  
This topic describes how to update the Domain Name System (DNS) records after migrating to Skype for Business Server 2019. After all users have been moved to Skype for Business Server 2019, but before the legacy pool or Director is decommissioned, you must update the DNS SRV records in your internal DNS for every SIP domain. This procedure assumes that your internal DNS has zones for your SIP user domains.
  
## To configure a DNS SRV record

1. On the DNS server, click **Start**, click **Administrative Tools**, and then click **DNS**.
    
2. In the console tree for your SIP domain, expand **Forward Lookup Zones**, expand the SIP domain in which Skype for Business Server 2019 is installed, and navigate to the **_tcp** setting. 
    
3. In the right pane, right-click **_sipinternaltls** and select **Properties**.
    
4. In **Host offering this service**, update the host FQDN to point to the Skype for Business Server 2019 pool.
    
5. Click **OK**.
    
## To verify that the FQDN of the Front End pool or Standard Edition server can be resolved

1. Log on to a client computer in the domain.
    
2. Click **Start**, and then click **Run**.
    
3. In the **Open** box, type cmd, and then click **OK**.
    
4. At the command prompt, type nslookup _\<FQDN of the Front End pool\>_ or  _\<FQDN of the Standard Edition server\>_, and then press ENTER.
    
5. Verify that you receive a reply that resolves to the appropriate IP address for the FQDN.
    

