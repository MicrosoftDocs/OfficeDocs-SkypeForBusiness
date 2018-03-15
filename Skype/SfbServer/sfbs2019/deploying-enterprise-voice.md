---
title: "Deploying Enterprise Voice in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b5b593a6-ac30-461c-8c8c-0041e2c9ab04
description: "Lync Server 2013, Enterprise Voice is part of the Lync Server 2013 infrastructure."
---

# Deploying Enterprise Voice in Lync Server 2013
[]
Lync Server 2013, Enterprise Voice is part of the Lync Server 2013 infrastructure.
  
Deploying Enterprise Voice requires that you:
  
1. Review the [Planning for Enterprise Voice in Lync Server 2013](planning-for-enterprise-voice.md) section of the Planning documentation. 
    
2. Finalize plans for features and components to deploy with this workload.
    
3. Run Planning Tool to design a topology that reflects your deployment decisions.
    
4. Open the topology design in Topology Builder, as described in [Defining and configuring the topology in Lync Server 2013](defining-and-configuring-the-topology.md) in the Deployment documentation. 
    
    > [!NOTE]
    > Installation of Topology Builder is part of the deployment process for the internal pool. For details, see [Install Lync Server 2013 administrative tools](install-lync-server-administrative-tools.md) in the Deployment documentation. 
  
Additionally, you must have already deployed Lync Server, Enterprise Edition at central sites and branch sites that correspond to the reference topology that you choose to deploy. You can't deploy Enterprise Voice components until you have defined, published, and installed files for at least one internal pool, and you must use Topology Builder to define and publish an internal pool.
  
### 

To view reference topologies with examples of where Enterprise Voice server roles can be deployed (and their relationship to one another and other Lync Server 2013 server roles), see [Reference topologies in Lync Server 2013](reference-topologies.md) in the Planning documentation. 
  
To view a reference topology that illustrates and explains a sample call admission control deployment, including network regions, network sites, and subnets, see [Example: Gathering your requirements for call admission control in Lync Server 2013](example-gathering-your-organization-s-requirements-for-call-admission-control.md) in the Planning documentation. 
  
> [!IMPORTANT]
> To deploy Enterprise Voice at a central site, continue reading the topics in this section. To deploy Enterprise Voice at a branch site, skip to [Deploying branch sites in Lync Server 2013](deploying-branch-sites.md) in the Deployment documentation. 
  
This section includes procedures for deployments in which a Mediation Server is collocated on each Front End Server or Standard Edition server, as recommended, and also for deployments with a stand-alone Mediation Server pool.
  
You can skip the following content if you used Topology Builder to define and publish a topology that collocates a Mediation Server on each Front End Server or Standard Edition server, because Deployment Wizard already automatically installed the files for Mediation Server when you installed files for your Front End Server pool or Standard Edition server:
  
- [Configuring trunks in Lync Server 2013](configuring-trunks.md)
    
If you used Topology Builder to define and publish a Mediation Server in a stand-alone pool, you can use the following content:
  
- Verify that your topology meets the software and environment prerequisites, as described in [Enterprise Voice prerequisites for Lync Server 2013](enterprise-voice-prerequisites.md).
    
## In This Section

> [Enterprise Voice prerequisites for Lync Server 2013](enterprise-voice-prerequisites.md)
    
> [Deploying Mediation Servers and defining peers in Lync Server 2013](deploying-mediation-servers-and-defining-peers.md)
    
> [Configuring trunks in Lync Server 2013](configuring-trunks.md)
    
> [Configuring dial plans in Lync Server 2013](configuring-dial-plans.md)
    
> [Configuring voice policies, PSTN usage records, and voice routes in Lync Server 2013](configuring-voice-policies-pstn-usage-records-and-voice-routes.md)
    
> [Exporting and importing voice routing configuration in Lync Server 2013](exporting-and-importing-voice-routing-configuration.md)
    
> [Test voice routing in Lync Server 2013](test-voice-routing.md)
    
> [Publish pending changes to the voice routing configuration in Lync Server 2013](publish-pending-changes-to-the-voice-routing-configuration.md)
    
> [Deploying on-premises Exchange UM to provide Lync Server 2013 voice mail](deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail.md)
    
> [Providing Lync Server 2013 users voice mail on hosted Exchange UM](providing-lync-server-2013-users-voice-mail-on-hosted-exchange-um.md)
    
> [Configuring on-premises Lync Server 2013 integration with Exchange Online](configuring-on-premises-lync-server-2013-integration-with-exchange-online.md)
    
> [Deploying advanced Enterprise Voice features in Lync Server 2013](deploying-advanced-enterprise-voice-features.md)
    
    - [About network regions, sites, and subnets in Lync Server 2013](about-network-regions-sites-and-subnets.md)
    
    - [Create or modify a network region in Lync Server 2013](create-or-modify-a-network-region.md)
    
    - [Create or modify a network site in Lync Server 2013](create-or-modify-a-network-site.md)
    
    - [Associate a subnet with a network site in Lync Server 2013](associate-a-subnet-with-a-network-site.md)
    
    - [Configure call admission control in Lync Server 2013](configure-call-admission-control.md)
    
    - [Configure Enhanced 9-1-1 in Lync Server 2013](configure-enhanced-9-1-1.md)
    
    - [Configure media bypass in Lync Server 2013](configure-media-bypass.md)
    
> [Enable users for Enterprise Voice in Lync Server 2013](enable-users-for-enterprise-voice.md)
    
## See also

#### 

[Deploying branch sites in Lync Server 2013](deploying-branch-sites.md)
  
[Configuring dial-in conferencing in Lync Server 2013](configuring-dial-in-conferencing.md)
  
[Configuring Call Park in Lync Server 2013](configuring-call-park.md)
  
[Configuring announcements for unassigned numbers in Lync Server 2013](configuring-announcements-for-unassigned-numbers.md)
  
[Deploying monitoring in Lync Server 2013](deploying-monitoring.md)

