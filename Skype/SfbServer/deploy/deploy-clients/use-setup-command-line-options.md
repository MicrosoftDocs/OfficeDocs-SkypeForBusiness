---
title: "Use Setup command-line options with Skype for Business clients"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 99878c3c-ff31-48e2-8424-580d7b07a7bf
description: "Summary: Learn about Setup.exe command line operations in Office setup."
---

# Use Setup command-line options with Skype for Business clients
 
**Summary:** Learn about Setup.exe command line operations in Office setup.
  
The Setup.exe command line is used for very few operations in Office setup. Instead of using the Setup command-line options, you'll typically use the Office Customization Tool and the Config.xml file for product setup and feature customization.
  
The Office Setup.exe command line recognizes the command-line options described in the following table.
  
**Office Setup Command-Line Options**

|**Setup Command-Line Option**|**Description**|
|:-----|:-----|
|/admin  <br/> |Runs the Office Customization Tool to create a Setup customization file (.msp file).  <br/> |
|/adminfile [path]  <br/> |Applies the specified Setup customization file to the installation. You can specify a path of a specific customization file (.msp file) or to the folder where you store customization files.  <br/> |
|/config [path]  <br/> |Specifies the Config.xml file that Setup uses during the installation. Use the /config option to specify the Config.xml file you customized for Skype for Business installations, for example:  `/config \\server\share\Skype15\Skype.WW\Config.xml` <br/> |
|/modify Skype  <br/> |Used with a modified Config.xml file to run Setup in maintenance mode and make changes to an existing Office installation. For example, you can use the /modify option to add or remove Skype for Business features.  <br/> |
|/repair Skype  <br/> |Runs Setup from the user's computer to repair Skype for Business.  <br/> |
|/uninstall Skype  <br/> |Runs Setup to remove Skype for Business from the user's computer.  <br/> |
   


