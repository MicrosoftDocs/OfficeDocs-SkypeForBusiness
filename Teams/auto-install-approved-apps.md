---
title: Auto install approved Teams apps
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.service: msteams
ms.subservice: teams-apps
ms.topic: article
ms.date: 03/03/2023
search.appverid: 
description: Auto install apps in Teams if admins approve it and users already use it outside Teams.
audience: admin
ms.localizationpriority: high
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
---

# Auto install approved apps in Microsoft Teams

>[!NOTE]
> The feature is currently available only as a public preview feature. To enable public preview for specific users in your organization, see [enable Teams public preview](/microsoftteams/public-preview-doc-updates). When the feature is available in your tenant, you'll be notified through the [Microsoft 365 Message Center post](/microsoft-365/admin/manage/message-center?view=o365-worldwide). The feature was previously called Zero-touch app install.

Some apps exist as web-based services or apps on desktop or in the browser. Users who use these apps may not know that the same app functionality is available as a Teams app. Using a Teams app allows them to be more productive as the users work without switching context and with the added benefits of having unique Teams capabilities. Some such unique capabilities are in-context notifications and collaboration within Microsoft Teams.

If an admin enables the Auto install approved apps feature, it automatically adds admin-approved apps to Teams for the permitted users. An app is added only after users use Azure Active Directory credentials to sign-in. The functionality respects all app governance controls and only installs an app if the users used it outside Teams.

Admins can allow users to use Azure Active Directory identity to sign into apps outside Teams, for example in a web browser. The sign-in permission is used as an intelligent signal by the functionality to add the app for such users. An admin must allow the apps in their organization and allow the users to use the app.

The Auto install approved apps functionality is available only for a few Teams apps. The **Auto install approved apps** section of [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page in Teams admin center lists the all such apps.

:::image type="content" source="media/approved-apps-list.png" alt-text="Screenshot showing Auto install approved apps feature toggle and list of apps are available in the org-wide app settings in admin center." lightbox="media/approved-apps.png":::

## Prerequisites for Auto install approved apps feature

To ensure that the feature installs the relevant apps and for the permitted users, meet the following requirements as a Global Admin or a Teams Administrator:

* [Allow the relevant app in your organization](#allow-third-party-apps-in-your-organization).
* [Ensure users can consent to app permissions or grant admin consent](#ensure-users-can-consent-or-grant-admin-consent-to-azure-ad-permissions-of-an-app) for Azure AD permissions that an app requires.

In addition, the app is only installed if a user signs in to the app outside Teams using Azure AD identity, for example in a web browser.

### Allow third-party apps in your organization

The functionality respects the app governance controls and works only if admins allow the use of an app. To allow an app, you must do the following:

* Allow use of third-party apps (allowed by default).
* Allow use of a particular app (allowed by default).
* Allow the relevant users to use the app (allowed by default but use [permission policies](/microsoftteams/teams-app-permission-policies) to refine your governance).

For more information, see [allow apps](/microsoftteams/manage-apps#allow-and-block-apps).

### Ensure users can consent or grant admin consent to Azure AD permissions of an app

Some apps require access to your user’s and organization’s information to work. By default, apps can't access such information and requires a user to grant their consent. Admins can grant consent on behalf of the users as well. To use the Auto install approved apps functionality, we recommend that you understand the required Azure AD permission and grant consent as a Teams Administrator. Each user isn't prompted for consent if admins do so.

Alternately, you can let the individual users provide the consent themselves. Ensure that the user consent setting in Azure AD portal permits it. By default, users can provide their consent for apps. See [how to grant admin consent to the app permissions in Teams admin center](app-permissions-admin-center.md) and [permissions and consent in the Microsoft identity platform](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal&pivots=portal).

## Enable the Auto install approved apps option

You must enable the Auto install approved apps feature as it is disabled by default. To do so, follow these steps:

1. Sign-in to the Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Select **Org-wide app settings** and enable the **Auto install approved apps** option.

    :::image type="content" source="media/approved-apps.png" alt-text="Screenshot showing Auto install approved apps option in admin center that must be enabled to use the feature." lightbox="media/approved-apps-large.png":::

1. Select **Save**.

After a user's first sign into an app using Azure AD on another platform, the app installation can take a few hours or up to a day. Users receive a welcome message from the app if the installed app supports bots. Users also receive an Activity Feed notification informing them about the new app that is added.

:::image type="content" source="media/zti-activity-feed.png" alt-text="Screenshot showing a new activity feed notification in Teams after an approved app is installed for a user." lightbox="media/zti-activity-feed-large.png":::

## Understand the benefits of the functionality

The feature benefits admins and users in the following ways:

* Single and easy control to auto-install apps. No need to create app setup policies and assign it to users. Last-mile app delivery happens while respecting all app governance controls. For example, you can turn the feature on or off, only permitted apps get added, and users who aren't permitted to use apps can't add apps to their Teams.
* Admins don't have to create app setup policies to deliver apps to the intended users. This feature only does the app rollout in accordance with admin policies. It adds the app in the Teams client for users as if the user installed it themselves.
* Businesses can realize more value from their SaaS licenses by letting their users use the web apps and Teams apps. Some Teams apps like Adobe Acrobat offer more functionality than the default Teams PDF viewer. The default PDF viewer in Teams can only read PDF files, but Acrobat allows editing and commenting in PDF files.
* Users don't have to discover and add apps, use a browser to use the same app in a browser or on mobile, or individually request admins for access to an app.
* Instead of switching context to browser for web apps or to email for notifications, users get it all within their Teams client.
* Users continue to have admin-approved access to use the apps on the surface and in the context that is most convenient to them. Users also receive the highly relevant apps as a Teams app if and when they demonstrate the need through their actions.

## Considerations for and limitations of Auto install approved apps feature

Before you use the functionality, understand the following considerations:

* The functionality adheres to all admin controls for app governance and doesn't override any admin policies.

* The feature can be enabled independently of the admin settings to allow and block policies for the supported apps. However, it respects all policies and doesn't install any blocked app. Also, it doesn't install a supported app if a user isn't allowed the use of the app.

* Only a few selected apps are supported by this functionality. More apps will be added with appropriate announcements. The default setting is off and only admins can enable it. For the list of apps, see the [Org-wide settings](https://admin.teams.microsoft.com/policies/manage-apps) in Teams admin center.

* If admin consent is not granted and users are not allowed to consent to an app, then users cannot use the app. Users may be prompted to contact their admin when trying to use the app.

* If an app supports mobile platforms, then the functionality installs it on the mobile client in addition to installing it on the desktop client.

* When the app is added to a user's client, an Activity feed notification informs the user. The notification isn't available on mobile devices.

* Users can remove an app added by this functionality. These users can manually add the app later. Once removed, the app isn't automatically added by the feature.

* If the app doesn’t support the language that the user is using in Teams, the app’s default supported language is used.

* The apps and their security, compliance, privacy, and other characteristics continue to remain as before. No change in apps.

## Related articles

* [How to allow apps in an organization](/microsoftteams/manage-apps#allow-and-block-apps)
* [Use app permission policies to permit users to use an app](/microsoftteams/teams-app-permission-policies)
* [How to grant admin consent to the app permissions](/microsoftteams/app-permissions-admin-center)
* [Permissions and consent in the Azure AD](/azure/active-directory/develop/permissions-consent-overview)
