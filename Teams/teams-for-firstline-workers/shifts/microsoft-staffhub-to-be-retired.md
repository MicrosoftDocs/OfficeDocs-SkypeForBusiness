---
title: Microsoft StaffHub to be retired 
ms.author: v-lanac
ms.reviewer: lisawu
manager: serdars
ms.date: 2/26/2019
ms.topic: article
ms.service: msteams
search.appverid: MET150
description: 
localization_priority: Normal
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Office for business, Microsoft Teams
---

# Microsoft StaffHub to be retired

Effective October 1, 2019, Microsoft StaffHub will be retired. We're building StaffHub capabilities, including schedule and task management, into Microsoft Teams. The Teams mobile app now includes shift management and a home screen experience. Additional capabilities for firstline workers will roll out to Teams over time. 

These changes are part of our continued efforts to empower every employee with Microsoft 365. With capabilities for firstline workers now in Teams, every employee in your organization will be able to use Teams to streamline their workday, collaborate with coworkers, and access information and expertise to help them do their best work.

## Frequently asked questions

- **When will Microsoft StaffHub be retired?**<br> 
Starting April 1, 2019, Microsoft StaffHub will no longer be available for new tenants and all other points of access. Current users will still be able to use the service until October 1, 2019, however no additional features will be made available.

- **What will happen once StaffHub is retired?**<br>
Microsoft StaffHub will stop functioning for all users on October 1, 2019. Anyone who attempts to open the app will be shown a message directing them to download Microsoft Teams. Provided the user has an active license that includes Teams, their data and the core functionality from StaffHub will be available to them upon their transition to Teams.
Between April 2019 and October 2019, StaffHub users will receive in-app notifications encouraging them to use Microsoft Teams.

- **What do I need to do to prepare for this change?**<br>
IT administrators of tenants with active Microsoft StaffHub users will be notified in the Office 365 Message Center on the actions they'll need to take to transition to the Shifts app in Teams. Information about how to migrate from StaffHub to Shifts in Teams, including tools to help with migration, will be available soon.

    Your users will be informed about the app’s retirement through in-app notifications, but you may want to communicate the change to them as well, and update any internal documentation that refers to Microsoft StaffHub.

    Please visit this page for additional information on how to successfully transition from StaffHub to Shifts in Teams, including data migration, managing the new StaffHub capabilities we're building into Teams (in the Microsoft Teams & Skype for Business admin center), and other information about actions required by administrators and end users.

- **Will Microsoft Teams offer all of the functionality currently offered in Microsoft StaffHub?**<br>  

    Yes, starting in November 2018, Microsoft Teams will offer a Shifts feature, which enables managers to create, update, and manage schedules, and lets employees post their availability, swap shifts, and request time off. In addition, the Home view in the Teams mobile app will display the employee’s schedule and important company announcements. 

    To learn more, admins can go to [Manage the Shifts app for your organization in Teams](../../manage-the-shifts-app-for-your-organization-in-teams.md). For end-user help on how to use Shifts in Teams, check out [Shifts Help for firstline workers and managers](https://support.office.com/article/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b). 

    See the [roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=) for full details on additional features to be released in Teams.

- **Why can't I access my StaffHub team from the Shifts app in Teams?**<br>

    Teams that were created with Microsoft StaffHub can only be viewed and managed in StaffHub. When we release support to migrate your StaffHub team to the Shifts app in Teams, you'll be able to view StaffHub schedules in Shifts.

*****

- **Which licenses/SKUs is Shifts available on?**<br>

     Shifts is currently available as part of Teams in the following plans without any additional cost.
     |Office 365 Small Business  |Office 365 Enterprise  |Office 365 Education |Microsoft 365|
     |---------|---------|---------|--------|
     |Office 365 Business Premium  |Office 365 Enterprise F1<br>Office 365 Enterprise E1<br>Office 365 Enterprise E3<br>Office 365 Enterprise E5|Office 365 Education|Microsoft 365 F1<br>Microsoft 365 E1<br>Microsoft 365 E3<br> Microsoft 365 E5|

- **What if I don’t have Teams enabled in my tenant?**<br> 

     If you don't have Teams enabled in your tenant, assign Teams licenses to users in your organization to enable them on Teams. For more information, see [Move your Microsoft StaffHub teams to Shifts in Teams](move-staffhub-teams-to-shifts-in-teams.md).
 
- **What if I currently don't have Teams because I have Skype for Business enabled in my tenant?** 
 Teams supports coexistence with Skype for Business. For more information, see [Understand Microsoft Teams and Skype for Business coexistence and interoperability](../../teams-and-skypeforbusiness-coexistence-and-interoperability.md) and [Migration and interoperability guidance for organizations using Teams together with Skype for Business](../../migration-interop-guidance-for-teams-with-skype.md).

- **Which devices or platforms is Shifts available on?** 
    
    Shifts is available on the Teams web client, Teams desktop client, and Teams mobile clients (iOS and Android).

- **How do I get Shifts?**

    If a customer is already on one of the above mentioned plans, they can start using Teams Shifts today as part of Microsoft Teams. Getting started is easy, Firstline managers can sign in with their Office 365 work account in Microsoft Teams. From there, they can go to Shifts app either pinned in the left navigation bar or in the overflow menu under ‘…’. In Shifts app, they can create and manage schedules for the teams they are owner of and can invite Firstline Workers to download the application.  

- **Where can I learn more about Shifts?**

    For product information, go to [https://products.office.com/microsoft-teams/staff-scheduling-software](https://products.office.com/microsoft-teams/staff-scheduling-software). 

     For admin guidance, go to **placeholder**.

- **I'm currently a StaffHub customer. What do I need to know to move workers to Shifts in Teams?**

    Customers who currently have StaffHub should ensure that each user is covered with a Teams license from a qualified plan. For more information, see .  
    
### Features

Here's a list of StaffHub features, showing those that are replaced by an equivalent experience in Teams and those that are deprecated. Capabilities that aren't available in Teams may be available at a later time.

|StaffHub feature |Teams experience |
|---------|---------|
|Files    | The **Files** tab in the General channel of the team        |
|Tasks    |         |
|Messages     | Chats        |
|Flow     | Graph API        |
|Kronos integration     | Kronos bot, channels, and tabs       |
|Corporate announcements  |         |
|Custom fields   |         |
|Home page    |         |
|Phone numbers of team members     | Displayed if the StaffHub phone number matches the phone number in Azure AD        |
|StaffHub PowerShell cmdlets   | [Teams PowerShell cmdlets](../../teams-powershell-overview.md)      |
|Conditional access policies    |         |
|Organizational shared employee resources | Channels and tabs       |
|Non-provisioned team members|         |
|Native StaffHub reports and Microsoft 365 admin center reports    | [Teams reporting in the Microsoft Teams admin center](../../teams-analytics-and-reports/teams-reporting-reference.md)<br>[Teams activity reports in the Microsoft 365 admin center](../../teams-activity-reports.md)      | 
|SMS and and email invitations to join teams and install the app    | Email invitations for Office 365 accounts in Azure AD        |
|In-app support   | [Teams feedback portal on UserVoice](https://microsoftteams.uservoice.com/forums/555103-public-preview/category/182881-developer-platform)      |

