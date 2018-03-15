---
title: "Issues with the environment test in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ff1fe0d3-35b2-41ef-87e7-6a61e9e1d2ca
description: "Best Practices Analyzer provides a way for you to verify that your Lync Server 2013 environment is a supported configuration. As part of the Active Directory Domain Services check, Best Practices Analyzer does the following:"
---

# Issues with the environment test in Lync Server 2013
[]
Best Practices Analyzer provides a way for you to verify that your Lync Server 2013 environment is a supported configuration. As part of the Active Directory Domain Services check, Best Practices Analyzer does the following: 
  
- Verifies the Active Directory Domain Services forest and schema preparation.
    
- Identifies the number of Active Directory Domain Services sites and domains in the deployment.
    
- Checks the forest and domain levels.
    
- Checks the domain controller version.
    
- Identifies the domain, configuration, and schema naming context.
    
- Identifies the number of enabled users.
    
- Checks where the global Active Directory Domain Services settings are stored.
    
- Checks for the service connection points (SCPs) for Lync Server.
    
- Identifies the database version.
    
## Resolving Issues with the Environment

If the environment test found problems with your environment, these problems are probably caused by issues with your Active Directory configuration or the level of software running on specific servers. For example, if Best Practices Analyzer identifies any domain controllers in your environment that are running Windows Server 2000, it will issue a warning and you will need to upgrade those domain controllers to a supported version of Windows Server.
  

