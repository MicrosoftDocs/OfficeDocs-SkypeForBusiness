---
title: Recommended methods and best practices for creating class teams  
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: lakuan
description: Learn about the recommended methods and best practices for how to create class teams for your school. 
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

# Recommended methods and best practices for creating class teams

Microsoft Teams for Education offers  [specific team types](https://support.office.com/article/choose-a-team-type-to-collaborate-in-microsoft-teams-0a971053-d640-4555-9fd7-f785c2b99e67)  for educational use. The [Class team type](https://support.office.com/article/create-a-class-team-in-microsoft-teams-fae422eb-58b7-4431-9ff2-a4b9b6ae7c5b) is designed for classroom use and comes with specific features that support classroom needs including:  

- Assignments
- Grades
- OneNote classroom notebook  
- [Class Materials folder](https://support.office.com/article/Use-folders-to-create-read-only-files-for-students-or-other-team-members-0e7791d7-8c9c-4749-9bca-984289477988)  for securing read-only content for students
- [Early educator access](https://support.microsoft.com/article/activate-early-access-class-teams-created-with-school-data-sync-0d154696-66ab-4fcf-b22f-c3d9a82aaf78) to set up the class before students are added 
- The ability to mute disruptive students and other special permissions  

There are a few ways in which class teams can be created, and Teams for Education has a unique set of deployment tools to make it as easy as possible.

 - [Automatic team creation using SDS](#automatic-team-creation-using-sds)
 - [Educator-led team creation from Office 365 class groups](#educator-led-team-creation-from-office-365-class-groups)
 - [PowerShell script using Graph APIs](#powershell-script-using-graph-apis)
 - [Manual team creation](#manual-team-creation)

We'll step through various options to help you choose the right deployment path that best fits your needs.  

## Automatic team creation using SDS

Automating team creation saves both IT admins and educators time. It ensures that educators have all their class teams created and ready to set up upon sign in. [School Data Sync (SDS)](https://docs.microsoft.com/SchoolDataSync) is a free Office 365 Education tool that reads the data from an educational institution's system of record, for example a Student Information System (SIS) or Learning Management system (LMS). SDS uses the data to enrich Office 365 setup in many ways, including creating class teams in bulk and staying in sync with your information system to keep your instructor and student membership updated as enrollment changes. SDS can import data from any system of record and has built-in connectors to many of the world’s existing [SIS vendors](https://docs.microsoft.com/schooldatasync/what-sis-and-mis-vendors-does-school-data-sync-support). We highly recommend using SDS, as it provides the following benefits.  

### Benefits

- Automatic creation and maintenance of class teams – educators will be able to sign in to  Teams and immediately start teaching.
- Membership sync with SIS/LMS to maintain student membership changes.
- EDU Customer Success Team available for free deployment assistance.
- [Early educator access](https://support.office.com/article/activate-early-access-class-teams-created-with-school-data-sync-0d154696-66ab-4fcf-b22f-c3d9a82aaf78): Educators have time to prepare their team before admitting students.  
- Optionally creates users and applies Office 365 licenses.
- Creates security groups for use across Office 365 including Teams policy.
- Creates Administrative Units for scoped administrative delegation and [Teacher Password Reset](https://docs.microsoft.com/schooldatasync/how-to-enable-teacher-password-reset). 
- Built-in error and retry handling, throttling backoff, and session stability for large scale processing to reduce work on admins.  
- Built-in cleanup capabilities to rename and archive groups and teams once they are obsolete.
- [Grade Sync](https://docs.microsoft.com/schooldatasync/grade-sync): Educators can do all their grading in Teams and have it automatically write grades from Teams back to the SIS gradebook. 
- [Student Data Protection](https://docs.microsoft.com/schooldatasync/protecting-student-personal-data): Prevent students from using non-Microsoft apps and to track and manage parent consent. 
- Imported data is used to enrich Education Insights with user roles, organizations (schools) and other important data.  

### Considerations

SDS creates teams in two steps. The first step creates a Microsoft 365 group in Azure Active Directory (Azure AD) and the second step automatically turns that group into a team. The second step of creating teams is optional in SDS. An admin may not want to automatically create teams depending on deployment time and the number of unused teams that may result. We recommend institutions with 500,000 teams or more to turn off the automatic team creation toggle in SDS and use the [educator-led team creation method](#educator-led-team-creation-from-office-365-class-groups).  

### Get started

To get started, go to [School Data Sync (SDS)](https://docs.microsoft.com/SchoolDataSync) and contact [https://aka.ms/sdssupport](https://aka.ms/sdssupport) deployment assistance.  

## Educator-led team creation from Office 365 class groups

Educator-led team creation is a great deployment option if you want to make it easy for educators to quickly create the classes they need. We also recommend that institutions with more than 500,000 teams use this method to minimize the number of extraneously-created teams.  

This hybrid approach allows you to either use SDS to create groups for each class (recommended) or use [Graph API](https://docs.microsoft.com/graph/api/educationroot-post-classes) to create them on your own. After class groups are prepared, educators can convert their groups into teams by using the **Suggested classes** icon.

:::image type="content" source="media/class-teams-edu-suggested-classes.png" alt-text="Screenshot showing Suggested classes icon":::

### Benefits

- [Early educator access](https://support.office.com/article/activate-early-access-class-teams-created-with-school-data-sync-0d154696-66ab-4fcf-b22f-c3d9a82aaf78): Educators have time to prepare their team before admitting students.  
- Reduces the number of unused and unnecessary teams. The classes are prepared and suggested but not created unless the teacher intends to use them. We recommend this option for large institutions that have more than 500,000 teams to reduce clutter.
- SDS
    - Membership sync with SIS/LMS to maintain student membership changes.
    - EDU Customer Success Team available for free deployment assistance.
    - Optionally creates users and applies Office 365 licenses.
    - Creates security groups for use across Office 365 including Teams policy.
    - Creates Administrative Units for scoped administrative delegation and [Teacher Password Reset](https://docs.microsoft.com/schooldatasync/how-to-enable-teacher-password-reset).
    - Built-in error and retry handling, throttling backoff, and session stability for large scale processing to reduce work on admins. 
    - Built-in cleanup capabilities to rename and archive groups and teams once they are obsolete. 
    - [Grade Sync](https://docs.microsoft.com/schooldatasync/grade-sync): Educators can do all their grading in Teams and have it automatically write grades from Teams back to the SIS gradebook. 
    - [Student Data Protection](https://docs.microsoft.com/schooldatasync/protecting-student-personal-data): Prevent students from using non-Microsoft apps and to track and manage parent consent. 
    - Imported data is used to enrich Education Insights with user roles, organizations (schools) and other important data.
- Graph API
    - Additional flexibility and control.
    - Doesn't require integration with SDS.

### Considerations

- Not fully automated and requires some educator action.
- Educators who don't have permission to create teams can still create teams from existing groups as shown [here](https://support.office.com/article/create-a-class-team-in-microsoft-teams-preview-fae422eb-58b7-4431-9ff2-a4b9b6ae7c5b).
- Graph API requires a high level of  technical expertise and time to create and run the script and fix any issues when creating class groups.

### Get started

To get started with the SDS method, go to [School Data Sync (SDS)](https://docs.microsoft.com/SchoolDataSync) and contact [https://aka.ms/sdssupport](https://aka.ms/sdssupport) deployment assistance. 

To use the Graph API method, see [Graph API](https://docs.microsoft.com/graph/api/educationroot-post-classes?view=graph-rest-1.0&tabs=http) and [Create a class team](https://docs.microsoft.com/graph/api/educationroot-post-classes?view=graph-rest-beta&tabs=http).  

> [!NOTE]
> To use this method with SDS, you'll need to turn the automatic team creation toggle off in your SDS profile. You can also use a combination of automatic and educator-led team creation for required and optional class teams by using two SDS profiles.

## PowerShell script using Graph APIs

With PowerShell, you can write a script to create teams, channels and configure settings automatically. It requires the admin to first create the group, add educators and students, and then create the team as outlined [here](https://docs.microsoft.com/graph/teams-create-group-and-team). You can also use the Microsoft Graph API to create, configure, clone, and archive teams. For more information, see [Use the Microsoft Graph API to work with Microsoft Teams](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/teams_api_overview), [Microsoft Teams PowerShell](https://docs.microsoft.com/powershell/module/teams) and [Create a class team](https://docs.microsoft.com/graph/api/team-post?view=graph-rest-beta&tabs=http#example-6-create-a-team-with-a-non-standard-base-template-type). Using Graph APIs is a great way to have more control and flexibility, however, it requires a high level of technical expertise and takes more time to set up initially.

### Benefits

- Additional flexibility and control.
- Option to create early educator access teams or immediate student access to teams.  
- If you [create teams from groups](https://docs.microsoft.com/graph/api/team-post?view=graph-rest-beta&tabs=http#example-4-create-a-team-from-group), educators will have early access and student membership changes to the Azure AD group will be synced.

### Considerations

- Requires a high level of technical expertise and time to create and run the script and fix any issues when creating class groups.
- No built-in error handling or retry logic.
- Membership changes are not synced with SIS. 

> [!NOTE]
> Class teams require hidden group membership so only educators and students within the class can see the members of that class. To create an Office 365 class group, see [Create a class team](https://docs.microsoft.com/graph/api/educationroot-post-classes?view=graph-rest-beta&tabs=http) to meet the same privacy requirements.

## Manual team creation

Students and educators will get the most out of Teams when they can use it with minimal barriers and have the flexibility to tailor it to their needs. One way users can tailor their Teams experience is by having the ability to create teams. Educators set up their own class type team and invite students as shown [here](https://support.microsoft.com/article/create-a-class-team-in-microsoft-teams-fae422eb-58b7-4431-9ff2-a4b9b6ae7c5b#ID0EADAAA=Create_a_team_from_scratch). Educators can invite students by [adding students to the team](https://support.office.com/article/add-a-student-to-a-class-team-b88263bb-ace1-4702-8a48-f8a2cf4af954), [sharing a join code](https://support.office.com/article/Create-a-link-or-a-code-for-joining-a-team-11b0de3b-9288-4cb4-bc49-795e7028296f), or [sharing a link to the team](https://support.office.com/article/Create-a-link-or-a-code-for-joining-a-team-11b0de3b-9288-4cb4-bc49-795e7028296f). If possible, it’s best to have educators add their students to the team to ensure the students get access and are notified that they’ve been added to a team.

### Benefits

- Additional flexibility for educators.
- Immediate team creation and access.  

### Considerations

- Requires educator action and time.
- Student membership is not synced with SIS and requires manual management.
- Doesn't give educators early access to their teams. Students will gain immediate access.

## Recommended best practices

- Deploy early! Deploy early to ensure everything is working reliably and ready for the first day of school.
- If you have more than 500,000 teams, we recommend using the [educator-led team creation method](#educator-led-team-creation-from-office-365-class-groups). It reduces unused teams and clutter by only creating class teams that are relevant and needed.  
- If there are any issues (for example, classes are missing) with SDS automatic team creation and educators need them immediately, then they can use the  [educator-led team creation method](#educator-led-team-creation-from-office-365-class-groups) to retry. [Manual team creation](#manual-team-creation) is another solution, however, it won't keep your team membership updated.  
- The tenant team limit is 500,000 teams. Therefore, admins should proactively try to reduce the number of unused teams to avoid hitting these limits and extending their setup time. For more information about limits, see [Limits and specifications for Microsoft Teams](limits-specifications-teams.md).  

## Early access to class teams

Early Access Class Teams allows educators access to their class teams before their students can view it and begin participating. This allows educators time to set up, add files, and get organized before granting access to their students. When they are ready for students to access the team, they can easily [activate their class](https://support.office.com/article/activate-early-access-class-teams-created-with-school-data-sync-0d154696-66ab-4fcf-b22f-c3d9a82aaf78). As an admin, you also have additional control and capabilities around creating and setting up Early Access Class Teams.

### How do I create class teams that allow educators early access to set up a team before admitting students?

Teams created from groups (through SDS, educator-led or Graph API) automatically create early access teams by default. To create your own early access teams using Graph API, you’ll need to [create a class](https://docs.microsoft.com/graph/api/educationroot-post-classes?view=graph-rest-beta&tabs=http) and [create the team from a group](https://docs.microsoft.com/graph/api/team-post?view=graph-rest-beta&tabs=http#example-4-create-a-team-from-group).

### How do I check if a class is activated?

In the [team resource type](https://docs.microsoft.com/graph/api/resources/team?view=graph-rest-beta), we added a new property, [isMembershipLimitedToOwners](https://docs.microsoft.com/graph/api/resources/team?view=graph-rest-beta#properties), to determine whether a class is activated. Use the [Get Team API](https://docs.microsoft.com/graph/api/team-get?view=graph-rest-beta&tabs=http) to query the ```isMembershipLimitedToOwners``` property for a specific class. If the team is activated, it will return a value of false. If the team hasn't been activated by the team owner, it will return a value of true.

### How do I activate a class for an educator?

Use the [Update Team API](https://docs.microsoft.com/graph/api/team-update?view=graph-rest-beta&tabs=http) and set the ```isMembershipLimitedToOwners``` property to  false to activate the team on your educator’s behalf. Note that after a team is activated, it can't be reversed.