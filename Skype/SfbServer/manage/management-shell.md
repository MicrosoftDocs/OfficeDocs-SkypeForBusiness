---
title: "Skype for Business Server Management Shell"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 674b523b-c0b7-4ed6-9e67-afa6e8ac7e12
description: "The Skype for Business Server Management Shell provides the command line interface for server administration and management. It is built on Windows PowerShell and includes a comprehensive set of management and administration cmdlets that are specific to Skype and legacy Lync server products."
---

# Skype for Business Server Management Shell
 
The Skype for Business Server Management Shell provides the command line interface for server administration and management. It is built on Windows PowerShell and includes a comprehensive set of management and administration cmdlets that are specific to Skype and legacy Lync server products.
  
Windows PowerShell allows you to manage Microsoft applications from the command line. It includes a command-line environment, product-specific commands, and a full scripting language. Windows PowerShell was first introduced as a downloadable release for the Windows operating system late in 2006, and was incorporated as the command-line interface for manageability of Microsoft Exchange Server 2007. It has been incorporated into most of the Microsoft Server products, including Lync and Skype servers beginning with Lync Server 2010. There are over 700 Lync and Skype specific cmdlets available in the Skype for Business Server Management Shell.
  
> [!NOTE]
> Skype for Business cmdlet reference has moved to docs.microsoft.com. Clicking on the links below will take you to the new docs.microsoft.com page. The content is now open sourced and available for community contributions through GitHub. Interested in contributing? Check out the README in the repo here: [https://github.com/MicrosoftDocs/office-docs-powershell](https://github.com/MicrosoftDocs/office-docs-powershell)
  
Skype for Business Server ships with more than 700 cmdlets that enable administrators to manage Skype for Business Server using the Skype for Business Server Management Shell. You can retrieve help for a cmdlet directly from the command line by typing a command similar to the following:
  
```
Get-Help New-CsVoicePolicy -Full
```

The preceding command retrieves the complete help available for the **New-CsVoicePolicy** cmdlet. To view help for a different cmdlet, substitute **New-CsVoicePolicy** with the name of the cmdlet for which you want to retrieve help.
  
To retrieve a full list of cmdlets available for managing Skype for Business Server, type the following at the shell command prompt: 
  
```
Get-Command * -Module SkypeforBusiness -CommandType cmdlet
```



Things to know about Windows PowerShell in Skype for Business Server:
  
- To run the Skype for Business Server cmdlets, open the Skype for Business Server Management Shell.
    
    > [!CAUTION]
    > If you open a Windows PowerShell window rather than the Skype for Business Server Management Shell, by default you may not be able to run the Skype cmdlets. To run Skype for Business Server cmdlets from within Windows PowerShell, first type the following at the Windows PowerShell command prompt: >  `Import-Module SkypeforBusiness`
  
- Skype for Business Server Management Shell is automatically installed on every Skype for Business Server Enterprise Edition Front End Server or Standard Edition server.
    
- You can update the Skype for Business Server Management Shell help content by running the [Update-Help](https://technet.microsoft.com/en-us/library/hh849720.aspx) cmdlet. The Update-Help cmdlet downloads and installs the newest help files available for all of the modules installed on your computer, including updates to Skype for Business cmdlets.
    
    By default, the **Update-Help** cmdlet will update all the modules installed on your Skype for Business Server. If you want to update only certain modules, you can use the _Module_ parameter to limit the scope of the cmdlet. The following example updates only the Skype for Business module.
    
  ```
  Update-Help -Module SkypeforBusiness
  ```

    If you need to update the Help on servers that are not connected to the internet, you can use the [Save-Help](https://technet.microsoft.com/en-us/library/hh849724.aspx) cmdlet to get the latest version of the help and save it to a location you specify. You can then use the **Update-Help** cmdlet with the _-SourcePath_ parameter on servers not connected to the internet to get the updated help from the location you selected. The following example shows how to save the help files to a network file share, and then update the help for the Skype for Business module from the file share.
    
  ```
  // Save the help files
   Save-Help -DestinationPath \\UpdateShare\HelpDownload
  // Run Update-Help against the local help files
   Update-Help -Module SkypeforBusiness -SourcePath \\UpdateShare\HelpDownload
  ```

    For more detailed information, see [About Updatable Help](https://technet.microsoft.com/library/hh847735.aspx).
    
    > [!NOTE]
    > If you are using PowerShell remotely you may need to allow communication through a firewall. To learn more about the ports PowerShell remoting uses, see [What Port Does PowerShell Remoting Use?](https://blogs.technet.microsoft.com/christwe/2012/06/20/what-port-does-powershell-remoting-use/).
    

