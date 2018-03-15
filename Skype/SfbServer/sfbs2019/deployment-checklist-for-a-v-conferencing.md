---
title: "Deployment checklist for A/V conferencing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6d47426f-6559-407b-9ac1-2453f0b7a2a2

description: "As with deployment of your other Lync Server 2013 components, deployment of A/V conferencing requires that you use Topology Builder to create and publish a topology that incorporates conferencing."
---

# Deployment checklist for A/V conferencing in Lync Server 2013
[]
As with deployment of your other Lync Server 2013 components, deployment of A/V conferencing requires that you use Topology Builder to create and publish a topology that incorporates conferencing.
  
## Deployment Sequence

You can deploy conferencing at the same time that you deploy your initial topology or after you have deployed at least one Front End pool or Standard Edition server.
  
## Conferencing Deployment Process

The following table provides an overview of the steps required to deploy conferencing into an existing topology.
  
|**Phase**|**Steps**|**Roles and group memberships**|**Documentation**|
|:-----|:-----|:-----|:-----|
|**Install prerequisite hardware and software** <br/> |Conferencing runs on Front End Servers of a Front End pool and Standard Edition servers. It has no additional hardware or software requirements beyond what is required to install those servers.  <br/> > [!NOTE]> Lync Server 2013 uses Office Web Apps and the Office Web Apps Server to handle sharing and rendering of PowerPoint presentations. For details about installing and configuring the Office Web Apps Server, see [Configuring integration with Office Web Apps Server and Lync Server 2013](enabling-office-web-apps-server-and-lync-server-2013.md).           |Domain user who is a member of the local Administrators group  <br/> |[Supported hardware for Lync Server 2013](supported-hardware.md) in the Supportability documentation  <br/> [Server software and infrastructure support in Lync Server 2013](server-software-and-infrastructure-support.md) in the Supportability documentation  <br/> [Determining your system requirements for Lync Server 2013](determining-your-system-requirements.md) in the Planning documentation.  <br/> [Technical requirements for Archiving in Lync Server 2013](technical-requirements-for-archiving.md) in the Planning documentation.  <br/> |
|**Create the appropriate internal topology to support conferencing** <br/> |Run Topology Builder to add conferencing to the topology, and then publish the topology.  <br/> |To define a topology, an account that is a member of the local Users group  <br/> To publish the topology, an account that is a member of the Domain Admins group and RTCUniversalServerAdmins group, and that has full control permissions (read/write/modify) on the file share to be used for the Lync Server 2013 file store (so that Topology Builder can configure the required DACLs)  <br/> |[Define and configure a topology in Topology Builder for Lync Server 2013](define-and-configure-a-topology-in-topology-builder.md) in the Deployment documentation.  <br/> |
|**Configure conferencing policies and support** <br/> |Use the Lync Server 2013 Control Panel or Lync Server Management Shell to configure conferencing settings.  <br/> |RTCUniversalServerAdmins group (Windows PowerShell only) or assign users to the [] or CSAdministrator role  <br/> |[Conferencing policies in Lync Server 2013](conferencing-policies.md) in the Operations documentation.  <br/> |
   
## See also

#### 

[Overview of conferencing in Lync Server 2013](overview-of-conferencing.md)
  
[Defining your requirements for conferencing in Lync Server 2013](defining-your-requirements-for-conferencing.md)

