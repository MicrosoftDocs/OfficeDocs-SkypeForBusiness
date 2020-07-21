---
title: Microsoft Teams resources for Education admins
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: lakuan
description: Remote learning startup guidance for Microsoft Teams for EDU.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ROBOTS: NOINDEX, NOFOLLOW
---

# Best practices and recommended methods for creating Class teams for secure classroom use  

Microsoft Teams for Education offers [specific team types](https://support.office.com/article/choose-a-team-type-to-collaborate-in-microsoft-teams-0a971053-d640-4555-9fd7-f785c2b99e67) for educational use. The [Class team type](https://support.office.com/article/create-a-class-team-in-microsoft-teams-fae422eb-58b7-4431-9ff2-a4b9b6ae7c5b) is designed for classroom use and comes with specific features that support classroom needs including:  

- Assignments
- Grades
- OneNote classroom notebook  
- [Class Materials folder](https://support.office.com/article/Use-folders-to-create-read-only-files-for-students-or-other-team-members-0e7791d7-8c9c-4749-9bca-984289477988) for securing read-only content for students
- [Early teacher access](https://support.microsoft.com/article/activate-early-access-class-teams-created-with-school-data-sync-0d154696-66ab-4fcf-b22f-c3d9a82aaf78) to set up the class before students are added 
- The ability to mute disruptive students and other special permissions  

There are a few ways in which class teams can be created, and Teams for Education has a unique set of deployment tools to make it as easy as possible. We'll step through various options to help you choose the right deployment path that best fits your needs.  

## Automatic team creation using SDS

**This feature is coming soon, by the end of July 2020.**

Automating team creation saves both IT admins and teachers time. It ensures that teachers have all their class teams created and ready to set up upon sign in. [School Data Sync (SDS)](https://docs.microsoft.com/SchoolDataSync) is a free Office 365 Education tool that reads the data from an educational institution's system of record, for example a Student Information System (SIS) or Learning Management system (LMS). SDS uses the data to enrich Office 365 setup in many ways, including creating class teams in bulk and staying in sync with your information system to keep your instructor and student membership updated as enrollment changes. SDS can import data from any system of record and has built-in connectors to many of the world’s existing [SIS vendors](https://docs.microsoft.com/schooldatasync/what-sis-and-mis-vendors-does-school-data-sync-support). We highly recommend using SDS, as it provides the following benefits.  

### Benefits

- Automatic creation and maintenance of class teams – teachers will be able to sign in to  Teams and immediately start teaching
- Membership sync with SIS/LMS to maintain student membership changes 
- EDU Customer Success Team available for free deployment assistance 
- [Early teacher access](https://support.office.com/article/activate-early-access-class-teams-created-with-school-data-sync-0d154696-66ab-4fcf-b22f-c3d9a82aaf78): Educators have time to prepare their team before admitting students  
- Optionally creates users and applies Office 365 licenses
- Creates security groups for use across Office 365 including Teams policy
- Creates Administrative Units for scoped administrative delegation and [Teacher Password Reset](https://docs.microsoft.com/schooldatasync/how-to-enable-teacher-password-reset) 
- Built-in error and retry handling, throttling backoff, and session stability for large scale processing to reduce work on admins  
- Built-in cleanup capabilities to rename and archive groups and teams once they expire 
- [Grade Sync](https://docs.microsoft.com/schooldatasync/grade-sync) so teachers can do all their grading in Teams and have it automatically written grades from Teams back to the SIS gradebook 
- [Student Data Protection](https://docs.microsoft.com/schooldatasync/protecting-student-personal-data) to prevent students from using non-Microsoft apps and track and manage parent consent 
- Imported data is used to enrich Education Insights with user roles, organizations (schools) and other important data  

### Considerations

SDS creates teams in two steps. The first step creates a Microsoft 365 group in Azure Active Directory and the second step automatically turns that group into a team. The second step of creating teams is optional in SDS. An admin may not want to automatically create teams depending on deployment time and number of unused teams. We recommend institutions with 500,000 teams or more to turn off the automatic team creation toggle in SDS and use the [teacher-led team creation method](#teacher-led-team-creation-using-office-365-class-groups).  

### Get started

To get started, go to [School Data Sync (SDS)](https://docs.microsoft.com/SchoolDataSync) and contact [https://aka.ms/sdssupport](https://aka.ms/sdssupport) deployment assistance.  

## Teacher-led team creation using Office 365 class groups 

**This feature is coming soon, by mid-August 2020.**

Teacher-led team creation is a great deployment option if you want to make it easy for teachers to quickly create the classes they need. We also recommend that institutions with more than 500,000 teams use this method to minimize the number of extraneously-created teams.  

This hybrid approach allows you to either use SDS to create groups for each class (recommended) or use [Graph API](https://docs.microsoft.com/graph/api/educationroot-post-classes) to create them on your own. After class groups are prepared, educators can convert their groups into teams by using the **Suggested classes** icon.

### Benefits

- [Early teacher access](https://support.office.com/article/activate-early-access-class-teams-created-with-school-data-sync-0d154696-66ab-4fcf-b22f-c3d9a82aaf78): Educators have time to prepare their team before admitting students  
- Reduces the number of unused and unnecessary teams. The classes are prepared and suggested but not created unless the teacher intends to use them. We recommend this option for large institutions that have more than 500,000 teams to reduce clutter.
- SDS
    - Membership sync with SIS/LMS to maintain student membership changes
    - EDU Customer Success Team available for free deployment assistance 
    - Optionally creates users and applies Office 365 licenses
    - Creates security groups for use across Office 365 including Teams policy
    - Creates Administrative Units for scoped administrative delegation and [Teacher Password Reset](https://docs.microsoft.com/schooldatasync/how-to-enable-teacher-password-reset) 
    - Built-in error and retry handling, throttling backoff, and session stability for large scale processing to reduce work on admins  
    - Built-in cleanup capabilities to rename and archive groups and teams once they expire 
    - [Grade Sync](https://docs.microsoft.com/schooldatasync/grade-sync) so teachers can do all their grading in Teams and have it automatically written grades from Teams back to the SIS gradebook 
    - [Student Data Protection](https://docs.microsoft.com/schooldatasync/protecting-student-personal-data) to prevent students from using non-Microsoft apps and track and manage parent consent 
    - Imported data is used to enrich Education Insights with user roles, organizations (schools) and other important data
- Graph API
    - Additional flexibility and control
    - Doesn't require integration with SDS

### Considerations

- Not fully automated and requires some teacher action
- Teachers who don't have permission to create teams can still create teams from existing groups as shown [here](https://support.office.com/article/create-a-class-team-in-microsoft-teams-preview-fae422eb-58b7-4431-9ff2-a4b9b6ae7c5b)
- Graph API requires a high level of  technical expertise and time to create and run the script and fix any issues when creating class groups

### Get started

To get started with the SDS method, go to [School Data Sync (SDS)](https://docs.microsoft.com/SchoolDataSync) and contact [https://aka.ms/sdssupport](https://aka.ms/sdssupport) deployment assistance. 

To use the Graph API method, see [Graph API](https://docs.microsoft.com/graph/api/educationroot-post-classes?view=graph-rest-1.0&tabs=http) and [Create a class team](https://docs.microsoft.com/graph/api/educationroot-post-classes?view=graph-rest-beta&tabs=http).  

> [!NOTE]
> To use this method with SDS, you'll need to turn the automatic team creation toggle off in your SDS profile. You can also use a combination of automatic and teacher-led team creation for required and optional class teams by using two SDS profiles.

##

Additional support resources include:

- [Teams Troubleshooting](https://docs.microsoft.com/MicrosoftTeams/troubleshoot/teams)
- [Troubleshoot Microsoft Teams installation and update issues](troubleshoot-installation.md)
- [File a support ticket (can be used by educators and staff)](https://aka.ms/edusupport)
- [Support and Help center for educators using Teams](https://support.office.com/article/microsoft-teams-5aa4431a-8a3c-4aa5-87a6-b6401abea114)
- [Student Help center](https://support.office.com/article/student-help-center-395ab230-55bf-44c6-b265-e832d729b694)
- [Teams for Virtualized Desktop Infrastructure](https://docs.microsoft.com/microsoftteams/teams-for-vdi)
- [How to quickly optimize Office 365 traffic for remote staff](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571)
- [Monitor and manage call quality](monitor-call-quality-qos.md)
- [Verify service health for Teams](service-health.md)
- [Support resources for Teams](https://docs.microsoft.com/microsoft-365/admin/contact-support-for-business-products)
- [Teams help center](https://support.office.com/teams)
