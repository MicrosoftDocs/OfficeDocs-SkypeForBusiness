---
title: "Open Lync Server 2013 administrative tools"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8c58de94-9e0a-4368-9e14-9afcaa1142d0
description: "In this articleDeployment WizardTopology BuilderLync Server 2013 Control PanelLync Server 2013 Management Shell"
---

# Open Lync Server 2013 administrative tools
[]
 **In this article**
  
[Deployment Wizard](#BKMK_OpenDeploymentWizard)
  
[Topology Builder](#BKMK_OpenTopologyBuilder)
  
[Lync Server 2013 Control Panel](#BKMK_OpenControlPanel)
  
[Lync Server 2013 Management Shell](#BKMK_OpenManagementShell)
  
You can use the procedures in this topic to open administrative tools to deploy, configure, or troubleshoot your Lync Server 2013 topology.
  
- [Deployment Wizard](open-lync-server-administrative-tools.md#BKMK_OpenDeploymentWizard)
    
- [Topology Builder](open-lync-server-administrative-tools.md#BKMK_OpenTopologyBuilder)
    
- [Lync Server 2013 Control Panel](open-lync-server-administrative-tools.md#BKMK_OpenControlPanel)
    
- [Lync Server 2013 Management Shell](open-lync-server-administrative-tools.md#BKMK_OpenManagementShell)
    
## Deployment Wizard
<a name="BKMK_OpenDeploymentWizard"> </a>

Use the following procedure to start the Deployment Wizard locally to add or remove Lync Server 2013 component files.
  
### To start Lync Server 2013 Deployment Wizard

1. Log on to the computer where the Lync Server Deployment Wizard is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.
    
2. Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Deployment Wizard**.
    
## Topology Builder
<a name="BKMK_OpenTopologyBuilder"> </a>

Use the following procedure to open the Topology Builder to define the servers that you want to deploy in your Lync Server 2013 topology.
  
### To open Lync Server 2013 Topology Builder to design the topology

1. Log on to the computer where Topology Builder is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.
    
    > [!NOTE]
    > You can define a topology by using an account that is a member of the local Users group, but to read, publish, or enable a topology, which is required to install Lync Server 2013 on a server, you must use an account that is a member of the Domain Admins group and the RTCUniversalServerAdmins group, and that has full control permissions (that is, read, write, and modify) on the file share that you are going to use for the archiving file store so that Topology Builder can configure the required discretionary access control list (DACLs), or an account with equivalent user rights. 
  
2. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
## Lync Server 2013 Control Panel
<a name="BKMK_OpenControlPanel"> </a>

Use one of the following procedures to open Lync Server 2013 Control Panel to manage the configuration of servers, users, clients, and devices in your environment.
  
> [!NOTE]
> You can use a user account that is assigned to the CsAdministrator role to perform any task in Lync Server 2013 Control Panel. You can use other roles to log on to Lync Server 2013 Control Panel to perform specific administration tasks, dependent on the task you need to perform. For example, you can use CSArchivingAdministrator to administer Archiving in Lync Server 2013 Control Panel. For details about roles, see [Planning for role-based access control in Lync Server 2013](planning-for-role-based-access-control-rbac.md) in the Planning documentation. For details about the roles that you can use to perform a specific task, see the documentation for the task. 
  
### To open Lync Server 2013 Control Panel from any computer inside your organization's firewall

1. From a user account that is assigned to the CsAdministrator role or other role that has appropriate user rights and permissions for the task to be performed, log on to any computer in your internal deployment with a minimum screen resolution of 1024 x 768.
    
    > [!IMPORTANT]
    > If you have configured an administration simple uniform resource locator (URL), you can access Lync Server 2013 Control Panel from an Internet browser that is running on any computer within your organization's firewall. For details about configuring the administration simple URL, see [Planning for simple URLs in Lync Server 2013](planning-for-simple-urls.md) in the Planning documentation and [Edit or configure simple URLs in Lync Server 2013](edit-or-configure-simple-urls.md) in the Deployment documentation. 
  
2. Open a browser window, and then enter the Admin URL configured for your organization.
    
### To open Lync Server 2013 Control Panel on a computer running Lync Server 2013

1. From a user account that is a member of the CsAdministrator role or other role that has appropriate user rights and permissions for the task to be performed, log on to a computer on which you have installed Lync Server 2013 or, at a minimum, the Lync Server 2013 administrative tools. To configure settings, the computer must have a minimum screen resolution of 1024 x 768.
    
2. Start Lync Server 2013 Control Panel: Click **Start**, click **All Programs**, point to **Administrative Tools**, point to **Microsoft Lync Server 2013**, and then click **Lync Server 2013 Control Panel**.
    
## Lync Server 2013 Management Shell
<a name="BKMK_OpenManagementShell"> </a>

Use the following procedure to open Lync Server 2013 Management Shell to administer servers, users, clients, and devices in your environment by using the command line.
  
> [!NOTE]
> You can use a user account that is assigned to the CsAdministrator role to perform any task in Lync Server 2013 Management Shell. You can log on using other roles to perform specific administration tasks, depending on the task you need to perform. For example, you can use CSArchivingAdministrator to run cmdlets related to Archiving administration. For details about roles, see [Planning for role-based access control in Lync Server 2013](planning-for-role-based-access-control-rbac.md) in the Planning documentation. For details about the roles that you can use to run a specific cmdlet, see the documentation for the cmdlet. > You can also run certain cmdlets by using a user account in the RTCUniversalServerAdmins, RTCUniversalUserAdmins, or RTCUniversalReadOnlyAdmins groups, depending on the cmdlet. 
  
### To open the Lync Server 2013 Management Shell

- If you open a Windows PowerShell window rather than the Lync Server 2013 Management Shell, by default you cannot run the Lync Server 2013 cmdlets. To run the Lync Server 2013 cmdlets from within Windows PowerShell, type the following at the Windows PowerShell command prompt:
    
     `Import-Module Lync`
    
- Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
## See also
<a name="BKMK_OpenManagementShell"> </a>

#### 

[Install Lync Server 2013 administrative tools](install-lync-server-administrative-tools.md)
#### 

[Lync Server 2013 administrative tools](lync-server-administrative-tools.md)

