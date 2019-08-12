---
title: Lync Server 2013 capacity planning calculator
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Using the Lync Server 2013 capacity planning calculator
ms:assetid: e86c1f05-1393-408a-9549-6001572ec50d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362852(v=OCS.15)
ms:contentKeyID: 56280894
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using the capacity planning calculator for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-21_

The Microsoft® Lync™ Server 2013 capacity planning calculator is available for download at <http://www.microsoft.com/en-us/download/details.aspx?id=36828>. It is designed to assist you in determining server requirements based on numbers of users and communication modalities that are enabled at your organization. You enter your organization’s profile, and the calculator provides recommendations that help you plan your topology.

The recommendations created by the calculator are for planning purposes only. Actual load simulation is required to ensure that Lync Server 2013 is adequately provisioned. To perform stress testing under a simulated load, use the [Lync Server 2013 Stress and Performance Tool](http://go.microsoft.com/fwlink/?linkid=282724).

After you have determined your user profile and the modalities that you want to enable for your users, it is time to use the calculator to plan the number of servers, memory, and bandwidth that you need. This version of the calculator does not provide guidance for disk I/O requirements.

This calculator complements the [Microsoft Lync Server](http://go.microsoft.com/fwlink/?linkid=282725) and [Microsoft Lync Server](lync-server-2013-planning.md). Use the calculator after you have reviewed the guide and created a recommended topology by using the Planning Tool.

You can benefit most from the calculator if you have accurate, detailed information about your specific user profile. For example, the percentage of voice-enabled users, average calls per user per hour, call duration, and the percentage of concurrent users in conferences can make a huge difference in server requirements. The accuracy of the recommendations created by the calculator depends on the accuracy of the information that you provide.

<div>

## Using the Capacity Calculator

The calculator is a Microsoft Excel® spreadsheet. Orange-colored cells are for input from you. Default values are entered (80,000 users in one pool with twelve Front End Servers), but you can change these values according to your organization’s needs.

The usage model contains the following sections. To calculate your capacity requirements, enter data as described:

**Instant Messaging and Presence**

  - Under Number of Users, type the number of users who will be concurrently signed in. This number is typically 80% of the total number of provisioned users. In most situations, 100% of your concurrent users will be enabled for IM and Presence. The default is 80,000.

  - Average number of contacts in Contact list indicates the number of contacts that we are using to validate your system requirements. This number is not changeable.

**Enterprise Voice**

  - In Users enabled for Enterprise Voice, type the percentage of your users who are enabled for Enterprise Voice. The default is 60%.

  - In Average number of calls per user per hour (peak), type the number of calls per hour that you expect the average user to participate in during times of peak load. The default is 4.

  - In Percentage of calls that use media bypass, type the percentage of calls placed by your users that will bypass the Mediation Server. The default is 65%.

  - In Percentage of voice users involved in UC-PSTN calls, type the percentage of your organization’s calls which are UC-PSTN phone calls. The default is 60%

  - In Percentage of voice users involved in UC-UC calls shows the percentage of users who are enabled for Enterprise Voice who will be enabled only for UC-UC calls. This number is calculated based on what you input for Percentage of voice users enabled for UC-PSTN calls.

**Conferencing**

  - In Percentage of users in concurrent conferences, type the percentage of users who will be concurrently participating in conferences. The default is 5%.

  - In Percentage of conferences with group IM only (no voice), type the percentage of conferences whose conferences will involve instant messaging only; that is, that do not include an audio component. The default is 10%

  - In Percentage of users using dial-in conferencing, type the percentage of concurrent participants in conferences who will be using dial-in conferencing. The default is 15%.

  - In Percentage of conferences using voice, type the percentage of conferences that will include an audio component.
    
      - If 20% of your voice conferences will also include regular video, select the Including video (no Multi View) check box.
    
      - If 20% of your conferences will also include Multi-View video, select the Including Multi View check box.
    
      - If 50% of your voice conferences will also include application sharing, select the Including application sharing check box.
    
      - If 20% of your voice conferences include data uploads, such as Microsoft PowerPoint® presentations, select the Including web conferencing check box.

**Mobility**

  - In Percentage of users enabled for Mobility, type the percentage of your users who will be enabled to connect to Lync Server using mobile devices. The default is 40%.

When you have entered all the necessary information, the capacity calculator estimates your requirements. The yellow cells show calculated values for CPU, memory, and bandwidth requirements based on tests performed in Lync Server 2013 performance labs. The numbers are provided as a guideline, not every single variation is tested and validated. The following values are calculated:

  - Front End CPU: Percentage of CPU usage if the entire load were being handled by one Front End Server of the same specifications as the server that was used in Microsoft testing.

  - Network in Mbps: Bandwidth requirements in megabits per second (Mbps) for the corresponding workload.

  - Memory in GB: Memory required in gigabytes (GB) for the corresponding workload.

The green cells show recommendations for the usage model that you entered.

  - Total Front End Servers: The number of physical servers required are based on dedicated servers running Lync Server 2013 with dual processor, hex-core, with 2,260 megacycles.

  - Note that enabling hyperthreading is recommended and has been proven to improve performance for servers that support audio/video.

  - Edge Servers: The number of Edge Servers required, based on 30% of all concurrent users communicating through the Edge Servers. This percentage cannot be changed in the calculator.

  - Archiving/Call Detail Recording/Quality of Experience services Store: The number of stores required for Archiving or Monitoring features, if they are enabled in your organization.

  - Back End Database Server Required (Pools Required): The number of back-end database servers required to support the selected workload.

Additionally, in the row next to Total Front End Servers, more information is provided about the load on your servers and network for all the planned workloads combined.

  - Average CPU Load: The average CPU usage per Front End server.

  - Network in Mbps: The required bandwidth allocation to support the usage model that you entered.

  - Memory in GB: Memory, in gigabytes, required for each Front End server.

</div>

<div>

## Adjusting For Your Processors

All the CPU usage figures in the spreadsheet assume that each server has a dual processor, hex-core with 2.26 GHz, at least 32 GB of memory, and 8 or more 10,000-RPM hard disk drives with at least 72 GB free disk space.

If your servers have different processors, you can adjust the figures to match your hardware.

</div>

</div>

<span> </span>

</div>

</div>

</div>

