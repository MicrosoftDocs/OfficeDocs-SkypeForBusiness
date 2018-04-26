---
title: "Migration from Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat to Lync Server 2013, Persistent Chat Server"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5b4d3db1-6eba-4932-b49c-f60bcf9488f9
description: "The topics in this section guide you through the process of migrating either Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat to Lync Server 2013, Persistent Chat Server. If you intend for your Lync Server 2013, Persistent Chat Server deployment to coexist with a Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat deployment, this guide also includes some essential information for operating in this mixed environment. This guide primarily focuses on data migration for Persistent Chat Server. For users who are migrating from legacy versions of Lync Server to Lync Server 2013, see Migration from Lync Server 2010 to Lync Server 2013 and Migration from Office Communications Server 2007 R2 to Lync Server 2013."
---

# Migration Persistent Chat Server
The topics in this section guide you through the process of migrating either Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat to Lync Server 2013, Persistent Chat Server. If you intend for your Lync Server 2013, Persistent Chat Server deployment to coexist with a Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat deployment, this guide also includes some essential information for operating in this mixed environment. This guide primarily focuses on data migration for Persistent Chat Server. For users who are migrating from legacy versions of Lync Server to Lync Server 2013, see
  
> [!IMPORTANT]
> This topic assumes that you have already installed Lync Server 2013 in coexistence with Lync Server 2010 or Office Communications Server 2007 R2. 
  
> [!IMPORTANT]
> This guide describes the steps generally required to accomplish each phase of migration. It does not address every possible legacy deployment topology or every possible migration scenario. Therefore, you may not need to perform every step that is described, or you may need to perform additional steps, depending on your deployment. The guide also provides examples of verification steps. These verification steps are provided to help you understand what you need to look for to be sure that each phase completes successfully as you progress through your migration. You can modify these verification steps to your specific migration process. 
  
This guide provides information specific to upgrading your existing deployment. It does not explain how to change your existing topology. This guide does not cover the implementation of new features. When a detailed procedure is documented elsewhere, this guide directs you to the appropriate document or document section.
  
This document defines terms as specified in the following list.
  
migration
  
> Moving your deployment from a previous version of Persistent Chat Server, formerly known as Group Chat Server, to Lync Server 2013, Persistent Chat Server.
    
upgrade
  
> Installing a newer version of software on a server or client computer.
    
coexistence
  
> The temporary environment that exists during migration, when some functionality has been migrated to Lync Server 2013, Persistent Chat Server, and other functionality still remains on a prior version of Group Chat Server.
    
Persistent Chat Server is an extension of the Lync Server 2013 infrastructure. Depending on your topology, you can migrate Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat to Lync Server 2013 Persistent Chat Server. 
  
If your organization requires compliance support, it is now automatically installed with each Persistent Chat Server. A separate server is no longer needed for compliance.
  
> [!IMPORTANT]
> Persistent Chat Server must be installed on an NTFS file system to help enforce file system security. FAT32 is not a supported file system for Persistent Chat Server. > If your organization requires compliance support, it is now automatically installed with each Persistent Chat Server. A separate server is no longer needed for compliance. 
  
## In This Section

- [Standard migration scenario - high-level](standard-migration-scenariohigh-level.md)
    
- [Migration process - details](migration-processdetails.md)
    
- [Coexistence considerations](coexistence-considerations.md)
    

