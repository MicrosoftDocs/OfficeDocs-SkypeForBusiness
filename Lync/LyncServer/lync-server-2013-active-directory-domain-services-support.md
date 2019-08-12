---
title: 'Lync Server 2013: Active Directory Domain Services support'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Active Directory Domain Services support
ms:assetid: aeb62d5e-e424-473a-b795-9452150c98dd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412831(v=OCS.15)
ms:contentKeyID: 48185136
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Active Directory Domain Services support in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-07_

Lync Server 2013 uses the Central Management store to store configuration data for servers and services, instead of relying on Active Directory Domain Services for this information, as in the past. Lync Server 2013 still stores the following in AD DS:

  - **Schema extensions**
    
      - User object extensions
    
      - Extensions for Lync Server 2010 and Office Communications Server 2007 R2 classes to maintain backward compatibility with previous supported versions

  - **Data** (stored in Lync Server 2013 extended schema and in existing classes)
    
      - User SIP URI and other user settings
    
      - Contact objects for applications (for example, the Response Group application and the Conferencing Attendant application)
    
      - Data published for backward compatibility
    
      - A service control point (SCP) for the Central Management store
    
      - Kerberos Authentication Account (an optional computer object)

This section describes the AD DS support requirements for Lync Server 2013. For details about topology support, see [Supported Active Directory topologies in Lync Server 2013](lync-server-2013-supported-active-directory-topologies.md) in the Supportability documentation.

<div>

## Supported Domain Controller Operating Systems

Lync Server 2013 supports domain controllers running the following operating systems:

  - Windows Server 2012 R2 operating system

  - Windows Server 2012 operating system

  - Windows Server 2008 R2 operating system

  - Windows Server 2008 operating system

  - Windows Server 2008 Enterprise 32-Bit

  - The 32-bit or 64-bit versions of the Window Server 2003 R2 operating system

  - The 32-bit or 64-bit versions of the Windows Server 2003 operating system

</div>

<div>

## Forest and Domain Functional Level

You must raise all domains in which you deploy Lync Server 2013 to a domain functional level of Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, or at least Windows Server 2003.

All forests in which you deploy Lync Server 2013 must be raised to a forest functional level of Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, or at least Windows Server 2003.

</div>

<div>

## Support for Read-Only Domain Controllers

Lync Server 2013 supports Active Directory Domain Services deployments that include read-only domain controllers or read-only global catalog servers, as long as there are writable domain controllers available.

</div>

<div>

## Domain Names

Lync Server does not support single-labeled domains. For example, a forest with a root domain named **contoso.local** is supported, but a root domain named **local** is not supported. For details, see Microsoft Knowledge Base article 300684, “Information about configuring Windows for domains with single-label DNS names,” at [http://go.microsoft.com/fwlink/p/?linkId=143752](http://go.microsoft.com/fwlink/p/?linkid=143752).

<div>


> [!NOTE]  
> Lync Server does not support renaming domains. If you need to rename a domain where Lync Server is deployed, you need to first uninstall Lync Server, then rename the domain, and then reinstall Lync Server.



</div>

</div>

<div>

## Locked Down AD DS Environments

In a locked-down AD DS environment, Users and Computer objects are often placed in specific organizational units (OUs) with permissions inheritance disabled to help secure administrative delegation and to enable use of Group Policy objects (GPOs) to enforce security policies. Lync Server 2013 can be deployed in a locked-down Active Directory environment. For details about what is required to deploy Lync Server in a locked-down environment, see [Preparing a locked-down Active Directory Domain Services in Lync Server 2013](lync-server-2013-preparing-a-locked-down-active-directory-domain-services.md) in the Deployment documentation.

</div>

</div>

<span> </span>

</div>

</div>

</div>

