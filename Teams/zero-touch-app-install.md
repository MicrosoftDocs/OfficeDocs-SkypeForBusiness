---
title: Zero-touch App Install for Teams apps
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.service: msteams
ms.subservice: teams-apps
ms.topic: article
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

Some apps exist as web-based services or desktop apps and users use these apps without being aware that they can use the equivalent Teams apps. Using a Teams app allows the users to work in the same context with added benefits of unique Teams capabilities such as in-context notifications and collaboration in Teams.

Zero-touch App Install feature automatically adds approved apps in Teams client of permitted users. The functionality respects all app governance controls and only installs apps that the users have used outside Teams.

Admins can allow users to use Azure Active Directory identify to sign into apps outside Teams, for example web apps. The sign-in permission is used as an intelligent signal by the functionality to add the app for such users. The apps must be allowed by admins in their organization and the users must be allowed to use the app.

The zero-touch install functionality is available only for a few Teams apps. You can view the apps in the **Zero-touch app install** section of [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page in Teams admin center.

:::image type="content" source="media/zero-touch-apps.png" alt-text="Screenshot showing zero-touch App Install feature toggle and list of apps are available in the org-wide app settings in admin center.":::

## Prerequisites and considerations for zero-touch App Install feature

The following prerequisites must be met before an app is installed so that admins have complete control over what apps are installed for their users:

* An admin must allow third-party apps to be used in their organization.
* An admin must allow a specific app to be used in their organization.
* An admin must permit the intended end-users to use a specific app.
* An admin must enable the Zero-touch App Install option, which is disabled by default.
* The functionality supports an app.
* User signs in to the app outside Teams using Azure AD identity, for example in a web app.

Before you use the functionality, understand the following considerations:

* The functionality adheres to all admin controls for app governance.
* If the app doesn’t support the language that the user is using in Teams, the app’s default supported language is used.
* Only a few apps are available with this functionality.
* If an app supports mobile platforms, then the functionality installs it on the mobile client in addition to installing it on the desktop client.
* The activity feed notification after app installation does not appear on mobile devices when we install it for the Azure AD sign-in automation.
* End-users can uninstall an app installed by this functionality. These users can manually reinstall the app later. Once uninstalled, the app isn’t automatically installed later.
* The following is a comparison with other methods of manual app installation and app governance

   | Feature behavior | Conceptually | Functionally |
   |--------------------|----------------------|-------------------|
   | What is different | <br> <li>Single and easy control to auto-install apps instead of creating app setup policies and assigning those to users.</li><li> Instead of switching context to browser for web apps or to email for notifications, users easily get the Teams apps in their Teams client. </li><li>Apps are installed without ad-hoc admin or user intervention but with predefined admin action. </li></br> | <br><li>A new admin control to enable (or disable). Zero-touch App Install functionality is made available in Teams admin center. </li><li>Apps are automatically installed when users take certain actions. For example, when a user opens a PDF file or signs into an app using Azure AD on another platform, like a web browser. </li></br> |
   | What doesn't change | <br><li> App governance controls set by admins are always respected.</li> <li> An app is installed only if it is allowed in the tenant and for the user. </li><li> User actions are respected, such as no reinstallation of an app if a user uninstalls it. </li></br> | <br><li>The apps and their security, compliance, privacy, and other characteristics continue to remain as before. No change in apps.</li> <li> The governance controls to allow or block apps and permission policy to control app access for end-users remain as before. </li> <li> Users can uninstall any apps added to their Teams client and the apps aren’t reinstalled. </li> </br> |

## Benefits of the Zero-touch App Install functionality

The feature benefits you and your end-users in the following ways:

* The feature helps admins with the last mile of app adoption. You must review and approve the selected apps and allow the users to use these apps. The feature simply adds the app in the Teams client of users without a need to create setup policies.
* Businesses can realize more value from their SaaS licenses by letting their users use the web apps and Teams apps. Some Teams apps like Adobe Acrobat offer more functionality than the default Teams PDF viewer. The default PDF viewer in Teams can only read PDF files, but Acrobat allows editing and commenting in PDF files.
* Users avoid context-switching by using the apps within Teams. They don’t have to use a browser or email to stay updated, work on their tasks, or receive notifications.

## Use the functionality

To enable and use the functionality, meet the following prerequisites and complete these tasks:

* [Allow apps in your tenant](#allow-apps-in-your-organization).
* [Allow end-users to use an app](#allow-end-users-to-use-specific-apps).
* [Enable the Zero-touch App Install option](#enable-the-zero-touch-app-install-option).
* [Grant admin consent](app-permissions-admin-center.md) for Microsoft Graph permissions that an app requires.

### Allow apps in your organization

The functionality respects the app governance controls and works only if use of third-party apps is allowed by admins. If you haven't changed the default admin configurations, third-party apps are allowed. To update or to verify, see [allow apps](/microsoftteams/manage-apps#allow-and-block-apps).

### Allow end-users to use specific apps

Allow the use of the specific apps that your end-users require for their daily tasks. To do so, allow individual apps and also ensure that app permission policies allow the intended users to use these apps. For more information, see [app permission policies](/microsoftteams/teams-app-permission-policies).

### Enable the Zero-touch App Install option

You must enable the zero-touch install feature manually. To do so, follow these steps:

1. Sign-in to the Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Select **Org-wide app settings** and enable the **Zero-touch app install** option.

    :::image type="content" source="media/zero-touch-apps.png" alt-text="Screenshot showing zero-touch app install feature toggle and list of apps are available in the org-wide app settings in admin center." lightbox="media/zero-touch-apps-large.png":::

1. Select **Save**.

The app installation takes a few hours or up to a day. End-users receive a welcome message to notify them of the installation if the installed app supports bots.

### Grant consent to Microsoft Graph permissions

Some apps require access to your user’s and organization’s information to work. A user must grant consent for the application or an admin can grant consent on behalf of the users. To use the zero-touch install functionality, we recommend that you grant Graph permission as an admin, so that each user is not prompted for consent. Otherwise, if you choose to let individual users provide the consent themselves, then ensure that the user consent setting in Azure portal permits it. By default, users can provide their consent for apps. If you’ve modified the default setting, then revert it to allow users to provide consent. See [how to grant admin consent to the app permissions](/microsoftteams/app-permissions-admin-center) and [permissions and consent in the Microsoft identity platform](/azure/active-directory/develop/permissions-consent-overview).

> [!NOTE]
> If admin consent is not granted and users are not allowed to consent to an app, then end-users cannot use the app.

## Related articles

* [How to allow apps in an organization](/microsoftteams/manage-apps#allow-and-block-apps)
* [Use app permission policies to permit users to use an app](/microsoftteams/teams-app-permission-policies)
* [How to grant admin consent to the app permissions](/microsoftteams/app-permissions-admin-center)
* [Permissions and consent in the Azure AD](/azure/active-directory/develop/permissions-consent-overview)
