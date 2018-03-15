---
title: "Active Directory support in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 28ed9ac4-586d-4803-ad45-99c4fa793f54
description: "The Active Directory Domain Services on-premises topologies that are supported by Lync Server 2013 are as follows:"
---

# Active Directory support in Lync Server 2013
[]
The Active Directory Domain Services on-premises topologies that are supported by Lync Server 2013 are as follows:
  
- Single forest with single domain
    
- Single forest with a single tree and multiple domains
    
- Single forest with multiple trees and disjoint namespaces
    
- Multiple forests in a central forest topology
    
- Multiple forests in a resource forest topology
    
> [!NOTE]
> Lync Server 2013 does not support single-label domains. For example, a forest with a root domain named **contoso.local** is supported, but a single-label root domain named **local** is not supported. For details, see Microsoft Knowledge Base article 300684, "Information about configuring Windows for domains with single-label DNS names," at [https://go.microsoft.com/fwlink/p/?linkId=143752](https://go.microsoft.com/fwlink/p/?linkId=143752). 
  
> [!NOTE]
> Lync Server 2013 does not support renaming domains. If you need to rename a domain where Lync Server is deployed, you need to first uninstall Lync Server, then rename the domain, and then reinstall Lync Server. 
  
For details about supported topologies and requirements for on-premises deployments, see [Active Directory Domain Services requirements, support, and topologies in Lync Server 2013](active-directory-domain-services-requirements-support-and-topologies.md) in the Planning documentation. 
  

