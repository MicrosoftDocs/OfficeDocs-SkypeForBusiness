---
title: IT Admin Guide to Insights in Teams for Education 
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: karsmith
description: An IT Admin guide to Insights in Microsoft Teams for Education.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# IT Admin Guide to Insights in Teams for Education

With Insights in Microsoft Teams for Education, educators and leaders can access analytics data about digital engagement, assignment workload, grades, communication and more.

Insights is active in Office 365 Education SKUs A1, A3, and A5.

> [!NOTE]
> Educators, learn how to use Insights [here](https://support.microsoft.com/article/27b56255-90c0-47aa-bac3-1c9f50157181).

## Permissions

### User types
- **Students** are identified by their license and _do not have_ access to the Insights tab (even if they are an owner of the team). 
- **Educators** are identified by faculty licenses. Educators must have a faculty license and be a class team owner to add and see the data presented in the Insights tab. 
- **Leaders** are also identified by faculty license, but in addition they need explicit permissions from the IT global admin to view the reports in the Insights app.
- Guest accounts _do not have_ access to Insights.

### Permission levels
Educators and leaders have different permission levels and logic:
- **Educators** can add the Insights app to a public channel within a class team by navigating to Apps in the Teams app bar and searching for Insights. The tab reflects activity from everyone in the class team who isn’t an owner (including educators who aren’t owners of the team). 
- **Leaders** can add the Insights app as a personal app (appears on Teams left menu) by navigating to Apps in the Teams app bar and searching for Insights. 

## Compliance

Insights has industry-leading compliance commitments, and is classified as a Tier-C service within the Office 365 Compliance Framework.

> [!NOTE]
> Visit the [Microsoft Trust Center](https://www.microsoft.com/trust-center) to learn more about how Microsoft protects your data.

## Privacy

The information collected and shown through Insights does meets more than 90 regulatory and industry standards, including GDPR and the Family Education Rights and Privacy Act (FERPA) for the security of students and children and other, similar, privacy-oriented regulations. It's important for IT admins to know that the information collected on a per-student basis is intended to be used in a class context only, to allow educators and leaders to determine students' behavior. The information is collected for meaningful learning activities, such as class meetings attendance, posting messages, responding to classmates' posts, working on assignments, editing files, and more. We don't show information about private chat or a Teams login, as an example.

Our goal is to help educators to understand engagement and shine a spotlight on student learning. While these class activities can be focused down to actions at the student level, there is no positive or negative value assigned to these actions by Microsoft Teams, and there is no judgmental identification of individual students based on criteria. The information in  Insights informs an educator that, for example, a student has not been active in the tool during a certain period in time, or has completed all their assignments last week on-time. It remains the responsibility of the educator to interact with the student and that student's family or guardians to determine the underlying reason for any activity or inactivity detected.

## Data collection

- We collect data for Insights when Education Analytics is turned on for the tenant. The data is collected from Teams activity in order to surface actionable insights for teaching and learning.
- Guests data _does not_ collected for Insights.
- By default, Education Analytics is turned **On**.

Currently, this data is pulled from the following areas of student and educator activity in class teams:

|Teams component  |Data collected  |
|-----------------|------------------------|------------------------|
|Assignments |Opening, turning in, and grade on assignments. |
|Channel engagement |Visiting a channel, creating a post, replying to and liking a post (not including chat content). |
|Files |Uploading, downloading, accessing, modifying, commenting on, and sharing a file (not including file content). |
|Meetings |Attendance (not including meeting content). |

## Data location

Insights data for European-based tenants is stored on servers in Europe. Data for US-based tenants is stored on servers in the United States. If you use Insights and your Office 365 tenant is in a region outside of Europe or the United States, your data will be stored in the appropriate geographic region.

## Performance and reliability

Insights is designed to handle a high volume of data collected from Teams activity with optimal performance and reliability.

The data collection process takes place on separate servers regardless of the installation of the Insights tab in Teams. The Insights tab or personal app does not affect application performance or network bandwidth for educators and students using the rest of Teams functionality.

> [!TIP]
> Read [here](edu-remote-low-bandwidth.md) about using Teams for Education when bandwidth is low.

## How to delete your data

Education services stores student and educator actions performed in the context of a class team. This data is considered a co-mingled data set and therefore isn't automatically deleted from the service once student or educator user accounts are deleted from your organization.

> [!NOTE]
> Deleting data has a negative impact on Insights' ability to analyze class team engagement over time.

- Open a support ticket [here](https://edusupport.microsoft.com/support). The support ticket must state clearly the request for a GDPR Delete DSR operation and contain the user object ID to be deleted. There is no ability to limit the data set or time window of the deletion.
- Once filed, the support ticket waits in the queue for one week in order to meet compliance minimal retention policy. You have the opportunity to cancel the operation during this time.
- After one week, the Education Analytics team takes action to ensure all data related to the user ID is deleted from the service. Microsoft support monitors the ICM ticket and will notify you once the deletion process is complete, in no more than 28 days.

## Turn Insights off and on using School Data Sync (SDS)

School Data Sync (SDS) helps to automate the process of importing and synchronizing Student Information System (SIS) data with Office 365.

The use of Insights does not require the use of SDS. However, you may choose to opt out from Education Analytics at any time by turning off the toggle in the SDS Admin Center under **Settings** > **Manage Education Analytics**.

:::image type="content" source="media/class-insights-on-off.png" alt-text="The on-off switch to enable or disable Insights.":::

By default, Education Analytics, and therefore Insights, is turned on. When you opt out of Analytics, we delete all data collected for the Insights tab. Turn Analytics back on, and we start collecting data from the time it's re-enabled.

Learn more:
[Educator's guide to Insights](https://support.microsoft.com/en-us/office/educator-s-guide-to-insights-in-microsoft-teams-27b56255-90c0-47aa-bac3-1c9f50157181)
