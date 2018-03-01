﻿---
title: Teams Guest Access checklist
author: romanma
ms.author: romanma
manager: serdars
ms.date: 2/15/18
ms.topic: article
ms.service: msteams
ms.reviewer: rramesan
description: Use this checklist to help set up guest access in Microsoft Teams Guest Access.
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---


Teams Guest Access checklist
==========================================

Use this checklist to help you enable and configure the Guest Access feature in Microsoft Teams according to the preferences of your organization.




## □  Enable guest access at the tenant level

At a minimum, you must turn on Microsoft Teams for all users of the license type **Guest**. For detailed instructions, see [Turn on or off guest access to Microsoft Teams](set-up-guests.md).

![Screenshot shows an example of a Teams Settings toggle](media/guest-access-checklist-TeamsSettings1.png)



## □ Enable specific settings for channels 
In the Teams application, at the individual team level, configure guest permissions so that guests can create, update, and delete channels. In addition to admins,  team owners can configure this setting.

![Screenshot shows an example of a Team/Channel Settings toggle](media/guest-access-checklist-TeamsSettings2.png)


For more information, including how-to videos, see [Guest access in Microsoft Teams](guest-access.md).



## □  Configure Sharing in Office 365 

□ Make sure users can add guests. Here's how:
 
1. In the Office 365 admin center, go to **Settings** > **Security & privacy**.![Screenshot shows an example of a Services settings](media/guest-access-checklist-Office365Admin_Services_addins.png)
2. In **Sharing**, select **Edit**.![Screenshot shows an example of a Sharing Settings edit button](media/guest-access-checklist-Office365Admin_Services_addins_Sharing1.png)
3. Set **Let users add new guests to this organization** to **On**, and then click **Save**. ![Screenshot shows an example of a Sharing Settings toggle](media/guest-access-checklist-Office365Admin_Services_addins_Sharing2.png)

 > [!NOTE]
> This setting is equivalent to the **Members can invite** setting in  User settings > External users  in Azure AD.  




## □ Configure Office 365 Groups

In the Office 365 admin center, go to **Settings** > **Services & Add-ins** > **Office 365 Groups**.

Make sure **Let group members outside the organization access group content" is set to **On**. If this setting is turned off, guests won't be able to access any group content.

Make sure **Let group owners add people outside the organization to groups** is set to **On**. If this setting is turned off, Team owners won't be able to add new guests. (However, if an admin had added a guest user to Azure AD, then the Team owner would be able to add that user to the Team.) At a minimum,  this setting must be "on" to support guest access.

For detailed instructions about configuring these settings, see the section "Office 365 Groups" in [Authorize guest access in Microsoft Teams](Teams-dependencies.md).
 


## □ Configure settings in Azure AD business-to-business (B2B)
1. Sign in to https://portal.azure.com.
2. Click **Azure Active directory** in the left pane.
3. Under **Manage**, click **User settings**.
4. In **External users**, make sure **Members can invite** is set to **Yes**.![Screenshot shows an example of a AAD Settings toggle. ](media/guest-access-checklist-AADSettings1.png)

	

► At a minimum to support guests, **Members can invite** must be set to **Yes**.

For more information, see [Authorize guest access in Microsoft Teams](Teams-dependencies.md).







## □ Verify sharing setting in SharePoint
1. Sign in to the Office 365 admin center.
2. Click **Admin center**, and then select **SharePoint**.
3. In the SharePoint admin center, select **Sharing**.
4. Make sure the option for **Don’t allow sharing outside your organization** is *not* selected.![Screenshot shows an example of a Sparepoint Online Settings toggle. ](media/guest-access-checklist-SPOSettings1.png)

## □ Configure AllowAddGuests parameter in PowerShell

Use the Get-UnifiedGroup cmdlet in PowerShell to see the current setting for the AllowAddGuests parameter, which indicates whether guests are allowed (True) or not allowed (False). 



Use the Set-UnifiedGroup cmdlet in PowerShell to change the value of this parameter.

► At a minimum to support guests, this parameter must be set to "True".

Get-UnifiedGroup <name> | fl AllowAddGuests

![Screenshot shows an example of a Unified Groups powershell output. ](media/guest-access-checklist-UnifiedGroup1.png)

For more details about the cmdlet, see [Set-UnifiedGroup](https://technet.microsoft.com/library/mt238274(v=exchg.160).aspx).

## □ Verify account licenses and types

- **Account licensed for Teams**: For a "Guest" account rooted in a real user account in some other Office 365 tenant, that real user account must be licensed for Teams for “Guest”. 
- **Account must be Office 365 school or work account, or MSA account**: Currently, users who have an email address corresponding to an Azure Active Directory, Office 365 work or school account, or a Microsoft account (MSA) can be added as a guest user. 
 
## □ Configure environment


Guests are required to use multi-factor authentication (MFA) if the hosting tenant requires it.
For more details, see [Identity models and authentication in Microsoft Teams](identify-models-authentication.md).

## □ Understand limitations for guests

The guest experience has limitations by design. Make sure you understand the guest experience so you don't try to fix something that isn't a problem.
For example, here's a list of some of the functionality that isn't available to a guest in Microsoft Teams:

- OneDrive for Business
- People search outside of Teams
- Calendar, Scheduled Meetings, or Meeting Details
- PSTN
- Organization chart
- Create or revise a team
- Browse for a team
- Upload files to a person-to-person chat

For more details, see [What the guest experience is like](guest-experience.md) and [Guest access in Office 365 groups](https://support.office.com/article/guest-access-in-office-365-groups-bfc7a840-868f-4fd6-a390-f347bf51aff6).




## Troubleshooting

If you have problems with adding guests in Microsoft Teams, see the [Guest Access Troubleshooting Guide](https://techcommunity.microsoft.com/t5/Microsoft-Teams/Guest-Access-Troubleshooting-Guide/td-p/119797).


