---
title: Sync Student Information System (SIS) data with Education Insights
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: karsmith
description: Sync Student Information System (SIS) data with Education Insights in Microsoft Teams.
ms.localizationpriority: high
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

## Plan your School Data Sync integration

The Microsoft School Data Sync (a.k.a SDS) provides the School Information System (a.k.a SIS) data and it's hierarchical structure of the educational system and maps which user is assigned where, as well as provides additional data on the student and organizational hierarchy.

Insights works best when using [SDS V2.1 file format](/schooldatasync/sds-v2.1-csv-file-format) but also supports [SDS V2 file format](/schooldatasync/sds-v2-csv-file-format) and  [SDS V1 file format](/schooldatasync/school-data-sync-format-csv-files-for-sds) *with limited functionality*.

### Differences between SDS V1 and V2 file formats

| Data type | V1 | V2 and V2.1 |
|:--- |:--- |:--- |
| **Users** |Supports only 'educator' role, as a result org-level permissions for your education leaders need to be set manually|Supports multiple roles so that role-based permissions can be set|
| **Orgs** | Supports only 'schools', aggregation level.<br><br>As a result, does not provide multiple aggregation levels and provide limited ability to compare different types of schools (e.g primary vs. secondary school, science vs. art school)|Supports multi-layer hierarchy, including district/institution, universities, colleges, faculties, campuses, regions, programs, etc.<br><br>Allows for multiple aggregation levels and to easily compare between organizational units at each level, assign permissions to specific levels, set goals by org level, etc.|
| **Additional optional information** |None|**V2.1 file format only**<br><br>*Academic Sessions* - timeframes of sessions (semesters, school years etc.)<br><br>Demographics and student flags* - data like race, ethnicity, and gender, as well as special programs (IEP, 504)|

> [!NOTE]
> Customers will not be able on onboard file format v2 starting July 15th 2021, and will need to use the v2.1 format instead, all future upgrades and new capabilitie will be done on the v2.1 format and it will be fully backward compatible to file format v1.

### Best practices

The accurate mapping of the hierarchy and where everyone belongs within that hierarchy, enables Insights to provide accurate data and more precise and relevant insights for the different types of education leaders.

The more detail you provide, the better and more relevant the reports and spotlights will be.

#### File format version to use adn data to sync

- Use file format V2.1 and sync the optional data used by Education Insights as described [here](/schooldatasync/sds-for-insights-overview#education-insights-capabilities-matrix-and-sds-v21-csv).

#### Users and Roles

- Make sure **all users are listed in the files** you provide and synced. This includes all students and staff that need to see data for the organizational units they cover.
- If you currently only have educators listed in your SIS, add all other users manually before uploading the files to SDS and syncing the data. The stats gathered by Insights will onlybe  from the registered students, if some students are missing, that will make the data and conclusions misleading.

- If you use SDS for provisioning as well, make sure to **provide the first and last name of each user**. Otherwise, students will be referenced by their email address, resulting in a non-optimal experience.

- The grade/year level must be based on this [mapping list](#supported-grade-level-values).

- Make sure to **add the year/grade level to all students** .

- Make sure to **assign each user to their relevant organizational unit**.

  - A student can be associated to more than one organizational unit, for example, students who are registered in a special program or two faculties. In case the student has more then one organizational unit, provide a line for each in the users file for that student.

  - IT admin can grant permissions based on organizational unit for staff. **Make sure staff members are associated with the correct unit level**, so they receive the permissions they need. For example, a counselor assigned to four schools needs to see all the grades in those schools; a principal needs to see all the classes in their school.

- **The role is vital**. Although this list is closed, try to match the role from [the list](/schooldatasync/sds-v2-csv-file-format#enumerated-values-enum-supported) to the real role of each user you upload. This will enable you to assign role-based permissions accordingly. For example, provide permissions for all principals to see the classes in their school, or for all professors to see their faculty.

#### Organizations

- Make sure to **reflect the real and full hierarchy of your organization**. In some cases, this hierarchy is not reflected in the SIS, in which case it needs to be added manually to the CSV file before syncing.

- Make sure that **all organization units down the organization tree include students or classes**. We recommend that students are on the lowest branch of the tree.

> [!NOTE]
> For more details about SDS deployment, visit [Planning SDS](/schooldatasync/planning-school-data-sync).

## Integrate SIS data using SDS

School Data Sync (SDS) is provided with Office 365 for Education. SDS reads the data from an educational institution's Student Information System (SIS) and integrates it with Microsoft applications like Teams to enable the automatic creation of online classrooms and users.

It also synchronizes the SIS data with Insights.

As an IT Admin, you can choose to use SDS for provisioning only, Insights only or for both.

To Sync your SIS information with Educations Insights follow the instructions in [How to deploy SDS for Insights](/schooldatasync/how-to-deploy-sds-for-insights).

### Deploy SDS

**If you already use SDS**, we recommend you follow our [best practices](#best-practices).

**If you don't use SDS yet**, you now need to [deploy it](/schooldatasync/deploying-school-data-sync).

During the deployment process, you can decide if you want to use SDS for provisioning users and classes to Teams or to use it only to provide user and organizational hierarchy to Insights as well.

> [!NOTE]
> If it's the middle of the year and you already created teams manually, use SDS only to provide the user and organizational hierarchy data to Insights, and next year consider using SDS for provisioning users and classes for Teams as well.

### Verify the sync process

To verify the sync status progress follow the instructions in [SDS for Insights Data Health and Monitoring](/schooldatasync/sds-for-insights-data-health-and-monitoring).

> [!IMPORTANT]
> If you run into any problems, [customer support](https://aka.ms/edusupport) is there to help you.

## Supported grade level values

In the SDS files, grade/year level defined as Enumerated values, which means you can only provide a selected set of values within the CSV file. Anything other than values specified will result in an error during sync processing.

The section below defines the supported values in the users file.

### United States / worldwide grade levels

|Value in file (Grade column) | Label in Insights|
|---|---|
|IT|Infant|
|PR|Pre-school|
|PK|Pre-kindergarten|
|TK|Transitional Kindergarten|
|KG|Kindergarten|
|01 or 1|First grade|
|02 or 2|Second grade|
|03 or 3|Third grade|
|04 or 4|Fourth grade|
|05 or 5|Fifth grade|
|06 or 6|Sixth grade|
|07 or 7|Seventh grade|
|08 or 8|Eighth grade|
|09 or 9|Ninth grade|
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
|---|---|
|IT|Nursery|
|PR|Pre-school|
|PK|Reception|
|01 or 1|Year 1|
|02 or 2|Year 2|
|03 or 3|Year 3|
|04 or 4|Year 4|
|05 or 5|Year 5|
|06 or 6|Year 6|
|07 or 7|Year 7|
|08 or 8|Year 8|
|09 or 9|Year 9|
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
