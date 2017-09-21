---
title: Manage guest access in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: article
ms.service: msteams
description: Guest access in Microsoft Teams allows teams in your organization to collaborate with people outside your organization by granting them access to teams and channels.
Set_Free_Tag: Strat_MT_TeamsAdmin
---

Manage guest access in Microsoft Teams
======================================
---
title: Guest access in Microsoft Teams
ms.prod: OFFICE365
ms.assetid: bd4cdeec-4044-4b4b-9df1-beb139013a3f
---


# Guest access in Microsoft Teams

Guest access in Microsoft Teams allows teams in your organization to collaborate with people outside your organization by granting them access to teams and channels. A guest is someone who isn't an employee, student, or member of your organization. They don't have a school or work account with your organization. For example, guests may include partners, vendors, suppliers, or consultants.
  
    
    

Organizations using Microsoft Teams can provide external access to teams, documents in channels, resources, chats, and applications to their partners, while maintaining complete control over their own corporate data.
Microsoft Teams is built upon Office 365 Groups and provides a new way to access shared assets for an Office 365 group. Microsoft Teams is the best solution for persistent chat among group/team members. Office 365 Groups is a service that provides cross-application membership for a set of shared team assets, like a SharePoint site or a Power BI dashboard, so that the team can collaborate effectively and securely.
  
    
    


## 


  
    
    
Use
  
    
    

### How a guest joins a team


  
    
    
A team owner in Microsoft Teams can add and manage guests in their teams via the web or desktop. Only users who have an email address corresponding to an Azure Active Directory or Office 365 work or school account can be added as a guest user.
  
    
    

> [!NOTE]
> Before guests can join a team, an admin must enable guest access in Microsoft Teams. To do that,  [sign in](https://portal.office.com/adminportal/home) with your Office 365 global admin account. Then, choose **Settings** > **Services &amp; add-ins** > **Microsoft Teams**. Select **Guest** in **Select the user/license type you want to configure**, and select **On** in **Turn Microsoft Teams on or off for all users of this type**. It can take up to an hour for the settings to take effect. For more details, see "Turn on or off guest access for Microsoft Teams" on this article's Manage tab. 
  
    
    

Here's how a guest becomes a member of a team:
  
    
    

- **Step 1** A team owner or an Office 365 admin [Adding guests to teams](teams-and-channels.md#BKMK_addingguests).
    
  
- **Step 2** The Office 365 admin or the team owner can manage a guest's capabilities as necessary. For example, allowing a guest to add or delete channels or disabling access to files.
    
  
- **Step 3** The guest receives a welcome email from the team owner, inviting them to join the team. After accepting the invitation, the guest can [Working in channels](teams-and-channels.md#BKMK_channels), receive and respond to channel messages,  [Files](files.md), and participate in chat. While using Microsoft Teams, a combination of text and icons gives all team members clear indication of guest participation in a team. For more details, see  [What the guest experience is like](guest-access-in-microsoft-teams.md#BKMK_GuestExperience)
    
  
Guests can leave the team at any time via Microsoft Teams web and desktop clients. For details, see  [How do I leave a team?](teams-and-channels.md#BKMK_HowDoILeaveATeam)
  
    
    

> [!NOTE]
> Only people who are outside of your organization, such as partners or consultants, can be added as guests. People from within your organization can join as regular team members. 
  
    
    


### What the guest experience is like
<a name="BKMK_GuestExperience"> </a>

When a guest is invited to join a team, they receive a welcome email message that includes some information about the team and what to expect now that they're a member. The guest must redeem the invitation in the email message before they can access the team and its channels.
  
    
    

  
    
    
![Screenshot shows an example of a welcome email message sent by a team owner in Microsoft Teams to a guest user. The message includes text that can be customized by the team owner and brief descriptions of Teams features like chat, calls, and meetings.](images/bc0deb82-6394-4280-8fed-312645c8fefe.png)
  
    
    
All team members see a message in the channel thread announcing that the team owner has added a guest and providing the guest's name. Everyone on the team can identify easily who is a guest. As shown in the following screenshot of a sample team, a banner indicates "This team has guests" and a "GUEST" label appears next to each guest's name.
  
    
    

  
    
    
![Screenshot shows a portion of the Marketing channel for Northwind Traders, with the notification in the top banner stating "This team has guests" and users who are guests identified with the word "GUEST" next to their name.](images/33394a31-7d10-4950-8b39-b7d9953397c3.png)
  
    
    
The following table compares the Microsoft Teams functionality available for an organization's team members to the functionality available for a guest user on the team.
  
    
    


|**Capability in Teams**|**Teams user in the organization**|**Guest user**|
|:-----|:-----|:-----|
||||
|Create a channel  <br/>  *Team owners control this setting.*  <br/> |![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)|![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)|
|Participate in a private chat  <br/> |![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)|![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)|
|Participate in a channel conversation  <br/> |![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)|![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)|
|Post, delete, and edit messages  <br/> |![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)|![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)|
|Share a channel file  <br/> |![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)|![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)|
|Share a chat file  <br/> |![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)||
|Add apps (tabs, bots, or connectors)  <br/> |![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)||
|Create tenant-wide and teams/channels guest access policies  <br/> |![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)||
|Invite a user outside the Office 365 tenant's domain  <br/> ||![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)|
|Create a team  <br/> |![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)||
|Discover and join a public team  <br/> |![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)||
|View organization chart  <br/> |![checkmark](images/5277fbec-0a8f-4bd0-b906-d6ddee85a46c.png)||
   

    
> [!NOTE]
> Office 365 admins control the features available to guests. 
  
    
    

Manage
### 
<a name="BKMK_GuestExperience"> </a>

Guest access is included with all Office 365 Business Premium, Office 365 Enterprise, and Office 365 Education subscriptions. No additional Office 365 license is necessary.
  
    
    
Microsoft Teams guest access is a tenant-level setting and is turned off by default. Admins can manage guest access via the Office 365 admin center. For more details, see  [Manage guest access to Microsoft Teams](guest-access-in-microsoft-teams.md#bkmk_ManageGuestAccess) and [Control guest access to Microsoft Teams](guest-access-in-microsoft-teams.md#bkmk_ControlGuestAccess).
  
    
    

> [!NOTE]
> The Microsoft Teams guest access tenant setting only prevents guest sign-in. Team owners will be able to invite new guests and add existing directory guest users to their respective teams. As a reminder, Microsoft Teams always honor Azure Active Directory external settings to allow or prevent guest user addition to the tenant. 
  
    
    

In addition, you can use the Azure Active Directory portal to manage guests and their access to Office 365 and Microsoft Teams resources. Microsoft Teams guest access makes use of Azure Active Directory business-to-business (B2B) collaboration capabilities as the underlying infrastructure to store security principles information such as identity properties, memberships, and multi-factor authentication settings. To learn more about Azure Active Directory B2B, see  [What is Azure AD B2B collaboration?](https://go.microsoft.com/fwlink/p/?linkid=853011) and [Azure Active Directory B2B collaboration FAQs](https://go.microsoft.com/fwlink/p/?linkid=853020).
  
    
    

#### Related key services and dependencies

Microsoft Teams relies on SharePoint Online and OneDrive for Business to store files and documents for channels and chat conversations. In addition, Microsoft Teams relies on Office 365 groups to store teams' memberships and other properties such as team data classification settings.
  
    
    
To enable the full Microsoft Teams guest access experience, Office 365 admins need to select **On** for the following settings:
  
    
    

- In SharePoint Online: **Only allow sharing with external users already in the directory**
    
    For more information, see  [Manage external sharing for your SharePoint Online environment](http://technet.microsoft.com/library/c8a462eb-0723-4b0b-8d0a-70feafe4be85%28Office.14%29.aspx).
    
  
- In Office 365 groups: **Let group owners add people outside the organization to groups**
    
    For more information, see  [Control guest access to Microsoft Teams](guest-access-in-microsoft-teams.md#bkmk_ControlGuestAccess).
    
  

### Turn on or off guest access for Microsoft Teams
<a name="bkmk_TurnonOrTurnOff"> </a>


1. Sign in with your Office 365 global admin account at  [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home).
    
  
2. In the navigation menu, choose **Settings** and then select **Services &amp; add-ins**.
    
     ![Sign in to Office 365, go to the Office 365 admin center, go to Settings, and then choose Services &amp; add-ins.](images/99e676d4-5b48-4525-9556-547031fa37d9.png)
  

  

  
3. Select **Microsoft Teams**.
    
     ![Screenshot shows the option for the Microsoft Teams add-in, as selected in the Office 365 admin center.](images/17ac5608-d212-4fa8-ae3a-e78c62003968.png)
  

  

  
4. In **Select the user/license type you want to configure**, select **Guest**.
    
    
  
    
    
![Screenshot of the Microsoft Teams add-in shows the Guest license selected and the Microsoft Teams option set to On.](images/92aabda5-431c-4fdd-803e-5ab49290f4f7.png)
  
    
    

  
    
    

  
    
    

    
  
5. Click or tap the toggle next to **Turn Microsoft Teams on or off for all users of this type** to **On** to turn on Teams and guest access for your organization, and then choose **Save**. 
    
  

> [!NOTE]
> It can take up to an hour for the settings to take effect. 
  
    
    


### Control adding guest users to Microsoft Teams and Office 365 groups
<a name="bkmk_ControlAddingGuestUsers"> </a>


1. Sign in with your Office 365 global admin account at  [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home).
    
  
2. In the navigation menu, choose **Settings** and then select **Services &amp; add-ins**.
    
  
3. Select **Office 365 Groups**.
    
     ![Office 365 groups](images/e25a7920-254c-4da3-bc5f-a8c7f6b61423.png)
  

  

  
4. On the Office 365 Groups page, set the toggle to **On** or **Off**, depending if you want to let team and group owners outside your organization access Office 365 groups. Click or tap the toggle to **On** next to **Let group owners add people outside the organization to groups**.
    
    
  
    
    
![Screenshot shows the Office 365 Groups panel with the options turned on to let group members outside the organization access group content and to let group owners add people outside the organization to groups.](images/eee77abd-4425-4585-91a8-5541c17ee7b2.png)
  
    
    

  
    
    

  
    
    

    
  

### Turn on or off the Sharing option for Office 365
<a name="bkmk_TurnOnOffSharingOption"> </a>

The Sharing option allows guests to be added to your organization. By default, the Sharing option is enabled. For information about how to turn off the Sharing option, see  [Control guest access to Office 365 Groups](http://technet.microsoft.com/library/7c713d74-a144-4eab-92e7-d50df526ff96%28Office.14%29.aspx#BKMK_Beforeyoubegin).
  
    
    

> [!IMPORTANT]
> If you turn off the Sharing option, guest access isn't available. 
  
    
    


### Use PowerShell to control guest access
<a name="bkmk_UsePowerShell"> </a>

In addition to using the Office 365 admin center and the Azure Active Directory portal, you can use Windows PowerShell to control guest access. With PowerShell, you can do the following:
  
    
    

- Allow or block guest access to all teams and Office 365 groups
    
  
- Allow guests to be added to all teams and Office 365 groups
    
  
- Allow or block guest users from a specific team or Office 365 group
    
  
For more details, see  [Guest access in Office 365 Groups](http://technet.microsoft.com/library/bfc7a840-868f-4fd6-a390-f347bf51aff6%28Office.14%29.aspx#bkmk_UsePowerShell).
  
    
    
You can also use PowerShell to allow or block a guest user based on their domain. For example, let's say your business (Contoso) has a partnership with another business (Fabrikam). You can add Fabrikam to your Allow list so your users can add those guests to their groups. For more information, see  [Allow/Block guest access to Office 365 groups](https://go.microsoft.com/fwlink/?linkid=854001).
  
    
    

### View guest users
<a name="bkmk_UsePowerShell"> </a>


1. Sign in with your Office 365 global admin account at  [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home).
    
  
2. Go to **Users** > **Guest users**.
    
    
  
    
    
![Screenshot shows the guest users option selected from the Users section of the Office 365 admin center.](images/95b83ff5-72ef-4668-b541-4e25b767620a.png)
  
    
    

  
    
    

  
    
    

    
  

### Invite guest users
<a name="bkmk_UsePowerShell"> </a>

A team owner or an Office 365 admin can  [How do I add a team member?](teams-and-channels.md#BKMK_HowDoIAddATeamMember) on an individual basis. However, admins can't use the Office 365 admin center or the Azure Active Directory portal to invite multiple guests in one action. To invite guests centrally, consider using the Azure Active Directory B2B collaboration preview. For more information, see [About the Azure AD B2B collaboration preview](https://go.microsoft.com/fwlink/p/?linkid=853011).
  
    
    

### Edit guest user information
<a name="bkmk_UsePowerShell"> </a>

Currently, you can't edit guest information from the Office 365 admin center or the Exchange admin center. To edit guest accounts (such as display name or profile photo), go to your Azure Active Directory portal. For more information, see  [Understanding Office 365 identity and Azure Active Directory](http://technet.microsoft.com/library/06a189e7-5ec6-4af2-94bf-a22ea225a7a9%28Office.14%29.aspx).
  
    
    
FAQ
### Frequently asked questions for admins
<a name="bkmk_UsePowerShell"> </a>

Here are common questions Office 365 admins have about inviting guests to join a team in Microsoft Teams.
  
    
    

#### What is a guest?


  
    
    
A guest is not an employee, student, or member of your organization. They don't have a school or work account with your organization.
  
    
    

  
    
    

#### Who can be added as a guest user?

Only users who have an email address corresponding to an Azure Active Directory or Office 365 work or school account can be added as a guest user.
  
    
    

#### Can users add people within my organization who are not part of the team as a guest?

Only people who are outside of your organization, such as partners or consultants, can be added as guests. Users can invite people from within your organization to join as regular team members or subscribers.
  
    
    

#### Why does a user get the message "Contact your administrator" when they try to add a guest to their team?

As the Office 365 admin, you must enable the guest feature before you or your organization's users (specifically, team owners) can add guests. When a user sees that message, it's likely that the guest feature hasn't been enabled.
  
    
    

#### How can a global admin add a new guest user to the organization?

As a global admin, you can add a new guest user to the organization in a couple ways:
  
    
    

- Global admins who are owners of a team and owners of a team can  [How do I add a team member?](teams-and-channels.md#BKMK_HowDoIAddATeamMember) through either the Microsoft Teams desktop or the web clients.
    
  
- Add guests to your organization through Azure Active Directory B2B collaboration. Azure Active Directory B2B collaboration allows a global admin to invite and authorize a set of external users by uploading a comma-separated values (CSV) file of no more than 2,000 lines to the B2B collaboration portal. For more details, check out  [Azure Active Directory B2B collaboration](https://go.microsoft.com/fwlink/p/?LinkId=826383).
    
  

#### Is there a way to block individual guest users?

No, individual guest users can't be blocked.
  
    
    

#### Can global admins block guests in teams and still allow guests to access SharePoint sites?

Yes, global admins can use Azure Active Directory Powershell cmdlets to disable the  _AllowGuestAccessToGroups_ parameter on the Company object, assuming external sharing is turned on for SharePoint sites.
  
    
    

#### What other controls are available to IT admins to manage guests in Microsoft Teams?

IT admins can add guests at the tenant level, set and manage guest user policies and permissions, determine which users can invite guests, and pull reports on guest user activity. These controls are available through the Office 365 admin center. Guest user content and activities are under the same compliance and auditing protection as the rest of Office 365.
  
    
    

#### Can users share a team file with an external user who isn't a member of the team?

No. Users can only share Microsoft Teams files with guests who have been invited to join the team.
  
    
    

#### Is an additional Office 365 license required for guest access?

No additional license is required. Guest access is included with all Office 365 Business Premium, Office 365 Enterprise, and Office 365 Education subscriptions.
  
    
    

#### Do Office 365 and Azure Active Directory service limits apply to guests?

Yes, guests are subject to  [Office 365](https://go.microsoft.com/fwlink/p/?linkid=282347) and [Azure Active Directory](https://go.microsoft.com/fwlink/p/?linkid=853019) service limits.
  
    
    

  
    
    

#### How long does it take until the guest user settings take effect in the Office 365 organization?

The guest settings are set in Azure Active Directory. It takes 2 hours to 24 hours for the changes to be effective across your Office 365 organization.
  
    
    

#### Can a global admin manage SharePoint Online external user settings for the Teams connected team site?

Yes, you can manage SharePoint Online external user settings for the Teams connected team site. For more details, see  [Manage your SharePoint team site settings](http://technet.microsoft.com/library/8376034d-d0c7-446e-9178-6ab51c58df42%28Office.14%29.aspx).﻿
  
    
    

  
    
    

#### How does conditional access work with guest access?

With Azure Active Directory B2B collaboration, organizations can enforce conditional access and multi-factor authentication (MFA) policies for B2B users. These policies can be enforced at the tenant, app, or individual user level, the same way that they are enabled for full-time employees and members of the organization. Such policies are enforced at the resource organization. For more information, see  [Conditional access for B2B collaboration users](https://go.microsoft.com/fwlink/?linkid=857454).
  
    
    

#### If I have a team with an Office 365 group, and I add a guest to the group, does that user automatically get access to the team?

Yes, the guest will get access to the team. Adding a guest via the Office 365 group doesn't generate an invitation email to the guest, so someone on the team should notify the guest.
  
    
    

#### What event appears in the audit log to indicate a guest has been sent an invitation?

You can track guest additions in Azure Active Directory or the Office 365 Security &amp; Compliance Center. Adding a guest in Microsoft Teams is audited and logged as an Azure AD group administration activity "Added member to group". For more details, see  [Auditing and reporting a B2B collaboration user](https://go.microsoft.com/fwlink/p/?linkid=858884) and [Search the audit log in the Office 365 Security &amp; Compliance Center](http://technet.microsoft.com/library/0d4d0f35-390b-4518-800e-0c7ec95e946c%28Office.14%29.aspx).
  
    
    

#### If I have existing guest users that were added via Azure AD B2B, Office 365 Groups, or SharePoint Online, do I have to do anything else with them for Microsoft Teams?

Guest users you have already added via Azure Active Directory B2B, Office 365 Groups or SharePoint Online are ready to go. The Office 365 admin or a team owner can add those guests to their respective teams.
  
    
    

#### If external accounts are available, does that mean external sharing is enabled?

Admins can create guest accounts in Azure Active Directory, independent from external sharing settings. If external sharing is off, only an admin can create guest accounts.
  
    
    

  
    
    

## More information

 [Administrator settings for Microsoft Teams](administrator-settings-for-microsoft-teams.md)
  
    
    
 [Frequently asked questions about Microsoft Teams - Admin Help](frequently-asked-questions-about-microsoft-teams-–-admin-help.md)
  
    
    
 [Adding guests to teams](teams-and-channels.md#BKMK_addingguests)
  
    
    
Video:  [Deep Dive into Guest Access](https://go.microsoft.com/fwlink/p/?linkid=858791)
  
    
    

