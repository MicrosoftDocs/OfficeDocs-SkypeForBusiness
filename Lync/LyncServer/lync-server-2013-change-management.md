---
title: 'Lync Server 2013: Change management'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Change management
ms:assetid: 73c774f5-c12f-4c72-be73-e07dc745b994
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720336(v=OCS.15)
ms:contentKeyID: 63969618
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Change management in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-08-18_

Changes to the IT environment are unavoidable. Changes include new technologies, systems, applications, hardware, tools, processes, and changes in roles and responsibilities. An effective change management system lets you introduce changes to the IT environment quickly and with minimal service disruption. A change management system brings together the teams involved in changing a system. For example, deciding to take advantage of the Office Web Apps. This is an integrated Lync Service application that enables users to read and edit documents in a browser. The implementation of this service, after you have gone into production, requires the involvement of several teams:

  - **Test Team**   This team load-tests the Office Web Apps on a test server, in the process providing information about the expected usage patterns and expected performance of the production servers.

  - **Lync Administrators**   This team determines the deployment strategy and scripts the installation where it was possible. The team is responsible for making sure that the change is deployed on the production environment, and it is responsible for administration afterward. The team must understand the effect of the changes and incorporate them in procedures before the changes are put into production

  - **Network Team**   This team is responsible for changes to firewall rules that allow access from the Internet to the internal Lync pool servers. The team is also responsible in working with the Lync administrators for making sure that the available bandwidth can support the additional load.

  - **Security Team**   This team assesses security and minimizes risks. The security team must review known vulnerabilities and help ensure that security risks are minimized.

  - **User Acceptance Team**   This team is composed of users who are willing to test the system and offer feedback for improvements.

The change management process defines the responsibilities of each team and schedules the work to be performed, incorporating checks and tests where they are required. Change controls will vary depending on the complexity and expected effect of a change. They can vary from automatic approval of minor changes, to change review meetings, to full project-level reviews. To explain this better, the groups of changes are discussed in this section.

  - **Major Changes**   Major changes have a global effect on the system and may require input from various teams. An example of this is upgrading to Lync Server 2013. Major changes affect many teams and perhaps different systems. The change management process will probably include one or more change review meetings to inform the teams that will be involved in the change or be affected by the change.

  - **Significant Changes**   Significant changes require significant resources to plan, build, and implement. Appropriate change controls should be introduced to help make ensure that the effect of the change is understood, deployment procedures are tested, and the rollback and contingency plans are ready. An example of a significant change is deploying a new cumulative update.

  - **Minor Changes**   Minor changes do not significantly affect the IT environment, for example, changing certain Lync policies via the Microsoft Lync Server 2013 Control Panel.

  - **Standard Changes**   Standard changes are performed regularly and are well understood and documented. The change management process should review all changes to the procedures. It should not be needed for routine changes like creating a content database or adding a user.

The following example of change management examines how different teams interact and the actions that are performed when a new service pack is deployed. These actions are organized and managed by the change management process.

  - **Raise a change request**   The security team has assessed the latest service pack and confirmed that it resolves a possible vulnerability in the production system. The team raises a change request to have the new cumulative update applied to all servers that are running Lync Server.

  - **Service pack release notes review**   The Lync administrator team reviews the service pack release notes to identify the effect on the system.

  - **A series of lab tests is performed**   The Lync administrator team must perform test updates on a server in a test environment to decide whether the service pack can be applied successfully without affecting any of the installed applications and server systems. If there are third-party or internally created applications that interface with Lync Server in a production environment, these should be also tested. These tests can also be used to estimate the time that is required to perform the upgrades.

  - **Users are informed of the outage**   The Lync administrator team, communications team, or user help desk informs all affected users about the planned maintenance cycle and how long the service will be unavailable.

  - **A full backup of Lync is performed before the upgrade**   The Lync administrator team must verify that there is a valid backup that can be used to revert to the original system state if the service pack installation fails. We recommend that the backup be restored to a standby server to have this system readily available if there are issues.

  - **The cumulative update is deployed**   The Lync administrator team does the installation during the planned maintenance cycle.

<div>

## Managing the timing of changes

We recommend that you implement a procedure for scheduling changes to avoid disruptions in overlapping sections of your work. For example, two teams may both be planning a minor change to a system. One team may be applying a cumulative update on a pool while another team is migrating legacy users into that pool. Neither team is affected by the changes that the other team is planning, and each team may not necessarily know about changes that the other team is planning. If both changes occurred at the same time, there might be issues implementing the changes. Also, if there are issues after the changes were applied, for example, if the user migration fails, it may be difficult to decide which change should be rolled back. There should be regular maintenance periods set up between IT and management to test the changes and accept them.

</div>

</div>

<span> </span>

</div>

</div>

</div>

