---
title: Auto install approved Teams apps
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.service: msteams
ms.subservice: teams-apps
ms.topic: article
ms.date: 05/05/2023
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
> The feature is gradually being made Generally Available (GA) to all tenants. For more information, see [Microsoft 365 Message Center post MC548106](https://admin.microsoft.com/Adminportal/Home?ref=MessageCenter/:/messages/MC548106). The feature was previously called Zero-touch app install.

Some apps exist as apps on the desktop or in the browser. Users who use these apps may not know that the same app feature is available as a Teams app. Using a Teams app allows them to be more productive as the users work without switching context and with the added benefits of having unique Teams capabilities. For more information, see the [benefits of Auto install approved apps feature](#benefits-of-the-feature).

When enabled, the feature respects all app governance controls and apps are installed only for the users who are allowed to use these apps. Admins can enable SSO and let users use their Azure AD identity to sign into apps outside Teams, for example in a web browser. This sign-in is used as an intelligent signal by the feature to add the Teams app for such users in their Teams client.

The Auto install approved apps feature is available only for a few Teams apps. The **Org-wide app settings** section of [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page in Teams admin center lists all such apps. We'll add more apps with appropriate announcements.

:::image type="content" source="media/approved-apps-list.png" alt-text="Screenshot showing Auto install approved apps feature toggle and list of apps are available in the org-wide app settings in admin center." lightbox="media/approved-apps.png":::

## Prerequisites for Auto install approved apps feature

To ensure that the feature installs the relevant apps and for the allowed users, meet the following requirements as a Global Admin or a Teams Administrator:

* [Allow the relevant app in your organization](#allow-third-party-apps-in-your-organization).
* [Ensure users can consent to app permissions or grant admin consent](#ensure-users-can-consent-or-grant-admin-consent-to-azure-ad-permissions-of-an-app) for Azure AD permissions that an app requires.

In addition, the app is only installed if a user signs in to the app outside Teams using Azure AD identity, for example in a web browser.

### Allow third-party apps in your organization

The feature respects the app governance controls and installs apps only if admins allow the use of an app. While the feature can be turned on independent from your app governance settings, to experience auto installs, admins must allow the use of third-party apps, allow a particular app, and allow the relevant users to use the app. For more information, see [allow apps](/microsoftteams/manage-apps#allow-and-block-apps).

### Ensure users can consent or grant admin consent to Azure AD permissions of an app

Some apps require access to the relevant information about your users and organization. Accessing this information requires users to grant their consent and/or admins to consent on behalf of their users. Admins can grant consent on behalf of the users as well. To use the Auto install approved apps feature, we recommend that you understand the required Azure AD permission and [grant consent as a Global Administrator](app-permissions-admin-center.md). Each user isn't prompted for consent if admins do so.

Alternately, you can let the individual users provide the consent themselves. By default, users can provide their consent for apps. Ensure that the [user consent setting in Azure AD portal](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal&pivots=portal) permits it.

## Enable the Auto install approved apps feature in Teams admin center

You must enable the Auto install approved apps feature as it is disabled by default. To do so, follow these steps:

1. Sign-in to the Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Select **Org-wide app settings** and enable the **Auto install approved apps** option.

    :::image type="content" source="media/approve-apps.png" alt-text="Screenshot showing Auto install approved apps option in admin center that must be enabled to use the feature." lightbox="media/approve-apps-large.png":::

1. To enable or disable specific apps, select **Manage selected apps** and change the setting for each app.

1. Optionally, to view the detailed information about an app, select the app name.

1. Select **Save**.

After a user signs in to the enabled app using Azure AD on another platform, the app installation can take up to two days. Users receive a welcome message from the app if the installed app supports bots. Users also receive an Activity Feed notification on Teams desktop or web client informing them about the new app that is added. The notification isn't available on mobile devices.

:::image type="content" source="media/autoinstall-activity-feed-large.png" alt-text="Screenshot showing a new activity feed notification in Teams after an approved app is installed for a user." lightbox="media/autoinstall-activity-feed-large.png":::

## Benefits of the feature

The feature benefits admins and users in the following ways:

* Admins get an easy control to automatically install apps. No need to create app setup policies and assign it to individual users. Last-mile app delivery happens while respecting all app governance controls. For example, you can turn the feature on or off, only the allowed apps get added, and users who aren't allowed to use apps can't add apps to their Teams.

* Users don't have to discover and manually add apps or individually request admins for access to an app. Users receive the Teams app if and when they demonstrate the need through their actions. Instead of switching context to browser for web apps or to email for notifications, users get it all within their Teams client.

* Businesses can realize more value from their SaaS licenses by letting their users use the web apps and Teams apps. Some Teams apps like Adobe Acrobat offer more feature than the default Teams PDF viewer. The default PDF viewer in Teams can only read PDF files, but Adobe Acrobat Teams app allows editing and commenting in PDF files.

## Considerations for Auto install approved apps feature

Before you use the feature, understand the following considerations:

* The feature can be enabled independently of the admin settings to allow and block policies for the supported apps. However, it respects all policies and doesn't install any blocked app. Also, it doesn't install a supported app if a user isn't allowed the use of the app.

* If admin consent isn't granted and users aren't allowed to consent to an app, then users can't use the app. Users may be prompted to contact their admin when trying to use the app.

* Users can remove an app added by this feature by uninstalling the app. These users can manually add the app later. Once the app is removed, the feature doesn't automatically add the app again.

* If the app doesn’t support the language that the user is using in Teams, the app’s default supported language is used.

* When you turn on Auto install approved apps for Adobe Acrobat, then Teams client uses the Adobe Acrobat app as the default file handler for the PDF files for the new and the existing app users. The change will be automatically applied later in 2023 and the admins will be informed via a [Microsoft 365 Message Center post](/microsoft-365/admin/manage/message-center?view=o365-worldwide).

* Teams admin may have blocked a Teams app for a user and your organization may allow Azure AD SSO for the user to use the app, say in a browser. If this feature has been turned on for the Teams app and the user is later allowed to use the app, the app will be auto installed for them if they have used Azure AD to sign in up to 30 days before they were allowed to use the app.

## Related articles

* [How to allow apps in an organization](/microsoftteams/manage-apps#allow-and-block-apps)
* [Use app permission policies to allow users to use an app](/microsoftteams/teams-app-permission-policies)
* [How to grant admin consent to the app permissions](/microsoftteams/app-permissions-admin-center)
* [Permissions and consent in the Azure AD](/azure/active-directory/develop/permissions-consent-overview)
