---
title: Use PowerShell to control guest access to a team
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
ms.reviewer: sbhatta
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about how to use PowerShell to allow or block guest access to all teams or specific teams in Microsoft Teams.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

Use PowerShell to control guest access to a team
================================================

In addition to using the Microsoft 365 admin center and the Azure Active Directory (Azure AD) portal, you can use Windows PowerShell to control guest access. With PowerShell, you can do the following:
  
- Allow or block guest access to all teams and Microsoft 365 Groups

- Allow guests to be added to all teams and Microsoft 365 Groups

- Allow or block guest users from a specific team or Microsoft 365 group

For details, see "Use PowerShell to control guest access" in [Manage guest access in Microsoft 365 Groups](https://docs.microsoft.com/microsoft-365/admin/create-groups/manage-guest-access-in-groups).

  
You can also use PowerShell to allow or block a guest user based on their domain. For example, let's say your business (Contoso) has a partnership with another business (Fabrikam). You can add Fabrikam to your Allow list so your users can add those guests to their groups. For more information, see [Allow/Block guest access to Microsoft 365 Groups](https://go.microsoft.com/fwlink/?linkid=854001).
  
If you want to block guests in Teams and still want to allow them to access SharePoint sites, you can use Azure AD PowerShell cmdlets to disable the AllowGuestsToAccessGroups parameter on the Company object, assuming external sharing is turned on for SharePoint sites.

> [!NOTE]
> This guide is dependant on the following module

```
Install-Module -Name MicrosoftTeams
```

## Use PowerShell to turn guest access on or off

1.  Download the Skype for Business Online PowerShell module from https://www.microsoft.com/download/details.aspx?id=39366
 
2.  Connect a PowerShell session to the Skype for Business Online endpoint.


> [!NOTE]
> Skype for Business Online Connector is currently part of the latest Teams PowerShell module.
>
> If you're using the latest [Teams PowerShell public release](https://www.powershellgallery.com/packages/MicrosoftTeams/), you don't need to install the Skype for Business Online Connector.


    ```powershell     
    Import-Module -Name MicrosoftTeams
    $Cred = Get-Credential
    $CSSession = New-CsOnlineSession -Credential $Cred
    Import-PSSession -Session $CSSession
    ```
    
3.  Check your configuration and if `AllowGuestUser` is `$False`, use the [Set-CsTeamsClientConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csteamsclientconfiguration?view=skype-ps) cmdlet to set it to `$True`.

    ```powershell
    Get-CsTeamsClientConfiguration

    Identity                         : Global
    AllowEmailIntoChannel            : True
    RestrictedSenderList             :
    AllowDropBox                     : True
    AllowBox                         : True
    AllowGoogleDrive                 : True
    AllowShareFile                   : True
    AllowOrganizationTab             : True
    AllowSkypeBusinessInterop        : True
    ContentPin                       : RequiredOutsideScheduleMeeting
    AllowResourceAccountSendMessage  : True
    ResourceAccountContentAccess     : NoAccess
    AllowGuestUser                   : True
    AllowScopedPeopleSearchandAccess : False
    
    Set-CsTeamsClientConfiguration -AllowGuestUser $True -Identity Global
    ```
You can now have guest users in Teams for your organization.


## Guest access vs. external access

[!INCLUDE [guest-vs-external-access](includes/guest-vs-external-access.md)]
