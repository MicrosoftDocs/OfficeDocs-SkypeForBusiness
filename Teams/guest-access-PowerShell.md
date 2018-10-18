---
title: Use PowerShell to control guest access to a team
author: LaithAlShamri
ms.author: laal
manager: serdars
ms.date: 10/20/17
ms.topic: article
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
ms.reviewer: laal
search.appverid: MET150
description: Use PowerShell to allow or block guest access to teams in Microsoft Teams.
appliesto: 
- Microsoft Teams
---

Use PowerShell to control guest access to a team
================================================

In addition to using the Office 365 admin center and the Azure Active Directory portal, you can use Windows PowerShell to control guest access. With PowerShell, you can do the following:
  
  
   

- Allow or block guest access to all teams and Office 365 groups
    
  
- Allow guests to be added to all teams and Office 365 groups
    
  
- Allow or block guest users from a specific team or Office 365 group
    
  
For more details, see the section "Use PowerShell to control guest access" on the Manage tab of [Guest access in Office 365 Groups](https://support.office.com/article/Use-PowerShell-to-control-guest-access-bfc7a840-868f-4fd6-a390-f347bf51aff6#bkmk_usepowershell).
  
    
    
You can also use PowerShell to allow or block a guest user based on their domain. For example, let's say your business (Contoso) has a partnership with another business (Fabrikam). You can add Fabrikam to your Allow list so your users can add those guests to their groups. For more information, see [Allow/Block guest access to Office 365 groups](https://go.microsoft.com/fwlink/?linkid=854001).
  
 
If you want to block guests in teams and still allow guests to access SharePoint sites, you can use Azure Active Directory Powershell cmdlets to disable the AllowGuestAccessToGroups parameter on the Company object, assuming external sharing is turned on for SharePoint sites.   

