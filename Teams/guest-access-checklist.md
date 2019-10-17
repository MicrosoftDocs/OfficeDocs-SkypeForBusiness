---
title: Microsoft Teams guest access checklist
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 06/21/2019
ms.topic: article
audience: admin
ms.service: msteams
ms.reviewer: sbhatta
description: Use this checklist to help set up guest access in Microsoft Teams.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---


Microsoft Teams guest access checklist
==========================================

Use this checklist to help you turn on and configure guest access in Microsoft Teams.

> [!IMPORTANT]
> You may have to wait up to 24 hours for your changes to take effect. 



## Step 1: Turn on guest access at the Teams org-wide level

At a minimum, you must turn on guest access for Teams in the **Microsoft Teams admin center**. 

1. In the Teams admin center, select **Org-Wide settings** > **Guest access**.
2. Set the **Allow guest access in Microsoft Teams** switch to **On**.

    ![Screenshot shows an example of a Teams settings toggle](media/guest-access-checklist-set-up-guests-image1.png)

3. On this same page, configure any other guest settings that you require.
4. Click **Save**.

> [!TIP]
> If you're using default settings in Azure Active Directory, SharePoint Online, and Office 365 Groups, you may be done configuring guest access. In this case, you can skip the rest of the steps. If you're not sure, or if you're using custom settings for AAD, SharePoint Online, or Office 365 Groups, continue with the rest of the steps in this checklist.





## Step 2: Configure Azure AD business-to-business settings

1. Sign in to the [Azure portal](https://portal.azure.com) as a tenant administrator.
2. Select **Azure Active Directory** > **Users** > **User settings**.
3. Under **External users**, select **Manage external collaboration settings**.
   > [!NOTE]
   > The **External collaboration settings** are also available from the **Organizational relationships** page. In Azure Active Directory, under **Manage**, go to **Organizational relationships** > **Settings**.
4. On the **External collaboration settings** page, choose the policies you want to enable.

  - **Guest users permissions are limited**: This policy determines permissions for guests in your directory. Select **Yes** to block guests from certain directory tasks, like enumerating users, groups, or other directory resources. Select **No** to give guests the same access to directory data as  regular users in your directory.
   - **Admins and users in the guest inviter role can invite**: To allow admins and users in the "Guest Inviter" role to invite guests, set this policy to **Yes**.
   - **Members can invite**: To allow non-admin members of your directory to invite guests, set this policy to **Yes**.
   
       > [!NOTE]
       > If you set **Members can invite** to **No** and then enable guest access in Office 365 Groups and Microsoft Teams, admins can control guest invitations to your directory. After guests are in the directory, they can be added to teams by non-admin members who are team owners. For more information, see [Authorize guest access in Microsoft Teams](Teams-dependencies.md).
   
   - **Guests can invite**: To allow guests to invite other guests, set this policy to **Yes**.
   - **Enable email one-time passcode for guests (Preview)**: For more information about the one-time passcode feature, see [Email one-time passcode authentication (preview)](https://docs.microsoft.com/azure/active-directory/b2b/one-time-passcode).

   - **Collaboration restrictions**: For more information about allowing or blocking invitations to specific domains, see [Allow or block invitations to B2B users from specific organizations](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list).

> [!NOTE]
> - For collaboration restrictions see [Enable B2B external collaboration and manage who can invite guests](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations).
> - Currently, Teams doesn't support the guest inviter role. At a minimum the "members can invite" toggle must be set to "Yes" for guest access to work in Teams. If you set "members can invite" to "No" and then enable guest access in Office 365 Groups and Microsoft Teams, admins can control guest invitations to your directory. After guests are in the directory, they can be added to teams by non-admin members who are team owners.
    
## Step 3: Configure Office 365 Groups

1. In the Microsoft 365 admin center, go to **Settings** > **Services & Add-ins** > **Office 365 Groups**.
2. Make sure **Let group members outside the organization access group content** is set to **On**. If this setting is turned off, guests won't be able to access any group content.
3. Make sure **Let group owners add people outside the organization to groups** is set to **On**. If this setting is turned off, Team owners won't be able to add new guests. At a minimum, this setting must be On to support guest access.

     ![Screenshot shows the Office 365 Groups toggles](media/guest-access-checklist-office365.png)

For detailed instructions about configuring these settings, see [Manage guest access in Office 365 Groups](https://support.office.com/article/manage-guest-access-in-office-365-groups-9de497a9-2f5c-43d6-ae18-767f2e6fe6e0?appver=MOE150) and [Control guest access in Office 365 Groups](Teams-dependencies.md#control-guest-access-in-office-365-groups).
 

## Step 4: Configure sharing in Office 365 

Make sure that users can add guests. Here's how:

1. In the Microsoft 365 admin center, go to **Settings** > **Security & privacy**.

     ![Screenshot shows an example of services settings](media/guest-access-checklist-Office365Admin_Services_addins.png)

2. In **Sharing**, select **Edit**.

     ![Screenshot shows an example of a sharing settings toggle](media/guest-access-checklist-Office365Admin_Services_addins_Sharing1.png)
 
3. Set **Let users add new guests to this organization** to **On**, and then click **Save**.

     ![Screenshot shows an example of a sharing settings toggle](media/guest-access-checklist-Office365Admin_Services_addins_Sharing2.png)
 
> [!NOTE]
> This setting is equivalent to the **Members can invite** setting in **User settings** > **External users** in Azure AD.  


## Step 5: Verify sharing setting in SharePoint

This one's a bit of a brain teaser. Guest access in Teams doesn't work if the **Don't allow sharing outside your organization** setting is selected in the SharePoint admin center.

1. Sign in to the Microsoft 365 admin center.
2. Click **Admin center**, and then select **SharePoint**.
3. In the SharePoint admin center, select **Sharing**.
4. Make sure the option for **Don’t allow sharing outside your organization** is *not* selected.
 
     ![Screenshot shows an example of a SparePoint Online settings toggle.](media/guest-access-checklist-SPOSettings1.png)


## Step 6: Configure channel permissions for guests

In the Teams application, at the individual team level, configure guest permissions so that guests can create, update, and delete channels. Teams admins and team owners can configure these settings.

![Screenshot shows an example of a team/channel settings toggle](media/guest-access-checklist-TeamsSettings2.png)

To learn more about guest access, see [Guest access in Teams](guest-access.md) and [Turn on or turn off guest access to Microsoft Teams](set-up-guests.md).


## Troubleshooting

If you have problems setting up guest access or adding guests in Teams, use these resources to help you:

[Troubleshoot problems with guest access in Microsoft Teams](guest-access-troubleshooting.md)

[Teams troubleshooting](https://docs.microsoft.com/MicrosoftTeams/troubleshoot/)



