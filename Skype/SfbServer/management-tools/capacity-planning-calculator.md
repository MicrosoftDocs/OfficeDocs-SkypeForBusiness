---
title: "Skype for Business Server Capacity Planning Calculator"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: bc4d93b1-0c38-4bf8-8b65-692ff3e2446d
description: "Summary: How to use the Capacity Calculator Tool."
---

# Skype for Business Server Capacity Planning Calculator
 
**Summary:** How to use the Capacity Calculator Tool.

> [!NOTE]
> This article references Skype for Business Server 2015 downloads, but it applies to:
> - Skype for Business Server 2019.
> - Skype for Business Server 2015.
  
The [Skype for Business Server 2015 Capacity Calculator](https://www.microsoft.com/en-us/download/details.aspx?id=51196) and [Skype for Business Server 2019 Capacity Calculator](https://www.microsoft.com/en-us/download/details.aspx?id=57509) augment the [Skype for Business Planning Tool](https://www.microsoft.com/en-us/download/details.aspx?id=50357) and your deployment documentation ([Plan for your Skype for Business Server 2015 deployment](../plan-your-deployment/plan-your-deployment.md) and [Plan for your Skype for Business Server 2019 deployment](../../SfBServer2019/plan/plan-your-deployment-2019.md) respectively). Use the calculator after you have reviewed the guide and created a recommended topology by using the Planning Tool.
  
The Skype for Business Server Capacity Calculator helps you determine server requirements based on the number of users and the communication tools your organization uses. After you have determined your user profile and the functions you want to enable for your users, use the calculator to determine the number of servers, memory, and bandwidth you will need. This version of the calculator does not provide guidance for disk I/O requirements.
  
You can benefit most from the calculator if you have accurate, detailed information about your specific user profile. For example, the percentage of voice-enabled users, average calls per user per hour, call duration, and the percentage of concurrent users in conferences can make a huge difference in server requirements. The accuracy of the recommendations created by the calculator depends on the accuracy of the information that you provide.
  
Once you have used the Planning Tool and the Capacity Planning Calculator, you should simulate your proposed and planned load to ensure that Skype for Business Server will be adequately provisioned. To perform stress testing under a simulated load, use the [Skype for Business Server Stress and Performance Tool](https://www.microsoft.com/en-us/download/details.aspx?id=50367) documented at [Skype for Business Server Stress and Performance Tool](https://technet.microsoft.com/en-us/library/mt631400.aspx).
  
## Using the Capacity Calculator

The calculator is a Microsoft Excel spreadsheet. Your input cells are colored orange. Default values are entered in the cells (For Skype for Business Server 2015, 80,000 users in one pool with twelve Front End Servers, while for Skype for Business Server 2019, 106,000 users in one pool with sixteen Front End Servers), but you should change these values to match your organization's needs.
  
The usage model contains the following sections. To calculate your capacity requirements, enter data as described starting at the top of the sheet and working down row by row: 
  
 **Instant Messaging and Presence**
  
- Under **Number of Users**, type the number of users who will be signed in at once. This number is typically 80% of the total number of provisioned users. In most situations, 100% of your concurrent users will be enabled for IM and Presence. The default is 80,000 for Skype for Business Server 2015, and 106,000 users for Skype for Business Server 2019.
    
- **Average number of contacts in Contact list** indicates the number of contacts that we are using to validate your system requirements. This number is fixed and not something you should change.
    
  **Enterprise Voice**
  
- In **Users enabled for Enterprise Voice**, type the percentage of your users enabled for Enterprise Voice. The default is 60%. 
    
- In **Average number of calls per user per hour (peak)**, type the number of calls per hour you expect the average user to participate in during times of peak load. The default is 4. 
    
- In **Percentage of calls that use media bypass**, type the percentage of calls placed by your users that will bypass the Mediation Server. The default is 65%, but could be lower if you are spread out geographically or have a large percentage of users who work from home.
    
- In **Percentage of voice users involved in UC-PSTN calls**, type the percentage of your organization's calls which are UC-PSTN phone calls. The default is 60%.
    
- **Percentage of voice users involved in UC-UC calls** shows the percentage of users who are enabled for Enterprise Voice who will be enabled only for UC-UC calls. This number is calculated based on what you input for **Percentage of voice users enabled for UC-PSTN calls**. 
    
  **Conferencing**
  
- In **Percentage of users in concurrent conferences**, type the percentage of users who will be participating in conferences at the same time. The default is 5%. 
    
- In **Percentage of conferences with group IM only (no voice)**, type the percentage of conferences that will involve instant messaging only and do not include audio. The default is 10%
    
- In **Percentage of users using dial-in conferencing**, type the percentage of participants in conferences who will be using dial-in conferencing at one time. The default is 15%.
    
- In **Percentage of conferences using voice**, type the percentage of conferences that will include audio. 
    
  - If 20% of your voice conferences will also include regular video, select the **Including video (no Multi View)** check box.
    
  - If 20% of your conferences will also include Multi-View video, select the **Including Multi View** check box.
    
  - If 50% of your voice conferences will also include application sharing, select the **Including application sharing** check box.
    
  - If 20% of your voice conferences include data uploads, such as PowerPoint presentations, select the **Including web conferencing** check box.
    
  **Mobility**
  
- In **Percentage of users enabled for Mobility**, type the percentage of your users who will be enabled to connect to Skype for Business Server using mobile devices. The default is 40%. 
    
When you have entered all the necessary information, the capacity calculator estimates your requirements. The yellow cells show calculated values for CPU, memory, and bandwidth requirements based on tests performed in Skype for Business Server performance labs. The numbers are provided as a guideline, not every single variation is tested and validated. The following values are calculated: 
  
- **Front End CPU**: Percentage of CPU usage if the entire load were being handled by one Front End Server of the same specifications as the server that was used in testing (see the description at the end of this article).
    
- **Network in Mbps**: Bandwidth requirements in megabits per second (Mbps) for the corresponding workload.
    
- **Memory in GB**: Memory required in gigabytes (GB) for the corresponding workload.
    
The green cells show recommendations for the usage model that you entered. 
  
- **Total Front End Servers**: The number of physical servers required are based on dedicated servers running Skype for Business Server 2015 with dual processor, hex-core, with 2,260 megacycles, or Skype for Business Server 2019 with Intel Xeon E5-2673 v3, dual processor, hex-core.
    
    Note that enabling hyperthreading is recommended and has been proven to improve performance for servers that support audio/video.
    
- **Edge Servers**: The number of Edge Servers required, based on 30% of all concurrent users communicating through the Edge Servers. This percentage cannot be changed in the calculator. 
    
- **Archiving/Call Detail Recording/Quality of Experience services Store**: The number of stores required for Archiving or Monitoring features, if they are enabled in your organization.
    
- **Back End Database Server Required (Pools Required)**: The number of back-end database servers required to support the selected workload.
    
Additionally, in the row next to Total Front End Servers, more information is provided about the load on your servers and network for all the planned workloads combined.
  
- **Average CPU Load**: The average CPU usage per Front End server.
    
- **Network in Mbps**: The required bandwidth allocation to support the usage model that you entered.
    
- **Memory in GB**: Memory, in gigabytes, required for each Front End server.
    
### Adjusting For Your Processors

All the CPU usage figures in the spreadsheet assume that each Skype for Business Server 2015 server has a dual processor, hex-core with 2.26 GHz, at least 32 GB of memory, and 8 or more 10,000-RPM hard disk drives with at least 72 GB free disk space. For each Skype for Business Server 2019 server, all the CPU usage figures in the spreadsheet assume that each server has a dual processor, hex-core with Intel Xeon E5-2673 v3, at least 64 GB of memory, and 8 or more 10,000-RPM hard disk drives with at least 72 GB free disk space.
  
If your servers have different processors, you can adjust the figures to match your hardware.
  
