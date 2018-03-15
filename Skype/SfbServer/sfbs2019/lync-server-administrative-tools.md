---
title: "Lync Server 2013 administrative tools"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9b006f93-4f3d-461d-89b8-e80a34fdb3c5
description: "In this articleDeployment WizardTopology BuilderLync Server Control PanelLync Server Management ShellLogging ToolIn This Section"
---

# Lync Server 2013 administrative tools
[]
 **In this article**
  
[Deployment Wizard](#sectionSection0)
  
[Topology Builder](#sectionSection1)
  
[Lync Server Control Panel](#sectionSection2)
  
[Lync Server Management Shell](#sectionSection3)
  
[Logging Tool](#sectionSection4)
  
[In This Section](#sectionSection5)
  
This topic describes the administrative tools for Lync Server 2013.
  
The administrative tools are installed by default on each Lync Server server. Additionally, you can install the administrative tools on other computers, such as dedicated administrative consoles. For procedures to install the administrative tools, see [Install Lync Server 2013 administrative tools](install-lync-server-administrative-tools.md). For procedures to open the tools to perform management tasks, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md). 
  
Ensure that you review infrastructure, operating system, software, and administrator rights requirements before you install or use the Lync Server administrative tools. For details about infrastructure requirements, see [Administrative tools infrastructure requirements in Lync Server 2013](administrative-tools-infrastructure-requirements.md). For details about operating system and software requirements to install the Lync Server administrative tools, see [Server and tools operating system support in Lync Server 2013](server-and-tools-operating-system-support.md), [Additional software requirements for Lync Server 2013](additional-software-requirements.md), and [Additional server support and requirements in Lync Server 2013](additional-server-support-and-requirements.md). The user rights and permissions required to install and use the tools are described in [Administrator rights and permissions required for setup and administration of Lync Server 2013](administrator-rights-and-permissions-required-for-setup-and-administration.md).
  
The administrative tools consist of the following:
  
- **Lync Server Deployment Wizard** Use to deploy Lync Server and to install all administrative tools. 
    
- **Lync Server Topology Builder** Use to define components in your deployment. 
    
- **Lync Server Control Panel** Use for ongoing management of your deployment by using a web-based interface. 
    
- **Lync Server Management Shell** Use for ongoing management of your deployment by using the command line. 
    
- **Lync Server Logging tool** Use to troubleshoot problems in your deployment. 
    
- **Centralized Logging Service** Collect logs and trace files from one computer, pool, site or global. Select and define scenarios that contain providers, flags and trace levels. Logging is collected, aggregated and displayed with tools such as any text-based tool or Snooper.exe. 
    
You can manage your deployment by primarily using Topology Builder and Lync Server Control Panel.
  
## Deployment Wizard
<a name="sectionSection0"> </a>

You must use the Lync Server Deployment Wizard included on the installation media to install all administrative tools onto a computer on which you have not already installed Lync Server. During the administrative tools installation process, the Lync Server Deployment Wizard is installed locally along with the other tools so that you can later use it to install files for additional components or remove files for components that you do not want on the computer.
  
For details about how to run the Lync Server Deployment Wizard for the first time from the Lync Server installation media, see [Install Lync Server 2013 administrative tools](install-lync-server-administrative-tools.md).
  
## Topology Builder
<a name="sectionSection1"> </a>

For details about deployment tasks that you can you perform by using Topology Builder, see the Deployment documentation for each server role.
  
## Lync Server Control Panel
<a name="sectionSection2"> </a>

You can use Lync Server 2013 Control Panel to perform most of the administrative tasks required to manage and maintain Lync Server 2013. Lync Server Control Panel provides you with a graphical user interface (GUI) to manage the configuration of the servers running Lync Server, in addition to the users, clients, and devices in your organization. Lync Server Management Shell uses Lync Server Control Panel as the underlying mechanism to perform Lync Server configuration. 
  
Lync Server Control Panel is automatically installed on every Lync Server Front End Server or Standard Edition server. In this release, you administer Edge Servers remotely. You can also install Lync Server Control Panel on another computer, such as a management console from which you want to centrally manage Lync Server. For details, see [Install Lync Server 2013 administrative tools](install-lync-server-administrative-tools.md).
  
> [!IMPORTANT]
>  To configure settings using Lync Server Control Panel, you must be logged in using an account that is assigned to the CsAdministrator role. For details about the predefined administrative roles available in Lync Server 2013, see [Planning for role-based access control in Lync Server 2013](planning-for-role-based-access-control-rbac.md). >  To configure settings using Lync Server Control Panel, you must also use a computer with a minimum screen resolution of 1024 x 768. 
  
## Lync Server Management Shell
<a name="sectionSection3"> </a>

In Lync Server, the Lync Server Management Shell provides a new method for administration and management. Lync Server Management Shell is a powerful management interface, built on the Windows PowerShell command-line interface, that includes a comprehensive set of cmdlets that are specific to Lync Server. With Lync Server Management Shell, you gain a rich set of configuration and automation controls. Topology Builder and Lync Server Control Panel both implement subsets of these cmdlets to support management of Lync Server. The Lync Server Management Shell includes cmdlets for all Lync Server administration tasks, and you can use the cmdlets individually to manage your deployment. For details, see [Lync Server 2013 Management Shell](lync-server-management-shell.md) documentation or the command-line help for each cmdlet. 
  
## Logging Tool
<a name="sectionSection4"> </a>

The Lync Server Logging Tool facilitates troubleshooting by capturing logging and tracing information from the product while the product is running. You can use the tool to run debug sessions on any Lync Server server role. For details about the Logging Tool, see the Lync Server 2010 Logging Tool documentation on the TechNet Library at [https://go.microsoft.com/fwlink/p/?linkId=199265](https://go.microsoft.com/fwlink/p/?linkId=199265).
  
> [!IMPORTANT]
> The Centralized Logging Service is recommended for all logging collection over the Lync Server Logging Tool in all circumstances. The Lync Server Logging Tool will still work, but it will interfere or be rendered mostly ineffective if the Centralized Logging Service is already running. You should use only the Centralized Logging Service or the Lync Server Logging Tool, but never both concurrently. For more information on the Centralized Logging Service and why you should use it exclusively, see [Using the Centralized Logging Service in Lync Server 2013](using-the-centralized-logging-service.md). 
  
## In This Section
<a name="sectionSection5"> </a>

- [Administrative tools infrastructure requirements in Lync Server 2013](administrative-tools-infrastructure-requirements.md)
    
- [Server and tools operating system support in Lync Server 2013](server-and-tools-operating-system-support.md)
    
- [Administrative tools software requirements in Lync Server 2013](administrative-tools-software-requirements.md)
    
- [Administrator rights and permissions required for setup and administration of Lync Server 2013](administrator-rights-and-permissions-required-for-setup-and-administration.md)
    
- [Requirements to publish a topology in Lync Server 2013](requirements-to-publish-a-topology.md)
    
- [Install Lync Server 2013 administrative tools](install-lync-server-administrative-tools.md)
    
- [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md)
    
- [Troubleshooting Lync Server 2013 Control Panel](troubleshooting-lync-server-2013-control-panel.md)
    
- [Using the Centralized Logging Service in Lync Server 2013](using-the-centralized-logging-service.md)
    
## See also
<a name="sectionSection5"> </a>

#### 

[Lync Server 2013 Management Shell](lync-server-management-shell.md)

