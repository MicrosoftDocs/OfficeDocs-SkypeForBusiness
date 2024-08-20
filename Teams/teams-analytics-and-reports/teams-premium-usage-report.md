---
title: Teams Premium feature usage report  
author: wlibebe
ms.author: wlibebe
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: vapati
ms.date: 7/18/2024
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
description: Learn how to use the Teams Premium usage report in the Teams admin center to know how often users are using each  Teams Premium feature.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Teams Premium feature usage report

[!INCLUDE[Teams Premium ECM](../includes/teams-premium-ecm.md)]

The Teams Premium feature usage report in the Microsoft Teams admin center allows you, as an admin, to view aggregated usage of Teams Premium features by users in your org. You can use this report to understand how individual users are using Teams Premium features, encourage users to try underused features, and measure the value of Teams Premium for your org.

The report provides the following metrics:  

- **Reached users across organization:**  Count of how many users attended meetings or events that used a Teams Premium feature.
- **Count of meetings across organization:** Count of meetings or events that used a Teams Premium feature.
- **Count of meetings for each user:** Count of meetings or events each user attended that used a Teams Premium feature.

> [!NOTE]
> This feature isn’t available for gov clouds (GCC, GCC-H and DoD).

## View the Teams Premium feature usage report

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. Using accounts with lower permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. To learn more, see [About admin roles in the Microsoft 365 admin center](/microsoft-365/admin/add-users/about-admin-roles).

You must be either a global admin, global reader, or Teams service admin to view the reports in the Microsoft Teams admin center. To learn more about getting admin roles and permissions, see [Use Teams administrator roles to manage Teams](../using-admin-roles.md).

1. In the left navigation of the Microsoft Teams admin center, select **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Teams Premium feature usage**.

2. Under **Date range**, select a range and then select **Run report**. It might take up to four days for the latest usage data to be reflected in this report.

:::image type="content" source="../media/premium-usage-report-small.png" alt-text="Diagram of the flow for when a Teams meeting or call is sent and received." lightbox="../media/premium-usage-report-expand.png":::

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |You can view the Teams Premium feature usage report for trends over the last 7, 30, 90, and 180 days. |
|**2**   |Each report has a date for when this report was generated. Reports usually reflect a 24-48 hour latency from the time a feature was used. For example, data for January 10 should show up in the report by around January 12. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the count of items.</li> </ul>To see the different metrics details on that given date, hover over each data point on the graph.|
|**4**   |The chart represents different usage metrics across the entire organization. You can filter what you see on the chart by selecting an item in the legend. For example, select **Total reached users**, **Total meetings**, and more to see only the info related to each one. Changing this selection doesn’t change the information in the table. The following list describes metrics available across different tabs: <ul><li>**Total usage**:  This tab covers usage metrics for all Teams Premium features across your tenant.  </li> <ul> <li>**Total reached users:** Count of users who had meetings or events that used a Teams premium feature. </li> <li>**Total meetings:** Count of meetings or events that used a Teams Premium feature.  </li> </ul> <li>**Intelligent collaboration**: This tab covers usage metrics for intelligent collaboration features across your tenant. </li> </li><ul><li>**Intelligent recap (Reached users):**  Count of users who viewed intelligent recap for their meetings.  </li><li>**Intelligent recap (Total meetings):** Count of meetings where users viewed intelligent meeting recap in a recent Teams client version released after June 4, 2024. Meeting count where intelligent recap is used by user is only counted if users updated their Teams client to a version release after June 4, 2024. If usage isn’t reflected for some users, you should update those users’ Teams client to the latest Teams client version. To learn more, see [Version update history for the new and classic Microsoft Teams app](/officeupdates/teams-app-versioning). </li> <li>**Live translated caption (Reached users):**  Count of users who enabled live translated captions for a meeting.  </li><li>**Live translated caption (Total meetings):**  Count of meetings where users enabled live translated captions.  </li></ul> <li>**Advanced protection**: This tab covers usage metrics for advanced  protection features across your tenant. </li><ul><li>**Sensitivity label (Reached users)**: Count of users who attended meetings where a sensitivity label was enabled. </li> </li><li>**Sensitivity label (Total meetings):**  Count of meetings where a sensitivity label was enabled.  </li><li>**Watermark (Reached users):** Count of users who attended meetings where a watermark was enabled. </li> <li>**Watermark (Total meetings) :** Count of meetings where a watermark was enabled.  </li><li>**Prevent chat copy (Reached users):**  Count of users who attended meetings where copying or forwarding of meeting chat was turned on/off. </li> <li>**Prevent chat copy (Total meetings)**: Count of meetings where copying or forwarding of meeting chat was turned on/off. </li><li>**Who can record (Reached users)**: Count of users who attended meetings where the **Who can record and transcribe** meeting option was specified. </li><li>**Who can record (Total meetings)**: Count of meetings where the **Who can record and transcribe** meeting option was specified. </li><li>**End-to-end encryption (Reached users)**: Count of users who attended meetings where end-to-end encryption was enabled. </li><li>**End-to-end encryption (Total meetings)**: Count of meetings where end-to-end encryption was enabled. </li></ul> <li>**Advanced personalization**: This tab covers usage metrics for advanced personalization features across your tenant. </li><ul><li>**Meeting theme (Reached users)**: Count of users who attended meetings where a custom theme representing organization’s brand was applied. </li> </li><li>**Meeting theme (Total meetings):**  Count of meetings where a custom theme representing organization’s brand was applied.  </li><li>**Custom meeting background (Reached users):** Count of users who applied an organization defined custom meeting background during meetings. </li> <li>**Custom meeting background (Total meetings):** Count of meetings where an organization defined custom meeting background was applied.  </li> <li>**Custom together mode (Reached users):** Count of meetings where custom together mode scenes were enabled. </li> <li>**Custom together mode (Total meetings)**: Count of meetings where custom together mode scenes were enabled. </li><li>**Meeting template (Reached users)**: Count of users who attended meetings where a custom meeting template was used. </li><li>**Meeting template (Total meetings)**: Count of meetings where a custom meeting template was used. </li></ul> <li>**Advanced events**: This tab covers usage metrics for advanced events features across your tenant. </li><ul><li>**Managed mode (Reached users)**: Count of users who enabled manage mode for what attendees see for an event/meeting. </li> </li><li>**Managed mode (Total meetings):** Count of events/meetings where manage mode for what attendee see was enabled.  </li><li>**RTMP-In (Reached users):** Count of users who participated in events/meetings where RTMP-In feature was used. </li> </li><li>**RTMP-In (Total meetings)**: Count of events/meetings where RTMP-In feature was used. </li></ul> |
|**5**   |The table gives you a breakdown of usage by feature for each Teams Premium licensed user in your org. <ul><li>**Username:** Name of the user</li> <li>**Ever licensed:** Describes if the user ever had Teams premium license during selected date range. </li> <li>**Total meetings:** Count of meetings for user where one or more Teams premium feature was used.</li> <li>**Intelligent recap (Total meetings):** Count of meetings where users viewed intelligent meeting recap in a recent Teams client version released after June 4, 2024. Meeting count where intelligent recap is used by user is only counted if users updated their Teams client to a version release after June 4, 2024. If usage isn’t reflected for some users, you should update those users’ Teams client to the latest Teams client version. To learn more, see [Version update history for the new and classic Microsoft Teams app](/officeupdates/teams-app-versioning). </li><li>**Live translated caption (Total meetings):** Count of meetings where users enabled live translated captions.</li> <li>**Sensitivity label (Total meetings):** Count of meetings given user attended where sensitivity label was enabled.</li><li>**Watermark (Total meetings):** Count of meetings given user attended where watermarks was enabled.</li><li>**Prevent chat copy (Total meetings):** Count of meetings given user attended where copying or forwarding of meeting chat was turned on/off. </li> <li>**Who can record (Total meetings):** Count of meetings given user attended where who can record and transcribe was specified. </li><li>**End-to-end encryption (Total meetings):** Count of meetings given user attended where end-to-end encryption was enabled. </li><li>**Meeting theme (Total meetings):** Count of meetings given user attended where custom theme representing organization’s brand was applied. </li><li>**Custom meeting background (Total meetings):** Count of meetings given user attended where organization defined custom meeting background was applied. </li><li>**Custom together mode (Total meetings):** Count of meetings given user attended where custom together mode scenes were enabled. </li><li>**Meeting template (Total meetings):** Count of meetings given user attended where custom meeting template was used. </li><li>**Managed mode (Total meetings):** Count of events/meetings given user attended where manage mode for what attendee see was enabled. </li><li>**RTMP-In (Total meetings):** Count of events/meetings given user attended where RTMP-In feature was enabled. </li></ul> |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |Export the report to a CSV file for offline analysis. Select the **Export to Excel** icon, and the report is downloaded within your browser.|
|**8** |Time series data represented in the top graph show different usage metrics aggregated for the entire tenant.|
|**9** |Tabular data represented in the bottom half shows different usage metrics aggregated per team.|

## Make user-specific data anonymous

To make the data in Teams user activity report anonymous, you must be a global administrator. Anonymizing the report hides identifiable information (using Message Digest 5 (MD5) hashes) such as display name, email, and Microsoft Entra Object ID in report and their export.

1. In Microsoft 365 admin center, go to the **Settings** > **Org Settings**, and under **Services** tab, choose **Reports**.
2. Select **Reports**, and keep the option for **Display concealed user, group, and site names in all reports** as checked. This setting applies to the usage reports in Microsoft 365 admin center and Teams admin center.
3. Select **Save changes**.

## Related articles

- [Teams analytics and reporting](teams-reporting-reference.md)
- [Microsoft Teams Premium - Overview for admins](../enhanced-teams-experience.md)