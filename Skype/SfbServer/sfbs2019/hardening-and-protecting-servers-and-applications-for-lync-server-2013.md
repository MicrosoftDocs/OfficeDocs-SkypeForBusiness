---
title: "Hardening and protecting servers and applications for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9ca2b233-26f1-4d72-96e7-81a82c727806
description: "In this articleSecuring Application ServersSecuring Virtual ServersGroup PolicyGroup Policy Security SettingsBest Practices"
---

# Hardening and protecting servers and applications for Lync Server 2013
[]
 **In this article**
  
[Securing Application Servers](#sectionSection0)
  
[Securing Virtual Servers](#sectionSection1)
  
[Group Policy](#sectionSection2)
  
[Group Policy Security Settings](#sectionSection3)
  
[Best Practices](#sectionSection4)
  
You should harden and protect your operating system and applications according to best practices for that specific component. This section describes how to harden application servers and use Group Policy to implement security lockdowns.
  
> [!NOTE]
> You can also harden and protect the databases used for you Microsoft Lync Server 2013 deployment. For details, see [Hardening and protecting the databases of Lync Server 2013](hardening-and-protecting-the-databases-of-lync-server-2013.md). 
  
## Securing Application Servers
<a name="sectionSection0"> </a>

For applications servers, the operating system and the application should be hardened. For example, a Windows Server 2008 computer dedicated to running Microsoft Internet Security and Acceleration (ISA) Server 2006 should be hardened from the operating system and from the application perspective. Minimizing the number of services running and provided by the server should be a primary goal.
  
## Securing Virtual Servers
<a name="sectionSection1"> </a>

Virtual server snapshots contain copies of the server's data disks and also contain dumps of in-memory data, both of which can contain sensitive cryptographic data that might lead to attacks. For production servers implemented using virtualization, you should disable all server snapshots or manage them in a very controlled manner. For details about securing Hyper-V virtual servers, see the Hyper-V Security Guide at: [https://go.microsoft.com/fwlink/p/?LinkId=214176](https://go.microsoft.com/fwlink/p/?LinkId=214176).
  
## Group Policy
<a name="sectionSection2"> </a>

In Windows Server 2008 and Windows Server 2008 R2, Group Policy provides directory-based desktop configuration management. You can use Group Policy to implement security lockdowns by defining Computer and User settings within a Group Policy object (GPO) for the following:
  
- Registry-based policies
    
- Security
    
- Software installation
    
- Scripts
    
- Folder redirection
    
- Remote installation services
    
To provide a user interface for the administrator to configure these settings, administrative templates are shipped with operating system releases, service pack releases, and some applications, including Lync Server 2013.
  
The Communicator.adm file is an administrative template that ships with Lync Server 2013, is installed to the  _%windir%_\inf\ directory, and provides an interface to the Group Policy settings. Each setting in Communicator.adm corresponds to a setting in the registry that affects application behavior.
  
The settings can be accessed from GPedit.dll, which is available from the Active Directory Users and Computers console and the Group Policy Management Console (GPMC).
  
## Group Policy Security Settings
<a name="sectionSection3"> </a>

Group Policy contains security settings for a GPO under Computer Configuration/Windows Settings/Security Settings when accessed from GPedit.dll. You can import security templates to configure security settings for the GPO. The Windows Server 2008 Security Guide at [https://go.microsoft.com/fwlink/p/?LinkId=145186](https://go.microsoft.com/fwlink/p/?LinkId=145186) and the Windows Server 2008 R2 Security Compliance Management Toolkit at [http://go.microsoft.com/fwlink/p/?LinkId=211882](http://go.microsoft.com/fwlink/p/?LinkId=211882) contain a number of sample templates that you can modify to meet your needs. 
  
## Best Practices
<a name="sectionSection4"> </a>

- Harden all server operating systems and applications.
    
- Protect server snapshots and enhance the security of all virtual servers.
    
- Use Group Policy to implement security lockdowns.
    

