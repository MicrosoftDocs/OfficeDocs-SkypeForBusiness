---
title: Lync Server 2013 Stress and Performance Tool FAQ
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Lync Server 2013 Stress and Performance Tool FAQ
ms:assetid: a5aff705-320c-4916-8094-23046b2a1b18
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945600(v=OCS.15)
ms:contentKeyID: 51541426
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Lync Server 2013 Stress and Performance Tool FAQ

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-24_

<div>

## Frequently Asked Questions

Here are some frequently asked questions about the Lync Server 2013 Stress and Performance Tool.

<div>

## Can I run LyncPerfTool.exe in production?

We do not recommend this. This tool will impact server performance, security, and user experience.

</div>

<div>

## I am logging on my users for the first time. Why are the servers running at such high load?

The first time the users log on, there are additional operations that occur. As a result, the performance on the Microsoft SQL Server Back End Server will be degraded. We recommend that you run a short test that logs on all of the users, and then restart the clients before you measure results. We do not support more than 12 concurrent user logon sessions per second, but this depends on your hardware configuration.

</div>

<div>

## My clients are running out of memory. What should I do?

If your clients are running out of memory, you need to reduce the number of users per computer.

</div>

<div>

## My clients are at 100 percent CPU all the time. What should I do?

If your clients are running with very high CPU after all the users have logged on, you need to reduce the number of users per computer. High CPU spikes are acceptable, but if it is sustained, you need to reduce the load.

</div>

<div>

## Can I run the tool on the server itself?

No. This scenario is not supported and may fail due to a binary mismatch. Also, because the point is to measure resource consumption on the server, running the tool there would render the measurements meaningless.

</div>

<div>

## Can I run LyncPerfTool.exe on a Virtual Server or on Microsoft Hyper-V Server 2008/2012?

Yes.

</div>

<div>

## What does MPOP mean?

MPOP stands for multiple points of presence. It is meant to simulate the scenario where users are logged on to Lync 2013 from multiple machines. Note that in LyncPerfTool.exe, each endpoint uses the default profile (that is, the profile is not split between the two points of presence).

</div>

<div>

## I started LyncPerfTool.exe but nothing is happening. What’s going on?

Check the Total Active Endpoints counter on the clients to see if the users are connecting. If users are not connecting, verify your Lync Server 2013 configuration. This issue usually occurs because the server name, the user prefix, or the password is incorrect. Note that external clients should specify the Access Proxy as the TargetServer value. Verify the port in the configuration file.

</div>

<div>

## How do I know something is happening?

The various LyncPerfTool performance counters indicate whether or not users are connecting and performing actions. However, an easy way to check is to log on to one of the accounts by using Lync 2013 and performing the action you want.

</div>

<div>

## I have Live Communications Server 2007 R2 Capacity Planning Tools and/or Lync Server 2010 installed. Is that OK?

No. There are interoperability issues, and you must uninstall all previous versions of this product.

</div>

<div>

## Will the Stress and Performance tools set up the CAA Call Information server topology?

No. The tools only create users, contacts, and distribution lists, and simulate user load.

</div>

<div>

## What is the maximum number of users that the tools support?

We have created up to a total of 80,000 users and executed tests totaling 30,000 users, using these tools. We suggest a maximum of 120,000 users, although the technical limitations allow for a higher value, depending on the client and server hardware available.

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

