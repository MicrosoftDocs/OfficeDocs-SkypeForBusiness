---
title: "Install and open administrative tools"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "This topic describes how to install and open the administrative tools you need to deploy and manage Skype for Business."
---

# Install and open administrative tools

This topic describes how to install the administrative tools you need to deploy and manage Skype for Business Server. The administrative tools are installed by default on each server running Skype for Business Server. Additionally, you can install the administrative tools on other computers, such as dedicated administrative consoles. We strongly recommend that you install the administrative tools on a computer that is in the same domain or forest as the Skype for Business Server deployment you are creating, to ensure that Active Directory Domain Services preparation steps are already complete, which enables you to use the administrative tools on that computer later to publish your topology. Also make sure to review the necessary requirements before you install or use the Skype for Business Server administrative tools. See the requirements documentation in [Skype for Business Server 2019](../../SfBServer2019/plan/system-requirements.md) or [Skype for Business Server 2015](../plan-your-deployment/requirements-for-your-environment/requirements-for-your-environment.md).
 
> [!Important]
> If your organization requires that you locate Internet Information Services (IIS) and all Web Services on a drive other than the system drive, you can change the installation location path for the Skype for Business Server files in the Setup dialog box. If you install the Setup files to this path, including OCSCore.msi, the rest of the Skype for Business Server files will be deployed to this drive as well. 

## To install the administrative tools

1. Log on as a local administrator (minimum requirement) to the computer where you want to install the administrative tools. If you are logged on as a standard user in Windows and User Account Control (UAC) is enabled, you will be prompted for the local administrator or a domain equivalent user name and password.
2. Locate the installation media on your computer, and then double-click \Setup\amd64\Setup.exe.
3. If you are prompted to install the Microsoft Visual C++ distributable, click **Yes**.
4. On the Installation Location page, click **OK**. Change this path to another location or drive if you need to have the files installed to another location.

    > [!Important]
    > If your organization requires that you locate Internet Information Services (IIS) and all Web Services on a drive other than the system drive, you can change the installation location path for the Skype for Business Server files in the Setup dialog box. If you install the Setup files to this path, including OCSCore.msi, the rest of the Skype for Business Server files will be deployed to this drive too. 

5. On the End User License Agreement page, review the license terms, click **I accept**, and then click **OK**. This step is required before you can continue.
6. On the Deployment Wizard page, click **Install Administrator Tools**. 
7. When the installation successfully completes, click **Exit**.

Use the following procedures to open administrative tools to deploy, configure, or troubleshoot your Skype for Business Server topology.

- [Deployment Wizard](#deployment-wizard)
- [Topology Builder](#topology-builder) 
- [Skype for Business Server Control Panel](#skype-for-business-server-control-panel)
- [Skype for Business Server Management Shell](#skype-for-business-server-management-shell)

## Deployment Wizard

Use the following procedure to start the Deployment Wizard locally to add or remove component files.

**To start the Skype for Business Server Deployment Wizard**

1. Log on to the computer where the Skype for Business Server Deployment Wizard is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.
2. Click **Start**, click **All Programs**, click **Skype for Business Server**, and then click **Skype for Business Server Deployment Wizard**.


## Topology Builder 

Use the following procedure to open the Topology Builder to define the servers that you want to deploy in your Skype for Business Server topology.

**To open the Skype for Business Server Topology Builder to design the topology**

1. Log on to the computer where Topology Builder is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.
    > [!NOTE]
    > You can define a topology by using an account that is a member of the local Users group, but to read, publish, or enable a topology, which is required to install Skype for Business Server on a server, you must use an account that is a member of the Domain Admins group and the RTCUniversalServerAdmins group, and that has full control permissions (that is, read, write, and modify) on the file share that you are going to use for the archiving file store so that Topology Builder can configure the required discretionary access control list (DACLs), or an account with equivalent user rights.
 
2. Start Topology Builder: Click **Start**, click **All Programs**, click **Skype for Business Server**, and then click **Skype for Business Server Topology Builder**.

## Skype for Business Server Control Panel 

Use one of the following procedures to open the Skype for Business Server Control Panel to manage the configuration of servers, users, clients, and devices in your environment.

> [!NOTE]
> You can use a user account that is assigned to the CsAdministrator role to perform any task in the Skype for Business Server Control Panel. You can use other roles to log on to the Skype for Business Server Control Panel to perform specific administration tasks, dependent on the task you need to perform. For example, you can use CSArchivingAdministrator to administer Archiving in the Skype for Business Server Control Panel. For details about roles, see [Planning for role-based access control](https://technet.microsoft.com/en-us/library/gg425917(v=ocs.15).aspx). For details about the roles that you can use to perform a specific task, see the documentation for the task. 

**To open the Skype for Business Server Control Panel from any computer inside your organization’s firewall**

1. From a user account that is assigned to the CsAdministrator role or other role that has appropriate user rights and permissions for the task to be performed, log on to any computer in your internal deployment with a minimum screen resolution of 1024 x 768.

    > [!IMPORTANT]
    > If you have configured an administration simple uniform resource locator (URL), you can access the Skype for Business Server Control Panel from an Internet browser that is running on any computer within your organization’s firewall. For details about configuring the administration simple URL, see [Planning for simple URLs](https://technet.microsoft.com/en-us/library/gg398287(v=ocs.15).aspx) and [Edit or configure simple URLs](https://technet.microsoft.com/en-us/library/gg398063(v=ocs.15).aspx). 

2. Open a browser window, and then enter the Admin URL configured for your organization.

**To open the Skype for Business Server Control Panel on a computer running Skype for Business Server**

1. From a user account that is a member of the CsAdministrator role or other role that has appropriate user rights and permissions for the task to be performed, log on to a computer on which you have installed Skype for Business Server or, at a minimum, the Skype for Business Server administrative tools. To configure settings, the computer must have a minimum screen resolution of 1024 x 768.
2. Start Skype for Business Server Control Panel: Click **Start**, click **All Programs**, point to **Administrative Tools**, point to **Skype for Business Server**, and then click **Skype for Business Server Control Panel**.

## Skype for Business Server Management Shell 

Use the following procedure to open the Skype for Business Server Management Shell to administer servers, users, clients, and devices in your environment by using the command line.

> [!NOTE]
> You can use a user account that is assigned to the CsAdministrator role to perform any task in the Skype for Business Server Management Shell. You can log on using other roles to perform specific administration tasks, depending on the task you need to perform. For example, you can use CSArchivingAdministrator to run cmdlets related to Archiving administration. For details about roles, see [Planning for role-based access control](https://technet.microsoft.com/en-us/library/gg425917(v=ocs.15).aspx). For details about the roles that you can use to run a specific cmdlet, see the documentation for the cmdlet.<br/><br/>You can also run certain cmdlets by using a user account in the RTCUniversalServerAdmins, RTCUniversalUserAdmins, or RTCUniversalReadOnlyAdmins groups, depending on the cmdlet. 

**To open Skype for Business Server Management Shell**

If you open a Windows PowerShell window rather than the Skype for Business Server Management Shell, by default you cannot run the Skype for Business Server cmdlets. To run the Skype for Business Server cmdlets from within Windows PowerShell, type the following at the Windows PowerShell command prompt:

`Import-Module Lync`

Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business Server**, and then click **Skype for Business Server Management Shell**.
