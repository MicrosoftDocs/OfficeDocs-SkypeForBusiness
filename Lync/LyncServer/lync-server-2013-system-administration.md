---
title: 'Lync Server 2013: System administration'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: System administration
ms:assetid: 063eb962-b96a-4699-8579-bb7125112df4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720318(v=OCS.15)
ms:contentKeyID: 63969577
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# System administration in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-08-18_

System administration includes the day-to-day administrative tasks, both planned and on-demand, that are required to keep an IT system operating smoothly. Typically, system administration tasks are covered by written procedures. These procedures help ensure that the same standard tools and methods are used by all support staff.

In a Lync environment, typical system administration tasks include backing up and archiving pools, monitoring logs, creating and managing users, and updating antivirus software.

<div>

## System troubleshooting

An organization must be prepared to deal with unexpected issues and should have a procedure to manage issues from the point at which they are reported until their resolution. Information about how support staff diagnosed an issue should be recorded and used in the future to avoid unnecessarily repeating completed work.

</div>

<div>

## System troubleshooting process

The following diagram shows the system troubleshooting process and the interactions with other operations roles.

**System troubleshooting flowchart**

![System Troubleshooting Flowchart](images/Dn720318.869d0b89-6473-4b1f-9d90-59604b4b8e98(OCS.15).jpg "System Troubleshooting Flowchart")

  - **Classify and Prioritize**   This task is typically performed by the service desk. For example, an issue may be grouped as a software issue or a hardware issue. The issue is then routed to the appropriate support team for investigation. The rules for determining the priority of an issue, together with the time to respond and time to resolve, are typically defined in the SLA.

  - **Investigate and Diagnose**   The appropriate support team diagnoses the issue and proposes changes to resolve the issue. If the solution is simple and does not require change control, the solution can be applied immediately. If the solution is not easy, a request for change should be raised and the proposed work should be managed by the change management process, frequently under a “fast-track” procedure. Any changes that are made should be recorded using the configuration management process.

  - **Close and Record**   After testing the resolution, the issue should be closed. If there are lessons to be learned from the issue, an entry should be created in the knowledge base.

  - **Review and Trend Analysis**   Periodic reviews of recent issues should be performed to identify issue trends. For example, if the users are experiencing frequent issues with slow logons to their Lync sites, network bandwidth issues may be the cause. Issue resolution times and the effect of any outages on system availability should be reviewed and compared with the SLA. The person who liaises with the customer on service issues, such as an account manager, should be informed of any significant issues.

</div>

<div>

## Issue management tools

Service desk tools enable staff to record, classify, and prioritize new issues. Tools will then provide the workflow processes to manage the issue service request through investigation and diagnosis, often by more than one support team. Tools, which will frequently provide reports about resolution times and historical trends, may also include a knowledge base database, which can be used to search through past issues.

The Microsoft Knowledge Base is a useful record of support issues that were encountered by Microsoft. For more information, see the Microsoft Support website (<http://go.microsoft.com/fwlink/?linkid=14898>).

Third-party software typically requires customization to suit the organization’s needs, such as the organization of teams, reporting requirements, and measures required by the SLA.

</div>

<div>

## Centralized vs. decentralized administration

Roles and responsibilities for performing system administration tasks depend on whether the organization follows a centralized model, a decentralized model, or a combination of both.

  - **Centralized Model**   In a centralized model, one or several administrative groups maintain complete control of the whole Lync Server environment. This administrative model resembles a data center where all administration tasks are performed by a single information technology group. Roles and responsibilities within the team should be defined according to experience and expertise.

  - **Decentralized Model**   Decentralized organizations are located in several geographic locations and have functioning Lync Server servers and teams of administrators in different locations. For example, there may be local administration staff and one or more servers that are running Lync Server 2013 for each country/region. Or, there may be a pool of servers that are running Lync Server 2013 and an administrative team for North America and one for Europe. Sometimes, you may want administrators to be responsible only for their own geographical area and restrict permissions to administer resources in other areas.

Lync Server also allows you to delegate specific administrative tasks to specific people or groups by using role-based access control (RBAC). RBAC allows administrators to delegate specific user rights and permissions to other administrators to perform a subset of the administrative tasks possible. By using RBAC, the user’s ability to perform specific administrative tasks depends on the RBAC roles that are assigned to the user. RBAC provides a list of cmdlets that the user can run based on the RBAC roles that the user is a member of.

</div>

</div>

<span> </span>

</div>

</div>

</div>

