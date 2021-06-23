---
title: Sync Student Information System (SIS) data with Education Insights
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: karsmith
description: Sync Student Information System (SIS) data with Education Insights in Microsoft Teams.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---
 
# Sync Student Information System (SIS) data with Education Insights
The more data is fed into [Education Insights](class-insights.md), the better educators can support their students, and education leaders can support the educators.

To provide organization-level Insights, we must use [School Data Sync (SDS)](/SchoolDataSync) to connect to the Student Information System (SIS) so that Insights has the hierarchical structure of the educational system mapped correctly. 

Viewing class-level Insights as the class educator *does not* require this sync because we use Teams' class structure and permissions.

## Plan your SIS integration
The SIS data provides the hierarchical structure of the educational system and maps which user is assigned where.

Insights works best when using [SDS V2 file format](/schooldatasync/sds-v2-csv-file-format) but also supports [SDS V1 file format](/schooldatasync/school-data-sync-format-csv-files-for-sds) with *limited* functionality.

### Differences between SDS V1 and V2 file formats

| Data type |	V1 | V2 (recommended for new customers) |
|:--- |:--- |:--- |
| **Users** | The V1 format contains **only educators**, so to set org-level permissions for your education leaders, you need to search for them and define each one's permission manually. | The V2 format contains **all the roles** so that you can assign role-based permissions. |
| **Orgs** | The V1 format contains **only schools**, so you see only one aggregation level (all your schools). You can zoom in to a specific school using a flat list, but this list may have a large number of schools or contain different types of schools that are hard to compare (such as primary to secondary school or science to art school).<br/><br/> When there is a hierarchy in place, you can create levels that make sense, such as a science or art department.| The V2 format contains **the full hierarchy of your district or institution**, including universities, colleges, faculties, campuses, regions, programs, and so on.<br/><br/> With a hierarchy, you can see relevant aggregation by each level of the hierarchy, quickly compare between organizational units at each level, assign permission to specific levels, set goals by org level, and so on.|

### Type of data required
The following table provides the type of data required to get the best out of Insights.

| Data type | Examples for what you need to provide|Why it's important?|
|:--- |:--- |:--- |
| **Users** |	Role (such as student)<br/> [Grade/Year level](#supported-grade-level-values) (such as 10)<br/> Org (name) | When we correctly assign each person to their role, grade/year level, and organization, we can ensure that the summaries and aggregations are correct.|
| **Orgs** | Org type (such as college) |	The hierarchy here is important. For example, schools may belong to a district, and that district may belong to a state.<br/> When a district education leader is permitted to see data, it's only for the schools in that district.|
| **Classes** | Title (such as Computer science 101) | This table details which classes are held in the organization. This table must be correctly mapped so that we can assign the student to the correct class. |
| **Enrollment** | Role (such as student) |	This table is for students and educators and enables us to know in which class they are registered. |

> [!NOTE]
> During the deployment process, you can decide if you want to use SDS for provisioning users and classes in Teams or to use it only to provide data to Insights.

## Best practices
The accurate mapping of the hierarchy and where everyone belongs within that hierarchy, enables Insights to provide accurate data and more precise and relevant insights for the different types of education leaders.

The more detail you provide here, the better and more relevant the reports and spotlights will be.
Here are some best practices to ensure the smooth deployment of SDS so that your users can make the most out of Insights.

### Users
*	Make sure *all users* are listed in the files you provide and synced. This includes all students and staff that need to see data for the organizational units they cover.

    If you currently only have educators listed in the SIS, add the other users manually before uploading the files to SIS and syncing the data.

    If some students are missing, the stats gathered by Insights is only from the registered students, and that will make the data and conclusions misleading.
	
*	Make sure to *provide the first and last name of each user*. If not, they are referenced by their email address, and this provides a less than positive experience in the reports and spotlights (cards with Insights on student activity or performance).

*	The *grade/year level must be input as 2 digits* (for example, 07 for Year 7). Check out the [mapping list](#supported-grade-level-values). 

*	It's important to *add the year/grade level to all students* so that a grade/year level can filter the data.    

*	Make sure to *assign each user to their relevant organizational unit*. In this way, we won't show misleading data in our spotlights based on aggregated data for each unit.

    *	A student can be associated with more than one org unit, for example, students who are registered in a special program or two faculties. In such a case, provide two lines in the users file for that student – one for each organization.
	
    *	Based on the org unit for staff, you will be able to define the relevant permissions. Make sure they are associated with the correct unit level, so they receive the permissions they need. For example, a counselor assigned to four schools needs to see all the classes in these schools; a principal needs to see all the classes in their school. 
	
*	The role is vital. Although this list is closed, try to match the role from [the list](/schooldatasync/sds-v2-csv-file-format#enumerated-values-enum-supported) to the real role of each user you upload. In this way, you can assign role-based permissions accordingly. For example, provide permissions for all principals to see the classes in their school, or for all professors to see their faculty. 

### Organizations

* Make sure to *reflect the real hierarchy of your organization*. This can be achieved by manually adding the file. In some cases, this hierarchy is not reflected in the SIS. Still, it may be necessary here to see the relevant aggregation by each level of the hierarchy, assign permission to specific levels, set goals by org level, and so on. 

* Ensure that *all org units down the org tree include students or classes* to aggregate student data for them. We recommend that students are on the lowest branch of the tree.

> [!NOTE]
> For more details about SDS deployment, visit [Planning SDS](/schooldatasync/planning-school-data-sync).

## Integrate SIS using SDS

School Data Sync (SDS) is provided with Office 365 for Education. SDS reads the data from an educational institution's Student Information System (SIS) and integrates it with Teams to enable the automatic creation of online classrooms and users.

It also synchronizes the SIS data with Insights.

### Sync with Insights

First, you need to turn the Insights toggle on to start the sync process.

* On the [**SDS portal**](https://sds.microsoft.com), go to **Settings**, scroll down to **Collect data for Insights**, and check that it's enabled (it's turned *on* by default).

* Scroll down to the next switch, **Sync organizational data from SDS (preview)**, and turn on.

If you do not see the option for *Sync organizational data from SDS (preview)* on the Settings page, go to the [sign-up page](https://aka.ms/insights/join) to provide your information, and a team member will reach out to you.

:::image type="content" source="media/insights-sds-settings.png" alt-text="Sync with Insights toggles":::

### Deploy SDS
**If you already use SDS**, we recommend you follow our [best practices](#best-practices). 

To sync your current profiles with Insights, go to your **Sync Profile(s)**, click **Edit**, and select **Sync to Insights**. For the initial sync, we recommend waiting 24 hours for the reports to be available after the data is refreshed from your SIS.  

:::image type="content" source="media/insights-sds-profile-sync.png" alt-text="Sync profile with Insights toggles":::

**If you don't use SDS yet**, you now need to [deploy it](/schooldatasync/deploying-school-data-sync).

During the deployment process, you can decide if you want to use SDS for provisioning users and classes in Teams or to use it only to provide data to Insights.

> [!NOTE]
> If it's the middle of the year and you already created teams manually, use SDS only to provide the data to Insights, and next year consider to use SDS for provisioning users and classes in Teams as well.

### Verify the sync process
A new status area appears next to Sync organizational data from SDS (preview) on the Settings page.
 
*	If the status is **In progress**, wait up to 24 hours after deployment of the SDS profile.

*	If the status is **Completed**, congratulations, you can see Insights at the organizational level, and continue to the next step.

*	If the status is **Completed with errors**, **Completed with warnings**, or **Aborted**, download the log file that contains the errors and warnings for the latest sync and check if you can fix these errors. 

> [!IMPORTANT]
> If you run into any problems, [customer support](https://aka.ms/edusupport) is there to help you.

## Supported grade level values

In the SDS files, grade/year level defined as Enumerated values, which means you can only provide a selected set of values within the CSV file. Anything other than values specified will result in an error during sync processing.

> [!NOTE]
> The *grade/year level must be input as 2 digits* (for example, 07 for Year 7).

The section below defines the supported values in the users file.

### United States / worldwide grade levels
|Value in file (Grade column) | Label in Insights|
|:---|:---| 
|IT|Infant|
|PR|Pre-school|
|PK|Pre-kindergarten|
|TK|Transitional Kindergarten|
|KG|Kindergarten|
|01|First grade|
|02|Second grade|
|03|Third grade|
|04|Fourth grade|
|05|Fifth grade|
|06|Sixth grade|
|07|Seventh grade|
|08|Eighth grade|
|09|Ninth grade|
|10|Tenth grade|
|11|Eleventh grade|
|12|Twelfth grade|
|PS|Postsecondary|
|PS1|Postsecondary freshman|
|PS2|Postsecondary sophomore|
|PS3|Postsecondary junior|
|PS4|Postsecondary senior|
|undergraduate|Undergraduate|
|graduate|Graduate|
|postgraduate|Postgraduate (graduate with an emphasis on research)|
|alumni|Alumni|
|adultEducation|Adult Education|
|UG|Ungraded|
|Other|Other|

### United Kingdom year groups
|Value in file (Grade column) | Label in Insights|
|:---|:---| 
|IT|Nursery|
|PR|Pre-school|
|PK|Reception|
|01|Year 1|
|02|Year 2|
|03|Year 3|
|04|Year 4|
|05|Year 5|
|06|Year 6|
|07|Year 7|
|08|Year 8|
|09|Year 9|
|10|Year 10|
|11|Year 11|
|12|Year 12|
|13|Year 13|
|PS|Postsecondary|
|PS1|Postsecondary Year 1|
|PS2|Postsecondary Year 2|
|PS3|Postsecondary Year 3|
|PS4|Postsecondary Year 4|
|undergraduate|Undergraduate|
|graduate|Graduate|
|postgraduate|Postgraduate (graduate with an emphasis on research)|
|alumni|Alumni|
|adultEducation|Adult Education|
|UG|Ungraded|
|Other|Other|
