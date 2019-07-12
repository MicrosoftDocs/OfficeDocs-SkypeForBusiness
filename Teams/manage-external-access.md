---
title: Manage external access (federation) in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 07/12/2019
ms.topic: article
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: karvell
search.appverid: MET150
f1keywords: 
- ms.teamsadmincenter.externalaccess.overview
description: Your IT admin can configure external access for other domains (federation) to let users from those domains participate in Teams. 
appliesto: 
- Microsoft Teams
localization_priority: Normal
---
Manage external access in Microsoft Teams
======================================================

With Microsoft Teams external access, Teams users from other domains can participate in your chats and calls. You can also allow othe external users who are still using Skype for Business Online, Skype for Business on-prem or even Skype to participate.

Use the steps in this article when:
  
- You have users in different domains in your business: for example, Rob@contoso.com and Ann@northwindtraders.com.

- You want the people in your organization to use Teams to contact people in specific businesses outside of your organization.

- You want anyone else in the world who uses Teams to be able to find and contact you, using your email address. If you and another user both enable external access and allow each other's domains, this will work. If it doesn't work, the other user should make sure his or her configuration isn't blocking your domain.

External access allows external users to find, call, and send you instant messages, as well as set up meetings with you. However, if you want external users to have access to teams and channels, guest access might be a better way to go. For more information about the differences between external access and guest access, see [External access vs. guest access](#external-access-vs-guest-access)), below. To turn on guest access, see [turn on guest access](set-up-guests.md) so that users can communicate.

> [!IMPORTANT]
> Currently, to federate within the Microsoft Teams app to an external user outside of your organization who's not currently a guest of your Azure Active Directory (Azure AD) or tenant, you must be correctly set up for hybrid and moved to Skype for Business Online. As of 2/25/2019, Teams doesn't support native federation without the user of the SIP profile being homed in Skype for Business Online. For more on setting up your account for hybrid and then moving to Teams, see [Upgrade Skype for Business hybrid deployment to Teams](https://docs.microsoft.com/en-us/microsoftteams/upgrade-to-teams-execute-skypeforbusinesshybrid).

## External access vs. guest access

External access (federation) and guest access are different:

- Guest access gives access permission to an individual. External access gives access permission to an entire domain.

- Guest access, once granted by a team owner, allows a guest to [access resources](guest-experience.md), such as channel discussions and files, for a specific team, and chat with other users in the team they have been invited to. With external access (federated chat), the external chat participants have no access to the inviting organization’s teams or team resources. They can only participate in one-on-one federated chat. Tenant admins can choose between the two communication options depending on which level of collaboration is desirable with the external party. Admins can choose either approaches or both, depending on their organizational needs, but we recommend enabling guest access for a fuller, collaborative Teams experience. 

See the following table for a comparison of external and guest access features.

| Feature | External access users | Guest access users |
|---------|-----------------------|--------------------|
| User can chat with someone in another company | Yes |Yes |
| User can call someone in another company | Yes | Yes |
| User can see if someone from another company is available for call or chat | Yes | Yes<sup>1</sup> |
| User can search for users across external tenants | Yes<sup>2</sup> | No |
| User can share files | No | Yes |
| User can access Teams resources | No | Yes |
| User can be added to a group chat | No | Yes |
| User can be added to a meeting | Yes | Yes |
| Additional users can be added to a chat with an external user | No<sup>3</sup> | N/A |
| User is identified as an external party | Yes | Yes |
| Presence is displayed | Yes | Yes |
| Out of office message is shown | No | Yes |
| Individual user can be blocked | No | Yes |
| @mentions are supported | No | Yes |
| Make private calls | Yes | Yes |
| Allow IP video | Yes | Yes |
| Screen sharing mode | No | Yes |
| Allow meet now | No | Yes |
| Edit sent messages | No | Yes |
| Can delete sent messages | No | Yes |
| Use Giphy in conversation | No | Yes |
| Use memes in conversation | No | Yes |
| Use stickers in conversation | No | Yes |
||||

<sup>1</sup> Provided that the user has been added as a guest and is signed in as a guest to the guest tenant.<br>
<sup>2</sup> Only by email or Session Initiation Protocol (SIP) address.<br>
<sup>3</sup> External (federated) chat is 1:1 only.

For more information on guest features and the guest experience, see [Turn on or off guest access to Microsoft Teams](https://docs.microsoft.com/microsoftteams/set-up-guests) and [What the guest experience is like](https://docs.microsoft.com/microsoftteams/guest-experience).

For more information about the free version of Teams and how it works with features found in External Access, see [Differences between Microsoft Teams and Microsoft Teams free](https://support.office.com/article/differences-between-microsoft-teams-and-microsoft-teams-free-0b69cf39-eb52-49af-b255-60d46fdf8a9c?ui=en-US&rs=en-US&ad=US).

## Quick steps for scenarios

|**You want to....**  |**Quick steps**  |
|---------|-----------------------|
|You want to let **Teams users** in your organization communicate with **Teams users** in another (external) organization.|In External Access, add the external domain to the Allowed list or use open federation. <p>Then have the administrator in the other Teams organization do the same thing.      |
|You want to let **Teams users**  in your organization  communicate with **Skype for Business Online users**  in the same organization.  |Enable Coexistence mode or choose the Islands upgrade mode to support Skype for Business users in your organization.   |
|You want to let **Teams users** in your organization communicate with **Skype for Business Online users** in another (external) organization.      |In External Access, add the external domain to the Allowed list or use open federation.  <p>Turn on **Users can communicate with Skype for Business and Teams users** setting in External Access. <p>Then have the administrator in the other Teams organization do the same thing. <p>**NOTE**: The external domain with Skype for Business users must enable Coexistence mode or choose the Islands upgrade mode to support Skype for Business users in that organization.|
|You want to let **Teams users** in your organization  communicate with **Skype** users from inside or outside your organization.   | Not a supported scenario at this time. <p>**IMPORTANT**: Your Teams users won't be able to communicate with Skype users, but your Skype for Business users in your organization can communicate with Skype users inside or outside your organization if these two requirements are met: <p>1)  Turn on **Users can communicate with Skype for Business and Teams users** and **Skype for Business users can communicate with Skype users** settings in External Access. <p> 2) Your organization is running in Coexistence mode. |
|You want to let your **Teams users** communicate with **Skype for Business Online users** from an on-premises organization and with **Skype users**.   |In External Access, add the external domain to the Allowed list or use open federation. . <p>Turn on **Users can communicate with Skype for Business and Teams users** setting in External Access. <p>Turn on **Skype for Business users can communicate with Skype users** setting in External Access. <p> Then have the administrator in the on-premises organization do the same thing.<p>**IMPORTANT** In this scenario, your Teams users won't be able to communicate with Skype users, but Skype for Business users in your organization can communicate with Skype users inside or outside your organization if you turn on **Users can communicate with Skype for Business and Teams users** and **Skype for Business users can communicate with Skype users** settings in External Access.|
|You want to let your **Skype for Business Online users** communicate with **Teams users** in another Office 365 organization.|Enable Coexistence mode or choose the Islands upgrade mode to support Skype for Business users in your organization. <p>In External Access, add the external domain to the Allowed list or use open federation.  <p> Turn on **Users can communicate with Skype for Business and Teams users**  setting in External Access. <p>Then have the administrator in the other Teams organization do the same things. |
|You want to let your **Skype for Business Online users** communicate with the **Skype for Business Online users** from another Office 365 organization.    | Enable Coexistence mode or choose the Islands upgrade mode to support Skype for Business users in your organization. <p>In External Access, add the external domain to the Allowed list or use open federation. <p> Turn on **Users can communicate with Skype for Business and Teams users**  setting in External Access.<p>Then have the administrator in the other Teams organization do all of the same things. |
|You want to let your **Skype for Business Online users** communicate with the **Skype for Business Online users** from an on-premises organization.     |Enable Coexistence mode or choose the Islands upgrade mode to support Skype for Business users in your organization. <p>In External Access, add the external domain to the Allowed list or use open federation.  <p>Turn on **Users can communicate with Skype for Business and Teams users** setting in External Access.  <p> Then have the administrator in the on-premises organization do the same things. |
|You want to let your **Skype for Business Online users** communicate with **Skype users** (inside or outside your organization).   |Enable Coexistence mode or choose the Islands upgrade mode to support Skype for Business users in your organization. <p>Turn on the **Skype for Business users can communicate with Skype users** setting in External Access.         |
|You want to let your **Skype for Business Online users** communicate with **Skype for Business Online users** in another organization and **Skype users** from inside or outside your organization.    |Enable Coexistence mode or choose the Islands upgrade mode to support Skype for Business users in your organization. <p>In External Access, add the external domain to the Allowed list or use open federation.  <p> Turn on **Users can communicate with Skype for Business and Teams users** and the **Skype for Business users can communicate with Skype users** setting in External Access. <p>Then have the administrator in the other Teams organization do the same things.       <p> **NOTE**: The administrator from the other external domain doesn't have to turn on **Skype for Business users can communicate with Skype users** setting in External Access.|

> [!IMPORTANT]
> You don't have to add any **"Skype domains"** as allowed domains to enable Teams or Skype for Business Online users to communicate with Skype users inside or outside your organization. All **Skype domains** are whitelisted which means all of these domains are considered ALLOWED.

## Let your Teams users chat and communicate with users in another organization

External access lets your Teams and Skype for Business users communicate with other users who are outside of your organization. By default, your organization can communicate with all external domains. If you add blocked domains, all other domains will be allowed but if you add allowed domains, all other domains will be blocked. You can easily set up external access for your organization. There are three scenarios for setting it up:

- **Scenario 1** - You can use **OPEN FEDERATION**. This is the default setting and it lets people in your organization find, call, and send instant messages, as well as set up meetings with people external to your organization.

    When you use this set up, your users can communicate with ALL external domains that are running Teams but have set up their domain/organization to allow your domain.

- **Scenario 2** - You can add a domain or domains to the **ALLOW** list. To do this, click **Add a domain**, add the domain name, click **Action to take on this domain**, and then select **Allowed**. It's important to know that if you do this it will **BLOCK** all other domains.

- **Scenario 3** - You can add a domain or domains to the **BLOCK** list. To do this, click **Add a domain**, add the domain name, click **Action to take on this domain**, and then select **Blocked**. It's important to know that if you do this it will **ALLOW** all other domains.

Follow these steps to allow or block domains.

### Step 1 - Enable your organization to communicate with another Teams organization

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png)  **Using the Microsoft Teams admin center**

1. In the left navigation, go to **Org-wide settings** > **External access**.

2. Toggle the **Users can communicate with Skype for Business and Teams users** switch to **On**.

     ![Screenshot of external access switch turned On](media/manage-external-access-2.png).

3. If you want to allow all Teams organizations to communicate with users in your organization, skip to step 5.

4. If you want to limit the organizations that can communicate with users in your organization, you can either allow all except some domains, or you can allow only specific domains. 

    - To allow all except some domains, add the domains you want to block by clicking **Add domain**. In the **Add a domain** pane, type the domain name, click **Blocked**, and then clik **Done**. 
    - To limit communications to specific organizations, add those domains to the list with a status of **Allowed**. Once you have added any domain to the Allow list, communications with other organizations will be limited to only those organizations whose domains are in the Allow list. 

5. Click **Save**.

6. Make sure the admin in the other Teams organization completes these same steps. For example, in their **allowed domains** list, their admin needs to enter the domain for your business if they limit the organizations that can communicate with their users.

### Step 2 - Test it

To test your setup, you need a Teams user who's not behind your firewall.
  
1. After you and the admin from the organization have changed the **External access** settings, you should be good to go.

2. In the Teams app, search for the person by email address, and send a request to chat.

3. Ask your Teams contact to send you a request to chat. If you don't receive their request, the problem is your firewall settings (assuming they've already confirmed their firewall settings are correct).

4. Another way to test whether the problem is your firewall is to go to a wifi location not behind your firewall. such as a coffee shop, and use Teams to send a request to your contact to chat. If the message goes through at the wifi location, but does not when you're at work, then you know the problem is your firewall.

## Communicate with users in a Skype for Business Online organization

If you are setting up external access to let your Teams users find and contact users who are in a Skype for Business organization that limits who can contact their users, follow the steps to set up external access from your domain to the other organization's domain. Then ask the admin in the other organization to follow the steps below to configure external access for Skype for Business Online.

![An icon showing the Skype for Business logo](media/sfb-logo-30x30.png) **Using the Skype for Business admin center**

Have the admin in that organization do these steps:

1. In the Microsoft 365 admin center, go to **Admin Centers** > **Teams & Skype** > **Legacy portal**.
  
2. In the **Skype for Business admin center**, choose **Organization** > **External communications**.

3. To set up communication with a specific business or with users in another domain, in the drop-down box, choose **On only for allowed domains**.

    OR, if they want to enable communication with everyone else in the world who has open Skype for Business policies, choose **On except for blocked domains**. This is the default setting.

4. Under **Blocked or allowed domains**, choose **+**, and then add the name of the domain you want to allow.

## Related topics

For information about guest access in Microsoft Teams, see [Manage guest access in Microsoft Teams](manage-guests.md).
