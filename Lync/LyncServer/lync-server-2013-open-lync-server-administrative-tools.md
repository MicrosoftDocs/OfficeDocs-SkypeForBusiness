---
title: 'Lync Server 2013: Open Lync Server administrative tools'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Open Lync Server administrative tools
ms:assetid: 8c58de94-9e0a-4368-9e14-9afcaa1142d0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg195741(v=OCS.15)
ms:contentKeyID: 48184778
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Open Lync Server 2013 administrative tools

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-28_

You can use the procedures in this topic to open administrative tools to deploy, configure, or troubleshoot your Lync Server 2013 topology.

  - Deployment Wizard

  - Topology Builder

  - Lync Server Control Panel

  - Lync Server Management Shell

<span id="BKMK_OpenDeploymentWizard"></span>

<div>

## Deployment Wizard

Use the following procedure to start the Deployment Wizard locally to add or remove Lync Server 2013 component files.

<div>

## To start Lync Server 2013 Deployment Wizard

1.  Log on to the computer where the Lync Server Deployment Wizard is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.

2.  Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Deployment Wizard**.

</div>

</div>

<span id="BKMK_OpenTopologyBuilder"></span>

<div>

## Topology Builder

Use the following procedure to open the Topology Builder to define the servers that you want to deploy in your Lync Server 2013 topology.

<div>

## To open Lync Server 2013 Topology Builder to design the topology

1.  Log on to the computer where Topology Builder is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.
    
    <div>
    

    > [!NOTE]  
    > You can define a topology by using an account that is a member of the local Users group, but to read, publish, or enable a topology, which is required to install Lync Server 2013 on a server, you must use an account that is a member of the Domain Admins group and the RTCUniversalServerAdmins group, and that has full control permissions (that is, read, write, and modify) on the file share that you are going to use for the archiving file store so that Topology Builder can configure the required discretionary access control list (DACLs), or an account with equivalent user rights.

    
    </div>

2.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

</div>

</div>

<span id="BKMK_OpenControlPanel"></span>

<div>

## Lync Server 2013 Control Panel

Use one of the following procedures to open Lync Server 2013 Control Panel to manage the configuration of servers, users, clients, and devices in your environment.

<div>


> [!NOTE]  
> You can use a user account that is assigned to the CsAdministrator role to perform any task in Lync Server 2013 Control Panel. You can use other roles to log on to Lync Server 2013 Control Panel to perform specific administration tasks, dependent on the task you need to perform. For example, you can use CSArchivingAdministrator to administer Archiving in Lync Server 2013 Control Panel. For details about roles, see <A href="lync-server-2013-planning-for-role-based-access-control.md">Planning for role-based access control in Lync Server 2013</A> in the Planning documentation. For details about the roles that you can use to perform a specific task, see the documentation for the task.



</div>

<div>

## To open Lync Server 2013 Control Panel from any computer inside your organization’s firewall

1.  From a user account that is assigned to the CsAdministrator role or other role that has appropriate user rights and permissions for the task to be performed, log on to any computer in your internal deployment with a minimum screen resolution of 1024 x 768.
    
    <div>
    

    > [!IMPORTANT]  
    > If you have configured an administration simple uniform resource locator (URL), you can access Lync Server 2013 Control Panel from an Internet browser that is running on any computer within your organization’s firewall. For details about configuring the administration simple URL, see <A href="lync-server-2013-planning-for-simple-urls.md">Planning for simple URLs in Lync Server 2013</A> in the Planning documentation and <A href="lync-server-2013-edit-or-configure-simple-urls.md">Edit or configure simple URLs in Lync Server 2013</A> in the Deployment documentation.

    
    </div>

2.  Open a browser window, and then enter the Admin URL configured for your organization.

</div>

<div>

## To open Lync Server 2013 Control Panel on a computer running Lync Server 2013

1.  From a user account that is a member of the CsAdministrator role or other role that has appropriate user rights and permissions for the task to be performed, log on to a computer on which you have installed Lync Server 2013 or, at a minimum, the Lync Server 2013 administrative tools. To configure settings, the computer must have a minimum screen resolution of 1024 x 768.

2.  Start Lync Server 2013 Control Panel: Click **Start**, click **All Programs**, point to **Administrative Tools**, point to **Microsoft Lync Server 2013**, and then click **Lync Server 2013 Control Panel**.

</div>

</div>

<span id="BKMK_OpenManagementShell"></span>

<div>

## Lync Server 2013 Management Shell

Use the following procedure to open Lync Server 2013 Management Shell to administer servers, users, clients, and devices in your environment by using the command line.

<div>


> [!NOTE]  
> You can use a user account that is assigned to the CsAdministrator role to perform any task in Lync Server 2013 Management Shell. You can log on using other roles to perform specific administration tasks, depending on the task you need to perform. For example, you can use CSArchivingAdministrator to run cmdlets related to Archiving administration. For details about roles, see <A href="lync-server-2013-planning-for-role-based-access-control.md">Planning for role-based access control in Lync Server 2013</A> in the Planning documentation. For details about the roles that you can use to run a specific cmdlet, see the documentation for the cmdlet.<BR>You can also run certain cmdlets by using a user account in the RTCUniversalServerAdmins, RTCUniversalUserAdmins, or RTCUniversalReadOnlyAdmins groups, depending on the cmdlet.



</div>

<div>

## To open the Lync Server 2013 Management Shell

  - If you open a Windows PowerShell window rather than the Lync Server 2013 Management Shell, by default you cannot run the Lync Server 2013 cmdlets. To run the Lync Server 2013 cmdlets from within Windows PowerShell, type the following at the Windows PowerShell command prompt:
    
    `Import-Module Lync`

  - Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

</div>

</div>

<div>

## See Also


[Install Lync Server 2013 administrative tools](lync-server-2013-install-lync-server-administrative-tools.md)  


[Lync Server 2013 administrative tools](lync-server-2013-lync-server-administrative-tools.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

