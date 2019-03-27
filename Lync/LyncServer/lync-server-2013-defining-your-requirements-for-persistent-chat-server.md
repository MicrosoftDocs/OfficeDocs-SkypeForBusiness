---
title: 'Lync Server 2013: Defining your requirements for Persistent Chat Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Defining your organization's requirements for Persistent Chat Server
ms:assetid: 568674fb-c08a-4170-ac38-e2f8428c69e0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398372(v=OCS.15)
ms:contentKeyID: 48184166
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Defining your organization's requirements for Persistent Chat Server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-01-15_

Before you deploy Persistent Chat Server for your organization, it’s essential to consider the following key questions to optimize your deployment:

  - Who (user profile) should be enabled for Persistent Chat Server? Persistent Chat Server is enabled by a policy that can be set at a Global, Site, Pool or User level.

  - How many users (scale) should be enabled for Persistent Chat Server? Persistent Chat Server supports 150,000 provisioned users (enabled by policy), and a maximum of 80,000 concurrent users using Persistent Chat Server. A single Persistent Chat Server can support 20,000 connected users, and a single Persistent Chat Server pool can have up to 4 active servers for a total of 80,000 concurrently connected users.

  - Are you migrating from a previous version of Group Chat Server, or are you deploying Persistent Chat Server for the first time?

  - Are there compliance requirements? Persistent Chat Server supports compliance. The compliance service runs collocated on the Persistent Chat Server Front End Server, as opposed to the requirement for a separate computer in previous Group Chat Server deployments. Compliance is optional, and if chosen, requires a compliance database that must be configured to store compliance data and events. You may want to also configure an adapter to take the data from the compliance database and convert to another format (such as XML files or Exchange-hosted archives).

  - How do you want to control scopes, ethical boundaries, and access? You can define **Categories** to segregate these boundaries, and choose who is allowed to be in rooms that are created in each of these categories.

  - How do you want to control who can create rooms? You can configure **Creators**, appropriate to your categories, who can create rooms. Creators can assign other members as **Chat Room Managers** for ongoing management of the rooms (adding or removing additional members), according to the scope for **AllowedMembers/DeniedMembers** configured by the category.

  - How do you want to create rooms? Persistent Chat Server provides a web-based feature for room creation and management. This can be launched from the Lync 2013 client. You can choose to define a custom solution (by using the Persistent Chat Server Software Development Kit (SDK)) that implements your business requirements and workflows, and configures Persistent Chat Server to direct users to your custom solution.

  - What kind of add-ins do you want to provision? **Add-ins** enhance the in-room experience by leveraging the extensibility pane in the Lync 2013 client to provide context that is relevant to the room. You can choose what general add-ins might be most useful (for example, your company website, internal collaboration documents, and so on). Chat room managers can choose one of the registered add-ins and associate it with their rooms, if desired.

  - What kind of high availability and disaster recovery requirements do you have? Persistent Chat Server supports SQL Server mirroring and SQL Server clustering for high availability and supports up to 8 servers (4 active and 4 standby) in a stretched pool with SQL Server log shipping for disaster recovery.

  - Are there regulatory requirements? If your company is in a country/region where data needs to be kept within the country, you may need to deploy multiple Persistent Chat Server pools, each local to a specific geography. A room, category, or add-in does not span pools—it belongs to only one Persistent Chat Server pool. You can manage the set of categories, add-ins and rooms for each Persistent Chat Server pool. Users can be configured to have access to rooms in one or more pools using the category AllowedMembers scope or Room’s membership scope, depending on how you design your categories.
    
    <div>
    

    > [!IMPORTANT]  
    > Having multiple Persistent Chat Server pools does not give you more scale (you can still have only 80,000 concurrently connected users across all your Persistent Chat Server pools). The primary reason for supporting multiple Persistent Chat Server pools is to support regulatory concerns.

    
    </div>

</div>

<span> </span>

</div>

</div>

</div>

