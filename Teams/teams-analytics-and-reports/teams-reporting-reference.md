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

Here's a list of the Teams reports available in the Microsoft Teams admin center and an overview of some of the information that's available in each report.

We're continually improving the Teams reporting experience and adding features and functionality. Over time, we'll be building additional capabilities into the reports and adding new reports in the Microsoft Teams admin center.

|Report  |What's measured? |
|---------|---------|
|[Teams usage report](teams-usage-report.md)  |  Active users<br/>Active users in teams and channels<br/>Active channels<br/>Messages<br/>Privacy setting of  teams<br/>Guests in a team   |
|[Teams user activity report](user-activity-report.md)  | Messages a user posted in a team chat<br/>Messages a user posted in a private chat<br/>  1:1 calls a user participated in<br/> Number of meetings user organized <br/>Number of meetings user participated in<br/>Meetings Audio, Video and Screen sharing time<br/>   Last activity date of a user     |
|[Teams device usage report](device-usage-report.md)   |  Windows users<br/>Mac users<br/>iOS users<br/>Android phone users     |
|[Teams live event usage report](teams-live-event-usage-report.md)   |  Total views<br>Start time<br>Event status<br>Organizer<br>Presenter<br>Producer<br>Recording setting<br>Production type    |
|[Teams PSTN blocked users report](pstn-blocked-users-report.md)   |  Display name<br>Phone number<br>Reason<br>Action type<br>Action date and time   |
|[Teams PSTN minute pools report](pstn-minute-pools-report.md) |  Country or region<br>Capability (license) <br>Total minutes<br>Minutes used<br>Minutes available|
|[Teams PSTN usage report - Calling Plans](pstn-usage-report.md#calling-plans)|  Time stamp<br>User name<br>Phone number<br>Call type <br>Called to<br>To country or region <br>Called from <br>From country or region<br>Charge<br>Currency<br>Duration<br>Domestic/International<br>Call ID<br>Number type<br>Country or region<br>Conference ID<br>Capability (license)|
|[Teams PSTN usage report - Direct Routing](pstn-usage-report.md#direct-routing)  |  Time stamp<br>Display name<br>SIP address<br>Phone number <br>Call type<br>Called to<br>Start time<br>Invite time<br>Failure time<br>End time<br>Duration<br>Number type<br>Media bypass<br>SBC FQDN<br>Azure region<br>Event type<br>Final SIP code<br>Final Microsoft subcode<br>Final SIP phrase<br>Correlation ID  |
|[Teams information protection license report](information-protection-license-report.md)  | <br>Whether users have valid licenses to push their messages via change notifications</br><br>Total number of change notification events triggered by a user<br><br>What apps are listening to org-wide change notification events<br>|
|[Teams Virtual Visits usage report](/microsoft-365/frontline/virtual-visits-usage-report?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json)  | Number of virtual appointments<br>Number of Bookings appointments<br>Number of Teams Electronic Health Records (EHR)-integrated appointments<br>Average duration of an appointment<br>Average lobby wait time of attendees<br>Start time<br>Meeting ID<br>Lobby wait time<br>Duration<br>Status<br>Product type<br>Attendees<br>SMS sent
|[Teams EHR connector Virtual Appointments report](/microsoft-365/frontline/ehr-connector-report?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json) | Start time<br>Duration<br>Primary (name of meeting organizer)<br>Primary's email (email of meeting organizer)<br>Department<br>Attendants<br>Lobby wait time<br>Whether the appointment is within the allocation limit|
[!INCLUDE [teams-reports-definitions](../includes/teams-reports-definitions.md)]

## Make the user specific data anonymous

To make the data in Teams user activity and Teams device usage report anonymous, you have to be a global administrator. This will hide identifiable information such as display name, email and Microsoft Azure Active Directory ID in reports and their exports.

1. In Microsoft 365 admin center, go to the **Settings** \> **Org Settings**, and under **Services** tab, choose **Reports**.
    
2. Select **Reports**, and then choose to **Display concealed user, group, and site names in all reports**. This setting gets applied both to the usage reports in Microsoft 365 admin center as well as Teams admin center.
  
3. Select **Save changes**.

> [!NOTE]
> Enabling this setting will de-identify information in [Teams user activity report](user-activity-report.md) and [Teams device usage report](device-usage-report.md) reports. It will not affect other usage reports available in Teams admin center.
> This setting also applies to Microsoft 365 usage reports in Microsoft 365 admin center, Microsoft Graph and Power BI.
