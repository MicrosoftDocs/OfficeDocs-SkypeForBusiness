---
title: "Move users between on-premises and cloud"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
ms.custom:
description: "Summary: In an on-premises deployment of Skype for Business Server that is enabled for hybrid, you can move users between the on-premises environment and the cloud (whether to Microsoft Teams or to Skype for Business Online).."
---

# Move users between on-premises and cloud

In an on-premises deployment of Skype for Business Server that is enabled for hybrid, you can move users between the on-premises environment and the cloud (whether to Microsoft Teams or to Skype for Business Online). Whether a user is located on-premises or in the cloud is known as the user’s Skype for Business home:

- Users who are homed on premises interact with on-premises Skype for Business servers.
- Users who are homed online may interact with Skype for Business Online service.

*Teams users inherently have a Skype for Business home, whether they use Skype for Business or not.* If you have on-premises Skype for Business users that are also using Teams (side by side), those users are homed on premises. Teams users with Skype for Business on premises do not have the ability to interoperate with Skype for Business users from their Teams client, nor can they communicate from Teams with users in a federated organization. Such functionality is only available after the user is moved from Skype for Business on premises to online. When you move a user to online, you can either allow them to use Skype for Business Online (and, optionally, Teams) or you can make them Teams Only. If your organization is already using Teams, it’s strongly recommended that you move them to Teams Only mode, which will ensure that routing of all incoming chats and calls lands in their Teams client. For more details, see [Teams coexistence with Skype for Business](microsoftteams/coexistence-chat-calls-presence) and [Migration and interoperability guidance for organizations using Teams together with Skype for Business](microsoftteams/migration-interop-guidance-for-teams-with-skype).


Pre-requisites to move a user to the cloud (whether to Skype for Business Only or Teams Only mode):

- The organization must have Azure AD Connect properly configured and be syncing all relevant attributes for the user as described in [Configure Azure AD Connect](configure-azure-ad-connect.md).
- Skype for Business hybrid must be configured, as described in [Configure Skype for Business hybrid](configure-federation-with-skype-for-business-online.md).
- The user must be assigned a license for Skype for Business Online, and if they will be using Teams, they must also have a Teams license.

When a user is moved from on-premises to the cloud:

- The user starts using Skype for Business Online services in the cloud for any Skype for Business functionality.
- Teams users become enabled for interoperability with Skype for Business users, and they can also federate with other organizations.
- Contacts from on premises are moved to the cloud (either Skype for Business or Teams).
- Existing meetings they organized that are scheduled in the future are migrated to online. Note that any content that was uploaded in advance of the meeting is not moved.

To move users between on premises and the cloud (whether to Teams or to Skype for Business Online), use either the Move-CsUser cmdlet or the Skype for Business Admin Control Panel, both of which are on-premises tools. These tools support three different move paths:

- From Skype for Business Server (on-premises) to Skype for Business Online.
- From Skype for Business Server (on premises) directly to Teams Only (which also moves them to Skype for Business Online).  The option to move directly from on premises to Teams Only is available in Skype for Business Server 2019 as well as Cumulative Update 8 for Skype for Business Server 2015. Organizations using earlier versions of Skype for Business Server can move users to Teams Only by first moving them to Skype for Business Online, and then applying the TeamsOnly mode to these users once they are online.
- From online (whether Teams Only or not), to on premises.

Important:

- Moving users between on premises and the cloud requires admin permissions in both the on-premises Skype for Business deployment and in Skype for Business Online. This is achieved by accessing the on-premises tools using on-premises credentials; then those tools (whether move-csuser or the UI) will prompt for credentials in the Office 365 tenant. 
- The users have either tenant admin privileges (“Global”) or Skype for Business Admin privileges in Office 365.
- If you are using the Skype for Business Admin Control Panel, when specifying the tenant admin credential you must use an account that ends in .onmicrosoft.com. 
- If you are using move-csuser in PowerShell, you can either use an account that ends in .onmicrosoft.com, or you can use any on-premises account that is synchronized into Azure AD, provided that you also specify a HostedMigrationOverrideUrl in the cmdlet.

Other considerations:

- The policies (such as to control messaging, meeting, and calling behavior) in on-premises and online environments are independent. You may want to consider configuring any policies in the environment and assigning them to the user before you move that user from on premises to the cloud, so that they have the correct configuration as soon as they are migrated to online.
- If users are configured for enterprise voice in on-premises, you will need to coordinate updating their voice configuration when you move them to online, or, alternatively, you could migrate them without telephony capabilities. The available options depend on whether the user will be using the Teams or Skype for Business client once they are online:
  - You can update a user’s telephony provider to use a Microsoft Calling Plan. This is an option whether users will use Teams or Skype for Business clients.
  - You can continue to use your on-premises PSTN provider in conjunction with Direct Routing for users that will use Teams.
  - You can continue to use your on-premises PSTN provider in conjunction with Skype for Business Hybrid Voice functionality for users that will continue to use Skype for Business client after they are moved online.
  - Users who will be using Teams must use Direct Routing.

  For more details, see XXXXX.
