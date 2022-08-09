---
title: View app permissions and grant admin consent in the Microsoft Teams admin center
author: guptaashish
ms.author: guptaashish
ms.reviewer: vaibhava
manager: prkosh
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to view permissions requested by apps and grant admin consent to apps on the Manage apps page of the Microsoft Teams admin center. 
ms.localizationpriority: high
ms.collection: M365-collaboration
appliesto: 
- Microsoft Teams
---

# View app permissions and grant admin consent in the Microsoft Teams admin center

The [Manage apps](manage-apps.md) page in the Microsoft Teams admin center is where you view and manage all Teams apps for your organization. For example, you can see the org-level status and properties of apps, approve or upload new custom apps to your organization's app store, block or allow apps at the org level, and manage org-wide app settings.

Here, you can also grant org-wide admin consent to apps that request permissions to access data and view resource-specific consent (RSC) permissions for apps.

## Grant org-wide admin consent to an app

If you're a global admin, you can review, and grant consent to apps that request permissions on behalf of all users in your organization. You do this so that users don't have to review and accept the permissions requested by the app when they start the app. Additionally, depending on the user's [consent settings](/azure/active-directory/manage-apps/configure-user-consent) in Azure Active Directory (Azure AD), some users may not be allowed to grant consent to apps that access company data.

Examples of permissions requested by apps include the ability to read information stored in a team, read a user's profile, and send an email on behalf of users. To learn more, see [Permissions and consent in the Microsoft identity platform endpoint](/azure/active-directory/develop/v2-permissions-and-consent).

The **Permissions** column indicates whether an app has permissions that need consent. You'll see a **View details** link for each app registered in Azure AD that has permissions that need consent. Keep in mind that this applies only to custom and third-party apps. The link isn't available for apps provided by Microsoft. Also, admins don't have to grant consent for such apps.

To grant org-wide consent to an app, follow these steps:

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Do one of the following:
    * Search for the app you want, select the app name to go to the app details page, and then select the **Permissions** tab.
    * Sort the **Permissions** column in descending order to find the app, and then select **View details**. Doing this takes you to the **Permissions** tab of the app details page.

1. Under **Org-wide permissions**, select **Review permissions and consent**.

    :::image type="content" source="media/app-perm-admin-center-org-wide.png" alt-text="Screenshot of org-wide permissions on the Permissions tab for an app.":::

    You must be a global admin to do this. This option isn't available to Teams service admins.

1. On the **Permissions** tab, review the permissions requested by the app.

    :::image type="content" source="media/app-perm-admin-center-org-wide-permissions.png" alt-text="Screenshot of permissions requested by an app.":::

    > [!IMPORTANT]
    > Granting org-wide consent to an app allows the app to access your organization's data. Carefully review the permissions requested by the app before you grant consent.

1. If you agree with the permissions requested by the app, select **Accept** to grant consent. A banner temporarily appears at the top of the page to let you know that the requested permissions have been granted for the app. The app now has access to the specified resources for all users in your organization and no one else will be prompted to review the permissions.

After you accept the permissions, you'll see a message under **Org-wide permissions** on the app details page to let you know that consent was granted. To view details about the app's permissions, select the **Azure Active Directory** link to go to the app's page in the Azure AD portal.

:::image type="content" source="media/app-perm-admin-center-org-wide-accepted-new.png" alt-text="Screenshot of message displayed when consent granted.":::

If users in your organization are allowed to grant consent and if one or more users granted consent to a particular app, you'll also see the same message to let you know that consent was granted and the Azure Active Directory link to the app's page in the Azure AD portal.

> [!NOTE]
> Although, the **Review permissions and consent** option isn't available to Teams service admins and they can't grant org-wide admin consent to apps, Teams service admins can view the content on the **Permissions** tab for an app. For example, a Teams service admin can click the **Azure Active Directory** link to view app permissions details in the Azure AD portal.

## View resource-specific consent permissions of an app

RSC permissions let team owners grant consent for an app to access and modify a team's data. RSC permissions are granular, Teams-specific permissions that define what an app can do in a specific team. Examples of RSC permissions include the ability to create and delete channels, get the settings for a team, and create and remove channel tabs.

RSC permissions are defined in the app manifest and not in Azure AD. You grant consent to RSC permissions when you add the app to a team. To learn more, see [Resource-specific consent (RSC)](/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

Global admins and Teams service admin can view RSC permissions for an app on the **Permissions** tab of the app details page.

To view RSC permissions for an app, follow these steps:

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
1. Search for the app you want, select the app name to go to the app details page, and then select the **Permissions** tab.
1. Under **Microsoft Graph resource-specific consent (RSC) permissions**, review the RSC permissions requested by the app.

    :::image type="content" source="media/app-perm-admin-center-rsc-new.png" alt-text="Screenshot of RSC permissions for an app.":::

## Known issues

### The "View details" link isn't displayed in the Permissions column for some third-party apps that request permissions

Currently, the ability to review permissions and grant consent isn't available for all third-party apps registered in Azure AD that request permissions. Instead of the **View details** link, you'll see **--** in the **Permissions** column. We're working with ISVs to enable this feature for their apps.

## Related topics

* [Manage your apps in the Microsoft Teams admin center](manage-apps.md)
* [Permissions and consent in the Microsoft identity platform endpoint](/azure/active-directory/develop/v2-permissions-and-consent)
* [Resource-specific consent in Teams](resource-specific-consent.md)
* [Resource-specific consent (RSC)](/microsoftteams/platform/graph-api/rsc/resource-specific-consent)
* [Navigate the Teams app lifecycle](https://aka.ms/PR132) (Ignite 2020 session)
