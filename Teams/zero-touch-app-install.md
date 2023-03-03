---
title: Zero-touch App Install for Teams apps
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.service: msteams
ms.subservice: teams-apps
ms.topic: article
ms.date: 03/03/2023
search.appverid: 
description: Zero-touch App Install functionality adds apps in Teams for users who are already using its web browser outside Teams.
audience: admin
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
---

# Zero-touch App Install of Microsoft Teams apps by admins

>[!NOTE]
> The feature is currently available only as a public preview. To enable public preview for specific users, see [Teams public preview](/microsoftteams/public-preview-doc-updates). When the feature is available on your tenant, you'll be notified through the [Microsoft 365 Message Center post](/microsoft-365/admin/manage/message-center?view=o365-worldwide).

Some apps exist as web-based services or apps on desktop or in the browser. Users who use these apps aren't aware that the same app functionality can be used as a Teams app. Using a Teams app allows the users to be more productive as the users work without switching context too often and with the added benefits of having unique Teams capabilities. Some such capabilities are in-context notifications and collaboration within Microsoft Teams.

If an admin enables the feature, Zero-touch App Install automatically adds admin-approved apps to Teams for the permitted users. It happens only after users have used Azure AD credentials to sign-in. The Zero-touch App Install feature automatically adds approved apps in the Teams clients of the permitted users. The functionality respects all app governance controls and only installs apps that the users have used outside Teams.

Admins can allow users to use Azure Active Directory identity to sign into apps outside Teams, for example in a web browser. The sign-in permission is used as an intelligent signal by the functionality to add the app for such users. The apps must be allowed by admins in their organization and the users must be allowed to use the app.

The Zero-touch install functionality is available only for a few Teams apps. You can view the apps in the **Zero-touch app install** section of [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page in Teams admin center.

:::image type="content" source="media/zero-touch-apps-list.png" alt-text="Screenshot showing Zero-touch App Install feature toggle and list of apps are available in the org-wide app settings in admin center." lightbox="media/zero-touch-apps.png":::

## Prerequisites and considerations for Zero-touch App Install feature

The feature can be turned on independently of the admin allow and block policies for apps. The feature respects these policies and doesn't install any blocked apps and for users who aren't allowed use of any apps.

To ensure that the feature installs the relevant apps and for the permitted users, meet the following requirements as a Global admin or a Teams admin:

* Enable the Zero-touch App Install option, which is disabled by default.
* Allow the app to be used in their organization. That is, admins must enable use of third-party apps, allow the use of one of the apps in the list apps supported by the feature, and permit the users to use the app.

In addition, the app is only installed if a user signs in to the app outside Teams using Azure AD identity, for example in a web browser.

Before you use the functionality, understand the following considerations:

* The functionality adheres to all admin controls for app governance.
* Only a few selected apps are available with this functionality. More apps will be added with default setting as off and with appropriate customer announcements.
* If an app supports mobile platforms, then the functionality installs it on the mobile client in addition to installing it on the desktop client.
* An Activity feed notification appears, informing users of the app install. The notification isn't available on mobile devices.
* End-users can uninstall an app installed by this functionality. These users can manually reinstall the app later. Once uninstalled, the app isn't automatically installed through Zero-touch App Install feature in the future.
* If the app doesn’t support the language that the user is using in Teams, the app’s default supported language is used.
* The following is a comparison with other methods of manual app installation and app governance

   | Feature behavior | Conceptually | Functionally |
   |--------------------|----------------------|-------------------|
   | What is different | <br> <li>Single and easy control to auto-install apps instead of creating app setup policies and assigning those to users.</li><li> Instead of switching context to browser for web apps or to email for notifications, users easily get the Teams apps in their Teams client. </li><li>Apps are installed without ad-hoc admin or user intervention but after an admin has enabled the feature. </li></br> | <br><li>A new admin control to enable (or disable). Zero-touch App Install functionality is made available in Teams admin center. </li><li>Allowed apps are automatically installed on Teams when users sign in to the app using Azure AD on another platform, like a web browser. </li></br> |
   | What doesn't change | <br><li> App governance controls set by admins are always respected.</li> <li> An app is installed only if it's allowed in the organization and allowed for the user. </li><li> User actions are respected. No reinstallation of an app via this feature if a user uninstalls it. </li></br> | <br><li>The apps and their security, compliance, privacy, and other characteristics continue to remain as before. No change in apps.</li> <li> The governance controls to allow or block apps and permission policy to control app access for end-users remain as before. </li> <li> Users can uninstall any apps added to their Teams client and the apps aren’t reinstalled. </li> </br> |

## Benefits of the functionality

The feature benefits admins and end-users in the following ways:

* Last-mile app delivery happens while respecting all app governance controls. For example, you can turn the feature on or off, only permitted apps get added, and users who aren't permitted to use apps can't add apps to their Teams.
* Admins don't have to create app setup policies to deliver apps to the intended users. This feature only does the app rollout in accordance with admin policies. It adds the app in the Teams client for users as if the user installed it themselves.
* Businesses can realize more value from their SaaS licenses by letting their users use the web apps and Teams apps. Some Teams apps like Adobe Acrobat offer more functionality than the default Teams PDF viewer. The default PDF viewer in Teams can only read PDF files, but Acrobat allows editing and commenting in PDF files.
* Users continue to use the app functionality inside Teams without switching context. They don’t have to discover apps and install the app, use a browser to use the app, or individually request admins for access to an app.
* Users continue to have admin-approved access to use the apps on the surface and in the context that is most convenient to them. Users also receive the highly relevant apps as a Teams app if and when they demonstrate the need through their actions.

## Use Zero-touch App Install feature

To enable and use the functionality, meet the following prerequisites and complete these tasks:

* [Allow apps in your organization](#allow-third-party-apps-in-your-organization).
* [Enable the Zero-touch App Install option](#enable-the-zero-touch-app-install-option).
* [Enable user consent or grant admin consent](app-permissions-admin-center.md) for Azure AD permissions that an app requires.

### Allow third-party apps in your organization

The functionality respects the app governance controls and works only if the use of an app is allowed by admins. To allow any app, you must also allow use of third-party apps. If you haven't changed the default admin configurations, third-party apps are allowed. To update or to verify, see [allow apps](/microsoftteams/manage-apps#allow-and-block-apps).

Allow the use of the specific apps that your end-users require for their daily tasks. To do so, allow individual apps and also ensure that app permission policies allow the intended users to use these apps. For more information, see [app permission policies](/microsoftteams/teams-app-permission-policies).

### Enable the Zero-touch App Install option

You must enable the Zero-touch App Install feature manually. To do so, follow these steps:

1. Sign-in to the Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Select **Org-wide app settings** and enable the **Zero-touch app install** option.

    :::image type="content" source="media/zero-touch-apps.png" alt-text="Screenshot showing Zero-touch App Install option in admin center that must be enabled to use the feature." lightbox="media/zero-touch-apps-large.png":::

1. Select **Save**.

After a user's first sign into an app using Azure AD on another platform, the app installation can take a few hours or up to a day. End-users receive a welcome message from the app if the installed app supports bots. End-users also receive an Activity Feed notification informing them about the new app that is added.

:::image type="content" source="media/zti-activity-feed.png" alt-text="Screenshot showing a new activity feed notification in Teams after a Zero-touch app is installed for a user." lightbox="media/zti-activity-feed-large.png":::

### Enable user consent or grant admin consent to Azure AD permissions

Some apps require access to your user’s and organization’s information to work. A user must grant consent for the application or an admin can grant consent on behalf of the users. To use the Zero-touch App Install functionality, we recommend that you grant Azure AD permission as an admin, so that each user isn't prompted for consent. Otherwise, if you choose to let individual users provide the consent themselves, then ensure that the user consent setting in Azure portal permits it. By default, users can provide their consent for apps. If you’ve modified the default setting, then update it to allow users to provide consent. See [how to grant admin consent to the app permissions](/microsoftteams/app-permissions-admin-center) and [permissions and consent in the Microsoft identity platform](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal&pivots=portal).

> [!NOTE]
> If admin consent is not granted and users are not allowed to consent to an app, then users cannot use the app. Users may be prompted to contact their admin when trying to use the app.

## Related articles

* [How to allow apps in an organization](/microsoftteams/manage-apps#allow-and-block-apps)
* [Use app permission policies to permit users to use an app](/microsoftteams/teams-app-permission-policies)
* [How to grant admin consent to the app permissions](/microsoftteams/app-permissions-admin-center)
* [Permissions and consent in the Azure AD](/azure/active-directory/develop/permissions-consent-overview)
