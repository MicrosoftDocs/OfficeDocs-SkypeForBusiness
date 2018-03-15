---
title: "Deployment checklist for Archiving in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7479734d-be01-40d9-ad82-320a09d19d04

description: "In this articleDeployment SequenceArchiving Deployment ProcessDeploying Lync Server and Microsoft Exchange in Different Forests"
---

# Deployment checklist for Archiving in Lync Server 2013
[]
 **In this article**
  
[Deployment Sequence](#sectionSection0)
  
[Archiving Deployment Process](#sectionSection1)
  
[Deploying Lync Server and Microsoft Exchange in Different Forests](#sectionSection2)
  
Archiving is automatically installed on each Front End Server in your Lync Server 2013 deployment, but you still need to set it up before you can use it. The steps required to set it up, as summarized in this section, constitute the deployment of Archiving.
  
## Deployment Sequence
<a name="sectionSection0"> </a>

How you set up Archiving depends on which storage option you choose: 
  
- If you use Microsoft Exchange integration for all users in your deployment, you don't need to configure Lync Server 2013 Archiving policies for your users. Instead, configure your Exchange In-Place Hold policies to support archiving for users homed on Exchange 2013, with their mailboxes put on In-Place Hold. For details about configuring these policies, see the Exchange 2013 product documentation.
    
- If you do not use Microsoft Exchange integration for all users in your deployment, you need to add Lync Server Archiving databases (SQL Server databases) to your topology and then publish it, as well as configure policies and settings for your users, before you can archive data for those users. You can deploy Archiving databases at the same time that you deploy your initial topology or after you have deployed at least one Front End pool or Standard Edition server. This document describes how to deploy Archiving databases by adding them to an existing deployment.
    
If you enable archiving in one Front End pool or Standard Edition server, you should enable it for all other Front End pools and Standard Edition servers in your deployment. This is because users whose communications are required to be archived can be invited to a group IM conversation or meetings hosted on a different pool. If archiving is not enabled on the pool where the conversation or meeting is hosted, the complete session may not be archived. In these cases, IMs with archiving-enabled users still can be archived, but not for conferencing content files, and conference join or leave events.
  
> [!IMPORTANT]
> If archiving is critical in your organization for compliance reasons, be sure to deploy Archiving, configure policies and other options at the appropriate level, and enable it for all appropriate users, before you enable those users for Lync Server 2013. 
  
## Archiving Deployment Process
<a name="sectionSection1"> </a>

The following table provides an overview of the steps required to deploy archiving in an existing topology.
  
|**Phase**|**Steps**|**Roles and group memberships**|**Documentation**|
|:-----|:-----|:-----|:-----|
|**Install prerequisite hardware and software** <br/> | To use Microsoft Exchange integration (using Exchange 2013 for archiving storage for some or all users), you need an existing Exchange 2013 deployment.  <br/>  To use separate Archiving databases (using SQL Server databases) for archiving storage for some or all users, SQL Server on the server that will store archiving data.  <br/> > [!NOTE]>  Archiving runs on Front End Servers of an Enterprise pool and Standard Edition servers. It has no additional hardware or software requirements beyond what is required to install those servers.           |Domain user who is a member of the local administrators group.  <br/> |[Supported hardware for Lync Server 2013](supported-hardware.md) in the Supportability documentation.  <br/> [Server software and infrastructure support in Lync Server 2013](server-software-and-infrastructure-support.md) in the Supportability documentation.  <br/> [Technical requirements for Archiving in Lync Server 2013](technical-requirements-for-archiving.md) in the Planning documentation.  <br/> [Setting up systems and infrastructure for Archiving in Lync Server 2013](setting-up-systems-and-infrastructure-for-archiving.md) in the Deployment documentation.  <br/> [Exchange and SharePoint integration support in Lync Server 2013](exchange-and-sharepoint-integration-support.md) in the Supportability documentation.  <br/> |
|**Create the appropriate internal topology to support archiving (only if not using Microsoft Exchange integration for all users in your deployment)** <br/> |Run Topology Builder to add Lync Server 2013 Archiving databases (SQL Server databases) to the topology, and then publish the topology.  <br/> |To define a topology to incorporate Archiving databases, an account that is a member of the local users group.  <br/> To publish the topology, an account that is a member of the domain admins group and RTCUniversalServerAdmins group, and that has full control permissions (read/write/modify) on the file share to be used for the Lync Server 2013 file store (so that Topology Builder can configure the required DACLs).  <br/> |[Adding Archiving databases to an existing Lync Server 2013 Deployment](adding-archiving-databases-to-an-existing-lync-server-2013-deployment.md) in the Deployment documentation.  <br/> |
|**Configure server-to-server authentication (only if using Microsoft Exchange integration)** <br/> |Configure servers to enable authentication between Lync Server 2013 and Exchange 2013. We recommend running **Test-CsExchangeStorageConnectivity testuser_sipUri -Folder Dumpster** to validate Exchange Archiving storage connectivity before enabling archiving.  <br/> |An account with the appropriate permissions for managing certificates on the servers.  <br/> |[Managing server-to-server authentication (OAuth) and partner applications in Lync Server 2013](managing-server-to-server-authentication-oauth-and-partner-applications.md) in the Deployment documentation or the Operations documentation.  <br/> |
|**Configure archiving policies and configurations** <br/> |Configure archiving, including whether to use Microsoft Exchange integration, the global policy and any site and user policies (when not using Microsoft Exchange integration for all data storage), and specific archiving options, such as critical mode and data export and purging.  <br/> If using Microsoft Exchange integration, configure Exchange In-Place Hold policies as appropriate.  <br/> |RTCUniversalServerAdmins group (Windows PowerShell only) or assign users to the CSArchivingAdministrator or CSAdministrator role.  <br/> |[Configuring support for Archiving in Lync Server 2013](configuring-support-for-archiving.md) in the Deployment documentation.  <br/> Exchange product documentation (if using Microsoft Exchange integration).  <br/> |
   
## Deploying Lync Server and Microsoft Exchange in Different Forests
<a name="sectionSection2"> </a>

If Microsoft Exchange Server is not deployed in the same forest as Lync Server, you must make sure that the following Exchange Active Directory attributes are synchronized to the forest where Lync Server is deployed:
  
1. msExchUserHoldPolicies
    
2. proxyAddresses
    
This is a multi-value attribute. When synchronizing this attribute, you need to merge the values, not replace them to ensure the existing values are not lost.
  

