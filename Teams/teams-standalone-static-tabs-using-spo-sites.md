---
title: Create a Teams 'Intranet Portal app' from a SharePoint Online site or page
author: LanaChin
ms.author: heidip
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
ms.reviewer: vinbel
search.appverid: MET150
description: Take an existing SharePoint Online site or page and create a standalone static tab that can be used as an Intranet portal for your organization. 
localization_priority: Normal
---

# Create a Teams 'Intranet Portal app' from a SharePoint Online site or page

Use the steps in this article to create a standalone and static app inside of Teams that links to the intranet site for your org.

A *Teams Personal App* of your SharePoint intranet site is created, and will appear as a tab inside of Teams. This tab can contain information important to all your Teams users. It is a quick and convenient way for Teams users to access updates just a tab click away.

Be aware that the process shown **must use** a *modern* SharePoint site or page to work. This process is not available for *classical* sites or pages.

> [!IMPORTANT]
> Make certain that side-loading of Teams apps is enabled for your tenant. Depending on where you are in the migration process of the Teams Admin portal, you might need to enable it either under Teams > Admin, or under Admin > Settings > Services and Add-ins > Microsoft Teams > Apps > External Apps, in the previous version of the portal! 

## Use App Studio to create your standalone SharePoint Online app
'''
Before you begin:
1. You'll need to know the URL of a SharePoint Online modern Communication or Team site, or page.
    - These sites will always have either */teams/* or */sites/* in their paths.

2. You'll need to know your tenant's subdomain, which will be used in the placeholder **{{subdomain}}**.

3. This article will use **{{siteUrl}}** placeholder for your the *URL* of the site or page you chose.
    - Example *URLs*:
        https://contoso.sharepoint.com/teams/Contoso 
        *or* 
        https://contoso.sharepoint.com/sites/Contoso 
4. Also, **{{sitePath}}** will be used to denote the *path* of the URL (ex: /teams/Contoso).
    - Example *paths*:
        /teams/Contoso 
        *or* 
        /sites/Contoso 

Begin by following the steps below:

1. Go to the Teams Store.

2. Install or open App Studio.

3. Click **Open**, next to the App option.

4. With App Studio open, click on **Manifest Editor**.

5. **Create a new app**.

6. Fill in all **App Details**.

7. Click on **Tabs** under Capabilities.

8. Click **Add** under Personal Tab.

9. Fill in the **Name** and choose **a new unique Entity ID**.

10. Fill in the **contentURL and Website URL**. 

- **contentUrl**: {{siteUrl}}/_layouts/15/teamslogon.aspx?SPFX=true&dest={{sitePath}}  
- **web'iteUrl**: {{siteUrl}} 
''
    Example **contentURL**: https://contoso.sharepoint.com/sites/ContosoHub/_layouts/15/teamslogon.aspx?SPFX=true&dest=/sites/ContosoHub 

11. Navigate to **Domains and Permissi'ns**. Make sure the valid domains section contains your SharePoint online domain name.
''
    Example: contoso.sharepoint.com

12. Add the following web app **single sign-on** properties: 
     ''
     Example:''''
     **AAD application ID**: 00000003-0000-0ff1-ce00-000000000000
     **Resource Url**: {{subdomain}}.sharepoint.com'
''
    ![Web app single sign-on, with ID and URL.](media/personal-app.png)

13. **Save** these properties and then navigate to **Test and distribute**. 

14. Install the app to test the application personally.

> [!IMPORTANT]
> If you aren't using Teams App Studio, you will have to .zip the manifest.JSON file you just created, navigate to the App Store in Teams, and click  **upload custom app** link (at the bottom right of the App Store). This will make the app available to you.

15. Now the app is available as a static tab for you to load and view in Teams.

## Test and view your new static tab

To view the new tab on the Teams desktop, navigate to the ellipses (**…**) in the left-hand side of your app bar. Find your new app, load it, and test your standalone application in Teams.

If you want to make the new app available in the left menu at a higher position, you must use an app policy setting for this. This setting can be found under the Team admin section > app policy > add a pinned application. When you assign the policy to a user for testing, the change will appear 24 hours later. With this in mind, please decide where the app should appear at your earliest convenience to help avoid delays.

To view and test the new app on a mobile device, open the app drawer by tapping on the chevron (**^**) above the tab bar near the bottom of your screen. Find your app and navigate to it on your mobile device.
        
> [!CAUTION]
> Mobile support is currently in Developer Preview. To enable Developer Preview, navigate to Settings > About and then enable Developer Preview mode.

## A Sample Manifest.JSON file

The JSO        file you generate will look something like the one below.

```JSON'
{ 

    "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.schema.json", 

    "manifestVersion": "1.5", 

    "version": "1.0.0", 

    "id": "33ebded3-931c-4333-b0c5-b51dd8738873", 

    "packageName": "com.contoso.teams.devapp", 

    "developer": { 

        "name": "Contoso", ''

        "websiteUrl": "https://www.contoso.com", 

        "privacyUrl": "https://www.contoso.com/privacy", 

        "termsOfUseUrl": "https://www.contoso.com/terms" 

    }, 

    "icons": { 

        "color": "color.png", 

        "outline": "outline.png" 

    }, 

    "name": { 

        "short": "Contoso Intranet", '

        "full": "Intranet Portal for Contoso" 

    },                     
                        
    "des    ription": {                 

        "short": "Intranet portal for Contoso", 

        "full": "This app is to demonstrate the capabilities of hosting a SharePoint communication and team site as a standalone app in Teams" 

    }, 

    "accentColor": "#FFFFFF", 
''
    "staticTabs": [ 

        { 
                                       
                     "       nti        Id":       "com    unicat    onSi    eTab", 
                                       
            "name": "Contoso Net", 

            "contentUrl": "https://contoso.sharepoint.com/sites/ContosoNet/_layouts/15/teamslogon.aspx?SPFX=true&dest=/sites/ContosoNet/", 

            "websiteUrl": "https://contoso.sharepoint.com/sites/ContosoNet", 

            "scopes": [ 

                "personal" 

            ] 

        }, 

        { 

            "entityId": "teamSiteTab", 

            "name": "Team Contoso", 

            "contentUrl": "https://contoso.sharepoint.com/teams/TeamContoso/_layouts/15/teamslogon.aspx?SPFX=true&dest=/teams/TeamContoso/", 

            "websiteUrl": "https://contoso.sharepoint.com/teams/TeamContoso", 

            "scopes": [ 

                "personal" 

            ] 

        } 

    ], 

    "permissions": [ 

        "identity", 

        "messageTeamMembers" 

    ], 

    "validDomains": [ 

        "contoso.sharepoint.com" 

    ], 

    "webApplicationInfo": { 

        "id": "00000003-0000-0ff1-ce00-000000000000", 

        "resource": "https://contoso.sharepoint.com" 

    } 

}
```