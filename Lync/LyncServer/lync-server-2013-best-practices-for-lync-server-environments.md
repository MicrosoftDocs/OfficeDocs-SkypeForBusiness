---
title: 'Lync Server 2013: Best practices for Lync Server environments'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Best practices for Lync Server environments
ms:assetid: b0e45d84-09c8-4d3e-aad0-bc6f34ce233b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720348(v=OCS.15)
ms:contentKeyID: 63969642
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Best practices for Lync Server 2013 environments

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-08-04_

The following general principles should be applied to ongoing operations of your system:

  - **Understand and utilize MOF**   MOF is a collection of best practices, principles, and models that provide organizations technical guidance about the management of IT assets, such as daily Lync Server 2013 operations. Following MOF guidelines can help you achieve mission-critical production system reliability, availability, supportability, and manageability for Microsoft products. For more information, see [Microsoft Operations Framework 4.0](http://go.microsoft.com/fwlink/p/?linkid=40939).

  - **Learn about best practices for Lync Server 2013**   We recommend that you implement practical and proven procedures to manage Lync Server 2013. By using tried, tested, and documented methods of managing operations may be more efficient than developing your own methods.

  - **Separate operations into daily, weekly, and monthly processes**   Document the required operational tasks that you'll regularly perform. Documenting how you perform tasks helps make sure that your information is preserved when there is a change in your operational environment such as when new technologies are deployed or staff changes occur. We recommend that operational tasks be separated into manageable workloads where tasks are performed daily, weekly, and monthly. Daily tasks would focus efforts on the functioning of a system, and monthly tasks would focus more on ensuring the long-term health of a system.
    
    This document can be used in environments deploying only instant messaging/presence (IM/P) components or IM/P with Enterprise Voice. When tasks or checklist items are specific to Enterprise Voice, this is mentioned and if your environment does not include Enterprise Voice the portion may be skipped.

  - **Deploy the tools that are required for operating Lync Server 2013**   Many tools are available to help troubleshoot issues, automate tasks, and help monitor and maintain the Lync Server 2013 environment. Define a standard set of tools for your organization so the tasks that are performed by the operations team are performed accurately, efficiently, consistently, and in a controlled manner. You should also implement processes to track incidents and major configuration changes.

<div>

## Reference

For the benefit of readers not already familiar with the basics of server management in general, we provide an overview of server management practices. Readers already familiar with server management may choose to skip this section.

Best practices are recommendations that are based on the knowledge and experience that IT professionals have gained across many environments. They provide standard procedures for typical tasks that your Lync Server administrators must perform daily, and list the tools that they should use to manage a Lync Server environment.

Typical tasks for Lync administrators include the following:

  - **Capacity and Availability Management**   Define how and what to measure to predict future capacity requirements and to report about the capacity, reliability, and availability of your systems. You must verify that servers that are running Lync Server are sized to handle the load on the system, and that unplanned downtime is kept under the levels defined in the service level agreement (SLA). Additionally, you'll have to upgrade hardware to continue to meet the defined requirements.

  - **Change Management and Configuration Management**   Control how changes are made to IT systems. This should include testing, application feedback and contingency plans, documentation of all changes, and approval from management if issues occur. Keep a record of your software and hardware assets and their configurations.

  - **System Administration**   Outline standard methods for doing administrative tasks such as database administration and site administration.

  - **Security Administration**   Have a detailed policy and plan that protects data confidentiality, data integrity, and data availability of the IT infrastructure. This includes day-to-day activities and tasks that are related to maintaining and adjusting the IT security infrastructure.

  - **System Troubleshooting**   Outline methods for dealing with unexpected issues, including steps to prevent similar issues in the future.

  - **Service Level Agreements**   Maintain a set of goals for the performance of the IT systems and regularly measure performance against these goals.

  - **Documentation**   Document standard procedures, such as configuration information and lessons learned, and make them available to the staff members that need them. As changes to the configuration are made, update the documentation accordingly.

</div>

<div>

## Related Sections

Review the following topics concerning system operations before proceeding:

  - [Capacity and availability management in Lync Server 2013](lync-server-2013-capacity-and-availability-management.md)

  - [Change management in Lync Server 2013](lync-server-2013-change-management.md)

  - [Configuration management in Lync Server 2013](lync-server-2013-configuration-management.md)

  - [System administration in Lync Server 2013](lync-server-2013-system-administration.md)

  - [Service level agreements in Lync Server 2013](lync-server-2013-service-level-agreements.md)

  - [Documentation in Lync Server 2013](lync-server-2013-documentation.md)

  - [Standard procedures in Lync Server 2013](lync-server-2013-standard-procedures.md)

  - [Emergency procedures in Lync Server 2013](lync-server-2013-emergency-procedures.md)

</div>

<div>

## See Also


[Microsoft Operations Framework 4.0](http://go.microsoft.com/fwlink/p/?linkid=40939)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

