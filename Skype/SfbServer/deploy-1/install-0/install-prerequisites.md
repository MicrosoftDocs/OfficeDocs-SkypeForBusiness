---
title: "Install prerequisites for Skype for Business Server 2015"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_Skype16
ms.custom: Strat_SB_Admin
ms.assetid: 2ef91a1e-2899-44c8-8e2c-527cb9114a0a
description: "Summary: Learn about the servers and server roles you must configure before you install Skype for Business Server 2015. Download a free trial of Skype for Business Server 2015 from the Microsoft Evaluation center at: https://www.microsoft.com/evalcenter/evaluate-skype-for-business-server."
---

# Install prerequisites for Skype for Business Server 2015
 
**Summary:** Learn about the servers and server roles you must configure before you install Skype for Business Server 2015. Download a free trial of Skype for Business Server 2015 from the [Microsoft Evaluation center](https://www.microsoft.com/evalcenter/evaluate-skype-for-business-server).
  
Installing prerequisites consists of setting up Windows Server by installing the required roles and features on each of the servers in the topology. The requirements are based on the role the server will fulfill in the topology. You can do steps 1 through 5 in any order. However, you must do steps 6, 7, and 8 in order, and after steps 1 through 5, as outlined in the diagram. Installing prerequisites is step 1 of 8.
  
![Overview diagram - install prerequisites.](../../media/0a85349b-b398-4e04-8901-8f4bd25d8afe.png)
  
## Setup Windows Server

Skype for Business Server 2015 requires the Windows Server operating system and a number of prerequisites before it can be installed. For details on planning for prerequisites, see [Server requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md). 
  
> [!TIP]
> This procedure uses Windows Server 2012 R2. If you are using a different version of Windows Server, the procedure might be slightly different. 
  
> [!IMPORTANT]
> Before you begin, make sure that Windows Server is up-to-date by using Windows Update. 
  
![Windows Server up to date.](../../media/a8d57a97-a55e-443b-b304-c534ae9a71b2.png)
  
Watch the video steps for **install prerequisites**:
  
![Your browser does not support video. Install Microsoft Silverlight, Adobe Flash Player, or Internet Explorer 9.](../../media/MSN_Video_Widget.gif)
  
### Install required roles and features for front-end servers

1. Open Server Manager, and click **Add roles and features**.
    
2. Read the **Before You Begin** page to familiarize yourself with installing roles and features in Windows Server, and then click **Next**.
    
3. Select **Role-based or feature-based installation**, and click **Next**.
    
4. Select the server on which you will be installing Skype for Business Server 2015, and click **Next**.
    
5. Select the **Web Server (IIS)** role, and when the required features window pops up, click **Add Features**, and then click **Next**.
    
6. Make sure the software features listed in [Software that should be installed before a Skype for Business Server 2015 deployment](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md#Software) are on the server that will run Skype for Business Server 2015. Here's an abbreviated list:
    
   - .NET Framework Features
    
   - WCF Services
    
   - HTTP Activation
    
    > [!NOTE]
    > HTTP Activation requires additional features. Click **Add Features** to the warning dialog box that pops up when you select HTTP Activation.
  
   - Media Foundation (required by Front End Servers and Standard Edition servers used for conferencing.)
    
   - Remote Server Administration Tools
    
   - Role Administration Tools
    
   - AD DS 
    
   - AD LDS
    
   - Windows Identity Foundation 3.5
    
7. Click **Next** to continue through the wizard.
    
8. Read through the notes about the **Web Server Role (IIS)**, and then click **Next**.
    
9. Select the following **Web Server (IIS) role services**.
    
   - Common HTTP Features
    
   - Default Document
    
   - Directory Browsing
    
   - HTTP Errors
    
   - Static Content
    
   - Health and Diagnostics
    
   - HTTP Logging
    
   - Logging Tools
    
   - Tracing
    
   - Performance
    
   - Static Content Compression
    
   - Dynamic Content Compression
    
   - Security
    
   - Request Filtering
    
   - Client Certificate Mapping Authentication
    
   - Windows Authentication
    
   - Application Development
    
   - .NET Extensibility 3.5
    
   - .NET Extensibility 4.5
    
   - ASP.NET 3.5
    
   - ASP.NET 4.5
    
   - ISAPI Extensions
    
   - ISAPI Filters
    
   - Management Tools
    
   - IIS Management Console
    
   - IIS Management Scripts and Tools
    
10. Click **Next** to continue through the wizard.
    
11. Review the installation selections to make sure all requirements are selected, and then click **Install**.
    
    > [!CAUTION]
    > Windows Server 2012 R2 does not install all of the source files for the required features by default. If the server is not connected to the Internet, you will need to insert the Windows Server 2012 R2 media and select **Specify an alternate source path** in order to install the required features. The source files are located in the sources\sxs directory. For example, if the Windows Server 2012 R2 media is in drive D, you would set the path to `d:\sources\sxs`. > It is important that you have the latest updates from Windows Update. If you are not connected to the Internet, you will need to manually install all relevant updates as well as any prerequisites to the required updates. 
  
12. When the dialog box indicates that the installation has completed, you will need to reboot the server to complete the process.
    
13. Run **Windows Update** again to check if there are any updates to the roles and services that were installed.
    
14. If you will be using Skype for Business Server Control Panel on this server then you must also install Silverlight. To install Silverlight, see [Microsoft Silverlight](https://www.microsoft.com/silverlight/).
    
The prerequisites can be installed by running the following PowerShell command. Note that the command looks for source files in a specific order. If you are online, the command accesses Windows Update. However, if you are offline, you need to make sure the source files are available to the command. For more information about using PowerShell to install roles and features, see [Install or Uninstall Roles, Role Services, or Features](https://technet.microsoft.com/en-us/library/hh831809.aspx) and [Install-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205467.aspx). Don't forget to run Windows Update again after you install prerequisites, even if you use the PowerShell command.
```
Add-WindowsFeature NET-Framework-Core, RSAT-ADDS, Windows-Identity-Foundation, Web-Server, Web-Static-Content, Web-Default-Doc, Web-Http-Errors, Web-Dir-Browsing, Web-Asp-Net, Web-Net-Ext, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Logging, Web-Log-Libraries, Web-Request-Monitor, Web-Http-Tracing, Web-Basic-Auth, Web-Windows-Auth, Web-Client-Auth, Web-Filtering, Web-Stat-Compression, Web-Dyn-Compression, NET-WCF-HTTP-Activation45, Web-Asp-Net45, Web-Mgmt-Tools, Web-Scripting-Tools, Web-Mgmt-Compat, Server-Media-Foundation, BITS
```

> [!IMPORTANT]
> The prerequisites for servers performing roles other than front-end server, such as the role of Director, Persistent Chat, or Edge, have their own prerequisites. For details on the exact prerequisites required by each server type, see [Server requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md). 
  

