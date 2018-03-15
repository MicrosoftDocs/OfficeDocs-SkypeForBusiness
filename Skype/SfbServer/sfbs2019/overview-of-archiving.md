---
title: "Overview of Archiving in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1e3c2ef1-f561-4f57-8b6a-7d78addc1ed1
description: "Archiving in Lync Server 2013 provides a way for you to archive communications that are sent through Lync Server 2013."
---

# Overview of Archiving in Lync Server 2013
[]
Archiving in Lync Server 2013 provides a way for you to archive communications that are sent through Lync Server 2013.
  
You can implement Archiving as part of your initial Lync Server 2013 deployment, or you can add it to an existing deployment. To use Lync Server 2013 Archiving databases (SQL Server databases) for storage of archiving data, you use Topology Builder to add the databases to your topology, and then publish the topology again. If all your users are homed on Exchange 2013 and have their mailboxes put on In-Place Hold, you do not have to update your topology, but only need to enable Microsoft Exchange integration to store archived data in Exchange 2013.
  
When you implement Archiving, you configure it to specify what is archived. By default, nothing is archived. You configure and manage Archiving by using Lync Server 2013 Control Panel. You can implement Archiving for internal communications, external communications, or both. You can configure archiving settings your entire organization and, optionally, for specific sites, specific pools, and specific users and user groups. For details about determining the appropriate options for your organization, see [Defining your requirements for Archiving in Lync Server 2013](defining-your-organization-s-requirements-for-archiving.md) in the Planning documentation. For details about how Archiving policies and configurations are implemented, and details about what information can or cannot be archived, see [How Archiving works in Lync Server 2013](how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation. 
  

