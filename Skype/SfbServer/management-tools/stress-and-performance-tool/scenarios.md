---
title: "Performance Scenarios for the Skype for Business Server 2015 Stress and Performance Tool"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
ms.date: 12/17/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: d972382f-971e-4fa7-b7ee-8ab9d3a5c11d
description: "Tasks you'll need to do to configure Skype for Business Server 2015 to do performance and load-testing, using the Stress and Performance Tool."
---

# Performance Scenarios for the Skype for Business Server 2015 Stress and Performance Tool
 
Tasks you'll need to do to configure Skype for Business Server 2015 to do performance and load-testing, using the Stress and Performance Tool.
  
To run the Skype for Business Server 2015 Stress and Performance Tool (LyncPerfTool), the Skype for Business Server 2015 topology must first be configured for scenarios relevant to you. If Skype for Business Server 2015 isn't configured, or is configured incorrectly, your load simulation is very likely to fail. With the Skype for Business Server 2015 Stress and Performance Tool, we're providing example Skype for Business Server Management Shell scripts and basic resource files as part of the [tool download](https://www.microsoft.com/download/details.aspx?id=50367). These can be used as a starting point for configuring your Skype for Business Server deployment. This article describes the Windows PowerShell examples provided.
  
> [!NOTE]
> This topic won't help you describe how to configure Skype for Business Server 2015 generally, we have other Planning and Deployment topics for that. For details about working with Windows PowerShell in Skype for Business Server 2015, see the Skype for Business Server Management Shell documentation at Insert introduction HERE. 
  
## About running Skype for Business Server management shell scripts

We're providing sample PowerShell scripts you can use to prepare for your load simulations. Because these scripts are intended for load simulation, you'll find them to be simple and permissive. That may not be appropriate for your production environment. Again we stress that these scripts are samples, you'll need to review them and in many cases make changes relevant to your environment before being able to make practical use of them. At a minimum, we'd expect you'd need to modify the Response Service Group (RSG) script with your topology in mind (to specify the agents assigned to the agent groups). But you don't have to run that, if you don't need to.
  
> [!CAUTION]
> Please take care in reviewing and understanding these samples. Scripts will overwrite any existing settings in the topology when run. 
  
## Stress and Performance Tool client version names

You might need to configure the Client Version Check policy if you've previously changed the settings from the default values. If you're unsure about this, check the [Client Version Check documentation](https://msdn.microsoft.com/en-us/vsto/jj923060).
  
The Stress and Performance Tool uses the following User Agent versions by default when communicating with Skype for Business Server 2015:
  
- LSPT/15.0.0.0 (Skype for Business Server 2015 Stress and Performance Tool)
    
- OCPHONE/.0.522
    
For the Mobility (UCWA) client in LyncPerfTool:
  
- UCWA Perf Tool/Web Conference
    
- UCWA Perf Tool/Mobile
    

