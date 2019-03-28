---
title: Lync Server 2013 technical requirements for IPv6
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Technical requirements for IPv6
ms:assetid: caff0123-ce41-4a62-87a0-00b1d118b72b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205278(v=OCS.15)
ms:contentKeyID: 48185465
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Technical requirements for IPv6 in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-30_

If you plan to configure Lync Server 2013 for IPv6, keep the following requirements in mind:

  - To use IPv6 addresses with Lync Server, you need to create domain name system (DNS) records for records that must be discovered and resolved to an IPv6 address. IPv6 DNS uses host AAAA (quad-A) records. If you use both IPv4 and IPv6 in your deployment, it is best to configure and maintain both host A records for IPv4 and host AAAA records for IPv6. Even when you fully transition your deployment to IPv6, you may still require IPv4 DNS host records for external users who still use IPv4.
    
    You can deploy IPv6 DNS host records before you start using IPv6. If the client or server doesn't use IPv6, the record will not be referenced. Transitional technologies will make the decision about which record to use, based on transition technology configuration and policies.

  - Each IPv6 address has a scope. The three scopes that you can use for IPv6 addressing are IPv6 global addresses (similar to public IPv4 addresses), IPv6 unique local addresses (similar to the private IPv4 address ranges), and IPv6 link-local addresses (similar to automatic private IP addresses in Windows Server for IPv4). All the servers within a pool should have IPv6 addresses with the same scope.

<div>


> [!IMPORTANT]  
> IPv6 is a complex topic and requires careful planning with your networking team and your Internet provider to help ensure that the addresses that you assign at the Windows Server level and at the Lync Server 2013 level work as expected. See the links at the end of this topic for additional resources on IPv6 addressing and planning.



</div>

<div>

## See Also


[IP Version 6 Addressing Architecture](http://tools.ietf.org/html/rfc4291)  
[IPv6 Global Unicast Address Format](http://tools.ietf.org/html/rfc3587)  
[Unique Local IPv6 Unicast Addresses](http://tools.ietf.org/html/rfc4193)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

