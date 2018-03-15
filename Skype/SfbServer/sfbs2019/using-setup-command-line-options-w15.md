---
title: "Using Setup command-line options in Lync Server 2013 [W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 99878c3c-ff31-48e2-8424-580d7b07a7bf
description: "The Setup.exe command line is used for very few operations in Office setup. Instead of using the Setup command-line options, you'll typically use the Office Customization Tool and the Config.xml file for product setup and feature customization."
---

# Using Setup command-line options in Lync Server 2013 [W15]
[]
The Setup.exe command line is used for very few operations in Office setup. Instead of using the Setup command-line options, you'll typically use the Office Customization Tool and the Config.xml file for product setup and feature customization.
  
The Office Setup.exe command line recognizes the command-line options described in the following table.
  
**Office Setup Command-Line Options**

|**Setup Command-Line Option**|**Description**|
|:-----|:-----|
|/admin  <br/> |Runs the Office Customization Tool to create a Setup customization file (.msp file).  <br/> |
|/adminfile [path]  <br/> |Applies the specified Setup customization file to the installation. You can specify a path of a specific customization file (.msp file) or to the folder where you store customization files.  <br/> |
|/config [path]  <br/> |Specifies the Config.xml file that Setup uses during the installation. Use the /config option to specify the Config.xml file you customized for Lync 2013 installations, for example:  `/config \\server\share\Lync15\Lync.WW\Config.xml` <br/> |
|/modify Lync  <br/> |Used with a modified Config.xml file to run Setup in maintenance mode and make changes to an existing Office installation. For example, you can use the /modify option to add or remove Lync features.  <br/> |
|/repair Lync  <br/> |Runs Setup from the user's computer to repair Lync.  <br/> |
|/uninstall Lync  <br/> |Runs Setup to remove Lync from the user's computer.  <br/> |
   
For details about using the setup command-line options, see [https://go.microsoft.com/fwlink/p/?linkid=267515](https://go.microsoft.com/fwlink/p/?linkid=267515). 
  

