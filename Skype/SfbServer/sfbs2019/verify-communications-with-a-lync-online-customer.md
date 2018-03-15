---
title: "Verify communications with a Lync Online customer in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c8287b15-e1bb-4b26-8354-0ec90b2fcfe7
description: "To enable Lync users in your organization to communicate with users of a Microsoft Lync Online 2010 customer, you must have completed the following steps:"
---

# Verify communications with a Lync Online customer in Lync Server 2013
[]
To enable Lync users in your organization to communicate with users of a Microsoft Lync Online 2010 customer, you must have completed the following steps:
  
- Met all prerequisites. This includes deploying your internal and edge servers, enabling federation support for your organization, and setting up user accounts. For details, see [Prerequisites for federating with a Lync Online customer in Lync Server 2013](prerequisites-for-federating-with-a-lync-online-customer.md).
    
- Configured domain access support in your internal deployment. This includes creating a host provider entry and configuring your deployment to allow access from the Lync Online customer's domain. For details, see [Configure federation support for a Lync Online domain in Lync Server 2013](configure-federation-support-for-a-lync-online-domain.md).
    
- Configured your user accounts to support federation. For details, see [Configure user access for federation with a Lync Online customer in Lync Server 2013](configure-user-access-for-federation-with-a-lync-online-customer.md).
    
After you complete all of these steps and the administrator of the Lync Online 2010 customer completes all configuration of their online services to support federation with your organization, verify communications by testing communications between an internal user in your organization and a user of the Lync Online customer. If communication is not successful, use the Logging Tool from your Edge Server to capture log and trace files in order to troubleshoot the problem. For details about using the Logging Tool, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md) in the Operations documentation. For details about the Logging Tool, see the Lync Server 2010 Logging Tool documentation on the TechNet Library at [https://go.microsoft.com/fwlink/p/?linkId=199265](https://go.microsoft.com/fwlink/p/?linkId=199265).
  

