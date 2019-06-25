---
title: Use PowerShell to control guest access to a team
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 06/25/2019
ms.topic: article
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: sbhatta
search.appverid: MET150
description: Use PowerShell to allow or block guest access to teams in Microsoft Teams.
appliesto: 
- Microsoft Teams
---

Use PowerShell to control guest access to a team
================================================

In addition to using the Microsoft 365 admin center and the Azure Active Directory (Azure AD) portal, you can use Windows PowerShell to control guest access. With PowerShell, you can do the following:
  
- Allow or block guest access to all teams and Office 365 Groups

- Allow guests to be added to all teams and Office 365 Groups

- Allow or block guest users from a specific team or Office 365 group

For details, see "Use PowerShell to control guest access" in [Manage guest access in Office 365 Groups](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups#use-powershell-to-control-guest-access).
  
You can also use PowerShell to allow or block a guest user based on their domain. For example, let's say your business (Contoso) has a partnership with another business (Fabrikam). You can add Fabrikam to your Allow list so your users can add those guests to their groups. For more information, see [Allow/Block guest access to Office 365 Groups](https://go.microsoft.com/fwlink/?linkid=854001).
  
If you want to block guests in Teams and still want to allow them to access SharePoint sites, you can use Azure AD Powershell cmdlets to disable the AllowGuestsToAccessGroups parameter on the Company object, assuming external sharing is turned on for SharePoint sites.

## Guest access vs. external access

[!INCLUDE [guest-vs-external-access](includes/guest-vs-external-access.md)]
