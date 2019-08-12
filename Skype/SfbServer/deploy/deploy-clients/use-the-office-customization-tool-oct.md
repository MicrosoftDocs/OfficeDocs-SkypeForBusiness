---
title: "Use the Office Customization Tool (OCT) in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 26647cb6-ba84-4ba7-8b6f-2cf86818e530
description: "Summary: How to use the Office Customization Tool with the Skype for Business client."
---

# Use the Office Customization Tool (OCT) in Skype for Business Server
 
**Summary:** How to use the Office Customization Tool with the Skype for Business client.
  
The Office Customization Tool (OCT) is part of the Setup program and is the recommended tool for many customizations. By using the OCT, you customize Office and save your customizations in a Setup customization .msp file. You place the file in the Updates folder on the network installation point. When you install Office, Setup looks for a Setup customization file in the Updates folder and applies the customizations. The Updates folder can be used only to deploy software updates during an initial installation of Office.
  
The OCT is part of setup and it is only used for volume licensed versions of the product. You run the OCT by typing  `setup.exe /admin` at the command line from the root of the network installation point that contains the Office source files. For example, use the following:
  
 ```
\\server\share\Office15\setup.exe /admin
```
  
Administrators use the OCT to create a setup customization .msp file and can customize the following areas:
  
- **Setup** Used to specify default installation location on the client and default organization name, additional network installation sources, product key, end-user license agreement, display level, earlier versions of Office to remove, custom programs to run during installation, security settings, and Setup properties.
    
- **Features** Used to configure user settings and to customize how Office features are installed. Administrators can use the OCT to specify initial default values of Office application settings for users. Users can modify most of the settings after the installation.
    
- **Additional content** Used to add or remove files, add or remove registry entries, and configure shortcuts.
    
- **Outlook** Used to customize a user's default Outlook profile, specify Exchange settings, add accounts, remove accounts and export settings, and specify Send\Receive groups.
    
For information about the OCT, see [Use the OCT to customize Office 2013](https://docs.microsoft.com/previous-versions/office/office-2013-resource-kit/cc179132(v=office.15)). Note that this information also applies to later versions of Office.
  

