---
title: 'Lync Server 2013: DNS requirements for automatic client sign-in'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: DNS requirements for automatic client sign-in
ms:assetid: 3bcd4bb3-a022-4ffa-b005-1a95ad2b1796
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425884(v=OCS.15)
ms:contentKeyID: 48183873
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS requirements for automatic client sign-in in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-19_

This section explains the Domain Name System (DNS) records that are required for automatic client sign-in. When you deploy your Standard Edition servers or Front End pools, you can configure your clients to use automatic discovery to sign in to the appropriate Standard Edition server or Front End pool. If you plan to require your clients to connect manually to Lync Server 2013, you can skip this topic.

To support automatic client sign-in, you must:

  - Designate a single server or pool to distribute and authenticate client sign-in requests. This can be an existing server or pool in your organization that hosts users, or you can designate a dedicated server or pool for this purpose that hosts no users. For high availability, we recommend that you designate a Front End pool for this function.

  - Create an internal DNS SRV record to support automatic client sign-in for this server or pool.
    
    <div>
    

    > [!NOTE]  
    > In the following record requirements, SIP domain refers to the host portion of the SIP URIs assigned to users. For example, if SIP URIs are of the form *@contoso.com, contoso.com is the SIP domain. The SIP domain is often different from the internal Active Directory domain. An organization can also support multiple SIP domains.

    
    </div>

To enable automatic configuration for your clients, you must create an internal DNS SRV record that maps one of the following records to the fully qualified domain name (FQDN) of the Front End pool or Standard Edition server that distributes sign-in requests from Lync clients:

  - \_sipinternaltls.\_tcp.\<domain\> - for internal TLS connections

You only need to create a single SRV record for the Front End pool or Standard Edition server or that will distribute sign-in requests.

The following table shows some example records required for the fictitious company Contoso, which supports SIP domains of contoso.com and retail.contoso.com.

### Example of DNS Records Required for Automatic Client Sign-in with Multiple SIP Domains

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>FQDN of Front End pool used to distribute sign-in requests</th>
<th>SIP domain</th>
<th>DNS SRV record</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>pool01.contoso.com</p></td>
<td><p>contoso.com</p></td>
<td><p>An SRV record for _sipinternaltls._tcp.contoso.com domain over port 5061 that maps to pool01.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>pool01.contoso.com</p></td>
<td><p>retail.contoso.com</p></td>
<td><p>An SRV record for _sipinternaltls._tcp.retail.contoso.com domain over port 5061 that maps to pool01.contoso.com</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> By default, queries for DNS records adhere to strict domain name matching between the domain in the user name and the SRV record. If you prefer that client DNS queries use suffix matching instead, you can configure the DisableStrictDNSNaming Group Policy. For details, see <A href="lync-server-2013-planning-for-clients-and-devices.md">Planning for clients and devices in Lync Server 2013</A> in the Planning documentation.



</div>

<div>

## Example of the Certificates and DNS Records Required for Automatic Client Sign-In

This example uses the same example names in the preceding table. The Contoso organization supports the SIP domains of contoso.com and retail.contoso.com, and all of its users have a SIP URI in one of the following forms:

  - \<user\>@retail.contoso.com

  - \<user\>@contoso.com

</div>

</div>

<span> </span>

</div>

</div>

</div>

