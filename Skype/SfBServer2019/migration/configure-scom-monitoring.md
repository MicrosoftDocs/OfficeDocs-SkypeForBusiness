---
title: "Configure SCOM monitoring"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "After migrating to Microsoft Skype for Business Server 2019, you must complete a few tasks to configure Skype for Business Server 2019 to work with System Center Operations Manager."
---

# Configure SCOM monitoring

After migrating to Skype for Business Server 2019, you must complete a few tasks to configure Skype for Business Server 2019 to work with System Center Operations Manager.
  
- Apply updates to a server elected to manage the central discovery logic.
    
- Update the central discovery candidate server registry key.
    
- Configure your primary System Center Operations Manager management server to override the candidate central discovery node.
    
Instructions for carrying out each of these tasks are provided below.
  
### Apply updates to a server elected to manage the central discovery logic.

1. Elect a server that has the System Center Operations Manager agent files installed and is configured as a candidate discovery node. 
    
2. Apply updates to this server. See the topic [Apply updates](apply-updates.md).
    
### Update the central discovery candidate server registry key.

1. On the server elected to manage the central discovery logic, open a Windows PowerShell command window. 
    
2. At the command line, type the following:
    
   ```
   New-Item -Path "HKLM:\Software\Microsoft\Real-Time Communications\Health"
   ```

   ```
   New-Item -Path "HKLM:\Software\Microsoft\Real-Time Communications\Health\CentralDiscoveryCandidate"
   ```

    > [!NOTE]
    > Whenever you edit the registry, you may experience an error that the command failed if the registry key already exists. If you experience this, you can safely ignore the error. 
  
### Configure your primary System Center Operations Manager management server to override the candidate central discovery watcher node.

1. On a computer where the System Center Operations Manager console has been installed, expand **Management Pack Objects** and then select **Object Discoveries**.
    
2. Click **Change Scope**
    
3. From the **Scope Management Pack Objects** page, select **LS Discovery Candidate**.
    
4. Override the **LS Discovery Candidate Effective Value** to the name of the candidate server elected in the earlier procedure. 
    
To finalize your changes, restart the health service on the System Center Operations Manager Root Management Server.
  

