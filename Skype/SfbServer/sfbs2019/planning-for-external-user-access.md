---
title: "Planning for external user access in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ea098933-eff5-461e-aba3-e7f128784dc2
description: "Communications in most organizations involve services and users that are not inside your internal network. These services and users include employees who are temporarily or permanently offsite, employees of customer or partner organizations, people who use public instant messaging (IM) services, and potential customers, partners and anonymous users whom you invite to meetings and presentations. In this documentation, these people are collectively referred to as external users."
---

# Planning for external user access in Lync Server 2013
[]
Communications in most organizations involve services and users that are not inside your internal network. These services and users include employees who are temporarily or permanently offsite, employees of customer or partner organizations, people who use public instant messaging (IM) services, and potential customers, partners and anonymous users whom you invite to meetings and presentations. In this documentation, these people are collectively referred to as external users.
  
With Microsoft Lync Server 2013, users in your organization can use IM and presence to communicate with external users, and they can participate in audio/video (A/V) conferencing and web conferencing with your offsite employees and other types of external users. You can also support external access from mobile devices and over Enterprise Voice. External users who are not members of your organization can participate in Lync Server 2013 meetings, allowing anonymous attendees.
  
To support communications across your organization's firewall, you deploy Lync Server 2013 Edge Server in your perimeter network (also known as DMZ, demilitarized zone, and screened subnet). The Edge Server controls how users outside the firewall can connect to your internal Lync Server 2013 deployment. It also controls communications with external users that originate within the firewall.
  
Depending on your requirements, you can deploy one or more Edge Servers in one or more locations. This section describes scenarios for external user access in Lync Server 2013, and it explains how to plan your edge and reverse proxy topology.
  
> [!NOTE]
> Although you need an Edge Server to support Enterprise Voice and external user access, this section focuses on support for IM, presence, A/V conferencing, federation, web conferencing, and Lync Mobile. For details about support for Enterprise Voice, see [Planning for Enterprise Voice in Lync Server 2013](planning-for-enterprise-voice.md) in the Planning documentation. 
  
## In this section

- [Changes in Lync Server 2013 that affect Edge Server planning](changes-in-lync-server-2013-that-affect-edge-server-planning.md)
    
- [System requirements for external user access components for Lync Server 2013](system-requirements-for-external-user-access-components.md)
    
- [Overview of external user access in Lync Server 2013](overview-of-external-user-access.md)
    
- [Understanding Autodiscover in Lync Server 2013](understanding-autodiscover.md)
    
- [Choosing a topology in Lync Server 2013](choosing-a-topology.md)
    
- [Data collection in Lync Server 2013](data-collection.md)
    
- [Determine DNS requirements for Lync Server 2013](determine-dns-requirements.md)
    
- [Determine external A/V firewall and port requirements for Lync Server 2013](determine-external-a-v-firewall-and-port-requirements.md)
    
- [Plan for Edge Server certificates in Lync Server 2013](plan-for-edge-server-certificates.md)
    
- [Scenarios for external user access in Lync Server 2013](scenarios-for-external-user-access.md)
    

