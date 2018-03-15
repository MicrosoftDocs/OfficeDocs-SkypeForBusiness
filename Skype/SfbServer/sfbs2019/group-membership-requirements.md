---
title: "Group membership requirements for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 01876843-8717-4e72-baf5-866ac8cceee6

description: "The following table summarizes the group or groups that a person should belong to in order to successfully install, manage, and troubleshoot Lync Server 2013."
---

# Group membership requirements for Lync Server 2013
[]
The following table summarizes the group or groups that a person should belong to in order to successfully install, manage, and troubleshoot Lync Server 2013.
  
|**Lync Server 2013 Executable**|**Group Membership Required**|
|:-----|:-----|
|**Setup.exe** - Executable that starts the installation of the Lync Server 2013 administrative tools.  <br/> |Member of the Local Administrators group on the computer from which the executable is run. Member of Domain Users group to read information in Active Directory Domain Services. This level of permission is required because the automatic installation of required MSI packages on the local computer requires privileges that allow reading from and writing to protected local computer resources such as Program Files directories, and protected registry such as the Local Machine hive.  <br/> > [!TIP]> You can also delegate setup permissions to users or groups to whom you do not want to grant membership in the Domain Admins group. For details, see [Granting setup permissions in Lync Server 2013](granting-setup-permissions.md) in the Deployment documentation.           |
|**Deploy.exe** - Called by setup.exe, deploy.exe is responsible for the deployment of the software components for the server roles.  <br/> |Member of the Local Administrators group on the computer from which the executable is run. Member of Domain Users group to read information in AD DS. This level of permission is required because the automatic installation of required MSI packages on the local computer requires privileges that allow reading from and writing to protected local computer resources such as Program Files directories, and protected registry such as the Local Machine hive. Membership in RtcUniversalReadOnlyAdmins group is necessary to read the Central Management store.  <br/> > [!NOTE]> If you are running the Windows Vista operating system or Windows 7 operating system, you will be prompted by User Account Control (UAC) to proceed with installation. If you are logged on with a standard user account, you will need someone who is a member of the Local Administrators group to provide credentials when prompted for an account with permissions to install the software.           |
|**Bootstrapper.exe** - Called by setup.exe, bootstrapper.exe is responsible for deployment and configuration of server roles.  <br/> |Member of the Local Administrators group on the computer from which the executable is run. Member of the RTCUniversalServerAdmins group to run Bootstrapper.exe. Member of Domain Users group to read information in AD DS. This level of permission is required because the automatic installation of required MSI packages on the local computer requires privileges that allow reading from and writing to protected local computer resources such as Program Files directories, and protected registry such as the Local Machine hive.  <br/> |
|**TopologyBuilder** - Wizard-driven user interface to create, view, adjust, and validate Lync Server 2013 topologies.  <br/> |Member of the Local Administrators group on the computer from which the executable is run to view the topology. Member of the RTCUniversalServerAdmins group to change configuration settings. Member of the RTCUniversalServerAdmins group and Domain Admins group, or member of the RTCUniversalServerAdmins group (only if the group has been granted delegate setup permissions), to publish the topology. For details about delegating setup permissions to allow members of the RTCUniversalServerAdmins group to publish the topology without being members of the Domain Admins group, see [Granting setup permissions in Lync Server 2013](granting-setup-permissions.md) in the Deployment documentation.  <br/> |
|**AdminUIHost** - Web-based graphical user interface for managing Lync Server 2013.  <br/> |Member of CsAdministrator group or member of another role-based access control (RBAC) role to which the specific administrative task is assigned. Lync Server 2013 Control Panel implements configuration changes by running Lync Server 2013 Management Shell cmdlets. For a list of predefined roles and the cmdlets members are permitted to run, see [Planning for role-based access control in Lync Server 2013](planning-for-role-based-access-control-rbac.md) in the Planning documentation.  <br/> |
|**PowerShell.exe with the Lync Server 2013 module loaded** - Command-line administrative tool with cmdlets specific to management of Lync Server 2013.  <br/> | Member of CsAdministrator group or member of another RBAC role to which the specific cmdlet has been assigned. For a list of predefined roles and the cmdlets members are permitted to run, see [Planning for role-based access control in Lync Server 2013](planning-for-role-based-access-control-rbac.md) in the Planning documentation.  <br/>  Or, member of one or more of the following groups, depending on the cmdlet:  <br/>  RTCUniversalServerAdmins  <br/>  RTCUniversalUserAdmins  <br/>  RTCUniversalReadOnlyAdmins  <br/> |
   

