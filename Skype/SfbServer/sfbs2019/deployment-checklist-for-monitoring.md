---
title: "Deployment checklist for monitoring in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4e798370-277c-4391-84b4-13a972b45ca6
description: "Although monitoring is already installed and activated on each Front End server, there are still several steps that you must undertake before you can actually being to collect monitoring data for Microsoft Lync Server 2013. These steps are outlined in the following checklist:"
---

# Deployment checklist for monitoring in Lync Server 2013
[]
Although monitoring is already installed and activated on each Front End server, there are still several steps that you must undertake before you can actually being to collect monitoring data for Microsoft Lync Server 2013. These steps are outlined in the following checklist:
  
|||||
|:-----|:-----|:-----|:-----|
|Phase  <br/> |Steps  <br/> |Role and group membership  <br/> |Documentation  <br/> |
|**Install prerequisite hardware and software** <br/> |Install a supported version of Microsoft SQL Server on the computer that will act as the backend data store for monitoring.  <br/> |Domain user who is also a member of the local administrators group.  <br/> |[Supported hardware for Lync Server 2013](supported-hardware.md) in the Supportability guide  <br/> [Server software and infrastructure support in Lync Server 2013](server-software-and-infrastructure-support.md) in the Supportability Guide  <br/> |
|**Create the appropriate internal topology to support monitoring** <br/> |Use Lync Server 2013 Topology Builder to add monitoring databases to the topology, then published the updated topology.  <br/> |To define a topology, a user who is a member of the local users group.  <br/> To publish the topology, a user who is a member if the domain administrators group and the RTCUniversalServerAdmins group.  <br/> |[Associating a monitoring store with a Front End pool in Lync Server 2013](associating-a-monitoring-store-with-a-front-end-pool.md) in the Deployment guide  <br/> |
|**Enable the appropriate monitoring settings** <br/> |Enable call detail recording (CDR) and/or Quality of Experience (QoE) monitoring at the global and/or the site scopes.  <br/> |A user who is a member of the RTCUniversalServerAdmins group or who has been assigned an RBAC role that provides access to the CsCdrConfiguration and CsQoEConfiguration cmdlets.  <br/> |[Configuring call detail recording and Quality of Experience settings in Lync Server 2013](configuring-call-detail-recording-and-quality-of-experience-settings.md) in the Operations guide  <br/> |
   

