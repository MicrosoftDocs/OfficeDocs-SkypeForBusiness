---
title: "Best practices for your core infrastructure in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 44aff88d-536c-4613-a81e-5398c9c6a648
description: "You have probably already taken steps to design fault tolerance in your system, using practices such as ensuring hardware redundancy, guarding against power loss, routinely installing security updates and antivirus measures, and Monitoring Server activity. These practices benefit not only your Skype for Business Server infrastructure, but also your entire network. If you have not implemented these practices, we recommend that you do so before deploying Skype for Business Server."
---

# Best practices for your core infrastructure in Skype for Business Server
 
You have probably already taken steps to design fault tolerance in your system, using practices such as ensuring hardware redundancy, guarding against power loss, routinely installing security updates and antivirus measures, and Monitoring Server activity. These practices benefit not only your Skype for Business Server infrastructure, but also your entire network. If you have not implemented these practices, we recommend that you do so before deploying Skype for Business Server.
  
To help protect the servers in your Skype for Business Server deployment from accidental or purposeful harm that might result in downtime, take the following precautions:
  
- Keep your servers up-to-date with security updates. Subscribing to the Microsoft Security Notification Service helps ensure that you receive immediate notification of security bulletin releases for any Microsoft product. To subscribe, go to the [Microsoft Technical Security Notifications website](https://go.microsoft.com/fwlink/p/?LinkId=145202).
    
- Ensure that access rights are set up correctly.
    
- Keep your servers in a physical environment that prevents unauthorized access. Ensure that adequate antivirus software is installed on all your servers. Keep the software up-to-date with the latest virus signature files. Use the automatic update feature of your antivirus application to keep the virus signatures current.
    
- We recommend that you disable the Windows Server operating system services that are not required on the computers where you install Skype for Business Server.
    
- Encrypt operating systems and disk drives where data is stored with a full-volume encryption system, unless you can guarantee constant and complete control of the servers, total physical isolation, and proper and secure decommissioning of replaced or failed disk drives.
    
- Disable all external Direct Memory Access (DMA) ports of the server, unless you can guarantee very tight control over the physical access to the servers. DMA-based attacks, which can be initiated fairly easily, could expose very sensitive information, such as private encryption keys.
    

