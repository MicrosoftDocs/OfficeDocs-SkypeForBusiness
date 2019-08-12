---
title: "Provisioning the topology to run load in Stress and Performance scenarios"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
ms.date: 12/17/2015
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 143cf9bd-b935-494d-817c-a8b0ccc61eb8
description: "Skype for Business Server 2015 topology changes or provisioning to allow users to successfully run the Stress and Performance tool."
---

# Provisioning the topology to run load in Stress and Performance scenarios
 
Skype for Business Server 2015 topology changes or provisioning to allow users to successfully run the Stress and Performance tool.
  
Depending on your existing settings and configuration for your deployment of Skype for Business Server 2015, you might need to make some changes in your environment. The following is a list of those changes:
  
1. Set the Windows PowerShell execution policy to Unrestricted. If you're not sure what it's set to currently, you can open the Skype for Business Server Management Shell and run this command:
    
   ```
   Get-ExecutionPolicy
   ```

   If the value Unrestricted is not returned, you'll need to run this next:
    
   ```
   Set-ExecutionPolicy -Unrestricted
   ```

2. To effectively configure Skype for Business Server, you'll need to:
    
    - Be familiar with your Skype for Business Server 2015 topology (such as computer names, service instances, site names, and policies).
    
    - Assign some of the users that are created to groups, such as Response Group hunt groups (for example, SIP URIs).
    
3. To run a script from command line, you can use:
    
   ```
   PowerShell.exe -file <path to the file>
   ```

4. Typically, after you've run a script from this package, the resulting traces will be stored in a file in the same path from where the script was run. There's a naming format as well, \<scriptname\>$h$m$s.txt. So if you ran the ArchivingPolicy.ps1 at 12:15 PM, you'll get a log file named ArchivingPolicy121500.txt.
    
5. While we've provided these examples for your server configuration, it's up to you to both modify your configuration and restore or roll it back after you've finished running the load testing.
    

