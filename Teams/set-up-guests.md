---
title: Set up guest access to Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: lolaj
ms.date: 10/20/17
ms.topic: article
ms.service: msteams
description: Enable the guest access feature in Microsoft Teams.
Set_Free_Tag: Strat_MT_TeamsAdmin
---


Set up guest access to Microsoft Teams
======================================

Microsoft Teams is built upon Office 365 Groups, and it also relies on SharePoint Online. That’s why specific settings must be enabled in Office 365 Groups and SharePoint Online in addition to turning on the guest access feature in Teams.


## Allow the addition of guests in Office 365 Groups
<a name="bkmk_ControlAddingGuestUsers"> </a>


1. Sign in with your Office 365 global admin account at [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home).
    
  
2. In the navigation menu, choose **Settings** and then select **Services &amp; add-ins**.
    
  
3. Select **Office 365 Groups**.
    
     ![Office 365 groups](media/e25a7920-254c-4da3-bc5f-a8c7f6b61423.png)
  

  

  
4. On the Office 365 Groups page, set the toggle to **On** or **Off**, depending if you want to let team and group owners outside your organization access Office 365 groups. Click or tap the toggle to **On** next to **Let group owners add people outside the organization to groups**.


![Screenshot shows the Office 365 Groups panel with the options turned on to let group members outside the organization access group content and to let group owners add people outside the organization to groups.](media/eee77abd-4425-4585-91a8-5541c17ee7b2.png)
    

## Enable sharing in SharePoint Online

The Sharing option in SharePoint Online allows guests to be added to your organization. By default, the Sharing option is enabled. For information about how to turn off the Sharing option, see [Turn on or off the Sharing option](https://support.office.com/en-us/article/Turn-on-or-off-the-Sharing-option-7c713d74-a144-4eab-92e7-d50df526ff96#bkmk_beforeyoubegin).
  
   Admins can create guest accounts in Azure Active Directory, independent from external sharing settings. If external sharing is off, only an admin can create guest accounts. 
    

> [!IMPORTANT]
> If you turn off the Sharing option, guest access isn't available. 
  

## Turn on or off guest access to Microsoft Teams
<a name="bkmk_TurnonOrTurnOff"> </a>

As the Office 365 admin, you must enable the guest feature before you or your organization's users (specifically, team owners) can add guests. 

The guest settings are set in Azure Active Directory. It takes 2 hours to 24 hours for the changes to be effective across your Office 365 organization. If a user sees the message "Contact your administrator" when they try to add a guest to their team, it's likely that either the guest feature hasn't been enabled or the settings haven’t become effective yet.



1. Sign in with your Office 365 global admin account at [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home).
    
  
2. In the navigation menu, choose **Settings** and then select **Services &amp; add-ins**.
    
     ![Sign in to Office 365, go to the Office 365 admin center, go to Settings, and then choose Services &amp; add-ins.](media/99e676d4-5b48-4525-9556-547031fa37d9.png)
  
 

  
3. Select **Microsoft Teams**.
    
     ![Screenshot shows the option for the Microsoft Teams add-in, as selected in the Office 365 admin center.](media/17ac5608-d212-4fa8-ae3a-e78c62003968.png)
  
  
4. In **Select the user/license type you want to configure**, select **Guest**.
   
    ![Screenshot of the Microsoft Teams add-in shows the Guest license selected and the Microsoft Teams option set to On.](media/92aabda5-431c-4fdd-803e-5ab49290f4f7.png)
      

  
  
5. Click or tap the toggle next to **Turn Microsoft Teams on or off for all users of this type** to **On** to turn on Teams and guest access for your organization, and then choose **Save**. 
    
  

