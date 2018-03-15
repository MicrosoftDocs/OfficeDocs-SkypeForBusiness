---
title: "System administration in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 063eb962-b96a-4699-8579-bb7125112df4
description: "In this articleSystem troubleshootingSystem troubleshooting processIssue management toolsCentralized vs. decentralized administration"
---

# System administration in Lync Server 2013
[]
 **In this article**
  
[System troubleshooting](#sectionSection0)
  
[System troubleshooting process](#sectionSection1)
  
[Issue management tools](#sectionSection2)
  
[Centralized vs. decentralized administration](#sectionSection3)
  
System administration includes the day-to-day administrative tasks, both planned and on-demand, that are required to keep an IT system operating smoothly. Typically, system administration tasks are covered by written procedures. These procedures help ensure that the same standard tools and methods are used by all support staff.
  
In a Lync environment, typical system administration tasks include backing up and archiving pools, monitoring logs, creating and managing users, and updating antivirus software.
  
## System troubleshooting
<a name="sectionSection0"> </a>

An organization must be prepared to deal with unexpected issues and should have a procedure to manage issues from the point at which they are reported until their resolution. Information about how support staff diagnosed an issue should be recorded and used in the future to avoid unnecessarily repeating completed work.
  
## System troubleshooting process
<a name="sectionSection1"> </a>

The following diagram shows the system troubleshooting process and the interactions with other operations roles.
  
**System troubleshooting flowchart**

![System Troubleshooting Flowchart](media/Lync_OpsGuide_System_Troubleshooting_Flowchart.jpg)
  
- **Classify and Prioritize** This task is typically performed by the service desk. For example, an issue may be grouped as a software issue or a hardware issue. The issue is then routed to the appropriate support team for investigation. The rules for determining the priority of an issue, together with the time to respond and time to resolve, are typically defined in the SLA. 
    
- **Investigate and Diagnose** The appropriate support team diagnoses the issue and proposes changes to resolve the issue. If the solution is simple and does not require change control, the solution can be applied immediately. If the solution is not easy, a request for change should be raised and the proposed work should be managed by the change management process, frequently under a "fast-track" procedure. Any changes that are made should be recorded using the configuration management process. 
    
- **Close and Record** After testing the resolution, the issue should be closed. If there are lessons to be learned from the issue, an entry should be created in the knowledge base. 
    
- **Review and Trend Analysis** Periodic reviews of recent issues should be performed to identify issue trends. For example, if the users are experiencing frequent issues with slow logons to their Lync sites, network bandwidth issues may be the cause. Issue resolution times and the effect of any outages on system availability should be reviewed and compared with the SLA. The person who liaises with the customer on service issues, such as an account manager, should be informed of any significant issues. 
    
## Issue management tools
<a name="sectionSection2"> </a>

Service desk tools enable staff to record, classify, and prioritize new issues. Tools will then provide the workflow processes to manage the issue service request through investigation and diagnosis, often by more than one support team. Tools, which will frequently provide reports about resolution times and historical trends, may also include a knowledge base database, which can be used to search through past issues.
  
The Microsoft Knowledge Base is a useful record of support issues that were encountered by Microsoft. For more information, see the Microsoft Support website ([https://go.microsoft.com/fwlink/?linkid=14898](https://go.microsoft.com/fwlink/?linkid=14898)).
  
Third-party software typically requires customization to suit the organization's needs, such as the organization of teams, reporting requirements, and measures required by the SLA. 
  
## Centralized vs. decentralized administration
<a name="sectionSection3"> </a>

Roles and responsibilities for performing system administration tasks depend on whether the organization follows a centralized model, a decentralized model, or a combination of both.
  
- **Centralized Model** In a centralized model, one or several administrative groups maintain complete control of the whole Lync Server environment. This administrative model resembles a data center where all administration tasks are performed by a single information technology group. Roles and responsibilities within the team should be defined according to experience and expertise. 
    
- **Decentralized Model** Decentralized organizations are located in several geographic locations and have functioning Lync Server servers and teams of administrators in different locations. For example, there may be local administration staff and one or more servers that are running Lync Server 2013 for each country/region. Or, there may be a pool of servers that are running Lync Server 2013 and an administrative team for North America and one for Europe. Sometimes, you may want administrators to be responsible only for their own geographical area and restrict permissions to administer resources in other areas. 
    
Lync Server also allows you to delegate specific administrative tasks to specific people or groups by using role-based access control (RBAC). RBAC allows administrators to delegate specific user rights and permissions to other administrators to perform a subset of the administrative tasks possible. By using RBAC, the user's ability to perform specific administrative tasks depends on the RBAC roles that are assigned to the user. RBAC provides a list of cmdlets that the user can run based on the RBAC roles that the user is a member of.
  

