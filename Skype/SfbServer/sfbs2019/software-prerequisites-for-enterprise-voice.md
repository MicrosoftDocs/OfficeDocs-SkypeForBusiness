---
title: "Software prerequisites for Enterprise Voice in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 41172119-9631-46c7-9d9f-386d951c650b
description: "Verify that the infrastructure in which you intend to deploy Enterprise Voice meets the following software prerequisites:"
---

# Software prerequisites for Enterprise Voice in Lync Server 2013
[]
Verify that the infrastructure in which you intend to deploy Enterprise Voice meets the following software prerequisites:
  
-  Lync Server 2013 Standard Edition or Enterprise Edition is installed and operational on your network. 
    
- All Edge Servers are deployed and operational in your perimeter network, including Edge Servers running Access Edge service, A/V Edge service, Web Conferencing Edge service, and a reverse proxy.
    
- Either Microsoft Exchange Server 2007 Service Pack 3 (SP3), Microsoft Exchange Server 2010 or Microsoft Exchange Server 2013 is required for integrating Exchange Unified Messaging with Lync Server and to provide rich notifications and call log information to the Lync endpoints.
    
- One or more users have been created and enabled for Lync Server.
    
- Lync clients and devices have been successfully deployed.
    
- Topology Builder is installed on a server on your network.
    
## Next Steps: Verify Security and Configuration Prerequisites

After verifying software prerequisites for Enterprise Voice, you can use the documentation to continue preparing for deploying Enterprise Voice:
  
1. Verify security, user configuration, and hardware perquisites, as described in [Security and configuration prerequisites for Enterprise Voice in Lync Server 2013](security-and-configuration-prerequisites-for-enterprise-voice.md).
    
2. Install the Mediation Server, as described in [Install the files for Mediation Server in Lync Server 2013](install-the-files-for-mediation-server.md), but only if you want to deploy a stand-alone Mediation Server or pool because Mediation Servers are installed as part of the Front End pool or Standard Edition server deployment process when collocated. 
    
3. Configure trunk connections to provide PSTN connectivity for users, as described in [Configuring trunks in Lync Server 2013](configuring-trunks.md).
    

