---
title: 'Lync Server 2013: Configuring DNS for Autodiscover'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring DNS for Autodiscover
ms:assetid: f07a634c-3cf3-4958-8556-84596319ef54
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945656(v=OCS.15)
ms:contentKeyID: 51541528
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring DNS for Autodiscover in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-12-12_

To support autodiscovery for Lync clients, you need to create the following Domain Name System (DNS) records:

  - An internal DNS record to support Lync clients who connect from within your organization's network

  - An external, or public, DNS record to support Lync clients who connect from the Internet

You must create an internal DNS record and an external DNS record for each SIP domain.

The DNS records can be either A (host) records or CNAME records, based on your ability to create new certificates with the additional subject alternate name (SAN). If you are not able to request and deploy a new external (public) certificate with the lyncdiscover.\<domain name\> SAN, use the procedure for using HTTP/TCP port 80. The following procedures describe how to create internal and external DNS records.

<div>

## To create DNS CNAME records

1.  Log on to a DNS server as follows:
    
      - To create an internal DNS record, log on to a DNS server in your network as a member of the Domain Admins group or a member of the DnsAdmins group.
    
      - To create an external DNS record, connect to your public DNS provider.

2.  Open the DNS administrative snap-in: Click **Start**, click **Administrative Tools**, and then click **DNS**.

3.  Do one of the following:
    
      - For an internal DNS record, in the console tree of the DNS server, expand **Forward Lookup Zones** for your Active Directory domain (for example, contoso.local).
        
        <div>
        

        > [!NOTE]  
        > This domain is the Active Directory domain where your Lync Server 2013&nbsp;Director pool and Front End pool are installed.

        
        </div>
    
      - For an external DNS record, in the console tree of the DNS server, expand **Forward Lookup Zones** for your SIP domain (for example, contoso.com).

4.  Verify that a host A record exists for your Director pool as follows:
    
      - For an internal DNS record, a host A record should exist for the internal Web Services fully qualified domain name (FQDN) for your Director pool (for example, lyncwebdir01.contoso.local).
    
      - For an external DNS record, a host A record should exist for the external web services FQDN for your Director pool (for example, lyncwebextdir.contoso.com).

5.  Verify that a host A record exists for your Front End pool as follows:
    
      - For an internal DNS record, a host A record should exist for the internal Web Services FQDN for your Front End pool (for example, lyncwebpool01.contoso.local).
    
      - For an external DNS record, a host A record should exist for the external Web Services FQDN for your Front End pool (for example, lyncwebextpool01.contoso.com).

6.  For an internal DNS record, in the console tree of your DNS server, expand **Forward Lookup Zones** for your SIP domain (for example, contoso.com).
    
    <div>
    

    > [!NOTE]  
    > If you are creating an external DNS record, <STRONG>Forward Lookup Zones</STRONG> is already expanded for your SIP domain from step 3.

    
    </div>

7.  Right-click the SIP domain name, and then click **New Alias (CNAME)**.

8.  In **Alias name**, type one of the following:
    
      - For an internal DNS record, type lyncdiscoverinternal as the host name for the internal Autodiscover Service URL.
    
      - For an external DNS record, type lyncdiscover as the host name for the external Autodiscover Service URL.

9.  In **Fully qualified domain name (FQDN) for target host**, do one of the following:
    
      - For an internal DNS record, type or browse to the internal Web Services FQDN for your Director pool (for example, lyncwebdir01.contoso.local), and then click **OK**.
    
      - For an external DNS record, type or browse to the external Web Services FQDN for your Director pool (for example, lyncwebextdir.contoso.com), and then click **OK**.
    
    <div>
    

    > [!NOTE]  
    > If you do not use a Director, use the internal and external Web Services FQDN for the Front End pool, or, for a single server, the FQDN for the Front End Server or Standard Edition server.

    
    </div>
    
    <div>
    

    > [!IMPORTANT]  
    > You must create a new Autodiscover CNAME record in the forward lookup zone of each SIP domain that you support in your Lync Server 2013 environment.

    
    </div>

</div>

<div>

## To create DNS A records

1.  Log on to a DNS server as follows:
    
      - To create an internal DNS record, log on to a DNS server in your network as a member of the Domain Admins group or a member of the DnsAdmins group.
    
      - To create an external DNS record, connect to your public DNS provider or external DNS server.

2.  Open the DNS administrative snap-in: Click **Start**, click **Administrative Tools**, and then click **DNS**.

3.  Do one of the following:
    
      - For an internal DNS record, in the console tree of the DNS server, expand **Forward Lookup Zones** for your Active Directory domain (for example, contoso.local).
        
        <div>
        

        > [!NOTE]  
        > This domain is the Active Directory domain where your Lync Server 2013&nbsp;Director pool and Front End pool are installed.

        
        </div>
    
      - For an external DNS record, in the console tree of the DNS server, expand **Forward Lookup Zones** for your SIP domain (for example, contoso.com).

4.  Verify that a host A (for IPv6, AAAA) record exists for your Director pool as follows:
    
      - For an internal DNS record, a host A (for IPv6, AAAA) record should exist for the internal Web Services FQDN for your Director pool (for example, lyncwebdir01.contoso.local).
    
      - For an external DNS record, a host A (for IPv6, AAAA) record should exist for the external Web Services FQDN for your Director pool (for example, lyncwebextdir.contoso.com).

5.  Verify that a host A (for IPv6, AAAA) record exists for your Front End pool as follows:
    
      - For an internal DNS record, a host A (for IPv6, AAAA) record should exist for the internal Web Services FQDN for your Front End pool (for example, lyncwebpool01.contoso.local).
    
      - For an external DNS record, a host A (for IPv6, AAAA) record should exist for the external Web Services FQDN for your Front End pool (for example, lyncwebextpool01.contoso.com).

6.  For an internal DNS record, in the console tree of your DNS server, expand **Forward Lookup Zones** for your SIP domain (for example, contoso.com).
    
    <div>
    

    > [!NOTE]  
    > If you are creating an external DNS record, <STRONG>Forward Lookup Zones</STRONG> is already expanded for your SIP domain from step 3.

    
    </div>

7.  Right-click the SIP domain name, and then click **New Host (A or AAAA)**.

8.  In **Name**, type the host name as follows:
    
      - For an internal DNS record, type lyncdiscoverinternal as the host name for the internal Autodiscover Service URL.
    
      - For an external DNS record, type lyncdiscover as the host name for the external Autodiscover Service URL.
    
    <div>
    

    > [!NOTE]  
    > The domain name is assumed from the zone in which the record is defined and, therefore, does not need to be entered as part of the A record.

    
    </div>

9.  In **IP Address**, type the IP address as follows:
    
      - For an internal DNS record, type the internal Web Services IP address of the Director (or, if you use a load balancer, type the virtual IP (VIP) of the Director load balancer).
        
        <div>
        

        > [!NOTE]  
        > If you do not use a Director, type the IP address of the Front End Server or Standard Edition server, or, if you use a load balancer, type the VIP of the Front End pool load balancer.

        
        </div>
    
      - For an external DNS record, type the external or public IP address of the reverse proxy.

10. Click **Add Host**, and then click **OK**.

11. To create an additional A record, repeat steps 8 through 10.
    
    <div>
    

    > [!IMPORTANT]  
    > You must create a new lyncdiscover and lyncdiscoverinternal A records in the forward lookup zone of each SIP domain that you support in your Lync Server 2013 environment.

    
    </div>

12. When you are finished creating A (for IPv6, AAAA) records, click **Done**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

