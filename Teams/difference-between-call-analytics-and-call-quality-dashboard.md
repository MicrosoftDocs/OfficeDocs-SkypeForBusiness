---
title: "Call Analytics and Call Quality Dashboard"
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.reviewer: mikedav, siunies, gageames
ms.topic: conceptual
ms.assetid: 4cd5fe35-8463-4996-a252-086cd3ca2d9a
ms.tgt.pltfrm: cloud
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
search.appverid: MET150
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Reporting
description: "Learn about Call Analytics and Call Quality Dashboard and when to use them to monitor and troubleshoot call-quality problems."
---

# Call Analytics and Call Quality Dashboard

Microsoft Teams and Skype for Business give you two ways to monitor and troubleshoot call-quality problems: Call Analytics and Call Quality Dashboard (CQD). This article describes both and tells you when to use each one.

Call Analytics and CQD run in parallel and can be used independently or together. For example, say a communications support specialist determines that they need more help troubleshooting a call problem. The communications support specialist passes the call to a communications support engineer, who has access to more information in Call Analytics than the communications support specialist. In turn, the communications support engineer can alert a network engineer to an issue. The network engineer might check CQD to see if an overall site-related issue could be a contributing cause of call problems.

## What's Call Analytics, and when should I use it?

**Call Analytics is now available in the [Microsoft Teams admin center](https://admin.teams.microsoft.com).** To see all of the call information and data for a user, use the **Call History** tab. You can do this by looking on the user's profile page by either searching for the user from the dashboard or finding the user from **Users** in the left navigation.

Call Analytics shows detailed information about the devices, networks, and connectivity related to the specific calls and meetings for each user in a Microsoft Teams or Skype for Business account. Why did this user have a poor call this afternoon? Using Call Analytics, an Office 365 admin or trained helpdesk agent can investigate the device, network, connectivity, and other factors related to his call to troubleshoot call quality and connection problems in Microsoft Teams and Skype for Business.

To see this information for a user in the Microsoft Teams admin center, click the **Call History** tab for that user in the user detail page, showing all the calls and meetings that user has participated in for the last 30 days.

![Call analytics user data.](media/teams-difference-between-call-analytics-and-call-quality-dashboard-image1.png)

To get additional information about a given session including detailed media and networking statistics, click on a session to see the details.

![Call analytics user session data.](media/teams-difference-between-call-analytics-and-call-quality-dashboard-image2.png)

If you want non-admins, such as helpdesk agents from an external vendor, to use Call Analytics, you can assign permissions so that they can use Call Analytics, but they can't access the rest of the Microsoft Teams admin center: 
  
- **Helpdesk agents with communications support specialist permissions**: Agents see a limited set of data and personally identifiable information (PII) in Call Analytics. They can troubleshoot calls, but they will hand off problems with meetings to a communications support engineer.
    
- **Helpdesk agents with communications support engineer permissions**: Agents see all available data in Call Analytics and troubleshoot both calls and meetings. They have full access to call logs and customer information.

> [!NOTE]
> The communications support specialist role is equivalent to tier 1 support role from the preview portal and the communications support engineer role is equivalent to tier 2 support role from the preview portal.

For more information about the communications support specialist and communications support engineer roles, see [Use Microsoft Teams admin roles to manage teams](using-admin-roles.md).

> [!IMPORTANT]
> Helpdesk agent permissions and network topology upload are available in the Microsoft Teams admin center. Communications Support Specialists and Communications Support Engineers can use this portal to access Call Analytics and the Call Quality Dashboard.
    
For details about setting up Call Analytics, see [Set up Skype for Business Call Analytics](set-up-call-analytics.md). For more information about how Helpdesk agents can work with Call Analytics, see [Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md).
  
## What's the Call Quality Dashboard, and when should I use it?
  
Whereas Call Analytics is designed to help admins and helpdesk agents troubleshoot call quality problems with specific calls, the Call Quality Dashboard (CQD) is designed to help Teams admins, Skype for Business admins, and network engineers optimize a network. CQD shifts focus from specific users and instead looks at aggregate information for an entire Teams or Skype for Business organization. For more details, see [Features of the Call Quality Dashboard for Teams and Skype for Business Online](turning-on-and-using-call-quality-dashboard.md#BKMKFeaturesOfTheCQD).
  
Maybe the user's poor call quality is due to a network issue that's also affecting many other users. The individual call experience isn't visible in CQD, but the overall quality of calls made using Microsoft Teams or Skype for Business is captured. With the CQD, overall patterns may become apparent, allowing network engineers to make informed assessments of call quality. CQD provides reports of call quality metrics that give you insights into overall call quality, server-client streams, client-client streams, and voice quality [SLA](https://go.microsoft.com/fwlink/p/?linkid=846252).
  
![Screenshot of Call Quality Dashboard. Tabs shown are Overall Call Quality, Server - Client, Client - Client, and Voice Quality SLA.](media/teams-difference-between-call-analytics-and-call-quality-dashboard-image3.png)

With the help of CQD's Location-Enhanced Reports, aggregate call quality and reliability within the user's building can be assessed to determine if the problem is isolated to a single user or affects a larger segment of users.

![Screenshot of Call Quality Dashboard's Location-Enhanced Reports. Tabs shown are Overview, Buildings - Wired, Buildings - WiFi, and Mobile (LTE). A filter is being applied to view the streams within a specific building.](media/teams-difference-between-call-analytics-and-call-quality-dashboard-image4.png)

> [!NOTE]
> To enable building or endpoint-specific views in CQD, an admin must [upload building or endpoint information](turning-on-and-using-call-quality-dashboard.md#upload-tenant-data-information) on CQD's Tenant Data Upload page. 

If you want non-admins, such as helpdesk agents, to use Call Quality Dashboard, you can assign those users the **Teams Communications Support Engineer**, **Teams Communications Support Specialist**, or **Reports Reader** role. Users with the following roles can access Call Quality Dashboard:

- Global Administrator
- Skype for Business Administrator
- Teams Service Administrator
- Teams Communications Administrator
- Teams Communications Support Engineer
- Teams Communications Support Specialist
- Reports Reader

> [!NOTE]
> The Teams Communications Support Engineer, Teams Communications Support Specialist, and Reports Reader roles cannot modify files on CQD's Tenant Data Upload page nor activate CQD for a tenant.

For more information about these roles, see [About Office 365 admin roles](/office365/admin/add-users/about-admin-roles).

For more information about CQD, see [Turning on and using Call Quality Dashboard for Microsoft Teams and Skype for Business Online](turning-on-and-using-call-quality-dashboard.md) and [Dimensions and measures available in Call Quality Dashboard for Microsoft Teams and Skype for Business Online](dimensions-and-measures-available-in-call-quality-dashboard.md).
  
## Related topics

[Video:	Call Quality Overview](https://aka.ms/teams-quality)

[Set up Call Analytics](set-up-call-analytics.md)

[Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)

[Turning on and using Call Quality Dashboard for Microsoft Teams and Skype for Business Online](turning-on-and-using-call-quality-dashboard.md)
