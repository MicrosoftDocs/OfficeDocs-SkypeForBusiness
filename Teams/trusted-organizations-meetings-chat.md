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

You can configure external meetings and chat in Teams using the *external access* feature. External access is a way for Teams users from outside your organization to find, call, chat, and set up meetings with you in Teams. You can also use external access to communicate with people from other organizations who are still using Skype for Business (online and on-premises) and Skype.

If you want people from other organizations to have access to your teams and channels, use guest access instead. For more information about the differences between external access and guest access, see [Compare external and guest access](communicate-with-users-from-other-organizations.md#compare-external-and-guest-access). 


Use external access when:
  
- You have users in external domains who need to chat. For example, Rob@contoso.com and Ann@northwindtraders.com are working on a project together along with some others in the contoso.com and northwindtraders.com domains.

- You want the people in your organization to use Teams to contact people in specific businesses outside of your organization.

- You want anyone else in the world who uses Teams to be able to find and contact you, using your email address. 


## Plan for external meetings and chat

External access policies include controls for both the organization and user levels. Turning a policy off at the organization level turns it off for all users, regardless of their user level setting. All external access settings are enabled by default.

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

**Using the Microsoft Teams admin center**

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

To communicate with another tenant, they must either enable **Allow all external domains** or add your tenant to their list of allowed domains by following the same steps above.  


### Enable federation between users in your organization and other organizations

To enable users in your organization to communicate with users in another organization, both organizations must enable federation. The steps to enable federation for a given organization depend on whether the organization is purely online, hybrid, or purely on-premises.

| If your organization is | Enable federation as follows |
|:---------|:-----------------------|
|Online with no Skype for Business on-premises. This includes organizations that have TeamsOnly users and/or Skype for Business Online users.| If using Teams Admin Center: <br>- Make sure the domains that you want to communicate with are allowed for external access.<br><br>If using PowerShell:<br>- Ensure the tenant is enabled for federation: `Get-CsTenantFederationConfiguration` must show `AllowFederatedUsers=true`. <br>- Ensure the user's effective value of `CsExternalAccessPolicy` has `EnableFederationAccess=true`.<br>- If you are not using open federation, ensure the target domain is listed in `AllowedDomains` of `CsTenantFederationConfiguration`. |
|On-premises only| In on-premises tools: <br>- Ensure federation is enabled in `CsAccessEdgeConfiguration`.<br>- Ensure federation for the user is enabled through `ExternalAccessPolicy` (either through the global policy, site policy, or user assigned policy). <br> - If you are not using open federation, ensure the target domain is listed in `AllowedDomains`.|
|Hybrid with some users online (in either Skype for Business or Teams) and some users on-premises. | Follow above steps for both online and on-premises organizations. |

## Delivery of incoming chats and calls 

Incoming chats and calls from a federation organization will land in the user's Teams or Skype for Business client depending on the recipient user's mode in TeamsUpgradePolicy.

| If you want to | Do this: |
|:---------|:-----------------------|
|Ensure incoming federated chats and calls arrive in the user's Teams client|Configure your users to be TeamsOnly.
|Ensure incoming federated chats and calls arrive in the user's Skype for Business client|Configure your users to be in any mode other than TeamsOnly.|

## Federation Diagnostic Tool

If you're an administrator, you can use the following diagnostic tool to validate a Teams user can communicate with a federated Teams user:

1. Select **Run Tests** below, which will populate the diagnostic in the Microsoft 365 Admin Center. 

   > [!div class="nextstepaction"]
   > [Run Tests: Teams Federation](https://aka.ms/TeamsFederationDiag)

2. In the Run diagnostic pane, enter the **Session Initiation Protocol (SIP) Address** and the **Federated tenant's domain name**, and then select **Run Tests**.

3. The tests will return the best next steps to address any tenant or policy configurations that are preventing communication with the federated user.

## Related topics

