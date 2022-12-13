---
title: Get started with Microsoft Teams for remote learning
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: karsmith, lakuan
description: Remote learning startup guidance for Microsoft Teams for EDU.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords: 
  - NOCSH
ms.collection: 
  - M365-collaboration
  - remotework
appliesto: 
  - Microsoft Teams
---
# Get started with Microsoft Teams for remote learning

This article covers the IT administration steps to get your educational institution set up for remote learning using Microsoft Teams.

Within Teams, **educators** can:

- Quickly converse with students.
- Share files and websites.
- Create OneNote Class Notebooks.
  - Organize interactive lessons.
  - Provide effective and timely feedback.
- Distribute and grade assignments.
- Share instructional material in Professional Learning Communities.

**Education administrators and staff** can:

- Stay up-to-date on events.
- Collaborate using Staff Teams for announcements and topical conversations.

# [Accounts & licenses](#tab/accounts)

## User accounts, licenses, and identity security

Teams uses Microsoft 365 to authenticate users and provide services. All users should have Microsoft 365 identities established to facilitate collaboration.

If user identities don't already exist, follow this process to establish them:

1. [Create users using School Data Sync](/microsoft-365/education/deploy/school-data-sync).
2. [Assign licenses to users](teams-edu-licensing.md).
3. [Create Microsoft 365 groups](Office-365-groups.md).
4. [Set up Exchange](Exchange-Teams-interact.md).
5. [Set up SharePoint and OneDrive](SharePoint-OneDrive-interact.md).
6. [Set up users who have Google email](/microsoft-365/education/deploy/enabling-teams-for-education-for-google-users).

Microsoft Teams is included in all Microsoft 365 plans, including the free A1 education plan.

For guidance on deploying Microsoft 365 and getting Teams set up, check out [Create your Microsoft 365 tenant](/microsoft-365/education/deploy/create-your-office-365-tenant).

# [Set up Teams](#tab/setup)

## Easily set up Teams

Here are the two things you need to do to get up and running with Teams:

### 1. Allow users to create teams

**By default, everyone can create Microsoft 365 groups and Teams**, but this ability may not always be appropriate.

For example, some schools may want to restrict students from creating Teams without supervision. Microsoft 365 group and team creation can be [restricted to certain security groups](/microsoft-365/admin/create-groups/manage-creation-of-groups).

For higher education institutions, we recommend allowing everyone, including students, to create teams for classes, research, group projects, and study groups.

For a walk-through of how to create Teams, see [Create a class team in Microsoft Teams](https://support.office.com/article/create-a-class-team-in-microsoft-teams-preview-fae422eb-58b7-4431-9ff2-a4b9b6ae7c5b).

### 2. Configure user experiences using policies

[!INCLUDE [policy-wizard-edu](includes/policy-wizard-edu.md)]

> [!NOTE]
> Check out [Keeping students safe in Teams for distance learning](https://support.office.com/article/f00fa399-0473-4d31-ab72-644c137e11c8).
>
> If you want to view our EDU policy recommendations, see [Teams policies and policy packages for Education](policy-packages-edu.md).

Teams policies control the capabilities available for specific users or groups. Policies can define who should be allowed to use private chat, private calling, meeting scheduling, content types that can be shared, and more.

**Higher education staff, educators, and students** can use the default (global) policies. You can adjust policies to add more functionality to Teams, including [translation capabilities](messaging-policies-in-teams.md#messaging-policy-settings) and [automatic meeting transcription](meetings-policies-recording-and-transcription.md#transcription).

**Primary-secondary school students** may need restricted capabilities. It's recommended that student policy changes be made to the 'Global (Org-wide default)' policy.

**Primary-secondary school staff and educators** should be assigned policies that grant key capabilities, like allowing private chat and meeting scheduling. [Assign these policies in bulk to your staff and educators](batch-group-policy-assignment-edu.md).

> [!IMPORTANT]
> For meeting policies assigned to any users, we recommend setting the **Automatically admit people** setting to **Everyone in your organization**. This will ensure that non-authenticated users must be admitted from the lobby before they can join Teams meetings.
>
> For more information, see [Manage meeting policies in Teams](meeting-policies-participants-and-guests.md#automatically-admit-people).

# [Class teams](#tab/class-teams)

## Create class teams for secure classroom use

Microsoft Teams for Education offers  [specific team types](https://support.office.com/article/choose-a-team-type-to-collaborate-in-microsoft-teams-0a971053-d640-4555-9fd7-f785c2b99e67)  for educational use. The [Class team type](https://support.office.com/article/create-a-class-team-in-microsoft-teams-fae422eb-58b7-4431-9ff2-a4b9b6ae7c5b) is designed for classroom use and comes with specific features that support classroom needs including:

- Assignments.
- Grades.
- OneNote classroom notebook.
- [Class Materials folder](https://support.office.com/article/Use-folders-to-create-read-only-files-for-students-or-other-team-members-0e7791d7-8c9c-4749-9bca-984289477988)  for securing read-only content for students.
- [Insights](./class-insights.md) to provide real-time data regarding student's engagement, assignments, and well-being for each classroom.
- [Early educator access](https://support.microsoft.com/article/activate-early-access-class-teams-created-with-school-data-sync-0d154696-66ab-4fcf-b22f-c3d9a82aaf78) to set up the class before students are added.
- The ability to mute disruptive students and other special permissions.

Class teams can be created through:

- [School Data Sync (SDS)](#automatic-team-creation-using-sds).
- [Educator-led creation using Microsoft 365 class groups](#educator-led-team-creation-from-microsoft-365-class-groups).
- [PowerShell scripts using Graph APIs](#powershell-script-using-graph-apis).
- [Manual team creation](#manual-team-creation).

We'll step through various options to help you choose the right deployment path that best fits your needs.

### Automatic team creation using SDS

[School Data Sync (SDS)](/SchoolDataSync) reads the data from an institution's system of record, like a Student Information System (SIS) or Learning Management system (LMS).

SDS can import data from any system of record and has built-in connectors to many [SIS vendors](/schooldatasync/frequently-asked-questions#what-sismis-vendors-does-school-data-sync-support).  

#### Benefits of SDS

- Automatically creates users and applies licenses.
- Automatically creates and maintains class teams.
- Syncs with SIS/LMS to maintain student membership changes.
- [Allows educators to prepare classes before adding students](https://support.office.com/article/activate-early-access-class-teams-created-with-school-data-sync-0d154696-66ab-4fcf-b22f-c3d9a82aaf78).
- Can automatically create security groups.
- Creates Administrative Units for scoped administrative delegation.
- [Allows Educator Password Reset](/schooldatasync/how-to-enable-teacher-password-reset).
- Has built-in cleanup capabilities to rename and archive groups and teams.
- [Syncs grades from Teams to SIS](/schooldatasync/grade-sync).
- [Protects students personal data](/schooldatasync/protecting-student-personal-data).
- Tracks and manages guardian consent.
- Provides better Education Insights data.

#### Considerations for SDS

SDS creates teams in two steps:

1. SDS creates a Microsoft 365 group in Azure Active Directory (Azure AD).
2. SDS automatically turns that group into a team.

The second step of creating teams is optional in SDS. An admin may not want to automatically create teams depending on deployment time and the number of unused teams that may result. Instead, see the [Educator-led team creation method](#educator-led-team-creation-from-microsoft-365-class-groups).  

#### Get started with SDS

To get started, go to [School Data Sync (SDS)](/SchoolDataSync) and contact [https://aka.ms/sdssupport](https://aka.ms/sdssupport) for free deployment assistance.  

### Educator-led team creation from Microsoft 365 class groups

Educator-led team creation makes it easy for educators to create the classes they need.  

This approach allows you to either use SDS to create groups for each class (recommended) or use [Graph API](/graph/api/educationroot-post-classes) to create them on your own.

After class groups are prepared, educators can convert their groups into teams:

1. Select the Teams tab in Teams.
2. At the top of the client, select the **Suggested classes** icon.

#### Benefits of educator-led team creation

- Classes are prepared and suggested but not created unless the educator intends to use them.
- For institutions with more than 500,000 teams, this method reduces the number of unnecessary teams.
- [SDS benefits](#benefits-of-sds).
- Graph API benefits.
  - Gives educators control to which classes get created.
  - Doesn't require integration with SDS.

#### Considerations for educator-led team creation

- Not fully automated and requires some educator action.
- Educators who don't have permission to create teams can still [create teams from existing groups](https://support.office.com/article/create-a-class-team-in-microsoft-teams-preview-fae422eb-58b7-4431-9ff2-a4b9b6ae7c5b).
- Graph API requires a high level of technical expertise, time to create and run the script, and time to fix any issues.

#### Get started with educator-led team creation

To get started with the SDS method, go to [School Data Sync (SDS)](/SchoolDataSync) and contact [https://aka.ms/sdssupport](https://aka.ms/sdssupport) for free deployment assistance.

- You'll need to turn the automatic team creation toggle off in your SDS profile.
- You can use a combination of automatic and educator-led team creation for class teams by using two SDS profiles.

To use the Graph API method, see [Graph API](/graph/api/educationroot-post-classes?tabs=http&view=graph-rest-1.0&preserve-view=true) and [Create a class team](/graph/api/educationroot-post-classes?tabs=http&view=graph-rest-beta&preserve-view=true).  

### PowerShell script using Graph APIs

With PowerShell, you can write a script to create teams and channels, and configure settings automatically.

This method requires the admin to [first create the group, add educators and students, and then create the team](/graph/teams-create-group-and-team).

You can also use the [Microsoft Graph API to create, configure, clone, and archive teams](/graph/api/resources/teams-api-overview).

#### Benefits of PowerShell scripts

- Gives IT admins control over class creation.
- Option to create early educator access teams or immediate student access to teams.
- [Syncs student membership changes to Azure AD group](/graph/api/team-post?tabs=http&view=graph-rest-beta#example-4-create-a-team-from-group&preserve-view=true).

#### Considerations for PowerShell scripts

- Requires a high level of technical expertise and time to create and run the script and fix any issues when creating class groups.
- No built-in error handling or retry logic.
- Membership changes aren't synced with SIS.

> [!NOTE]
> Class teams require hidden group membership so only educators and students within the class can see the members of that class. To create an Microsoft 365 class group, see [Create a class team](/graph/api/educationroot-post-classes?tabs=http&view=graph-rest-beta&preserve-view=true) to meet the privacy requirements.

### Manual team creation

Users can tailor their Teams experience by having the ability to create their own teams.

Depending on a user's permissions, they can:

- [Set up their own teams and invite users, including students](https://support.microsoft.com/article/create-a-class-team-in-microsoft-teams-fae422eb-58b7-4431-9ff2-a4b9b6ae7c5b#ID0EADAAA=Create_a_team_from_scratch).
- [Manually add users to the team](https://support.office.com/article/add-a-student-to-a-class-team-b88263bb-ace1-4702-8a48-f8a2cf4af954).
- [Share a join code](https://support.office.com/article/Create-a-link-or-a-code-for-joining-a-team-11b0de3b-9288-4cb4-bc49-795e7028296f).
- [Share a link to the team](https://support.office.com/article/Create-a-link-or-a-code-for-joining-a-team-11b0de3b-9288-4cb4-bc49-795e7028296f).

It’s best to have educators add their students to the team to ensure the students get access and are notified that they’ve been added.

#### Benefits of manual team creation

- Gives educators full control of class creation.
- Class teams are created immediately.

#### Considerations for manual team creation

- Requires educator action and time.
- Student membership isn't synced with SIS and requires manual management.
- Students will gain immediate access to class teams.

### Recommended best practices

- Deploy early to ensure everything is working reliably and ready for the first day of school.

- For issues with SDS automatic team creation, educators can use the [educator-led team creation method](#educator-led-team-creation-from-microsoft-365-class-groups) to retry. [Manual team creation](#manual-team-creation) is another solution, but classes won't sync with SIS.

- The tenant team limit is 500,000 teams. Therefore, admins should reduce the number of unused teams to avoid hitting these limits. For more information, see [Limits and specifications for Microsoft Teams](limits-specifications-teams.md).  

# [Educator early access](#tab/early-access)

## Early access to class teams

Early Access Class Teams allows educators access to their class teams before their students can view it. Educators will have time to set up, add files, and get organized before granting access to their students.

When they're ready for students to access the team, they can [activate their class](https://support.office.com/article/activate-early-access-class-teams-created-with-school-data-sync-0d154696-66ab-4fcf-b22f-c3d9a82aaf78).

### How do I create class teams that allow educators early access to set up a team before admitting students?

Teams created from groups (through SDS, educator-led or Graph API) automatically create early access teams by default.

To create your own early access teams using Graph API, you’ll need to [create a class](/graph/api/educationroot-post-classes?tabs=http&view=graph-rest-beta&preserve-view=true) and [create the team from a group](/graph/api/team-post?tabs=http&view=graph-rest-beta#example-4-create-a-team-from-group&preserve-view=true).

### How do I check if a class is activated?

In the [team resource type](/graph/api/resources/team?view=graph-rest-beta&preserve-view=true), view the property [isMembershipLimitedToOwners](/graph/api/resources/team?view=graph-rest-beta#properties&preserve-view=true), to see if a class is activated.

Use the [Get Team API](/graph/api/team-get?tabs=http&view=graph-rest-beta&preserve-view=true) to query the ```isMembershipLimitedToOwners``` property for a specific class. If the team is activated, it will return a value of false. If the team hasn't been activated, it will return a value of true.

### How do I activate a class for an educator?

Use the [Update Team API](/graph/api/team-update?tabs=http&view=graph-rest-beta&preserve-view=true), and set the ```isMembershipLimitedToOwners``` property to false to activate the team on your educator’s behalf. After a team is activated, it can't be reversed.

### Create staff teams for staff communication and collaboration

[Staff type teams](https://support.office.com/article/create-a-staff-team-in-microsoft-teams-314ac9d5-36a9-408e-8ae4-7ef20e9f1ddf) are for education administrators and staff to share information and work together on institute-wide initiatives.

Education administrators can add staff to the team with the team creation wizard, [by adding members after the team is created](https://support.office.com/article/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9), or by [sharing a join code or link to the team](https://support.office.com/article/create-a-link-or-a-code-for-joining-a-team-11b0de3b-9288-4cb4-bc49-795e7028296f).

# [Meeting scenarios](#tab/scenarios)

## Teams meeting scenarios

### Collaborative meetings for virtual classes

[Microsoft Teams meetings](./tutorial-meetings-in-teams.yml) support up to 250 concurrent attendees, including the ability to have audio, video, [content sharing](https://support.office.com/article/show-your-screen-during-a-meeting-90c84e5a-b6fe-4ed4-9687-5923d230d3a7), whiteboards, and shared notes.

Meetings can be:

- [Scheduled within the Teams client](./tutorial-meetings-in-teams.yml).
- Recorded and saved for attendees to review later.
- [Transcribed to easily find content](https://support.office.com/article/Microsoft-Stream-automatically-creates-closed-captions-for-videos-8d6ac353-9ff2-4e2b-bca1-329499455308).
- Accessed using a laptop or mobile phone webcam, microphone, and speaker.
- [Optimized for specific devices](https://products.office.com/microsoft-teams/across-devices/devices).
- Ended for all participants to ensure students aren't in a meeting unsupervised.

### District/University events or updates

Some meetings have a large audience and extra production needs. These meetings often have defined presenters, producers, and moderated Q&A.

Teams supports these sessions using [Microsoft Teams live events](teams-live-events/what-are-teams-live-events.md).

Live Events can be used for scenarios, such as:

- District or university-wide updates.
- Leadership addresses.
- Instructions for large classes or student groups.
- Extending to your community.

Learn about conducting live sessions at:

- [Plan and schedule a live event](https://support.office.com/article/video-plan-and-schedule-a-live-event-f92363a0-6d98-46d2-bdd9-f2248075e502).
- [Produce a live event](https://support.office.com/article/video-produce-a-live-event-34c89e79-ffd4-4a6a-baf6-77055e0709cb).
- [Attend a live event](https://support.office.com/article/video-attend-a-live-event-d837ad8d-ce34-44d0-9744-9beb50e943ac).
- [Moderating a Q&A](https://support.office.com/article/video-moderating-a-q-a-4984e582-8c66-4ea3-aaaf-d93cf62e1b76).

# [Resources](#tab/resources)

## Support resources

For a generic overview of transitioning to remote learning, [start here](https://www.microsoft.com/education/remote-learning)

If you're an IT admin, educator, student, or guardian, these resources may help you use Teams:

- **IT admins**
  - [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).
  - [Download and distribute Teams clients](get-clients.md).
  - [Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams).
  - [Teams for Virtualized Desktop Infrastructure](./teams-for-vdi.md).
  - [Monitor and manage call quality](monitor-call-quality-qos.md).
  - [Verify service health for Teams](service-health.md).
  - [Optimize Microsoft 365 traffic for remote staff](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571).
  - [Support contacts for Teams](/microsoft-365/admin/contact-support-for-business-products).
  - [Teams for Education webinars](https://aka.ms/TeamsEDUWebinars).

- **Educators**
  - [Help center for educators](https://support.office.com/article/microsoft-teams-5aa4431a-8a3c-4aa5-87a6-b6401abea114).
  - [Remote learning help](https://aka.ms/RemoteLearningHelp).
  - [Download Teams](get-clients.md).
  - [Teams for Education webinars](https://aka.ms/TeamsEDUWebinars).
  - [Online course for educators using Teams](https://education.microsoft.com/course/9c9f5c11/overview).
  - [Online course to craft Collaborative Learning Environments with Teams](https://education.microsoft.com/course/b1e15cfc/overview).
  - [File a support ticket](https://www.microsoft.com/microsoft-teams/download-app).

- **Students**
  - [Help center for students](https://support.office.com/article/student-help-center-395ab230-55bf-44c6-b265-e832d729b694).
  - [Remote learning help](https://aka.ms/RemoteLearningHelp).
  - [Download Teams](https://www.microsoft.com/microsoft-teams/download-app).

- **Guardians**
  - [Remote learning help](https://aka.ms/RemoteLearningHelp).
  - [Download Teams](https://www.microsoft.com/microsoft-teams/download-app).

---
