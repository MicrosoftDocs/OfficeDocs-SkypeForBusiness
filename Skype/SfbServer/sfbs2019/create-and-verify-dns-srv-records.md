---
title: "Create and verify DNS SRV records in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 86888c7e-1401-458f-9a7b-08ac726deeec
description: "To successfully complete this procedure, you should be logged on to the server or domain minimally as a member of the Domain Admins group or a member of the DnsAdmins group."
---

# Create and verify DNS SRV records in Lync Server 2013
[]
To successfully complete this procedure, you should be logged on to the server or domain minimally as a member of the Domain Admins group or a member of the DnsAdmins group.
  
This topic describes how to configure the Domain Name System (DNS) records that you are required to create in Lync Server 2013 deployments and those required for automatic client sign in. When you create a Front End pool, Setup creates Active Directory objects and settings for the pool, including the pool fully qualified domain name (FQDN). Similar objects and settings are created for a Standard Edition server. For clients to be able to connect to the pool or Standard Edition server, the FQDN of the pool or Standard Edition server must be registered in DNS. You must create DNS SRV records in your internal DNS for every SIP domain. This procedure assumes that your internal DNS has zones for your SIP user domains.
  
### To configure a DNS SRV record

1. On the DNS server, click **Start**, click **Administrative Tools**, and then click **DNS**.
    
2. In the console tree for your SIP domain, expand **Forward Lookup Zones**, and then right-click the SIP domain in which Lync Server 2013 will be installed.
    
3. Click **Other New Records**.
    
4. In **Select a resource record type**, click **Service Location (SRV)**, and then click **Create Record**.
    
5. Click **Service**, and then type _sipinternaltls.
    
6. Click **Protocol**, and then type _tcp.
    
7. Click **Port Number**, and then type 5061.
    
8. Click **Host offering this service**, and then type the FQDN of the pool or Standard Edition server.
    
9. Click **OK**, and then click **Done**.
    
### To verify the creation of a DNS SRV record

1. Log on to a client computer in the domain with an account that is a member of the Authenticated Users group or has equivalent permissions.
    
2. Click **Start**, and then click **Run**.
    
3. In the **Open** box, type cmd, and then click **OK**.
    
4. At the command prompt, type nslookup, and then press ENTER.
    
5. Type set type=srv, and then press ENTER.
    
6. Type _sipinternaltls._tcp.contoso.com, and then press ENTER. The output displayed for the Transport Layer Security (TLS) record is as follows:
    
    Server:  _\<dns server\>_.contoso.com
    
    Address:  _\<IP address of DNS server\>_
    
    Non-authoritative answer: 
    
    _sipinternaltls._tcp.contoso.com SRV service location:
    
     priority = 0 
    
     weight = 0 
    
     port = 5061 
    
     svr hostname = poolname.contoso.com (or Standard Edition server A record) 
    
    poolname.contoso.com internet address =  _\<virtual IP Address of the load balancer\>_ or  _\<IP address of a single Enterprise Edition server for pools with only one Enterprise Edition server\>_ or  _\<IP address of the Standard Edition server\>_
    
7. When you are finished, at the command prompt, type exit, and then press ENTER.
    
### To verify that the FQDN of the Front End pool or Standard Edition server can be resolved

1. Log on to a client computer in the domain.
    
2. Click **Start**, and then click **Run**.
    
3. In the **Open** box, type cmd, and then click **OK**.
    
4. At the command prompt, type nslookup _\<FQDN of the Front End pool\>_ or  _\<FQDN of the Standard Edition server\>_, and then press ENTER.
    
5. Verify that you receive a reply that resolves to the appropriate IP address for the FQDN.
    

