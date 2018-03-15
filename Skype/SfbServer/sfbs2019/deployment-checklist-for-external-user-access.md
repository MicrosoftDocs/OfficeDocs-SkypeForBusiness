---
title: "Deployment checklist for external user access in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3f55f502-88a0-4315-8783-45a32a0b78ea

description: "Before you deploy your perimeter network and implement support for external users, you must already have deployed your Microsoft Lync Server 2013 internal servers, including a Front End pool or a Standard Edition server. If you plan to deploy the optional Directors in your internal network, you should also deploy them prior to deploying Edge Servers. For details about the Director deployment process, see Scenarios for the Director in Lync Server 2013 in the Planning documentation."
---

# Deployment checklist for external user access in Lync Server 2013
[]
Before you deploy your perimeter network and implement support for external users, you must already have deployed your Microsoft Lync Server 2013 internal servers, including a Front End pool or a Standard Edition server. If you plan to deploy the optional Directors in your internal network, you should also deploy them prior to deploying Edge Servers. For details about the Director deployment process, see [Scenarios for the Director in Lync Server 2013](scenarios-for-the-director.md) in the Planning documentation. 
  
Microsoft Lync Server 2013 includes tools to facilitate planning and deployment of both internal servers and Edge Servers. After the topology is completed, publish the resulting topology definition to your production environment. To do this, you must be a member of the **Domain Admins** group and the **RTCUniversalServerAdmins** group. 
  
- **Planning Tool** Office Communications Server 2007 R2 included a Planning Tool and an Edge Planning Tool that you could use to help guide topology design. In Lync Server 2010, these two tools were combined into a single Planning Tool that has additional features and functionality, such as collecting planned user count, voice requirements, external user access types, and federation options. Additionally, you can plan your infrastructure's network parameters, such as IP addresses, load balancer types and other perimeter network considerations. 
    
- **Topology Builder** Lync Server 2013 Topology Builder helps you define your topology and components. Topology Builder is essential to deploying servers running Lync Server 2013. Topology Builder publishes the results to a Central Management store that is used to configure all of the servers running Lync Server 2013 in your organization. You cannot install Lync Server 2013 on servers without using Topology Builder. 
    
If you designed your edge topology during your planning process, including running Topology Builder to define your edge topology, you can use those results to start your Edge Server deployment. If you did not finish building your edge topology earlier or you want to change the information you previously specified, you must finish running Topology Builder before proceeding with other deployment steps. For details about how to build your topology, see [Scenarios for external user access in Lync Server 2013](scenarios-for-external-user-access.md).
  
For details about the Planning Tool and Topology Builder, see [Beginning the planning process for Lync Server 2013](beginning-the-planning-process.md) in the Planning documentation. 
  
The following table provides an overview of the Edge Server deployment process. To review the planning decisions that must be made before deploying external user access, see [Scenarios for external user access in Lync Server 2013](scenarios-for-external-user-access.md).
  
> [!CAUTION]
> The information in the following table focuses on a new deployment. If you have deployed Edge Servers in a Lync Server 2010, Office Communications Server 2007 R2 or Office Communications Server 2007 environment, see the [Migration](migration.md) for details about migrating to Lync Server 2013. Migration is not supported from any version prior to Office Communications Server 2007 R2, including Office Communications Server 2007, Live Communications Server 2005, and Live Communications Server 2003. 
  
To enhance Edge Server performance and security, and to facilitate deployment, apply the following best practices when you deploy your perimeter network and Edge Servers:
  
- Deploy Edge Servers only after you have tested and verified operation of Lync Server 2013 inside your organization.
    
- We recommend that you deploy Edge Servers in a workgroup rather than a domain. Doing so simplifies installation and keeps Active Directory Domain Services (AD DS) out of the perimeter network. Locating AD DS in the perimeter network can present a significant security risk.
    
- Joining an Edge Server to a domain located entirely in the perimeter network is supported but not recommended. An Edge Server as part of the internal domain violates trusted network boundaries, where the Internet is least trusted, perimeter network is more trusted than the Internet, and the internal network is most trusted. An Edge server as a member of the domain is automatically a part of the most trusted network, but resides in a less trusted network (the perimeter).
    
## Deployment Process for Edge Servers

****

|**Phase**|**Steps**|**Permissions**|**Documentation**|
|:-----|:-----|:-----|:-----|
|Create the appropriate edge topology and determine the appropriate components.  <br/> | Run Topology Builder to configure Edge Server settings and create and publish the topology, and then use Lync Server Management Shell to export the topology configuration file.  <br/> |**Domain Admins** group and **RTCUniversalServerAdmins** or **CsAdmins** group  <br/> > [!NOTE]> You can define a topology using an account that is a member of the local users group, but publishing a topology requires an account that is a member of the **Domain Admins** group and the **RTCUniversalServerAdmins** group.           |[Building an edge and Director topology in Lync Server 2013](building-an-edge-and-director-topology.md) in the Deployment documentation  <br/> |
|Prepare for setup.  <br/> |
Ensure that system prerequisites are met. Configure IP addresses (IPv4 and IPv6, if used) for both internal and public facing network interfaces on each Edge Server. Configure internal and external DNS records (host A and AAAA for IPv4 and IPv6), including configuring the DNS suffix on the computer to be deployed as an Edge Server. (Optional) Create and install public certificates. The time required to obtain certificates depends on which certification authority (CA) issues the certificate. If you do not perform this step at this point, you must do it during Edge Server installation. The Edge Server services cannot be started until certificates are obtained and installed. Provision support for public IM connectivity, if your deployment is to support communications with Windows Live, AOL, or Yahoo! users. Important As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License ("PIC USL") is no longer available for purchase for new or renewing agreements.  Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shut down date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see Support for public instant messenger connectivity in Lync Server 2013.   The PIC USL is a per-user per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger.  Microsoft's ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which is winding down.   More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world.  Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL.  Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people with IM and voice.  Provision support for XMPP and federation support for Office Communications Server 2007, Office Communications Server 2007 R2, Lync Server 2010 partners, if your deployment will use these Configure firewalls. |As appropriate to your organization  <br/> |[Preparing for installation of servers in the perimeter network for Lync Server 2013](preparing-for-installation-of-servers-in-the-perimeter-network.md) in the Deployment documentation  <br/> |
|Set up reverse proxy.  <br/> | Set up the reverse proxy (for example, for Microsoft Forefront Threat Management Gateway 2010 or Microsoft Internet Security and Acceleration (ISA) Server with Service Pack 1) in the perimeter network, obtain the necessary public certificates, and configure the web publishing rules on the reverse proxy server.  <br/>  Prepare the reverse proxy for Mobility services if you have planned for Mobility and are deploying the Mobility services on the Front End pool or Standard Edition server.  <br/> |**Administrators** group or Reverse Proxy administrator  <br/> |[Setting up reverse proxy servers for Lync Server 2013](setting-up-reverse-proxy-servers.md) in the Deployment documentation  <br/> |
|Setup a Director (optional).  <br/> | (Optional) Install and configure one or more Directors in the internal network.  <br/> |**Administrators** group  <br/> |[Setting up the Director in Lync Server 2013](setting-up-the-director.md) in the Deployment documentation  <br/> |
|Set up Edge Servers.  <br/> |
Install prerequisite software. Transport the exported topology configuration file to each Edge Server. Install the Lync Server 2013 software on each Edge Server. Configure the Edge Servers. Request and install certificates for each Edge Server. Start the Edge Server services. |**Administrators** group  <br/> |[Setting up Edge Servers in Lync Server 2013](setting-up-edge-servers.md) in the Deployment documentation  <br/> |
|Configure deployment for external user access.  <br/> |
 Use the  Lync Server Control Panel to configure support for each of the following (as applicable):    Media relay   Federation route   Remote user access   Federation with Lync Server, Office Communications Server and Live Communications Server   Public IM connectivity   XMPP federation   Anonymous users  Configure user accounts for remote user access, federation, public IM connectivity, XMPP and anonymous user support (as applicable) |**RTCUniversalServerAdmins** group or user account that is assigned to the **CSAdministrator** role  <br/> |[Configuring support for external user access in Lync Server 2013](configuring-support-for-external-user-access.md) in the Deployment documentation  <br/> |
|Verify your Edge Server configuration.  <br/> |
Verify server connectivity and replication of configuration data from internal servers. Verify that external users can connect, including remote users, users in federated domains, public IM users, and anonymous users, as appropriate to your deployment. Verify configuration and communication using the Lync Server Remote Connectivity Analyzer https://www.testocsconnectivity.comTroubleshoot configuration and communication difficulties |For verification of replication, **RTCUniversalServerAdmins** group or user account that is assigned to the **CSAdministrator** role  <br/> For verification of user connectivity, a user for each type of external user access that you support  <br/> Remote users  <br/> |[Verifying your edge deployment in Lync Server 2013](verifying-your-edge-deployment.md) in the Deployment documentation  <br/> |
   

