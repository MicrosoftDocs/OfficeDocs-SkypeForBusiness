---
title: "Branch-site resiliency solutions in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1700f99b-709c-4e47-88eb-c0a5490e26e2
description: "There are obvious advantages to providing branch-site resiliency to your organization. Specifically, if you lose the connection to the central site, branch site users will continue to have Enterprise Voice service and voice mail (if you configure voice mail rerouting settings; for details, see Branch-site resiliency requirements for Lync Server 2013). However, for sites with fewer than 25 users, a resiliency solution may not provide a sufficient return on investment."
---

# Branch-site resiliency solutions in Lync Server 2013
[]
There are obvious advantages to providing branch-site resiliency to your organization. Specifically, if you lose the connection to the central site, branch site users will continue to have Enterprise Voice service and voice mail (if you configure voice mail rerouting settings; for details, see [Branch-site resiliency requirements for Lync Server 2013](branch-site-resiliency-requirements.md)). However, for sites with fewer than 25 users, a resiliency solution may not provide a sufficient return on investment. 
  
If you decide to provide branch-site resiliency, you have three options. The following table can help you determine the best option for your organization.
  
## 

|**If you…**|**We recommend that you use a…**|
|:-----|:-----|
|Host between 25 and 1000 users at your branch site, and if the return on investment does not support a full deployment or where local administrative support is unavailable  <br/> |Survivable Branch Appliance  <br/> The Survivable Branch Appliance is an industry-standard blade server with a Lync Server Registrar and Mediation Server running on Windows Server 2008 R2. The Survivable Branch Appliance also contains a public switched telephone network (PSTN) gateway. Qualified third-party devices (developed by Microsoft partners in the Survivable Branch Appliance (SBA) qualification/certification program) provide a continuous PSTN connection in the event of WAN failure, but this approach does not provide resilient presence and conferencing because these features depend on Front End Servers at the central site.  <br/> For details about Survivable Branch Appliances, see "Survivable Branch Appliance Details," later in this topic.  <br/> **Note:** If you decide to also use a SIP trunk with your Survivable Branch Appliance, contact your Survivable Branch Appliance vendor to learn about which service provider is best for your organization.  <br/> |
|Host between 1000 and 2000 users at your branch site, lack a resilient WAN connection, and have trained Lync Server administrators available  <br/> |Survivable Branch Server or two Survivable Branch Appliances.  <br/> The Survivable Branch Server is a Windows Server meeting specified hardware requirements that has Lync Server Registrar and Mediation Server software installed on it. It must connect to either a PSTN gateway or a SIP trunk to a telephone service provider.  <br/> For details about Survivable Branch Servers, see "Survivable Branch Server Details," later in this topic.  <br/> |
|If you require presence and conferencing features in addition to voice features for up to 5000 users, and have trained Lync Server administrators available  <br/> |Deploy as a central site with a Standard Edition server rather than as a branch site.  <br/> A full-scale Lync Server deployment provides a continuous PSTN connection and resilient presence and conferencing in the event of WAN failure.  <br/> For details about preparing for this solution, see [Organization planning for Lync Server 2013](planning-primer-planning-for-your-organization.md), [Determining your system requirements for Lync Server 2013](determining-your-system-requirements.md), [Determining your infrastructure requirements for Lync Server 2013](determining-your-infrastructure-requirements.md), and other relevant sections of the Planning documentation.  <br/> |
   
### Resiliency Topologies

The following figure shows the recommended topologies for branch-site resiliency.
  
**Branch site resiliency options**

![Voice Branch Resiliency Options](media/Plan_OCS_Voice_BranchResiliencyOptions.jpg)
  
### Survivable Branch Appliance Details

The Lync Server Survivable Branch Appliance includes the following components:
  
- A Registrar for user authentication, registration and call routing
    
- A Mediation Server for handling signaling between the Registrar and a PSTN gateway
    
- A PSTN gateway for routing calls to the PSTN as a fallback transport in the event of a WAN outage
    
- SQL Server Express for local user data storage
    
The Survivable Branch Appliance also includes PSTN trunks, analog ports, and an Ethernet adapter. 
  
If the branch site's WAN connection to a central site becomes unavailable, internal branch users continue to be registered with the Survivable Branch Appliance Registrar and obtain uninterrupted voice service by using the Survivable Branch Appliance connection to the PSTN. Branch site users who connect from home or other remote locations will be able to register with a Registrar server at a central site if the WAN link to the branch site is unavailable. These users will have full unified communications functionality, with the one exception that inbound calls to the branch site will go to voice mail. When the WAN connection becomes available, full functionality should be restored to branch site users. Neither the failover to the Survivable Branch Appliance nor the restoration of service requires the presence of an IT administrator.
  
Lync Server supports up to two Survivable Branch Appliance at a branch site. 
  
> [!NOTE]
> Users who are homed on a Lync Server Survivable Branch Appliance are unable to create new Chat Rooms or view the Room Card for existing rooms. 
  
#### Survivable Branch Appliance Deployment Overview

The Survivable Branch Appliance is manufactured by original equipment manufacturers in partnership with Microsoft and deployed on their behalf by value-added retailers. This deployment should occur only after Lync Server has been deployed at the central site, a WAN connection to the branch site is in place, and branch site users are enabled for Enterprise Voice.
  
For details about these phases, see [Deploying a Survivable Branch Appliance or Server with Lync Server 2013](deploying-a-survivable-branch-appliance-or-server.md) in the Deployment documentation. 
  
|**Phase**|**Steps**|**User Rights**|
|:-----|:-----|:-----|
|Set up Active Directory Domain Services for the Survivable Branch Appliance  <br/> |**At the central site:** <br/>  Create a domain user account (or enterprise identity) for the technician who will install and activate the Survivable Branch Appliance at the branch site.  <br/>  Create a computer account (with the applicable fully qualified domain name (FQDN)) for Survivable Branch Appliance in Active Directory Domain Services.  <br/>  In Topology Builder, create and publish the Survivable Branch Appliance.  <br/> |The technician user account must be a member of RTCUniversalSBATechnicians. The Survivable Branch Appliance must belong to the RTCSBAUniversalServices group, which happens automatically when you use Topology Builder.  <br/> |
|Install, and activate the Survivable Branch Appliance.  <br/> |**At the branch site:** <br/>  Connect the Survivable Branch Appliance to an Ethernet port and PSTN port.  <br/>  Start the Survivable Branch Appliance.  <br/>  Join the Survivable Branch Appliance to the domain, using the domain user account created for the Survivable Branch Appliance at the central site. Set the FQDN and IP address to match the FQDN created in the computer account.  <br/>  Configure the Survivable Branch Appliance using the OEM user interface.  <br/>  Test PSTN connectivity.  <br/> |The technician user account must be a member of RTCUniversalSBATechnicians.  <br/> |
   
### Survivable Branch Server Details

In Topology Builder create the branch site, add the Survivable Branch Server to that site, and then run the Lync Server Deployment Wizard on the computer where you want to install the role.
  
## See also

#### 

[Deploying Lync Server 2013](deploying-lync-server-2013.md)

