---
title: Configure trusted organizations for external meetings and chat
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: alsolom
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - m365initiative-externalcollab
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
- ms.teamsadmincenter.externalaccess.overview
- chat-teams-channels-revamp
appliesto: 
  - Microsoft Teams
ms.localizationpriority: normal
description: 
---

# Configure trusted organizations for external meetings and chat

You can configure meetings and chat with people in other organizations using the *external access* feature in Teams. External access is a way for Teams users from outside your organization to find, call, chat, and set up meetings with you in Teams. (If you are using Skype for Business hybrid, see [Configure external meetings and chat with Skype for Business Server hybrid](external-meetings-skype-for-business-server-hybrid.md).)

This article covers how to manage external meetings and chat with people in other Microsoft 365 and Azure Active Directory organizations. For information about managing chat and meetings with people who are not managed by an organization, see [Manage external meetings and chat with Teams for Life, Skype, and extended directory](skype-extended-directory-access.md).

If you want people from other organizations to have access to your teams and channels, use guest access instead. For more information about the differences between external access and guest access, see [Compare external and guest access](communicate-with-users-from-other-organizations.md#compare-external-and-guest-access). 

External access policies include controls for both the organization and user levels. Turning a policy off at the organization level turns it off for all users, regardless of their user level setting. All external access settings are enabled by default.

## Plan for external meetings and chat

The Teams admin center controls external access at the organization level. Most options (except domain restrictions) are available at the user level by using PowerShell. See [Using PowerShell](#using-powershell) below for more information.

> [!NOTE]
> If you turn off external access in your organization, people outside your organization can still join meetings through anonymous join. To learn more, see [Manage meeting settings in Teams](meeting-settings-in-teams.md).

> [!NOTE]
> Teams users can add apps when they host meetings or chats with people from other organizations. They can also use apps shared by people in other organizations when they join meetings or chats hosted by those organizations. The data policies of the hosting user's organization, as well as the data sharing practices of any third-party apps shared by that user's organization, are applied.

## Specify trusted organizations

You can allow or block certain domains in order to define which organizations your organization trusts for external meetings and chat. (Note that the other organizations will need to allow your organization's domain as well.)

If you add blocked domains, all other domains will be allowed; and if you add allowed domains, all other domains will be blocked. The exception to this rule is if anonymous participants are allowed in meetings. There are four scenarios for setting up external access in the Teams admin center (**Users** > **External access**):

- **Allow all external domains**: This is the default setting in Teams, and it lets people in your organization find, call, chat, and set up meetings with people external to your organization in any domain.

    In this scenario, your users can communicate with all external domains that are running Teams or Skype for Business so long as the other tenant also supports external communications.
    
- **Allow only specific external domains**: By adding domains to an **Allow** list, you limit external access to only the allowed domains. Once you set up a list of allowed domains, all other domains will be blocked. 

- **Block specific domains** - By adding domains to a **Block** list, you can communicate with all external domains *except* the ones you've blocked.  Once you set up a list of blocked domains, all other domains will be allowed.

- **Block all external domains** - Prevents people in your organization from finding, calling, chatting, and setting up meetings with people external to your organization in any domain.

> [!NOTE]
> People from blocked domains can still join meeting anonymously if anonymous access is allowed.

![Screenshot of external domains settings](./media/external-access-domain-settings.png)

To allow specific domains

1. In the Teams admin center, go to **Users** > **External access**.

2. Under **Choose which domains your users have access to**, choose **Allow only specific external domains**.

3. Select **Allow domains**.

4. In the **Domain** box, type the domain that you want to allow and then click **Done**.

5. If you want to allow another domain, click **Add a domain**.

6. Click **Save**.

To block specific domains

1. In the Teams admin center, go to **Users** > **External access**.

2. Under **Choose which domains your users have access to**, choose **Block only specific external domains**.

3. Select **Block domains**.

4. In the **Domain** box, type the domain that you want to allow and then click **Done**.

5. If you want to block another domain, click **Add a domain**.

6. Click **Save**.

To communicate with another organization, they must either enable **Allow all external domains** or add your organization to their list of allowed domains by following the same steps above.  



Note if you want chats and calls to arrive in the user's Skype for Business client, configure your users to be in any mode other than TeamsOnly.

## Diagnostic Tool

If you're an administrator, you can use the following diagnostic tool to validate if a Teams user can communicate with a Teams user in a trusted organization:

1. Select **Run Tests** below, which will populate the diagnostic in the Microsoft 365 Admin Center. 

   > [!div class="nextstepaction"]
   > [Run Tests: Teams Trusted Organizations](https://aka.ms/TeamsFederationDiag)

2. In the Run diagnostic pane, enter the **Session Initiation Protocol (SIP) Address** and the **Federated tenant's domain name**, and then select **Run Tests**.

3. The tests will return the best next steps to address any tenant or policy configurations that are preventing communication with the external user.

## Related topics

