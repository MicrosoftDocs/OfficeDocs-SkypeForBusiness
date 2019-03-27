---
title: "Upgrade Statistics Manager for Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 71f5d0a0-ca81-4ac1-b590-8f854504f21f
description: "Summary: Read this topic to learn how to upgrade Statistics Manager for Skype for Business Server."
---

# Upgrade Statistics Manager for Skype for Business Server
 
**Summary:** Read this topic to learn how to upgrade Statistics Manager for Skype for Business Server.
  
This topic describes how to upgrade an existing installation of Statistics Manager for Skype for Business Server—a powerful tool that allows you to view Skype for Business Server health and performance data in real time. You can poll performance data across hundreds of servers every few seconds, and view the results instantly on the Statistics Manager Website. 
  
For more information about Statistics Manager and the new features in Release 2.0, see [Plan for Statistics Manager for Skype for Business Server](plan.md) and [Deploy Statistics Manager for Skype for Business Server](deploy.md).
  
There are two methods for upgrading:
  
- **Automated upgrade.** This method uses an automated script. It is the easiest method and should be applicable to all upgrade scenarios.
    
- **Manual upgrade.** This method is provided as a backup plan in the unusual case that the automated upgrade fails.
    
## Prerequisites

Before you upgrade, be sure you have the following information:
  
- Active Listener Certificate Thumbprint
    
- Listener Service Password (entered on install of the listener and every agent)
    
- SSL Certificate configuration for the website
    
## Automated upgrade

The script will gather your current certificate information and listener password, uninstall the old version of the product, and then install the new version of the product. The Redis instance installed on the server will not be touched, so any data stored in the cache will be retained through the upgrade process.
  
1. Place the MSI files for the new version of the agent, listener and website along with the Update-StatsMan.ps1 script into a single folder on the Listener computer.
    
2. Open an administrative PowerShell window. Upgrade the Listener component:
    
   ```
   .\Update-StatsMan.ps1 -Service Listener
   ```

> [!NOTE]
> The Statistics Manager service password will be displayed in clear text on the command line as it is passed to the installer. Be sure to shield your monitor as needed. 
  
1. On running the script, you should be prompted to uninstall the old version of the product. Answer Yes.
    
2. If the Listener service is running, you will be prompted to close the application before continuing. Allow the application to close (the Statistics Manager Listener service will be stopped).
    
3. Continue the install process. You should notice that the service password and certificate thumbprint are pre-populated. If not, add the values you saved before continuing.
    
4. Open an administrative PowerShell window. Upgrade the Website component:
    
   ```
   .\Update-StatsMan.ps1 -Service Website
   ```

5. On running the script, you should be prompted to uninstall the old version of the product. Answer Yes.
    
6. If the Agent service is running, you will be prompted to close the application before continuing. Allow the application to close (the StatsMan Agent service will be stopped).
    
7. Continue the install process. You should notice that the service password and certificate thumbprint are pre-populated. If not, add the values you saved before continuing.
    
8. Open an administrative PowerShell window. Upgrade the Agent component:
    
   ```
   .\Update-StatsMan.ps1 -Service Agent
   ```

9. On running the script, you should be prompted to uninstall the old version of the product. Answer Yes.
    
10. Continue the install process. You should notice that the website port is pre-populated. If not, add the value you saved before continuing.
    
11. Verify the website is working as expected using the browser.
    
> [!NOTE]
> The Agent upgrade can be used with the -NoPrompt switch. This will allow the uninstall/install process to run silently, allowing tools such as PSExec to run the upgrade remotely on a large number of servers. 
  
### Manual upgrade

If for some reason, the automated upgrade fails, you can always perform a manual upgrade as follows:
  
1. On the Listener computer, uninstall the Listener, Website and the Agent (if it was installed on this server) via the Programs and Features control panel. 
    
    > [!NOTE]
    >  Keep Redis installed so that the data in the cache will then be maintained through the upgrade process.
  
2. Install the new versions of the components, including the values you saved above when prompted for them. For more information about installing components, see [Deploy Statistics Manager](deploy.md#BKMK_Deploy)

    
## For more information
<a name="BKMK_Fixed"> </a>

For more information, see the following:
  
- [Plan for Statistics Manager for Skype for Business Server](plan.md)
    
- [Deploy Statistics Manager for Skype for Business Server](deploy.md)
    
- [Troubleshoot Statistics Manager for Skype for Business Server](troubleshoot.md)
