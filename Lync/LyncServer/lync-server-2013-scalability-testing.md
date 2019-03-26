---
title: Lync Server 2013 scalability testing
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Scalability testing
ms:assetid: bf41bac6-d4ec-4de6-9a44-a82d01a87279
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205226(v=OCS.15)
ms:contentKeyID: 48185289
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Scalability testing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

Lync Server 2013 provides the server infrastructure for all Lync Server real-time communications, including instant messaging (IM) and presence, conferencing, and Enterprise Voice. This includes any features that use the hardware resources of a Lync Server 2013 pool and, therefore, affect performance and scale. All organizations do not use all features equally.

For example, some organizations might use video in conferences very heavily while others might have little or no video usage. Some organizations prefer PowerPoint slide sharing to application sharing, while others prefer the opposite. Those organizations that deploy Enterprise Voice might or might not use the Response Group application heavily. Most organizations deploy Monitoring Servers, but not many of them deploy Archiving Servers. Additionally, organizations do not all have the same infrastructures, including hardware capacities, network capacities, and the number of pools and size of pools deployed. The diversity of features and infrastructures poses a challenge to scalability testing – it is not possible to simulate all possible combinations of features and infrastructures.

To determine scalability support for Lync Server, we conduct testing by using all Lync Server features concurrently, based on an average usage model (user model). To determine an appropriate user model for Lync Server workloads, we analyze many data points, including customer surveys, feedback from the Microsoft customer experience improvement program, Lync Server usage data from the internal IT department at Microsoft, and data mined from our Live Meeting Service. In many cases, the user model has a bias towards heavier loads to provide a comfortable margin for usage within an organization.

In our scalability tests, we set up Lync Server 2013 pools according to the recommended hardware and software specifications, including infrastructure components, such as Active Directory Domain Services, hardware load balancers, and firewalls. We set up Lync Server environments as closely as possible to typical real-world environments. We then use the Lync Server 2013 Stress and Performance Tool to simulate Lync Server 2013 loads (based on our user model). .

We do multiple iterations of scalability tests (including multiple three-week test runs). We use the results of all tests to help with performance tuning and to verify support for the scalability numbers in our user model.

</div>

<span> </span>

</div>

</div>

</div>

