---
title: Dependencies of Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 10/20/17
ms.topic: article
ms.service: msteams
description: Microsoft Teams relies on Office 365 groups, SharePoint Online, and OneDrive for Business.
Set_Free_Tag: Strat_MT_TeamsAdmin
---

Dependencies of Microsoft Teams


Microsoft Teams relies on Office 365 groups to store teams' memberships and other properties such as team data classification settings. Office 365 Groups is a service that provides cross-application membership for a set of shared team assets, like a SharePoint site or a Power BI dashboard, so that the team can collaborate effectively and securely. 

Teams also relies on SharePoint Online and OneDrive for Business to store files and documents for channels and chat conversations. In addition, Teams relies on Office 365 groups to store teams' memberships and other properties such as team data classification settings.
  
    
    
To enable the full Teams guest access experience, Office 365 admins need to select **On** for the following settings:
  
    
    

- In SharePoint Online: **Only allow sharing with external users already in the directory**
    
    For more information, see [Manage external sharing for your SharePoint Online environment](https://support.office.com/en-us/article/Manage-external-sharing-for-your-SharePoint-Online-environment-c8a462eb-0723-4b0b-8d0a-70feafe4be85).
    
  
- In Office 365 groups: **Let group owners add people outside the organization to groups**
    
    For more information, see [Control guest access to Microsoft Teams](#controlguest).
    