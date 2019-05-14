---
title: Combining Skype for Business Online cmdlets with other Windows PowerShell cmdlets in
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Combining Skype for Business Online cmdlets with other Windows PowerShell cmdlets
ms:assetid: 8bb8800a-f966-4570-8c8b-db87a91ad783
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362816(v=OCS.15)
ms:contentKeyID: 56558835
ms.date: 05/04/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Combining Skype for Business Online cmdlets with other Windows PowerShell cmdlets in

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

When you connect to Skype for Business Online by using Windows PowerShell, approximately 40 Skype for Business Online cmdlets will available for your use. However, you are not limited to using just those 40 cmdlets when managing Skype for Business Online. In addition to the Skype for Business Online cmdlets, you can also use any other Windows PowerShell cmdlets that are installed on your computer. (When you install Windows PowerShell 3.0, hundreds of core Windows PowerShell cmdlets are installed, as well.) Your commands can mix and match Skype for Business Online cmdlets and any other cmdlets available on your computer.

Although a complete course in Windows PowerShell 3.0 goes beyond the scope of this article, here are a few examples that show why you might want to mix and match cmdlets. First of all, none of the Skype for Business Online cmdlets include a Print command, and no such command can be found in the Windows PowerShell console, either. So how do you get a printout of the information retrieved by a cmdlet? One way is to retrieve the information, and then send that information to the **Out-Printer** cmdlet:

    Get-CsTenant | Out-Printer

Because no additional parameters are included, all the information returned by **the Out-Printer** cmdlet will be printed to the default printer.

Likewise, none of the Skype for Business Online cmdlets include a parameter that allows you to save data to a file. But that’s OK: this command uses the **Out-File** cmdlet to save the returned information to the text file C:\\Logs\\Tenants.txt:

    Get-Tenant | Out-File -FilePath "C:\Logs\Tenants.txt"

And this command uses the **Select-Object** cmdlet to limit the data that is returned and displayed onscreen. In this example, the [Get-CsOnlineUser](https://technet.microsoft.com/en-us/library/JJ994026(v=OCS.15)) cmdlet retrieves information for all of your Skype for Business Online users, and then the **Select-Object** cmdlet is used to limit the displayed data to the user’s Identity value and their archiving policy:

    Get-CsOnlineUser | Select-Object Identity, ArchivingPolicy

Because there will be hundreds of cmdlets available for use on your computer, you might have difficulty determining which cmdlets are Skype for Business Online cmdlets and which ones are not. To return a list of the Skype for Business Online cmdlets (and only Skype for Business Online cmdlets), you must first determine the name of the temporary Windows PowerShell module that contains all the Skype for Business Online cmdlets. To do that, run this command from the Windows PowerShell prompt:

    Get-Module

Information similar to the following will appear onscreen:

    ModuleType Name                 ExportedCommands
    ---------- ----                 ----------------
    Manifest   Microsoft.PowerS...  {Add-Computer, Add-Content, A...}
    Script     tmp_5astd3uh.m5v     {Disable-CsMeetingRoom, Enabl...}

The module with the ModuleType Script is the module that contains the Skype for Business Online cmdlets. To return a list of those cmdlets, run the **Get-Command** cmdlet, using the name of the Script module as the module name:

    Get-Command -Module tmp_5astd3uh.m5v

It’s possible that you could have multiple modules with a ModuleType equal to Script. In that case, you can run the following command to find out which module includes the **Get-CsTenant** cmdlet:

    Get-Command Get-CsTenant

The module returned for the **Get-CsTenant** cmdlet will be the module containing all the Skype for Business Online cmdlets:

    CommandType     Name                                               ModuleName
    -----------     ----                                               ----------
    Function        Get-CsTenant                                       tmp_5astd3uh.m5v

<div>

## See Also


[An introduction to Windows PowerShell and Skype for Business Online](https://technet.microsoft.com/en-us/library/Dn362785(v=OCS.15))  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

