---
title: "Configure call admission control in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ce3e6e71-1e33-4cff-849a-c0468e61fef6
description: "Call admission control (CAC) is a solution that determines whether a real-time session can be established based on the available bandwidth to help prevent poor audio/video quality for users on congested networks. CAC controls real-time traffic only for audio and video, and does not affect data traffic. CAC may route the call through an Internet path when the default WAN path does not have the required bandwidth. For details, see Planning for call admission control in Lync Server 2013 in the Planning documentation."
---

# Configure call admission control in Lync Server 2013
[]
Call admission control (CAC) is a solution that determines whether a real-time session can be established based on the available bandwidth to help prevent poor audio/video quality for users on congested networks. CAC controls real-time traffic only for audio and video, and does not affect data traffic. CAC may route the call through an Internet path when the default WAN path does not have the required bandwidth. For details, see [Planning for call admission control in Lync Server 2013](planning-for-call-admission-control-cac.md) in the Planning documentation. 
  
This section provides a set of example procedures that illustrate how to deploy and manage CAC in your network.
  
> [!IMPORTANT]
> Before you deploy CAC, you must gather all of the required information for your enterprise network topology, as described in [Example: Gathering your requirements for call admission control in Lync Server 2013](example-gathering-your-organization-s-requirements-for-call-admission-control.md) in the Planning documentation. Also be sure that CAC components have been installed and activated, as described in [Define and configure a Front End pool or Standard Edition server in Lync Server 2013](define-and-configure-a-front-end-pool-or-standard-edition-server.md) in the Deployment documentation. 
  
> [!NOTE]
> All CAC deployment and management examples in this section are performed by using the Lync Server Management Shell. As an alternative, you can also use the **Network Configuration** section of Lync Server Control Panel to manage CAC. 
  
## In this section

- [Configure network regions for CAC in Lync Server 2013](configure-network-regions-for-cac.md)
    
- [Create bandwidth policy profiles in Lync Server 2013](create-bandwidth-policy-profiles.md)
    
- [Configure network sites for CAC in Lync Server 2013](configure-network-sites-for-cac.md)
    
- [Associate subnets with network sites for CAC in Lync Server 2013](associate-subnets-with-network-sites-for-cac.md)
    
- [Create network region links in Lync Server 2013](create-network-region-links.md)
    
- [Create network interregion routes in Lync Server 2013](create-network-interregion-routes.md)
    
- [Create network intersite policies in Lync Server 2013](create-network-intersite-policies.md)
    
- [Enable call admission control in Lync Server 2013](enable-call-admission-control.md)
    
- [Call admission control deployment checklist for Lync Server 2013](call-admission-control-deployment-checklist.md)
    

