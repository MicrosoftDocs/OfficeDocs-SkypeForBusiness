---
title: "FAQ for the Skype for Business Server 2015 Stress and Performance Tool"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
ms.date: 11/11/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: ce18db60-5f6b-423d-bc41-91e7c80fb7e3
description: "Skype for Business 2015 Stress and Performance Tool frequently asked questions (FAQ), useful for finding out what tool configurations are supported, troubleshooting tool issues, and clarifying behaviours you may see when running the Stress and Performance tools."
---

# FAQ for the Skype for Business Server 2015 Stress and Performance Tool
 
Skype for Business 2015 Stress and Performance Tool frequently asked questions (FAQ), useful for finding out what tool configurations are supported, troubleshooting tool issues, and clarifying behaviours you may see when running the Stress and Performance tools.
  
 This FAQ covers some of the most frequently asked questions about the Skype for Business Server 2015 Stress and Performance tool, and may help with troubleshooting and tool configuration choices.
  
## Can I run LyncPerfTool.exe in production?

This is **not** recommended. The tool would impact your production server performance, security, and the end user experience.
  
## I'm logging my users on for the first time. Why are my servers running a high load?

The first time the users log on, additional operations occur in the background. As a result, the performance on the Microsoft SQL Server Back End Server can be degraded. It's recommended that you run a short test that logs on all of your users, and then restart the clients before you begin to measure results with the tool. Skype for Business Server doesn't support more than 12 concurrent user logon sessions per second, but please be aware the actual number that can be handled by your servers depends on your hardware configuration, and may be lower than the supported value.
  
## My clients are running out of memory! What should I do?

If clients are running out of memory, you should reduce the number of users logged on per Skype for Business Server Front End pool. You can also choose to scale out Front End pools if the problem is persistent.
  
## Can I run this tool on a Skype for Business server, itself?

You shouldn't do that. This scenario isn't supported because it may fail due to a binary mismatch, and also because the goal is to measure resource consumption on the server. Actually running the tool there would impact server performance and invalidate your data and measurements.
  
## Can I run LyncPerfTool.exe on a Virtual Server or on Microsoft Hyper-V Server 2008/2012?

Yes you can.
  
## What does MPOP mean?

MPOP is a shortened way of saying "multiple points of presence". MPOP is meant to simulate scenarios where users are logged on to Skype for Business 2015 client from multiple machines or devices. Be aware that, in LyncPerfTool.exe, each endpoint uses the default profile. In other words, the profile isn't split between two points of presence.
  
## I started LyncPerfTool.exe but nothing is happening. What's going on?

Check the Total Active Endpoints counter on the servers to see if the users are connecting. If the users aren't connecting, verify your Skype for Business Server 2015 configuration. The issue you're seeing usually occurs because one of server name, user prefix, or password, is incorrect. Take note that external clients should specify Access Proxy and TargetServer values. Verify the port number in the configuration file.
  
## How can I be sure that something is being measured?

There are LyncPerfTool performance counters that indicate whether or not users are connecting and performing actions, but the easiest way to make sure actions are being measured is to log on to one of the accounts with a Skype for Business 2015 client and do those actions yourself. Check the results to confirm measurements were taken.
  
## I have Lync Server 2010 Capacity Planning Tools and/or Lync Server 2013 Capacity Planning tools installed. Is that okay?

 These tools have interoperability issues! You must uninstall all the previous versions of these tools to get valid data from the Skype for Business Server 2015 Stress and Performance tool.
  
## Will the Stress and Performance tools set up the CAA Call Information server topology?

No, the tools won't do this. The tools only create users, contacts, and distribution lists, to simulate user load.
  
## What is the maximum number of users that the tools support?

In testing, we've created up to a total of 80,000 users, and executed tests totaling 30,000 users running these tools. We suggest a maximum of 120,000 users, although the technical limitations allow for a higher values. Remember that these values depend on the server and hardware in your environment.
  

