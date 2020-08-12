---
title: Grant admin consent to apps in Microsoft Teams
author: LanaChin
ms.author: v-lanac
ms.reviewer: vaibhava
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to give admin consent to apps on the Manage apps page of the Microsoft Teams admin center. 
localization_priority: Normal
ms.collection: M365-collaboration
appliesto: 
- Microsoft Teams
---

# Grant admin consent to apps in Microsoft Teams

*****************

> [!NOTE]
> [!INCLUDE [new-feature-coming-soon-article](includes/new-feature-coming-soon-article.md)]



## Grant org-wide admin consent to an app

As an admin you can review and accept the permissions that an app requires for all users in your organization. You do this so users won’t have to review and accept the permissions for the app individually when they start the app.

Any app that has Azure AD permissions is listed in the **Permissions** column on the Manage apps page. This is for third-party apps registered in Azure AD that request permissions from users and admins, who must approve the request before the app can access data or act on a user's behalf. To learn more, see [Permissions and consent in the Microsoft identity platform endpoint](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent).



You have to be a global admin to grant org-wide consent to an app.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
2. Do one of the following:
    - Search for and find the app you want, click the app name to go to the app details page, and then select the **Permissions** tab.
    - Sort the **Permissions** column in descending order to find the app, and then select **View details**. Doing this takes you to the **Permissions** tab of the app details page.
3. Under **Org-wide permissions**, select **Review permissions and consent**.
4. Review the permissions requested by the app.

    > [!Warning]
    > Granting org-wide consent to an app allows the app to access your organization's data. Carefully review the permissions requested by the app before you grant consent.
5. If you agree with the permissions requested by the app, click **Accept** to grant consent. A banner temporarily appears at the top of the page to let you know that the requested permissions have been granted for the app. The app now has access to the specified resources for all users in your organization and no one else will be prompted to review the permissions.

After you accept the permissions, you'll see a message under **Org-wide permissions** on the app details page to let you know that the app has been granted consent for permissions.

To view details about the app's permissions, click **Azure Active Directory** to go to the app's page in the Azure AD portal. 

## Grant Microsoft Graph resource-specific consent permissions

Resource-specific consent (RSC) permissions lets admins and team owners grant consent for an app to access team data. RSC permissions are defined in the app manifest and not in Azure AD. You grant consent to RSC permissions when you add an app to a team. To learn more, see [Resource-specific consent (RSC)](https://docs.microsoft.com/microsoftteams/platform/graph-api/rsc/resource-specific-consent).


*****************

[!INCLUDE [preview-feature](includes/preview-feature.md)]

Resource-specific consent in Microsoft Teams lets team owners give consent to apps to access team data. Examples of such access include the ability to read channel messages, create and delete channels, and create and remove channel tabs.

As an admin, you control whether team owners in your organization can give consent through settings that you configure by using the Azure Active Directory (Azure AD) PowerShell module or the Azure portal and the Microsoft Teams admin center.  

## Set whether team owners can give consent to apps

Here are the settings that you must set to control whether team owners can give consent to apps. Be sure to review all the following settings.

### Settings in Azure AD

The following two settings determine whether team owners can give consent to apps.

> [!IMPORTANT]
> Changing any of these settings doesn't affect data access for apps that were already granted consent. For example, if you configure these settings to prevent team owners from giving consent, these changes don't remove data access that's already been granted.

#### The "Users can consent to apps accessing company data on their behalf" setting

This setting controls whether users in your organization can consent to apps on their behalf. To enable team owners to give consent, this setting must be set to **Yes**. To manage this setting, do the following:

1. In the Azure portal, go to **Enterprise applications** > **User settings**.
2. Under **Enterprise applications**, set **Users can consent to apps accessing company data on their behalf** to **No** or **Yes**.

You can also manage this setting using PowerShell. To learn more, see [Configure user content to applications](https://docs.microsoft.com/azure/active-directory/manage-apps/configure-user-consent#configure-user-consent-to-applications).

#### The "EnableGroupSpecificConsent" setting

This setting controls whether users in your organization can consent to apps accessing company data for the groups that they own. This setting must be enabled for team owners to give consent. For steps on how to manage this setting by using PowerShell, see [Configure group owner consent to apps accessing group data](https://docs.microsoft.com/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-to-apps-accessing-group-data).

### Settings in the Microsoft Teams admin center

In addition to settings in Azure AD, [org-wide app settings](manage-apps.md#manage-org-wide-app-settings) on the [Manage apps](manage-apps.md) page, whether an app is blocked or allowed on the [Manage apps](manage-apps.md#allow-and-block-apps) page, and the [app permission policy](teams-app-permission-policies.md) assigned to the team owner determine whether a team owner can give consent.

> [!IMPORTANT]
> Changing any of these settings doesn't affect data access for apps that were already granted consent. For example, if you disable third-party apps org-wide or if you block specific apps to prevent team owners from giving consent, these changes don't remove data access that's already been granted.  

#### The "Allow third party apps" setting in org-wide app settings

This org-wide app setting controls whether users in your organization can use third-party apps. This setting must be on to enable team owners to give consent. To manage this setting, do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**, and then click **Org-wide app settings**.
2. Under **Third party apps**, turn off or turn on **Allow third party apps**.

    ![Screenshot of the "Allow third party apps in Teams" setting](media/resource-specific-consent-org-wide-setting.png)

You may have to wait up to 24 hours for your changes to take effect.

#### Allow or block the app at the org level

When you block or allow an app on the [Manage apps](manage-apps.md#allow-and-block-apps) page, that app is blocked or allowed for all users in your organization. Team owners can only give consent to an app if the app is allowed. To allow or block an app at the org level, do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
2. On the Manage apps page, select the app, and then click **Block** to block it or click **Allow** to allow it.

    ![Screenshot of the blocked apps in org-wide settings](media/resource-specific-consent-allow-block-apps.png)

#### App permission policy assigned to the team owner

Team owners can only give consent to apps that their app permission policy allows them to run. To view and manage the app permission policy that's assigned to a team owner, do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**.
2. Double-click the display name of the team owner, and then click **Policies**.
3. The policy assigned to the team owner is listed under **App permission policy**.
    - To assign a different policy, click **Edit**, and then select the policy that you want to assign.
    - To edit the settings of the policy that's assigned to the team owner, click the policy name, and then make the changes that you want.  

## Uploading custom apps

When uploading a custom app (also known sideloading) that uses resource-specific consent, the app must come from the tenant that it's being installed to. In other words, the Azure AD app registration must be from this tenant. Global admins are exempted from this restriction, and can upload custom apps from any tenant, either directly to a team (sideloading) or to the tenant app catalog.

## Related topics

- [Resource-specific consent in Teams](resource-specific-consent.md)
- [Available RSC permissions](https://aka.ms/teams-rsc)
- [Microsoft Graph](https://developer.microsoft.com/graph)
- [Manage your apps in the Microsoft Teams admin center](manage-apps.md)
- [Manage app permission policies in Teams](teams-app-permission-policies.md)
