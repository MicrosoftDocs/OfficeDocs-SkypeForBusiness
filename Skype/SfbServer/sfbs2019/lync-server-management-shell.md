---
title: "Lync Server 2013 Management Shell"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 9/20/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 674b523b-c0b7-4ed6-9e67-afa6e8ac7e12
description: "Microsoft Lync Server 2010 introduced a large set of new and improved features compared to what was available in Microsoft Office Communications Server 2007 R2. One improvement is the way in which you manage your implementation. For example, there's a new user interface, called the Lync Server Control Panel, which represents a big shift from what most people are used to with the Microsoft Management Console. The other major improvement to manageability is the inclusion of Windows PowerShell."
---

# Lync Server 2013 Management Shell
[]
> [!NOTE]
> Skype for Business cmdlet reference has moved to docs.microsoft.com. Clicking on the links below will take you to the new docs.microsoft.com page. The content is now open sourced and available for community contributions through GitHub. Interested in contributing? Check out the README in the repo here: [https://github.com/MicrosoftDocs/office-docs-powershell](https://github.com/MicrosoftDocs/office-docs-powershell)
  
Microsoft Lync Server 2010 introduced a large set of new and improved features compared to what was available in Microsoft Office Communications Server 2007 R2. One improvement is the way in which you manage your implementation. For example, there's a new user interface, called the Lync Server Control Panel, which represents a big shift from what most people are used to with the Microsoft Management Console. The other major improvement to manageability is the inclusion of Windows PowerShell.
  
Windows PowerShell allows you to manage Microsoft applications from the command line. It includes a command-line environment, product-specific commands, and a full scripting language. Windows PowerShell was first introduced as a downloadable release for the Windows operating system late in 2006, and was incorporated as the command-line interface for manageability of Microsoft Exchange Server 2007. From that point it continued to grow, and it has been incorporated into most of the Microsoft Server products, the most recent of these being Microsoft Lync Server 2013. Lync Server 2010 introduced close to 550 product-specific cmdlets that you can use to manage every aspect of your deployment.
  
The following sections contain a list of cmdlets and their descriptions. This information is also available directly from the command line. Simply type the following at the Lync Server Management Shell command prompt:
  
```
Get-Help <cmdlet name> -Full
```

For example, to retrieve help from the command prompt on the **New-CsVoicePolicy** cmdlet, type the following: 
  
```
Get-Help New-CsVoicePolicy -Full
```

Things to know about Windows PowerShell in Lync Server 2013:
  
- To run the Lync Server cmdlets, open the Lync Server Management Shell.
    
    > [!CAUTION]
    > If you open a Windows PowerShell window rather than the Lync Server Management Shell, by default you will not be able to run the Lync Server cmdlets. To run the Lync Server cmdlets from within Windows PowerShell, first type the following at the Windows PowerShell command prompt: > Import-Module Lync 
  
- Lync Server Management Shell is automatically installed on every Lync Server Enterprise Edition Front End Server or Standard Edition server.
    
- New and updated information, sample scripts, and help for getting started and learning more about Windows PowerShell and Microsoft Lync Server 2013 cmdlets is available at the Lync Server Windows PowerShell Blog [https://go.microsoft.com/fwlink/p/?linkId=203150](https://go.microsoft.com/fwlink/p/?linkId=203150).
    

