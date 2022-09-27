---
title: Microsoft Teams analytics and reporting
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: conceptual
ms.service: msteams
ms.reviewer: svemu
f1.keywords:
- NOCSH
- ms.teamsadmincenter.analyticsandreports.overview
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: In this article, you will learn about the Teams reports that are available in the Microsoft Teams admin center.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Microsoft Teams analytics and reporting

A new analytics and reporting experience for Microsoft Teams is available in the Microsoft Teams admin center. You can run different reports to get insights into how users in your organization are using Teams. For example, you can see how many users communicate through channel and chat messages and the kinds of devices they use to connect to Teams. Your organization can use the information from the reports to better understand usage patterns, help make business decisions, and inform training and communication efforts.

## How to access the reports

To access the reports, you must be a global admin in Microsoft 365 or Office 365, global reader in Microsoft 365 or Office 365, Teams service admin, or Skype for Business admin. To learn more about Teams admin roles and which reports each admin role can access, see [Use Teams administrator roles to manage Teams](../using-admin-roles.md).

Go to the Microsoft Teams admin center, in the left navigation, select **Analytics & reports**, and then under **View Reports**, choose the report you want to run.

> [!NOTE]
> The reports in the Microsoft Teams admin center are separate from the activity reports for Teams that are part of the Microsoft 365 reports in the Microsoft 365 admin center. For more information about the activity reports in the Microsoft 365 admin center, see [Microsoft 365 Reports in the admin center](/microsoft-365/admin/activity-reports/activity-reports).

## Teams reporting reference

Here's a list of the Teams reports available in the Microsoft Teams admin center across different environments and an overview of some of the information that's available in each report.

We're continually improving the Teams reporting experience and adding features and functionality. Over time, we'll be building additional capabilities into the reports and adding new reports in the Microsoft Teams admin center.

|Report  |Public |GCC |GCCH |DoD |What's measured? |
|---------|---------|---------|---------|---------|---------|
|[Teams usage report](teams-usage-report.md)  |Yes|Yes|Yes|Yes|  Active users<br/>Active users in teams and channels<br/>Active channels<br/>Messages<br/>Privacy setting of  teams<br/>Active guests in a team  <br/>Active external users (in shared channels)<br/>Shared channel-specific details within a team (new)|
|[Teams user activity report](user-activity-report.md)  |Yes|Yes|Yes|Yes|Active internal and external (In shared channels) users<br/> Messages a user posted in a team chat<br/>Messages a user posted in a private chat<br/>  1:1 calls a user participated in<br/> Number of meetings user organized <br/>Number of meetings user participated in<br/>Meetings Audio, Video and Screen sharing time<br/>   Last activity date of a user  <br>Shared channel interactions of a user (new)</br>   |
|[Teams device usage report](device-usage-report.md)   |Yes|Yes|Yes|Yes|  Windows users<br/>Mac users<br/>iOS users<br/>Android phone users     |
|[Teams app usage report (new)](app-usage-report.md)   |Yes|Yes|No|No|  Total active users of the app<br/>Total active teams using the app<br/>Total apps installed (new)<br/>Total inactive apps <br/>Total 1P vs 3P vs LoB app usage (new)     |
|[Teams live event usage report](teams-live-event-usage-report.md)   |Yes|Yes|No|No|  Total views<br>Start time<br>Event status<br>Organizer<br>Presenter<br>Producer<br>Recording setting<br>Production type    |
|[Teams PSTN blocked users report](pstn-blocked-users-report.md)   |Yes|Yes|No|No|  Display name<br>Phone number<br>Reason<br>Action type<br>Action date and time   |
|[Teams PSTN minute pools report](pstn-minute-pools-report.md) |Yes|Yes|No|No|  Country or region<br>Capability (license) <br>Total minutes<br>Minutes used<br>Minutes available|
|[Teams PSTN usage report - Calling Plans](pstn-usage-report.md#calling-plans)|Yes|Yes|No|No|  Time stamp<br>User name<br>Phone number<br>Call type <br>Called to<br>To country or region <br>Called from <br>From country or region<br>Charge<br>Currency<br>Duration<br>Domestic/International<br>Call ID<br>Number type<br>Country or region<br>Conference ID<br>Capability (license)|
|[Teams PSTN usage report - Direct Routing](pstn-usage-report.md#direct-routing)  |Yes|Yes|No|No|  Time stamp<br>Display name<br>SIP address<br>Phone number <br>Call type<br>Called to<br>Start time<br>Invite time<br>Failure time<br>End time<br>Duration<br>Number type<br>Media bypass<br>SBC FQDN<br>Azure region<br>Event type<br>Final SIP code<br>Final Microsoft subcode<br>Final SIP phrase<br>Correlation ID  |
|[Teams information protection license report](information-protection-license-report.md)  |Yes|Yes|No|No| <br>Whether users have valid licenses to push their messages via change notifications</br><br>Total number of change notification events triggered by a user<br><br>What apps are listening to org-wide change notification events<br>|
|[Teams Virtual Visits usage report](/microsoft-365/frontline/virtual-visits-usage-report?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json)  |Yes|Yes|No|No| Number of virtual appointments<br>Number of Bookings appointments<br>Number of Teams Electronic Health Records (EHR)-integrated appointments<br>Average duration of an appointment<br>Average lobby wait time of attendees<br>Start time<br>Meeting ID<br>Lobby wait time<br>Duration<br>Status<br>Product type<br>Attendees<br>SMS sent
|[Teams EHR connector Virtual Appointments report](/microsoft-365/frontline/ehr-connector-report?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json) |Yes|Yes|No|No| Start time<br>Duration<br>Primary (name of meeting organizer)<br>Primary's email (email of meeting organizer)<br>Department<br>Attendants<br>Lobby wait time<br>Whether the appointment is within the allocation limit|
[!INCLUDE [teams-reports-definitions](../includes/teams-reports-definitions.md)]

## Make the user specific data anonymous

To make the data in Teams user activity report anonymous, you have to be a global administrator. The global administrator can hide identifiable information (using MD5 hashes) such as display name, group name, email, and AAD ID in the report and its export.

1. In Microsoft 365 admin center, go to the **Settings** \> **Org Settings**, and under **Services** tab, choose **Reports**.
    
2. Select **Reports**, and then choose to **Display concealed user, group, and site names in all reports**. This setting gets applied both to the usage reports in Microsoft 365 admin center as well as Teams admin center.
  
3. Select **Save changes**.

> [!NOTE]
> Enabling this setting will de-identify user, group, and site name information in the [Teams user activity report](user-activity-report.md), [Teams device usage report](device-usage-report.md), and [Teams usage report](teams-usage-report.md). Starting September 1, 2021, this setting is enabled by default for everyone as part of our ongoing commitment to help protect important information and enable companies to support their local privacy laws. 
>This setting also applies to Microsoft 365 usage reports in Microsoft 365 admin center, Microsoft Graph and Power BI.
