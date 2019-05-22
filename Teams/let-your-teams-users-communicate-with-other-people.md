---
title: "Communicate with Teams users in another organization"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.date: 09/12/2018
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
audience: Admin
search.appverid: MET150
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: ms.teamsadmincenter.externalaccess.overview
description: "See how to configure Teams to let users communicate with users in another organization."
---

# Let your Teams users chat and communicate with users in another Teams organization

Use the steps in this article when:
  
- You have users in different domains in your business. For example, Rob@ContosoEast.com and Ann@ContosoWest.com.
    
- You want the people in your organization to use Teams to contact people in specific businesses outside of your organization.
    
- You want anyone else in the world who uses Teams to be able to find and contact you, using your email address. If you and another user both enable External Access and allow each other's domains, this will work. If it doesn't work, the other user should make sure his or her configuration isn't blocking your domain.

This will allow users to find, call, and send you instant messages, as well as set up meetings with you. If you want external users to have access to teams and channels, guest access might be a better way to go. Follow the steps in this article and make sure to [turn on guest access](set-up-guests.md) so that users can communicate.

> [!IMPORTANT]
> In order to currently federate within the Microsoft Teams client to an external user outside of your organization who's not currently a Guest of your AAD/Tenant, you must be correctly setup for hybrid and moved to Skype for Business Online. As of 2/25/2019, Teams doesn't yet support native federation without the user of the SIP profile being homed in Skype for Business Online. For more on setting up your account for Hybrid and then moved to Teams, please see [Upgrade Skype for Business Hybrid Deployment to Teams](https://docs.microsoft.com/en-us/microsoftteams/upgrade-to-teams-execute-skypeforbusinesshybrid).

## Let your Teams users chat and communicate with users in another Teams organization

Follow these steps.

### Step 1 - Make sure to set up the ports and URLs that are needed.

**The most common issue people encounter when setting up business-to-business communication is getting their [Office 365 URLs and IP address ranges](https://docs.microsoft.com/microsoftteams/office-365-urls-ip-address-ranges) right.**

### Step 2 - Enable your organization to communicate with another Teams organization

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

   1. In the left navigation, go to **Org-wide settings** > **External access**. 

   2. At the top of the **External access** page, click **External access** to **On**. 

   3. If you want to allow all Teams organizations to communicate with users in your organization, skip to step 5. 
   
   4. If you want to limit which organizations can communicate with users in your organization you can either allow all but some domains, or only allow specific organizations. To allow all but some domains, add the domains you want to block by clicking **Add domain**. In the **Add a domain** pane, put in the domain name, click **Blocked** and then **Done**. To limit communications to specific organizatioins, add those domains to the list with a status of **Alowed**. Once you have added any domain to the Allow list, communications to other organizations will be limited to only those organizations whose domains are in the Allow list. 
   
   5. Click **Save**. 

   6. Then make sure the admin in the other Teams  organization does these same steps. For example, in their **allowed domains** list, their admin needs to enter the domain for your business if they limit which organizations can communicate with their users. 

### Step 3 - Test it
To test your setup, you need a Teams user who's not behind your firewall.
  
   1. After you and the admin from the organization have changed the **External access** settings, you should be good to go.
    
   2. In the Teams app, search for the person by email address, and send a request to chat.
    
   3. Ask your Teams contact to send you a request to chat. If you don't receive their request, the problem is your firewall settings (assuming they've already confirmed their firewall settings are correct).
    
   4. Another way to test whether the problem is your firewall is to go to a wifi location not behind your firewall such as a coffee shop, and use Teams to send a request to your contact to chat. If the message goes through there, but not when you're at work, then you know the problem is your firewall.

## Communicate with users in a Skype for Business Online organization

If you are setting it up to let your Teams users find and contact users that are in a Skype for Business organization that limits who can contact their users, you will ask the admin in that organization to follow these steps.

![sfb-logo-30x30.png](media/sfb-logo-30x30.png) **Using Skype for Business admin center** 

Have the admin in that organization do these steps:
    
1. In the Office 365 admin center, go to **Admin Centers** > **Teams & Skype** > **Legacy portal**.
  
2. In the **Skype for Business admin center**, choose **Organization** > **External communications**.
    
3. To set up communication with a specific business or with users in another domain, in the drop-down box, choose **On only for allowed domains**.
    
    OR, if they want to enable communication with everyone else in the world who has open Skype for Business policies, choose **On except for blocked domains**. This is the default setting.
    
4. Under **Blocked or allowed domains**, choose **+** and add the name of the domain you want to allow. Make sure the admin in the other organization does these same steps. For example, in their **allowed domains** list, their admin needs to enter the domain for your business.
    
### Related topics

[Sign in to Microsoft Teams](sign-in-teams.md)
[End user training for Teams](enduser-training.md)

