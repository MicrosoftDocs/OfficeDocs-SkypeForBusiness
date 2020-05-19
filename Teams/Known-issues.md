---
title: Support Microsoft Teams in your organization
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: troubleshooting
ms.service: msteams
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
ms.custom:
  - seo-marvel-apr2020
ms.reviewer: marcl, billkau
audience: admin
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
description: Use these resources to support Microsoft Teams in your organization, whether you're the Teams admin or the Helpdesk support engineer.
ms.custom: seo-marvel-mar2020
appliesto: 
  - Microsoft Teams
---

# Support Microsoft Teams in your organization

If you're looking for Teams Known Issues, you're in the right place. Use the resources in this article to help you support Teams in your organization. 

Start by reviewing the most [common issues and resolutions](#common-issues-and-resolutions) list, below in this article.

Then, if you don't find what you need, go to [Teams Troubleshooting](https://docs.microsoft.com/MicrosoftTeams/troubleshoot/teams) and search for your problem in the table of contents, or in the **Filter by title** box. 
:::image type="content" source="media/known-issues1.png" alt-text="Screenshot of the table of contents and filter box on the Teams Troubleshooting page":::

If you're still stuck, contact [Microsoft Support](https://docs.microsoft.com/office365/admin/contact-support-for-business-products?toc=/microsoftteams/toc.json&bc=/microsoftteams/breadcrumb/toc.json).


## Common issues and resolutions

> [!NOTE]
> If you need help deploying Teams to support Remote Workers (WFH) due to COVID-19, please review [Support remote workers using Teams](support-remote-work-with-teams.md). Also, you may be eligible for deployment assistance from the Microsoft 365 FastTrack Program - please visit the [FastTrack Center](https://www.microsoft.com/fasttrack) to submit a request.

### For all Teams customers

| |  |
|---------|---------|
|**New to Teams?**    |Check out [Get Started with Microsoft Teams](get-started-with-teams-quick-start.md).         |
|**Enable Teams guest access**     |Review the [Teams guest access checklist](guest-access-checklist.md) and make sure all steps are completed. See the following additional resources:<ul><li>[Understanding Guest Access in Microsoft Teams](guest-access.md)</li>[How a guest joins a Team](guest-joins.md) <li>[Setup – Microsoft Teams Guest Access Checklist](guest-access-checklist.md)</li></ul>|
|**Teams meetings and dial-in**    |Need help turning on or setting up Audio Conferencing in Teams? Has this user been recently created? If so, you'll need to wait 2 – 24 hrs **for the settings to take effect**.<br>To verify that the user is licensed for Audio Conferencing and has a default toll number:<br><ol><li>In the Microsoft 365 admin center, go to **Active users**, and then select the user in question.</li><li> Depending on the admin center version, choose either **Licenses and Apps** or click **Edit** on **Product licenses**.</li><li> Confirm that the user has licenses selected for Audio Conferencing, Microsoft Teams, and Skype for Business Online (Plan 2).</li><li>Under **Admin centers**, click **Show all**, and then click **Teams**.</li><li>In the Microsoft Teams admin center, click **Legacy portal**.</li><li>In the Skype for Business admin center, click **audio conferencing**, and then click **users**.</li><li>Select the user in question and verify the user has a default toll number.</li> </ol> For more information, see [Calling Plans for Office 365](calling-plans-for-office-365.md) or call the Microsoft Commerce Billing team for help with a licensing related questions. <br><br>Additional resources:<ul><li>[Meetings and conferencing in Microsoft Teams](deploy-meetings-microsoft-teams-landing-page.md)</li><li>[Audio Conferencing in Office 365](audio-conferencing-in-office-365.md)</li></ul>       |
|**Teams Exploratory License**     |The Microsoft Teams Exploratory experience lets users in your organization who have Azure Active Directory (AAD) and are not licensed for Teams initiate an exploratory experience of Teams. Admins can switch this feature on or off for users in their organization. The earlier [Microsoft Commercial Cloud Trial](iw-trial-teams.md) is now replaced by The Teams Exploratory experience. <br><br>Additional resources:<ul><li>[How users sign up for the Teams Exploratory experience](teams-exploratory.md#how-users-sign-up-for-the-teams-exploratory-experience)</li><li>[Manage the Teams Exploratory experience](teams-exploratory.md#manage-the-teams-exploratory-experience)</li></ul>|
|**Private channels**    |Private channels in Microsoft Teams create focused spaces for collaboration within your teams. Only the users on the team who are owners or members of the private channel can access the channel. Anyone, including guests, can be added as a member of a private channel as long as they are already members of the team.<br><br>You might want to use a private channel if you want to limit collaboration to those who have a need to know or if you want to facilitate communication between a group of people assigned to a specific project, without having to create an additional team to manage.<br><br>Additional resources:<ul><li>[How users sign up for the Teams Exploratory experience](teams-exploratory.md#how-users-sign-up-for-the-teams-exploratory-experience)</li><li>[Manage the Teams Exploratory experience](teams-exploratory.md#manage-the-teams-exploratory-experience)</li><ul>        |
|**Meeting policies**|[Meeting policies](meeting-policies-in-teams.md) are used to control the features that are available to meeting participants for meetings that are scheduled by users in your organization. After you create a policy and make your changes, you can then assign users to the policy.         |
||**Change or create a meeting policy**<br><br>To change or create a meeting policy, go to the Microsoft Teams admin center > **Meetings** > **Meeting policies**. Select a policy from the list or select **Add**. If you're creating a new policy, add a name and description. The name can't contain special characters or be longer than 64 characters. Choose your settings, and then click **Save**. For example, say you have a bunch of users and you want to limit the amount of bandwidth that their meeting would require. You would create a new custom policy named "Limited bandwidth" and disable the following settings:<br><br>Under **Audio & video**:<ul><li>Turn off Allow cloud recording.</li><li>Turn off Allow IP video.</li></ul>Under **Content sharing**:<ul><li>Disable screen sharing mode.</li><li>Turn off Allow whiteboard.</li><li>Turn off Allow shared notes.</li></ul>Then assign the policy to the users.         |
| |**Assign a meeting policy to users**<br><br><ol><li>In the left navigation of the Microsoft Teams admin center, go to **Users**, and then click the user.</li><li>Select the user by clicking to the left of the user name, and then click **Edit settings**.</li><li>Under **Meeting policy**, select the policy you want to assign, and then click **Apply**.</li></ol>To assign a policy to multiple users at a time, see [Edit Teams user settings in bulk](edit-user-settings-in-bulk.md). Or you can do the following:<ol><li>In the left navigation of the Microsoft Teams admin center, go to **Meetings > Meeting policies**.</li><li>Select the policy by clicking to the left of the policy name.</li><li>Select **Manage users**.</li><li>In the **Manage users** pane, search for the user by display name or by user name, select the name, and then click **Add**. Repeat this step for each user that you want to add.</li><li>After you finish adding users, click **Save**.</li>         |
|**Troubleshoot a missing dial pad**     |Do the following: <ul><li>Make sure the user has been assigned a [Teams license](teams-add-on-licensing/assign-teams-add-on-licenses.md).</li><li>Make sure the user has a [Calling Plan](calling-plan-landing-page.md) assigned.</li><li>Enable the user for [Enterprise Voice](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/enable-users-for-enterprise-voice-online-and-phone-system-voicemail#to-enable-your-users-for-phone-system-in-office-365-voice-and-voicemail).</li></ul>      |
|**Troubleshoot Teams sign-in**   |First, make sure the [Microsoft Teams service is healthy](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/servicehealth). Then check for any common error codes and review [Why am I having trouble signing in to Microsoft Teams?](https://support.office.com/article/a02f683b-61a3-4008-9447-ee60c5593b0f)  You may also need to review [Identity models and authentication in Microsoft Teams](identify-models-authentication.md).         |

### For Education customers

|||
|---------|---------|
|Your users are seeing a "You're missing out!" message.   |Be sure to [Enable Microsoft Teams for your school](https://docs.microsoft.com/microsoft-365/education/intune-edu-trial/enable-microsoft-teams). In EDU tenants, Teams isn't enabled by default; you'll have to turn it on first. <br><br>Next, review [Remote teaching and learning in Office 365 Education](https://support.office.com/article/remote-teaching-and-learning-in-office-365-education-f651ccae-7b65-478b-8366-51bb884025c4) to learn the most up-to-date guidance on setting up your school, lesson planning, meeting virtually, and sharing content with students.<br><br>Finally, be sure to check out Microsoft Teams IT admin training videos, decks, and a lot more at [Admin training for Teams](itadmin-readiness.md).        |


## Related topics

[Teams Troubleshooting](https://docs.microsoft.com/MicrosoftTeams/troubleshoot/teams)

[Support resources for Teams](https://docs.microsoft.com/office365/admin/contact-support-for-business-products?toc=/microsoftteams/toc.json&bc=/microsoftteams/breadcrumb/toc.json)
