---
title: Auto install approved Teams apps
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.service: msteams
ms.subservice: teams-apps
ms.topic: article
ms.date: 10/18/2023
ms.reviewer: nguyenb
search.appverid: 
description: Auto install apps in Teams that are approved by admins and used by users outside Teams.
audience: admin
ms.localizationpriority: high
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
---

# Auto install approved apps in Microsoft Teams

>[!IMPORTANT]
> Some apps supported by Auto install approved apps require setup by admins before turning on the feature. See the [list of these apps and setup instructions](#apps-requiring-setup-before-deployment-to-users).

Some apps exist as apps on the desktop or in the browser. Users who use these apps may not know that the same app feature is available as a Teams app. Using a Teams app allows them to be more productive as the users work without switching context and with the added benefits of having unique Teams capabilities. For more information, see the [benefits of Auto install approved apps feature](#benefits-of-the-feature).

When enabled, the feature respects all app governance controls and apps are installed only for the users who are allowed to use these apps. Admins can enable SSO and let users use their Microsoft Entra identity to sign into apps outside Teams, for example in a web browser. This sign-in is used as an intelligent signal by the feature to add the Teams app for such users in their Teams client.

The Auto install approved apps feature is available only for a few Teams apps. For the list of all the supported apps, see the **Org-wide app settings** section of [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page in Teams admin center. We'll add more apps with appropriate announcements.

:::image type="content" source="media/approved-apps-list.png" alt-text="Screenshot showing Auto install approved apps feature toggle option and list of apps that are available in the org-wide app settings in admin center." lightbox="media/approved-apps.png":::

## Prerequisites for Auto install approved apps feature

To ensure that the feature installs the relevant apps and for the allowed users, meet the following requirements:

* [Allow the relevant app in your organization](#allow-third-party-apps-in-your-organization).
* [Ensure users can consent to app permissions or grant admin consent](#ensure-users-can-consent-or-grant-admin-consent-to-microsoft-entra-permissions-of-an-app) for Microsoft Entra permissions that an app requires.

In addition, the app is installed for a user only if the user signs in to the app outside Teams using Microsoft Entra identity. For example, the web version of the app may be already allowed in your organization and a user signs into the app in a browser using their Entra identity. This will initiate a Teams app installation only for the specific user, if the Teams app is allowed for them.

### Allow third-party apps in your organization

The feature respects the app governance controls and installs apps only if admins allow the use of an app. The feature can be turned on independent of your app governance settings. However, to auto install apps, admins must allow the use of third-party apps, allow a particular app, and allow the relevant users to use the app. For more information, see [how to allow Teams apps](/microsoftteams/manage-apps#allow-or-block-apps).

### Ensure users can consent or grant admin consent to Microsoft Entra permissions of an app

Some apps require access to the relevant information about your users and organization. Accessing this information requires users to grant their consent and/or admins to consent on behalf of their users. Admins can grant consent on behalf of the users as well. To use the Auto install approved apps feature, we recommend that you understand the required Microsoft Entra permission and [grant consent as a Global Administrator](app-permissions-admin-center.md). Each user isn't prompted for consent if an admin does so.

Alternately, you can let the individual users provide the consent themselves. By default, users can provide their consent for apps. Ensure that the [user consent setting in Microsoft Entra admin center](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal&pivots=portal) permits it.

## Enable the Auto install approved apps feature in Teams admin center

You must enable the Auto install approved apps feature as it is disabled by default. To do so, follow these steps:

1. Sign-in to the Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Select **Org-wide app settings** and enable the **Auto install approved apps** option.

    :::image type="content" source="media/approve-apps.png" alt-text="Screenshot showing Auto install approved apps option in admin center that must be enabled to use the feature." lightbox="media/approve-apps-large.png":::

1. To enable or disable specific apps, select **Manage selected apps** and change the setting for each app.

1. Optionally, to view the detailed information about an app, select the app name.

1. Select **Save**.

After a user signs in to the enabled app using Microsoft Entra ID on another platform, the app installation can take up to two days. Users receive a welcome message from the app if the installed app supports bots. Users also receive an Activity Feed notification on Teams desktop or web client informing them about the new app that is added. The notification isn't available on mobile devices.

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

* When you turn on Auto install approved apps for Adobe Acrobat, then Teams client uses the Adobe Acrobat app as the default file handler for the PDF files. This experience impacts the new and the existing users of Adobe Acrobat app. The change will be automatically applied later in 2023 and the admins will be informed via a [Microsoft 365 Message Center post](/microsoft-365/admin/manage/message-center?view=o365-worldwide).

* Teams admin may have blocked a Teams app for a user and your organization may allow Microsoft Entra SSO for the user to use the app, say in a browser. If this feature has been turned on for the Teams app and the user is later allowed to use the app, the app will be auto installed for them if they have used Microsoft Entra ID to sign in up to 30 days before they were allowed to use the app.

* The feature installs an app in the personal scope.

## Apps requiring setup before deployment to users

A few specific Teams apps require a prior setup before you roll out these apps to your organization's users. Follow the app setup instructions from the app developers that are provided below and then turn on the Auto install approved apps feature for these apps.

Some apps require consent to its Graph permissions for the app to work. In Teams Admin Center, only a Global Administrator can grant consent on behalf of users of their organization.

| App                                                                                                      | Setup instruction                                                                                                                                       | Admin consent to Graph permissions required                                                                                              |
|----------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| [Box for Teams](https://appsource.microsoft.com/product/office/WA200001458)                              | [Deploy Box for Teams](https://support.box.com/hc/en-us/articles/360044681354-Deploying-Box-for-Teams-in-your-Enterprise)                               | [Consent in admin center](https://admin.teams.microsoft.com/policies/manage-apps/8d04bcf6-86d8-4ab1-9602-bc3b56e06c37/permission).       |
| [Freshdesk](https://appsource.microsoft.com/product/office/WA104381505)                                  | [Deploy Freshdesk for Teams](https://support.freshdesk.com/en/support/solutions/articles/232273-the-microsoft-teams-app)                                | [Consent in admin center](https://admin.teams.microsoft.com/policies/manage-apps/86ce8ab3-7472-47ef-9cf5-7225ff0c77d5/permission).       |
| [MyHub](https://appsource.microsoft.com/product/office/WA200000726)                                      | Setup isn't required.                                                                                                                                   | [Consent in admin center](https://admin.teams.microsoft.com/policies/manage-apps/c3ff6344-f6f0-4bfa-8697-b9d47b32ca4b/permission).       |
| [OfficeSpace](https://appsource.microsoft.com/product/office/WA200002052)                                | [Deploy OfficeSpace for Teams](https://support.officespacesoftware.com/s/article/Integrating-OfficeSpace-with-Microsoft-Teams-HC?language=en_US)        | Not required                                                                                                                             |
| [SAP S/4HANA for Microsoft Teams](https://appsource.microsoft.com/product/office/WA200005087)            | [Deploy SAP S/4HANA for Teams](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/257ec7408db6420682462cd1d000e744.html)       | [Consent in admin center](https://admin.teams.microsoft.com/policies/manage-apps/db5b69c6-0430-4ae1-8d6e-a65c2220b50c/permission).       |
| [ServiceBot](https://appsource.microsoft.com/product/office/WA200000757)                                 | [Deploy ServiceBot for Teams](https://support.freshservice.com/en/support/solutions/articles/50000000656-freshservice-integration-with-microsoft-teams) | [Consent in admin center](https://admin.teams.microsoft.com/policies/manage-apps/f1f1c9fe-bc63-4b4b-8cfc-472108147118/permission).       |
| [ServiceDesk Plus Cloud for Microsoft Teams](https://appsource.microsoft.com/product/office/WA200000037) | [Deploy ServiceDesk Plus Cloud for Teams](https://help.servicedeskplus.com/integration-with-microsoft-teams)                                            | Not required                                                                                                                             |
| [Smartsheet](https://appsource.microsoft.com/product/office/WA104380975)                                 | Setup isn't required.                                                                                                                                   | [Consent in admin center](https://admin.teams.microsoft.com/policies/manage-apps/f4d81e8e-4500-44c2-8328-9e06cbe037c5/permission)        |
| [Templafy](https://appsource.microsoft.com/product/office/WA200004361)                                   | [Deploy Templafy for Teams](https://support.templafy.com/hc/en-us/articles/360015220358)                                                                | Not required                                                                                                                             |
| [Thrive Global](https://appsource.microsoft.com/product/office/WA200004531)                              | [Contact Thrive Global](https://thriveglobal.com/products/thrive-for-teams) for information.                                                                                                                  | [Consent in admin center](https://admin.teams.microsoft.com/policies/manage-apps/d4774f88-9a5e-470c-9a8f-c77b63b6e322/permission) |
| [Workplace from Facebook](https://appsource.microsoft.com/product/office/WA200003462)                    | [Deploy Workplace from Facebook for Teams](https://www.workplace.com/help/work/641802850313984)                                                         | Not required                                                                                                                             |
| [Zendesk for Teams](https://appsource.microsoft.com/product/office/WA200003782)                          | [Deploy Zendesk for Teams](https://zendeskforteams.com/installation-guide)                                                                              | [Consent in admin center](https://admin.teams.microsoft.com/policies/manage-apps/f36c0433-ea87-4102-bea7-0a8456fa8a2e/permission).       |
| [Zoho Projects](https://appsource.microsoft.com/product/office/WA104381668)                              | [Deploy Zoho Projects for Teams](https://help.zoho.com/portal/en/kb/projects/integration/microsoft/articles/microsoft-teams-integration)                | Not required                                                                                                                             |

Consider the following app installation information when following the above developer instructions for this feature.

* Some app setup instructions include deploying the app using app setup policies. Using setup policy is optional with this feature. You may continue preinstalling apps8 as an admin with app setup policies or you may enable Auto install approved apps feature to install for your users without your intervention.

* Some app setup instructions include steps to install the app in multiple scopes that are personal, team, chat, and meeting. Auto install approved apps feature installs an app only in the personal app for an individual user. You can follow app developer's setup instructions to deploy the other app scopes, besides personal apps.

## Related articles

* [How to allow apps in an organization](/microsoftteams/manage-apps#allow-or-block-apps)
* [Use app permission policies to allow users to use an app](/microsoftteams/teams-app-permission-policies)
* [How to grant admin consent to the app permissions](/microsoftteams/app-permissions-admin-center)
* [Permissions and consent in the Microsoft Entra ID](/azure/active-directory/develop/permissions-consent-overview)
* [Configure in Microsoft Entra admin center how users consent to apps](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal&pivots=portal)
