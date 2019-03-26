---
title: 'Lync Server 2013: Establishing a backup and restoration plan'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Establishing a backup and restoration plan
ms:assetid: 9f562ef1-3804-41e2-b3e4-d45b2e8c63c9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202183(v=OCS.15)
ms:contentKeyID: 51541499
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Establishing a backup and restoration plan for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-17_

Creating a backup and restoration plan involves the following steps:

  - Developing the plan.

  - Implementing the plan.

  - Maintaining the plan.

<div>

## Developing a Backup and Restoration Plan

After you develop your backup and restoration strategy for Lync Server, use it to document a detailed backup and restoration plan. Your plan should clearly convey the priorities and requirements for backing up data and settings. You can use the information in [Establishing a backup and restoration strategy for Lync Server 2013](lync-server-2013-establishing-a-backup-and-restoration-strategy.md) and the worksheets in [Backup and restoration worksheets for Lync Server 2013](lync-server-2013-backup-and-restoration-worksheets.md) to facilitate the documentation of your strategy. Your plan should also contain criteria for deciding when and how to restore service.

As you develop your plan, you need to consider, and account for, the following:

  - How you will recover servers on new hardware.

  - How you will recover services that require action on the part of multiple business areas or departments.

  - How you can acquire spare servers quickly.

  - The time it takes to recover by using your strategy. Consider your organization’s requirements for recovery time objective (RTO).

Modify the backup and restoration procedures in this topic, adding and deleting procedures as appropriate, to reflect the servers and components in your deployment. You can also add appropriate details, such as the backup schedule, to the appropriate procedures to make sure that the information is not overlooked.

<div>


> [!NOTE]  
> It is good practice to create scripts for as many steps as possible, to help ensure the quality and reproducibility of procedures.



</div>

In your plan, specify who is responsible for reviewing the plan, who is responsible for testing and validating any new procedures or tools, and who must approve any changes to the plan and related procedures.

To make sure that your backup and restoration plan fully meets all established goals and priorities, get the approval of the appropriate business decision makers and technical decision makers in your organization before you implement the plan.

</div>

<div>

## Implementing the Backup and Restoration Plan

Implementing a backup and restoration plan requires the following steps:

  - Testing and validating the plan.

  - Communicating the plan.

  - Validating backup and restoration operations.

<div>

## Testing and Validating the Plan

The procedures described here have been tested and validated in a lab environment. To make sure that these or any other procedures work in your environment, you should test and validate each procedure you intend to implement. Complete the testing and the validation before you submit your plan for final approval.

</div>

<div>

## Communicating the Plan

Your backup and restoration plan should clearly describe who implements procedures and step-by-step instructions for carrying out the procedures. You should make sure that everyone responsible for any aspect of backup and restoration understands the plan, how it is to be implemented, and what their role is. This includes all implementation requirements for the following:

  - Pool and server backup.

  - Restoration of service.

**Pool and server backup**

The backup and restoration plan should include all information required to complete backup procedures on an ongoing basis. The primary information to be communicated to responsible team members includes the following:

  - Team or person (specified as an individual or role) responsible for backing up each server.

  - Specific schedules for backing up each server.

  - Backup locations for each type of data (settings, database, and file shares).

  - Backup procedures to be used, including the tools required to complete each procedure.

  - Information required to complete backups, as covered in [Backup and restoration worksheets for Lync Server 2013](lync-server-2013-backup-and-restoration-worksheets.md).

  - Validation methods to be used to help ensure that data and settings are appropriately backed up and available for restoration, which can include periodic audits and test restorations.

**Restoration of service**

The backup and restoration plan should include all information required to restore service, in case one or more servers experience a loss that makes service unavailable. The primary information to be communicated to responsible team members includes the following:

  - Team or person (specified as an individual or a role) that is responsible for determining when restoration of service is required and the procedures to be used to restore service, and also the team or person responsible for implementing procedures for each restoration scenario.

  - Criteria for determining which restoration procedures are most appropriate for a specific situation.

  - Time estimates for restoration of service and recovery time objective (RTO) in each restoration scenario.

  - Restoration procedures to be used, including the tools required to complete each procedure.

  - Information required to restore data and settings. Worksheets are provided in [Backup and restoration worksheets for Lync Server 2013](lync-server-2013-backup-and-restoration-worksheets.md).

</div>

<div>

## Validating Backup and Restoration Operations

After completing initial backup efforts in your production environment and at specified intervals (as covered in your backup and restoration plan), you should verify the following:

  - Backups are occurring as required.

  - Backed-up data and settings are accessible.

  - Restoration procedures can be performed within the recovery time objective (RTO) times specified in the backup and restoration plan, and the results meet all business requirements.

  - Backup worksheets have been completed and verified, and they are stored in a secure location. These worksheets are provided in [Backup and restoration worksheets for Lync Server 2013](lync-server-2013-backup-and-restoration-worksheets.md).

  - Restoration procedures have been tested and verified to work as expected, as specified in your backup and restoration plan.

</div>

</div>

<div>

## Maintaining the Backup and Restoration Plan

A Lync Server topology is a dynamic environment that changes with your organization. Reassess your backup and restoration plan as your organization changes, and review it periodically to make sure that it continues to meet the needs of your business.

</div>

</div>

<span> </span>

</div>

</div>

</div>

