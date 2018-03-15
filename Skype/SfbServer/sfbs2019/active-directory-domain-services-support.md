---
title: "Active Directory Domain Services support in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aeb62d5e-e424-473a-b795-9452150c98dd
description: "In this articleSupported Domain Controller Operating SystemsForest and Domain Functional LevelSupport for Read-Only Domain ControllersDomain NamesLocked Down AD DS Environments"
---

# Active Directory Domain Services support in Lync Server 2013
[]
 **In this article**
  
[Supported Domain Controller Operating Systems](#sectionSection0)
  
[Forest and Domain Functional Level](#sectionSection1)
  
[Support for Read-Only Domain Controllers](#sectionSection2)
  
[Domain Names](#sectionSection3)
  
[Locked Down AD DS Environments](#sectionSection4)
  
Lync Server 2013 uses the Central Management store to store configuration data for servers and services, instead of relying on Active Directory Domain Services for this information, as in the past. Lync Server 2013 still stores the following in AD DS:
  
- **Schema extensions**
    
  - User object extensions
    
  - Extensions for Lync Server 2010 and Office Communications Server 2007 R2 classes to maintain backward compatibility with previous supported versions
    
- **Data** (stored in Lync Server 2013 extended schema and in existing classes) 
    
  - User SIP URI and other user settings
    
  - Contact objects for applications (for example, the Response Group application and the Conferencing Attendant application)
    
  - Data published for backward compatibility
    
  - A service control point (SCP) for the Central Management store
    
  - Kerberos Authentication Account (an optional computer object)
    
This section describes the AD DS support requirements for Lync Server 2013. For details about topology support, see [Supported Active Directory topologies in Lync Server 2013](supported-active-directory-topologies.md) in the Supportability documentation. 
  
## Supported Domain Controller Operating Systems
<a name="sectionSection0"> </a>

Lync Server 2013 supports domain controllers running the following operating systems:
  
- Windows Server 2012 R2 operating system
    
- Windows Server 2012 operating system
    
- Windows Server 2008 R2 operating system
    
- Windows Server 2008 operating system
    
- Windows Server 2008 Enterprise 32-Bit
    
- The 32-bit or 64-bit versions of the Window Server 2003 R2 operating system
    
- The 32-bit or 64-bit versions of the Windows Server 2003 operating system
    
## Forest and Domain Functional Level
<a name="sectionSection1"> </a>

You must raise all domains in which you deploy Lync Server 2013 to a domain functional level of Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, or at least Windows Server 2003. 
  
All forests in which you deploy Lync Server 2013 must be raised to a forest functional level of Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, or at least Windows Server 2003. 
  
## Support for Read-Only Domain Controllers
<a name="sectionSection2"> </a>

Lync Server 2013 supports Active Directory Domain Services deployments that include read-only domain controllers or read-only global catalog servers, as long as there are writable domain controllers available.
  
## Domain Names
<a name="sectionSection3"> </a>

Lync Server does not support single-labeled domains. For example, a forest with a root domain named **contoso.local** is supported, but a root domain named **local** is not supported. For details, see Microsoft Knowledge Base article 300684, "Information about configuring Windows for domains with single-label DNS names," at [https://go.microsoft.com/fwlink/p/?linkId=143752](https://go.microsoft.com/fwlink/p/?linkId=143752).
  
> [!NOTE]
> Lync Server does not support renaming domains. If you need to rename a domain where Lync Server is deployed, you need to first uninstall Lync Server, then rename the domain, and then reinstall Lync Server. 
  
## Locked Down AD DS Environments
<a name="sectionSection4"> </a>

In a locked-down AD DS environment, Users and Computer objects are often placed in specific organizational units (OUs) with permissions inheritance disabled to help secure administrative delegation and to enable use of Group Policy objects (GPOs) to enforce security policies. Lync Server 2013 can be deployed in a locked-down Active Directory environment. For details about what is required to deploy Lync Server in a locked-down environment, see [Preparing a locked-down Active Directory Domain Services in Lync Server 2013](preparing-a-locked-down-active-directory-domain-services.md) in the Deployment documentation. 
  

