---
title: Microsoft Teams on Surface Hub - Admin Help
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 03/20/2018
ms.topic: article
ms.service: msteams
ms.reviewer: jatpatel
description: Configure admin settings for Microsoft Teams on Surface Hub.
ms.custom:
- Devices
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

Microsoft Teams on Surface Hub - Admin Help
===========================================
> [!IMPORTANT]
> [!INCLUDE [new-teams-sfb-admin-center-notice](includes/new-teams-sfb-admin-center-notice.md)]

Before you deploy Microsoft Teams for Surface Hub, be sure you have meet the operating system and hardware requirements. For more information, see the [Microsoft Surface Hub admin guide](https://docs.microsoft.com/en-us/surface-hub/).

## Set up user accounts
 
To set up user accounts that can be used with Teams for Surface Hub, create the device account as you would for support with Skype for Business. The device account needs to have Multi-Factor Authentication disabled (to allow automatic login) for the following dependent services of Teams in Office 365:  
- Exchange 
- SharePoint 
- Office Apps 

### Add a device account 

1. Start a remote Windows PowerShell session on a PC and connect to Exchange. Be sure you have the right permissions set to run the associated cmdlets. The following are some examples of cmdlets that can be used and modified in your environment.

```Set-ExecutionPolicy Unrestricted
$org='contoso.com'
$cred=Get-Credential $admin@$org
$sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ 
-Credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $sess```


## Install Teams for Surface Hub from the Microsoft Store 
These instructions include the current workarounds for installing Teams for Surface Hub from the Microsoft Store. 
 
1. Start the Windows Store 
a.	Start > All Apps > Settings 
b.	Tap on the "Surface Hub Device account, management" 
c.	On the left, tap on the "Apps & Features" tab. 
d.	Tap on the "Open Store" button on the right. 
2.	Open the Edge browser. 
3.	In the location bar of Edge, type in one of the following ms-windows-store protocol links to see Teams for Surface Hub in the Microsoft Store. 
4.	The Microsoft Store should appear showing the version you linked above for Microsoft Teams for Surface Hub.  Click on the "Get the app" button to install. 
5.	Once the installation is complete, restart the Surface Hub. 
6.	Once the Surface Hub restarts you should be able to start the Teams app from the Start menu and join a meeting from the calendar. 

