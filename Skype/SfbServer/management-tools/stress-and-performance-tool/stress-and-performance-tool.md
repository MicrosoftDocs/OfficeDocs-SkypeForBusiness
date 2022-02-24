---
title: "Skype for Business Server 2015 Stress and Performance Tool"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
ms.date: 4/6/2016
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: IT_Skype16
ms.assetid: f2f7d19b-18c8-4a41-9b17-80d35b73d742
description: "The Skype for Business Server 2015 Stress and Performance Tool is used during capacity planning and performance tuning in non-production or test environments."
---

# Skype for Business Server 2015 Stress and Performance Tool
 
The Skype for Business Server 2015 Stress and Performance Tool is used during capacity planning and performance tuning in non-production or test environments.
  
The Skype for Business Server 2015 Stress and Performance Tool includes tools that will simplify your capacity planning for Skype for Business Server 2015. The Skype for Business Server 2015 Stress and Performance Tool will help you to:
  
- Simplify your hardware planning for Skype for Business Server
    
- Give you increased knowledge and best practices for performance tuning
    
- Measure the performance of your Skype for Business Server deployments
    
You would typically use this tool after you use the [Skype for Business Server 2015 Planning Tool](../../management-tools/planning-tool/planning-tool.md) to design the topology, and refining the topology with the [Skype for Business Server 2015 Capacity Planning Calculator](../../management-tools/capacity-planning-calculator.md). 

> [!NOTE]
> This tool will not be updated for Skype for Business Server 2019.
  
## Tests

The Stress and Performance Tool can simulate these types of user load:
  
|&nbsp;|&nbsp;|
|:-----|:-----|
|Instant Messaging (IM) and presence   |Audio conferencing   |
|Application sharing   |Voice over IP (VoIP), including public switched telephone network (PTSN) simulation   |
|Web Access Client conferencing   |Conference auto attendant   |
|Response Groups   |Distribution list expansion   |
|Address book download and address book query   |Enhanced 911 (E911) calls and location profile (dial plan)   |
|MultiView   |Data collaboration   |
|Mobility   ||
   
## Applications and files included with the Skype for Business Server 2015 Stress and Performance Tool

These applications are a part of the Skype for Business Server Stress and Performance Tool:
  
|Tool|Description|
|:-----|:-----|
|UserProvisioningTool.exe   |This tool is used to create users and contacts.   |
|UserProfileGenerator.exe   |Used to configure the characteristics of the user load you're simulating.   |
|LyncPerfTool.exe   |The tool that simulates user load.   |
|Default.tmx   |Required to use the Skype for Business Server 2015 Logging Tool.   |
|Provisioning script examples   |Used to configure the topology for running load tests, based on specific scenarios. You'll likely need to modify them to make them relevant for your particular environment.   |
   
## Topics in this section

You should review the following articles if you need to know more:
  
- [Prerequisites and setup for the Skype for Busines Stress and Performance Tool](prerequisites-and-setup.md)
    
- [Performance Scenarios for the Skype for Business Server 2015 Stress and Performance Tool](scenarios.md)
    
  - [Provisioning the topology to run load in Stress and Performance scenarios](provisioning-the-topology-to-run-load.md)
    
  - [Configuring policies for the Skype for Business Server 2015 Stress and Performance Tool](configuring-policies.md)
    
- [Using the Skype for Business Server 2015 Stress and Performance Tool](using-the-tool.md)
    
- [FAQ for the Skype for Business Server 2015 Stress and Performance Tool](faq.md)
    

