---
title: Grant and manage consent to Teams app permissions
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: how-to
audience: admin
ms.service: msteams
ms.subservice: teams-apps
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - M365-collaboration
  - Tier1
search.appverid: MET150
ms.date: 12/19/2023
ms.reviewer: Orion.OMalley
description: Manage consent to Teams apps permissions to access the required org information.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Grant and manage consent to Teams app permissions

<!---

Add this content:
1 para summary of permissions
Link back to [View and understand app permissions](app-permissions.md)
related articles from AAD:
- Revoke consent
- Grant consent by constructing your own AAD URL
- Re-grant permissions after app update. Screenshot already available locally. Link to [conditions when an app update requires re-consenting](apps-update-experience.md)
- Consent for self vs for users when using the app

 
Add this content later; move this list to an ADO:
- About device permissions
- About custom apps and Graph permissions? If Global Admin uploads a custom app or approves a custom app, is there a prompt to give consent at that time OR is the consent implied if a Global Admin does it?
- Any examples of JIT consent
- Discrepancy in permissions shown in client vs in TAC listing. Refer chat with Deepjyoti
- How to grant consent to RSC permissions? Example app to take screenshot of? If admins can't, then is it always users who do it?
- Will the app completely stop working OR will it work with limited functionality if limited consent is granted? Example of both? Vantage Rewards continued to work but Talview stopped working.
- Verify if delegated admin eval mentioned in AAD docs is applicable for Teams app or not.

 
--->

Examples of permissions requested by apps include the ability to read information stored in a team, read a user's profile, and send an email on behalf of users. To learn more, see [Permissions and consent in the Microsoft identity platform endpoint](/azure/active-directory/develop/v2-permissions-and-consent).

If you're a Global Administrator, you can review, and grant consent to apps that request permissions on behalf of all users in your organization. You do this so that users don't have to review and accept the permissions requested by the app when they start the app. Additionally, depending on the user's [consent settings](/azure/active-directory/manage-apps/configure-user-consent) in Microsoft Entra ID, some users may not be allowed to grant consent to apps that access company data.









The **Permissions** column indicates whether an app has permissions that need consent. You'll see a **View details** link for each app registered in Microsoft Entra ID that has permissions that need consent. Keep in mind that this applies only to custom and third-party apps. The link isn't available for apps provided by Microsoft. Also, admins don't have to grant consent for such apps.






## Let resource owners consent to RSC permissions

Admins can configure whether users can let apps access their groups' or teams' data or not. Global Administrators can change the **Group owner consent for apps accessing data** settings in Entra ID, to [let users to consent to RSC permissions](/entra/identity/enterprise-apps/configure-user-consent-groups#manage-group-owner-consent-to-apps-by-directory-settings).

If you don't let group owner consent for apps, then users can't consent to RSC permissions in an app, if RSC permissions are used.

## Let users grant consent to low risk Graph permissions

You can configure user consent settings in way that lets users to:

* Not be able to consent to any apps and hence use only admin-approved apps.
* Consent to selected permissions (recommended approach) and use app that required only these specific permissions.

The recommended approach works together with permissions classification. The classification let admins define some or all of the Delegated Graph permissions as low risk permissions within their organization. Admins decide low risk permissions based on their organization's risk posture. As a safety measure, you can't categorize Application permissions low risk. Application permissions require only an admin to consent. For more information, see [configure how users consent to applications](/azure/active-directory/manage-apps/configure-user-consent?pivots=portal) and [how to classify permissions as low or high risk](/azure/active-directory/manage-apps/configure-permission-classifications?pivots=portal).

To accomplish this configuration, you must have a Global Administrator, Application Administrator, or Cloud Application Administrator role in your tenant.

This configuration applies to all Teams apps as all Teams apps are from verified publishers. Before an app developer can submit their app to Microsoft, a developer is required to undergo a verification. Publisher verification helps admins and users understand the authenticity of application developers. For more details, see [publisher verification](overview-of-app-certification.md).

## Grant org-wide admin consent to app permissions

If you're a Global Administrator, you can review app permissions and grant consent to those on behalf of all users in your organization. You do this so that users don't have to review and accept the permissions requested by the app when they start the app. Additionally, depending on the user's [consent settings](/azure/active-directory/manage-apps/configure-user-consent) in Azure Active Directory (Azure AD), some users may not be allowed to grant consent to apps that access company data.

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

RSC permissions let team owners grant consent for an app to access and modify a team's data. RSC permissions are granular, Teams-specific permissions that define what an app can do in a specific resource. Examples of RSC permissions include the ability to create and delete channels, get the settings for a team, and create and remove channel tabs.

RSC permissions are defined in the app manifest and not in Azure AD. You grant consent to RSC permissions when you add the app to a team. To learn more, see [Resource-specific consent (RSC)](/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

Global admins and Teams service admin can view RSC permissions for an app on the **Permissions** tab of the app details page.

To view RSC permissions for an app, follow these steps:

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
1. Search for the app you want, select the app name to go to the app details page, and then select the **Permissions** tab.
1. Under **Microsoft Graph resource-specific consent (RSC) permissions**, review the RSC permissions requested by the app.

    :::image type="content" source="media/app-perm-admin-center-rsc-new.png" alt-text="Screenshot of RSC permissions for an app.":::









## Related articles

* [View and understand app permissions](app-permissions.md)
* [RSC permissions reference](/graph/permissions-reference#teams-resource-specific-consent-permissions).
