---
title: "Using the Office Customization Tool (OCT) in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 26647cb6-ba84-4ba7-8b6f-2cf86818e530
description: "The Office Customization Tool (OCT) is part of the Setup program and is the recommended tool for many customizations. By using the OCT, you customize Office and save your customizations in a Setup customization .msp file. You place the file in the Updates folder on the network installation point. When you install Office, Setup looks for a Setup customization file in the Updates folder and applies the customizations. The Updates folder can be used only to deploy software updates during an initial installation of Office 2013."
---

# Using the Office Customization Tool (OCT) in Lync Server 2013
[]
The Office Customization Tool (OCT) is part of the Setup program and is the recommended tool for many customizations. By using the OCT, you customize Office and save your customizations in a Setup customization .msp file. You place the file in the Updates folder on the network installation point. When you install Office, Setup looks for a Setup customization file in the Updates folder and applies the customizations. The Updates folder can be used only to deploy software updates during an initial installation of Office 2013.
  
The OCT is part of setup and it is included in volume license versions of the product. You run the OCT by typing  `setup.exe /admin` at the command line from the root of the network installation point that contains the Office 2013 source files. For example, use the following: 
  
 `\\server\share\Office15\setup.exe /admin`
  
Administrators use the OCT to create a setup customization .msp file. As in the Microsoft Office 2010 OCT, administrators can customize the following areas:
  
- **Setup** Used to specify default installation location on the client and default organization name, additional network installation sources, product key, end-user license agreement, display level, earlier versions of Office to remove, custom programs to run during installation, security settings, and Setup properties. 
    
- **Features** Used to configure user settings and to customize how Office features are installed. Administrators can use the OCT to specify initial default values of Office application settings for users. Users can modify most of the settings after the installation. 
    
- **Additional content** Used to add or remove files, add or remove registry entries, and configure shortcuts. 
    
- **Outlook** Used to customize a user's default Outlook profile, specify Exchange settings, add accounts, remove accounts and export settings, and specify Send\Receive groups. 
    
For information about the OCT, see [https://go.microsoft.com/fwlink/p/?linkid=267516](https://go.microsoft.com/fwlink/p/?linkid=267516).
  

