---
title: Teams apps permissions and consent
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.subservice: teams-apps
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - M365-collaboration
  - Tier1
search.appverid: MET150
ms.date: 10/27/2023
ms.reviewer: Orion.OMalley
description: Understand permissions and manage consent for Teams apps to access the required org information.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Understand Teams app permissions and consent

IT admins grant consent to apps after they validate the compliance, security, and data handling information of an app and also understand the permissions requested by the app and how are those permissions relevant to the app's use cases. IT admins create a balance between their user's need for productivity and their organizations needs for safety and security. To do so, admins must understand the potential of permissions, how Teams apps use these, and how they can approve or reject the apps that seek a set of such permissions.

## Teams apps and permissions

Depending on their functionality, Teams apps may or may not access your user's or organization's information.

* Apps that don't seek access to organization's data, don't require an approval or consent. Users can use such apps without admin approval or consent as these apps can't get any internal data.
* Apps that require access to your organization's or user's information can't be used unless an admin or a user allows an app to do so. Admins can configure if users can grant consent to some permissions or not. You must do your diligence to evaluate apps based on the access it needs on your organization's information and the reason why it needs the access. You can also revoke consent that you've granted to some permissions of an app.

An application can access an organization's information in the following ways depending on the permissions used by the developer. Understand it to know the different ways in which you can provide consent or enable users to consent for Teams apps in your org.

|                              | Delegated permissions                                               | Application permissions         | Remarks           |
|------------------------------|---------------------------------------------------------------------|--------------------------------|---------------------|
| How apps access information  | App accesses info using its identity                                | App access information on behalf of a user.    |                 |
| What information is accessed | Any info that a consented permission is associated with             | Permissions that app is granted consent to and signed-in user's access to information.   |       |
| What roles can consent       | Admins or users or group owners depending on Azure AD configuration | Only admins   |     |
| Can users consent            | Users can consent depending on Azure AD configuration               | Only admins can consent   |     |
| Can admins let users consent for some permissions | Admins can classify some or all Delegated permissions as low-risk to let users consent to these in any app   |   Admins can't classify any Application permissions as low-risk   |    |




Teams app permissions are defined in the following two places:

* **Azure Active Directory**: Graph permissions lets an app access org-wide resources. Permissions that are needed for an app to work are added in Azure AD by the app developers. As an admin, you must consent to these permissions otherwise the app can't be used in your tenant. Admins can define if users can consent to these permissions or not.
* **Teams app manifest**: RSC permissions are defined in the app manifest file by the app developers. RSC permissions lets an app access local resources within Teams such as information in a group or a team. These allow only for Application access and not for Delegated access. Only those users who have access to the resources, can consent for these permissions. Admin consent at org-level is not required though admins control how users consent to these permissions or can block users from consenting.







For each app, these permissions are listed in the app details page in the admin center.

| App permission type | Access context | Declaration source | When is consent required? | Who can consent? | Documentation |
|---------------------|----------------|-------------|--------------------------|-----------------|-----------------------|
| Microsoft Entra ID for Graph and legacy endpoint access | Delegated | Microsoft Entra ID | App sign-in  | Global Admin, Cloud Application Admin, and Application Admin | See [Microsoft Graph permissions required by Teams apps](#graph-permissions-required-by-teams-apps-to-access-your-organizations-information). |
| Microsoft Entra ID for Graph and legacy endpoint access | Application | Microsoft Entra ID |  App sign-in  |  Global Admin, Cloud Application Admin, and Application Admin | See [Microsoft Graph permissions required by Teams apps](#graph-permissions-required-by-teams-apps-to-access-your-organizations-information). |
| RSC for information of teams, chats, and users | Delegated | App manifest file | Adding app to a team, chat, meetings | Resource owner. | See [RSC permissions reference](/graph/permissions-reference#teams-resource-specific-consent-permissions). |
| RSC for information of teams, chats, and users | Application | App manifest file |  Adding app to a team, chat, meetings  | Resource owner | See [RSC permissions reference](/graph/permissions-reference#teams-resource-specific-consent-permissions). |
| Other permissions and data access | Delegated via SDKs | Manifest properties define it | Add app in a client | Consent is implied at install. | Available in the `Permissions` tab in app details page of each app. More details are [here](#what-can-apps-do-in-teams). |

## Privacy and data access considerations

In the terms of use and privacy policy of any app, the app developer discloses what data their app uses and how it's handled. This information is available on app developer's website and you can access the URLs in the app details page in Teams admin center.

:::image type="content" source="media/app-details-tou-url.png" alt-text="Screenshot that shows privacy and terms of use URLs in the app details page." lightbox="media/app-details-large.png":::

Many app developers choose to undergo the Microsoft 365 app compliance program. The program checks and audits an app against controls that are derived from leading industry-standard frameworks. The detailed information about each such app is available on Microsoft website at [Teams Apps Security and Compliance](/microsoft-365-app-certification/teams/teams-apps).

The program demonstrates that strong security and compliance practices are in place to protect customer data. See the details in [app compliance program for security, data handling, and privacy](overview-of-app-certification.md).

## Graph permissions required by Teams apps to access your organization's information

Microsoft Graph is used to allow app developers access to the requisite Microsoft cloud information but always with the appropriate consent. App developers choose from a wide variety of Graph APIs to create their apps and fetch the relevant org information to make the app functionality work. However, the permissions for an app to fetch such information must be consented to for the APIs to access an org's info.

In Teams admin center, you can view Graph permission that an app requests if deployed and you can know what organization's information can an app access, if you grant consent to it.

1. Access Teams admin center and open the **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** page.

1. Search for the required app and select its name to open the app details page.

1. In the app details page, in the **Permissions** tab, notice the permissions required by the app.

   :::image type="content" source="media/app-permissions.png" alt-text="Screenshot showing the page in admin center that list and requests permissions for an app and also allows admins to grant consent for such permissions for all org-users.":::

A complete list of all the possible permissions is available at [Microsoft Graph permissions reference](/graph/permissions-reference).

## Settings related to consent for permissions

Azure AD configurations control the flow of consent for an organization. Global Administrator and Cloud Application Administrator can configure a tenant to achieve the following use cases for Teams apps:

* [Let resource owners consent to RSC permissions](#let-resource-owners-consent-to-rsc-permissions) for any app.
* [Let users grant consent to low risk Graph permissions](#let-users-grant-consent-to-low-risk-graph-permissions) for any app.
* [Grant org-wide consent for a Teams app](#grant-org-wide-admin-consent-to-app-permissions).





## Let resource owners consent to RSC permissions







### Let users grant consent to low risk Graph permissions

You can configure user consent settings in way that lets users to:

* Not be able to consent to any apps.
* Consent to selected permissions (recommended approach).
* Consent to all apps.

The recommended approach works together with permissions classification. The classification let admins define some or all of the Delegated Graph permissions as low risk permissions within their organization. Admins decide low risk permissions based on their organization's risk posture. As a safety measure, you can't categorize Application permissions low risk. Application permissions require only an admin to consent. For more information, see [configure how users consent to applications](/azure/active-directory/manage-apps/configure-user-consent?pivots=portal) and [how to classify permissions as low or high risk](/azure/active-directory/manage-apps/configure-permission-classifications?pivots=portal).

To accomplish this configuration, you must have a Global Administrator, Application Administrator, or Cloud Application Administrator role in your tenant.

This configuration applies to all Teams apps as all Teams apps are from verified publishers. Before an app developer can submit their app to Microsoft, a developer is required to undergo a verification. Publisher verification helps admins and users understand the authenticity of application developers. For more details, see [publisher verification](overview-of-app-certification.md).

### Grant org-wide admin consent to app permissions

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

















## What can apps do in Teams

As an admin, you manage Teams apps and not their capabilities. [Teams apps have capabilities](apps-in-teams.md#understand-app-capabilities) that allow apps to accomplish their core use case and accomplish some tasks. The [capabilities are provided by SDKs](/microsoftteams/platform/concepts/build-and-test/tool-sdk-overview) and don't require any consent. The tasks that apps can accomplish that are associated with capabilities are different from the permissions that require consent by an admin.

Depending on the capabilities, apps interact with users and access the data that users provide to it. You as an admin must consider what an app can do and how it interacts with users based on the following capabilities.

* [Bots and Messaging extensions](#bots-and-messaging-extensions)
* [Tabs](#tabs)
* [Connectors](#connectors)
* [Outgoing webhooks](#outgoing-webhooks)

### Bots and Messaging Extensions

Consider the following types of user interaction, required permissions, and data access by bots and messaging extensions:

* A bot can receive messages from users and reply to them. Bots only receive messages in chats where users explicitly mention a bot by its name. This data leaves the corporate network.

* After a user has sent a message to a bot, the bot can send the user direct or proactive messages at any time.

* Some bots only send messages. They're called notification-only bots and the bot doesn't offer a conversational experience.

* A bot added to teams can get a list of names and IDs of the channels in a team.

* When it's used in a channel, in a personal chat, or a group chat, the app's bot can access basic identity information of team members (first name, last name, user principal name [UPN], and email address).

* It's possible for an app's bot to send direct or proactive messages to team members even if they haven't interacted with the bot.

* Depending on settings and functioning of an app that is a bot, it can send and receive files in personal chat only. It isn't supported for group chats or channels.

* Bots only have access to teams to which they've been added or to users who have installed them.

* When a user converses with a bot, if the bot stores the user's ID, it can send the user direct messages at any time.

* If necessary, a user or an admin can block a bot. Microsoft can also remove a bot from the store. [App verification and validation checks](overview-of-app-validation.md) ensures high quality apps are available in Teams store.

* A bot can retrieve and may store basic identity information for the team members the app has been added to, or for individual users in personal or group chats. To get further information about these users, the bot must require them to sign in to Microsoft Entra ID.

* Bots can retrieve and may store the list of channels in a team. This data leaves the corporate network.

* By default, bots don't have the ability to act on behalf of the user, but bots can ask users to sign in; as soon as the user signs in, the bot has an access token with which it can do other tasks. The tasks depend on the bot and where the user signs in: a bot is a Microsoft Entra app registered at `https://apps.dev.microsoft.com/` and can have its own set of permissions.

* When a file is sent to a bot, the file leaves the corporate network. Sending and receiving files requires user approval for each file.

* Bots are informed whenever users are added to or deleted from a team.

* Bots don't see users' IP addresses or other referrer information. All information comes from Microsoft. (There's one exception: if a bot implements its own sign-in experience, the sign-in UI sees users' IP addresses and referrer information.)

* Messaging extensions, on the other hand, do see users' IP addresses and referrer information.

* App guidelines (and our AppSource review process) require discretion in posting personal chat messages to users (via the POST_MESSAGE_TEAM permission) for valid purposes. If necessary, users can block the bot, tenant admins can block the app, and Microsoft can remove the app that works as a bot.

> [!NOTE]
>
> * If a bot has its own sign-in, there's a different consent experience the first time the user signs in.
> * Users can search apps with the `botId` that was available in the app. While users can view the app name but they can't interact with such bots.

### Tabs

A tab is a website running inside Teams. It can be as a tab in a meeting, a chat, or a channel.

Consider the following types of user interaction or data access for Tabs:

* Users opening a tab in a browser or in Teams is exactly the same. The website itself can't have access to any organization's information on its own.

* A tab also gets the context in which it's running, including the sign-in name and UPN of the current user, the Microsoft Entra Object ID for the current user, the ID of the Microsoft 365 group in which it resides (if it's a team), the tenant ID, and the current locale of the user. However, to map these IDs to a user's information, the tab would have to make the user sign in to Microsoft Entra ID.

### Connectors

A connector posts messages to a channel when events in an external system occur. The required permission for Connectors is to be able to post messages in channel. An optional permission for Connectors is the permission to reply to a message. Some connectors support actionable messages, which allow users to post targeted replies to the connector message. For example, by adding a response to a GitHub issue or adding a date to a Trello card. Consider the following types of user interaction, required permissions, and data access by Connectors:

* The system that posts connector messages doesn't know who it's posting to or who receives the messages. No information about the recipient is disclosed. (Microsoft is the actual recipient, not the tenant; Microsoft does the actual post to the channel.)

* No data leaves the corporate network when Connectors post messages in a channel.

* Connectors that support actionable messages also don't see IP address and referrer information; this information is sent to Microsoft and then routed to HTTP endpoints that were previously registered with Microsoft in the Connectors portal.

* Each time a Connector is configured for a channel, a unique URL for that connector instance is created. If that connector instance is deleted, the URL can no longer be used.

* Connector messages can't contain file attachments.

* The Connector instance URL should be treated as secret or confidential. Anyone who has the URL can post to it. If necessary, team owners can delete the connector instance.

* If necessary, a tenant administrator can prevent new Connector instances from being created and Microsoft can block all usage of a Connector app.

### Outgoing webhooks

Team owners or team members create Outgoing webhooks. Outgoing webhooks can receive messages from users and reply to them. Consider the following types of user interaction, required permissions, and data access by Outgoing webhooks:

* Outgoing webhooks are similar to bots but have fewer privileges. They must be explicitly mentioned, just like bots.

* When an outgoing webhook is registered, a secret is generated, which allows the outgoing webhook to verify that the sender is Microsoft Teams as opposed to a malicious attacker. This secret should remain a secret; anyone who has access to it can impersonate Microsoft Teams. If the secret is compromised, delete and re-create the outgoing webhook to generate a new secret.

* Although it's possible to create an outgoing webhook that doesn't validate the secret, we recommend against it.

* Other than receiving and replying to messages, outgoing webhooks can't do much: they can't proactively send messages, they can't send or receive files, they can't do anything else that bots can do except receive and reply to messages.

## Related articles

* [RSC permissions reference](/graph/permissions-reference#teams-resource-specific-consent-permissions).

