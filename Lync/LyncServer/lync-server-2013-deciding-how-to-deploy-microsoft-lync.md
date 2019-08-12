---
title: 'Lync Server 2013: Deciding how to deploy Microsoft Lync'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deciding how to deploy Microsoft Lync
ms:assetid: 6ca677d3-745d-4935-8f05-19274a8bccf2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204979(v=OCS.15)
ms:contentKeyID: 48184423
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deciding how to deploy Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-03_

When planning for Lync, the first major decision is how to deploy Microsoft Lync: as Lync Server 2013 on premises, or Lync Online with Microsoft Office 365 in the cloud.

  - **Lync Server 2013 on-premises** : This choice provides the complete Lync feature set and provides ultimate flexibility in configuring, customizing, and operating your deployment. All servers are installed onsite and maintained by your organization. An on-premises deployment provides the full range of Lync Server features.

  - **Lync Online in the cloud** Lync Online is designed for organizations that want the cost and agility benefits of cloud-based instant messaging, presence, and meetings without sacrificing the business-class capabilities of Lync Server. With Lync Online, Microsoft deploys and maintains the required server infrastructure, and handles ongoing maintenance, patches, and upgrades. Some features available in an on-premises deployment are not available in Lync Online.

Which type of deployment would be best for you depends on the workloads you want to deploy, and your organization’s geographical and business status.

<div>

## Lync Server

An on-premises Lync Server deployment is best for the following scenarios:

  - **Full Enterprise Voice Capabilities**   If you plan to deploy a full Enterprise Voice solution to replace your PBX or which uses advanced calling features, an on-premises Lync Server deployment is required. On-premises supports direct connectivity with PBX systems and trunks, and advanced phone features such as response groups and call park. Lync Online does not currently support these features.

  - **Media Quality Controls**   If you want the full range of media quality assurance features, such as Call Admission Control (CAC) and Quality of Service (QoS) features, you will want an on-premises deployment .

  - **Persistent Chat**   If you need to deploy Persistent chat for your organization, you must choose an on-premises deployment.

  - **3rd-Party Server Applications**   Only on-premises deployments can work with trusted 3rd-party applications that use the Microsoft Unified Communications Managed API (UCMA).

  - **Multi-National/Multi-Regional Companies Needing Regional Support**   If you have datacenters in multiple countries or regions and need servers to be deployed and managed on a regional basis, an on-premises deployment is best, as it provides this type of regional management capabilities.

  - **Complete control over policies, reports, and upgrades**   With an on premises Lync Server deployment, you have access to the full set of server and client policies, Monitoring and other reports, and timing of upgrades. Lync Online provides a subset of policy setting and reports, and provides a limited, though significant, window for accepting upgrades.

</div>

<div>

## Lync Online

If none of the factors in the preceding list are critical for you, you may want to choose Lync Online, for simpler deployment and manageability. Lync Online provides a robust IM, presence and conferencing feature set, and also enables voice and video calls over IP between users in your organization.

</div>

</div>

<span> </span>

</div>

</div>

</div>

