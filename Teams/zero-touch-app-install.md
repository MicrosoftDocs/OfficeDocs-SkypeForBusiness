---
title: Zero-touch App Install for Teams apps
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.service: msteams
ms.subservice: teams-apps
ms.date: 02/10/2023
search.appverid: 
description: Zero-touch App Install functionality adds apps in Teams for users who are already using its web app outside Teams.
audience: admin
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
---

# Zero-touch App Install for Teams apps

Some apps exist as web-based services or desktop apps   and   users use these apps without being aware that they can use them in Microsoft Teams. Using apps in Teams allows the users to work in the same context with added benefits from unique Teams capabilities like receiving notifications and collaborating in Teams.

Zero-touch App Install feature helps users and admins by automatically adding apps in Teams that are relevant to them and ones they already use outside of Teams.   It doesn’t require admin  or user intervention and respects all admin and user governance controls.

The functionality uses intelligent signals   from end-users and IT admins to install and surface the apps that admins have already allowed for the tenant. These signals help users to easily find and use apps within Microsoft Teams that are highly relevant to their needs.

## Benefits of the Zero-touch App Install functionality

The feature provides a convenient way to bring a few selected and commonly used apps. Only a few apps are supported currently, and more apps will be added in the future. This feature makes the most relevant apps available to users while supporting and adhering to all the app governance controls.

The following are the benefits of the functionality:

* Users can avoid context-switching by using the required apps in Teams. They don’t have to use a browser or email to stay updated, work on their tasks, or receive notifications. Users can use relevant   apps within Teams itself.
* Businesses can realize more value from their SaaS licenses by letting their users use the web apps and Teams apps. Some Teams apps like Adobe Acrobat offer more functionality than the default Teams PDF viewer. The Teams viewer can only read PDFs, but Acrobat allows editing and commenting.
* The feature helps admins with the last mile of app adoption. The admins have already reviewed and approved apps and users are allowed on Teams. The feature simply makes it easier to get those apps into the hands of the users who are authorized.

## Understand the change for admins and end-users

|   | Conceptually  | Functionally  |
|--------------------|----------------------|-------------------|
| What's changing  | <br> <li>Single and easy control to auto-install apps instead of creating app setup policies and assigning those to users.</li><li> Instead of switching context to browser for web apps or to email for notifications, users easily get the Teams apps in their Teams client. </li><li>Apps are installed without ad-hoc admin  or user intervention but with predefined admin action. </li></br>  |  <br><li>A new admin control to enable (or disable). Zero-touch App Install functionality is made available in Teams admin center. </li><li>Apps are automatically installed when users take certain actions. For example , when a user opens a PDF file or signs into an app using Azure AD on another platform, like a web browser. </li></br> |
| What's not changing  | <br><li> App governance controls set by admins are always respected.</li> <li> An app is installed only if it is allowed in the tenant and for the user. </li><li> User controls  are respected, such as  no reinstallation of an app if a user uninstalls it. </li></br> |  <br><li>The apps and their security, compliance, privacy, and other characteristics continue to remain as before.</li> <li> The governance controls to allow or block apps and permission policy to control app access for end-users remain as before. </li> <li> Users can uninstall any apps added to their Teams client and the apps aren’t reinstalled. </li> </br> |

## Considerations before you onboard to this functionality

Before you get onboard to use the functionality, consider the following:

* This functionality installs an app that is already approved for use on Teams  , has Azure AD, single sign-on (SSO), and is relevant to the user’s workflow  .
* The functionality isn’t available for tenants registered in the European Union (EU). However, the feature is available for EU users of a tenant registered in a non-EU country.
* If the app doesn’t support the language that the user is using in Teams, the app’s default supported language is used.  
* The activity feed notification will not appear on mobile when we  install it for the Azure AD sign-in automation.
* Only a few selected apps are available with this functionality. These apps are   installed only if Teams admin has already allowed the app, if the user has a scenario to use the app , and if permission policies allow a user to use the app.
* If an app supports mobile platforms, then the functionality installs it on the mobile client in addition to installing it on the desktop client.
* End-users can uninstall an app installed by this functionality. These users can manually reinstall the app later. The app isn’t automatically installed anymore.

The following prerequisites must be met before an app is installed so that admins have complete control over which apps are installed for their users:

* An admin has allowed the Zero-touch App Install feature.
* The app is listed as an app that can be installed using this feature.
* The app is allowed to be used in the organization.
* User signs in to Azure Active Directory.
* The user is allowed to use the app.

The zero-touch install functionality is applicable only for the following apps:

* Adobe Acrobat
* Asana
* Figma
* Jira Cloud
* Miro

In Teams admin center, to view the list of apps supported under this functionality, follow these steps:

1. Sign in to the Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Select **Org-wide app settings** and view the list of apps in the **Zero-touch app install** section.

## Use the functionality

To enable and use the functionality, meet the following prerequisites and complete these tasks:

* [Allow apps in your tenant](#allow-apps-in-the-tenant).
* [Allow end-users to use an app](#allow-end-users-to-use-an-app).
* [Enable the zero-touch install option](#enable-the-zero-touch-app-install-option).
* Optionally, [grant admin consent]() for Microsoft Graph permissions of an app.

### Allow apps in the tenant

The functionality respects the app governance policy. It works when third-party apps and the requisite app is allowed. If you haven't changed the default admin configurations, end-users have access to the apps by default.

To update or to verify app access, see [allow apps](https://learn.microsoft.com/microsoftteams/manage-apps#allow-and-block-apps).

### Allow end-users to use an app

Allow the use of the required (or all) apps for the intended end-users in your organization. To do so, ensure that app permission policies allow the intended users to use the apps. 

For more information, use the familiar governance controls of [app permission policies](https://learn.microsoft.com/microsoftteams/teams-app-permission-policies).

### Enable the Zero-touch App Install option

You must enable the zero-touch install feature manually. To do so, follow these steps:

1. Sign in to the Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Select **Org-wide app settings** and enable the **Zero-touch app install** option.

1. Select **Save**.

### Grant consent to Microsoft Graph permissions

Some apps require access to your user’s and organization’s information to work. A user must grant consent for the application or an admin can grant consent on behalf of the users. To use the zero-touch install functionality, we recommend that you grant Graph permission to all users, so that each of the users allowed to use the app are not prompted individually. Otherwise, if you choose to let individual users provide the consent themselves, then ensure that the user consent setting in Azure portal permits it. By default, users can provide their consent for all apps. If you’ve modified the default setting, then revert it to allow users to provide consent.

> [!NOTE]
> If admin consent is not granted and users are not allowed to consent to an app, then end-users cannot use the app.

See [how to grant admin consent to the app permissions](https://learn.microsoft.com/microsoftteams/app-permissions-admin-center). For more information, see [permissions and consent in the Microsoft identity platform](https://learn.microsoft.com/azure/active-directory/develop/permissions-consent-overview).

## Scenario 2: Azure AD sign in automation

Your organization’s users may use a SaaS web app using Azure AD credentials. After you complete the configuration required to use the zero-touch install functionality and if a user enters a scenario where the app is required, then Teams detect this signal and automatically installs the app. For example, if a user uses Azure AD to sign in to a web app that’s enabled for Zero-touch App Install, then the Teams app gets installed automatically.

The user receives an activity feed notification in Teams informing them of the app’s installation. Typically, the app installation takes a few hours or up to a day.

Users also receive a welcome message to notify them of the installation if the installed app supports bots.
