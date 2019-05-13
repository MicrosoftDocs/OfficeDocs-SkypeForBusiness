---
title: "Prerequisites and setup for the Skype for Busines Stress and Performance Tool"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
ms.date: 12/20/2018
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 948c176c-75ce-418d-891a-a68427d61e40
description: "Requirements or prerequisites for the Skype for Business Server 2015 Stress and Performance Tool. How to install or setup the Stress and Performance Tool."
---

# Prerequisites and setup for the Skype for Busines Stress and Performance Tool
 
Requirements or prerequisites for the Skype for Business Server 2015 Stress and Performance Tool. How to install or setup the Stress and Performance Tool.
  
We have the following sections of hardware, software and system configuration requirements you'll need to be aware of prior to running the Stress and Performance Tool:
  
- [Client hardware requirements](prerequisites-and-setup.md#ClientHardwareReqs)
    
- [Client software requirements](prerequisites-and-setup.md#ClientSoftwareReqs)
    
- [Configuration requirements](prerequisites-and-setup.md#ConfigReqs)
    
Additionally, we also have a section below for [Installing the Skype for Business Server 2015 Stress and Performance Tool](prerequisites-and-setup.md#Installing)
  
## Client hardware requirements
<a name="ClientHardwareReqs"> </a>

When running the Stress and Performance Tool against your Skype for Business Server 2015 deployment, you'll, at a minimum, need these hardware requirements met for every 4500 users in your test:
  
- 1 gigabit network adapter
    
- 8 GB RAM
    
- 2 dual-core CPUs
    
## Client software requirements
<a name="ClientSoftwareReqs"> </a>

The supported operating systems for the Stress and Performance Tool are:
  
- Windows Server 2012
    
- Windows Server 2008 (64-bit)
    
Additionally, computers need to meet the following software requirements:
  
- You'll need the Microsoft .NET 4.5 Framework installed. [Download the .Net 4.5 Framework here.](https://www.microsoft.com/en-us/download/details.aspx?id=30653)
    
- You'll need the Desktop Experience feature enabled in Windows.
    
- You'll need Microsoft Visual C++ 2013 (x64) installed. [Download Visual C++ 2013 here](https://www.microsoft.com/en-us/download/details.aspx?id=40784)
    
- You're going to need Skype for Business Server 2015 successfully deployed.
    
## Configuration requirements
<a name="ConfigReqs"> </a>

You'll need these additional configurations done to run the Stress and Performance Tool successfully:
  
- You need to log into the server as a member of the Domain or Local Administrator's group.
    
- You can't install the Skype for Business Server 2015 User Creation tool (UserProvisioningTool.exe) on any Front End Server or Standard Edition server where the user accounts will reside.
    
- When the User Creation tool is run multiple times, each user who's enabled for Microsoft Unified Communications needs to have a unique phone number.
    
- The page file size should be systems-managed, or otherwise needs to be at least 1.5 times the amount of RAM in the computer system.
    
## Installing the Skype for Business Server 2015 Stress and Performance Tool
<a name="Installing"> </a>

Installing couldn't be simpler. You need to run the Windows Installer file, **CapacityPlanningTool.msi**, on each client computer you're going to use to simulate user traffic, and on a Front End Server in each pool where you'll create users and contacts.
  
To download the .msi, along with the sample scripts mentioned in our other articles, go to the Download Center link: [Skype for Business Server 2015, Stress and Performance Tool](https://www.microsoft.com/download/details.aspx?id=50367).
  

