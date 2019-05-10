---
title: "Add Front End Server Collocations 2010"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddFrontEndCollocationsPage2010
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 4d328bf4-85bc-4870-8d6f-008c0e46520e
description: "For an Enterprise Edition deployment, you can collocate either the A/V Conferencing service, the Mediation Server, or both on the Front End pool, or you can deploy each as stand-alone servers. For a Standard Edition server deployment, the A/V Conferencing service is always collocated if conferencing is enabled."
---

# Add Front End Server Collocations 2010

For an Enterprise Edition deployment, you can collocate either the A/V Conferencing service, the Mediation Server, or both on the Front End pool, or you can deploy each as stand-alone servers. For a Standard Edition server deployment, the A/V Conferencing service is always collocated if conferencing is enabled.

> [!NOTE]
> An A/V Conferencing service is required if **Conferencing** was selected on the **Select features** page. An Enterprise Edition Front End pool may use a collocated A/V Conferencing service or a stand-alone A/V conferencing pool. If Conferencing was not selected, the Collocate A/V Conferencing service will not be available.

You can collocate the Mediation Server role on a Standard Edition Front End Server or Enterprise Edition Front End pool. If you deploy Direct SIP connections to a qualified public switched telephone network (PSTN) gateway that supports media bypass and Domain Name System (DNS) load balancing, a stand-alone Mediation Server pool is not necessary. A stand-alone Mediation Server pool is not necessary because qualified gateways are capable of DNS load balancing to a pool of Mediation Servers and they can receive traffic from any Mediation Server in a pool. We also recommend that you collocate the Mediation Server on a Front End pool when you have deployed IP-PBXs or connect to an Internet Telephony Server Provider's Session Border Controller (SBC), as long as any of the following conditions are met:

- The IP-PBX or SBC is configured to receive traffic from any Mediation Server in the pool and can route traffic uniformly to all Mediation Servers in the pool.

- The IP-PBX or SBC is configured to receive traffic from any Mediation Server in the pool and can route traffic uniformly to all Mediation Servers in the pool.

You can use the Microsoft Lync Server 2013, Planning Tool to evaluate whether the Front End pool where you want to collocate the Mediation Server can handle the load. If your environment cannot meet these requirements, then you must deploy a stand-alone Mediation Server pool.

In general, collocation of A/V Conferencing Server or Mediation Server is not recommended if your organization has high availability and scalability requirementsFor details about collocating these server roles in a Front End pool in an Enterprise Edition deployment, see [Define and Configure a Front End Pool](https://technet.microsoft.com/library/713fc263-23dd-414a-b001-82932e4fe966.aspx) in the Deployment documentation. For details about the A/V Conferencing feature and components, see [Planning for Conferencing](https://technet.microsoft.com/library/983a272a-e1b3-4d70-8f84-836b092fe526.aspx) in the Planning documentation. For details about Enterprise Voice features and components, including Mediation Server, see [Plan for Enterprise Voice in Skype for Business Server 2015](../../plan-your-deployment/enterprise-voice-solution/enterprise-voice.md) in the Planning documentation.


