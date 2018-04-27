---
title: "Communicate with Teams users in another organization"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: Strat_MT_TeamsAdmin
ms.audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
description: "See how to configure Teams to let users communicate with users in another organization."
---

# Communicate with Teams users in another organization

## Communicate with Teams users in another organization

Use the steps in this article when:
  
- You have users on different domains in your business. For example, Rob@ContosoEast.com and Ann@ContosoWest.com.
    
- You want the people in your organization to use Skype for Business to contact people in specific businesses outside of your organization.
    
-You want anyone else in the world who uses Skype for Business to be able to find and contact you, using your email address. If you and they use the default Skype for Business settings, this will work automatically. If they don't, then they need to make sure their configuration isn't blocking your domain.

Follow these steps:

### Step 1 - Setup your firewall and open the following ports:
    - TCP port 80
    - TCP port 443
    - Next port

### Step 2 - Enable a Teams organization to communicate with another Teams organization

![teams-logo-30x30.png](media/teams-logo-30x30.png) **Using the Microsoft Teams and Skype for Business Admin Center**

   1. In the left navigation, go to **Org-wide settings** > **External access**. 

   2. At the top of the **External access** page, click **External access** to **On**. 

   3. Click **Save**. 

   4. Make sure the admin in the other organization does these same steps in their **Skype for Business admin center**. For example, in their **allowed domains** list, their admin needs to enter the domain for your business.

### Step 3 - Test it
To test your setup, you need a Teams user who's not behind your firewall.
  
   1. After you and the admin from the organization have changed the External access settings, **WAIT UP TO 24 HOURS TO TEST**.
    
   2. In Teams, search for your contact, and send a request to chat.
    
   3. Ask your Teams contact to send you a request to chat. If you don't receive their request, the problem is your firewall settings (assuming they've already confirmed their firewall settings are correct).
    
   4. Another way to test whether the problem is your firewall is to go to a wifi location not behind your firewall such as a coffee shop, and use Teams to send a request to your contact to chat. If the message goes through there, but not when you're at work, then you know the problem is your firewall.

## Communicate with users in a Skype for Business Online organization

![sfb-logo-30x30.png](media/sfb-logo-30x30.png) **Using Skype for Business admin center** 

Have the admin in that organization do these steps:
    
1. In the Office 365 admin center, go to **Admin Centers** > **Skype for Business**.
  
2. In the **Skype for Business admin center**, choose **Organization** > **External communications**.
    
3. To set up communication with a specific business or with users in another domain, in the drop-down box, choose **On only for allowed domains**.
    
    OR, if you want to enable communication with everyone else in the world who has open Skype for Business policies, choose **On except for blocked domains**. This is the default setting.
    
4. Under **Blocked or allowed domains**, choose **+** and add the name of the domain you want to allow. Make sure the admin in the other organization does these same steps. For example, in their **allowed domains** list, their admin needs to enter the domain for your business.
    
###Related topics

Need links.
