---
title: "Lync Server sites for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 022cb6dd-37e2-4882-a53e-5ddfdbc6f53a
description: "In Lync Server, you define sites on your network that contain Lync Server components. A site is a set of computers that is well-connected by a high-speed, low-latency network, such as a single local area network (LAN) or two networks connected by a high-speed fiber optic network. Note that Lync Server sites are a separate concept from Active Directory Domain Services sites and Microsoft Exchange Server sites. Your Lync Server sites do not need to correspond to your Active Directory sites."
---

# Lync Server sites for Lync Server 2013
[]
In Lync Server, you define sites on your network that contain Lync Server components. A site is a set of computers that is well-connected by a high-speed, low-latency network, such as a single local area network (LAN) or two networks connected by a high-speed fiber optic network. Note that Lync Server sites are a separate concept from Active Directory Domain Services sites and Microsoft Exchange Server sites. Your Lync Server sites do not need to correspond to your Active Directory sites. 
  
## Site Types

Each site is either a central site, which contains at least one Front End pool or a Standard Edition server, or a branch site. Each branch site is associated with exactly one central site, and the users at the branch site get most of their Lync Server functionality from the servers at the associated central site.
  
Each branch site contains one of the following: 
  
- A Survivable Branch Appliance (SBA), which is an industry-standard blade server with a Lync Server Registrar and a Mediation Server running on Windows Server. The Survivable Branch Appliance also contains a public switched telephone network (PSTN) gateway. The Survivable Branch Appliance is designed for branch sites with between 25 and 1000 users. 
    
- A Survivable Branch Server (SBS), which is a server running Windows Server that meets specified hardware requirements, and that has Lync Server Registrar and Mediation Server software installed on it. It must connect to either a PSTN gateway or a SIP trunk to a telephone service provider. The Survivable Branch Server is designed for branch sites with between 1000 and 5000 users. 
    
- A PSTN gateway, and, optionally, a Mediation Server. For details on this and other server roles, see [Server roles in Lync Server 2013](server-roles.md).
    
A branch office with a resilient wide area network (WAN) link to a central site can use the third option—a PSTN gateway, and, optionally, a Mediation Server. Branch office sites with less-resilient links should use a Survivable Branch Appliance or Survivable Branch Server, which provide resiliency in times of wide-area network failures. For example, in a site with a Survivable Branch Appliance or Survivable Branch Server deployed, users can still make and receive Enterprise Voice calls if the WAN connecting the branch site to the central site is down. For details about the Survivable Branch Appliance, Survivable Branch Server, and resiliency, see [Planning for Enterprise Voice resiliency in Lync Server 2013](planning-for-enterprise-voice-resiliency.md) in the Planning documentation. 
  
## Site Topologies

Your deployment must include at least one central site, and can include zero to many branch sites. Each branch site is affiliated with one central site. The central site provides the Lync Server services to the branch site that are not hosted locally at the branch site, such as presence and conferencing.
  
If you have multiple sites, you can pair together the Front End pools at different sites to enable disaster recovery abilities. For details, see [High availability and disaster recovery support in Lync Server 2013](high-availability-and-disaster-recovery-support.md).
  
## See also

#### 

[Server roles in Lync Server 2013](server-roles.md)
  
[High availability and disaster recovery support in Lync Server 2013](high-availability-and-disaster-recovery-support.md)
#### 

[Planning for Enterprise Voice resiliency in Lync Server 2013](planning-for-enterprise-voice-resiliency.md)

