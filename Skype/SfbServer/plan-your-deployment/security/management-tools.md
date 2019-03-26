---
title: "Windows PowerShell and Skype for Business Server management tools"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6a285f7c-0ef5-4cab-9976-d03be276e35d
description: "In Skype for Business Server, management tools are implemented using Windows PowerShell. Windows PowerShell includes a command-line environment, product-specific commands, and a full scripting language. Skype for Business Server tools that are implemented using Windows PowerShell include the following:"
---

# Windows PowerShell and Skype for Business Server management tools
 
In Skype for Business Server, management tools are implemented using Windows PowerShell. Windows PowerShell includes a command-line environment, product-specific commands, and a full scripting language. Skype for Business Server tools that are implemented using Windows PowerShell include the following: 
  
- **Topology Builder**. You use Topology Builder to create, adjust, and publish your planned topology, and it validates your topology before you begin server installations. When you install Skype for Business Server on individual servers, the servers read the published topology as part of the installation process, and the installation program deploys the server as directed in the topology. After setup, configuration information is automatically replicated to all servers. Components can be added to your deployment only by using Topology Builder.
    
- **Skype for Business Server Management Shell**. You can use Skype for Business Server Management Shell for full command-line management of your deployment.
    
- **Skype for Business Server Control Panel**. You can use the Skype for Business Server Control Panel user interface to manage the most common tasks in your deployment.
    
These tools use Windows PowerShell cmdlets for management of your deployment, including close to 550 product-specific cmdlets. The security cmdlets included in Skype for Business Server are primarily used to manage authentication, and user rights and permissions. A wide variety of cmdlets are available for managing authentication, including cmdlets for certificate and personal identification number (PIN) authentication. In addition, a number of cmdlets enable you to use the new Role-Based Access Control (RBAC) feature to delegate administrative control of Skype for Business Server. For details about the Skype for Business Server cmdlets, see [Skype for Business Server Management Shell](../../manage/management-shell.md).
  
The script security features for Windows PowerShell are specifically designed to help prevent some of the scripting-related security problems of older technologies, including Microsoft Visual Basic Scripting Edition (VBScript). The Windows PowerShell security features are intended to create an environment in which users cannot easily or unknowingly run scripts. By default, Windows PowerShell security features are enabled. You can modify the state of those features to accommodate your scripting needs and a variety of security goals. This is not to say that the shell makes it impossible for users to run scripts. Rather, the shell makes it difficult—by default—for users to run scripts without realizing they are doing so. For details, see [Windows PowerShell Script Security](https://go.microsoft.com/fwlink/p/?LinkId=213145).
  

