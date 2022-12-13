---
title: Assignments for Teams
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
search.appverid: MET150
ms.reviewer: jastark
f1.keywords: 
- CSH
ms.custom:
  - ms.teamsadmincenter.assignments.overview
  - ms.teamsadmincenter.assignments.tooltip.emaildigest
  - ms.teamsadmincenter.assignments.tooltip.makecode
  - ms.teamsadmincenter.assignments.tooltip.turnitin
description: Learn how to manage assignments in the Microsoft Teams admin center in Teams for Education.
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
---

# Assignments in Teams for Education

The Assignments and Grades features in Teams for Education allow educators to assign tasks, work, or quizzes to their students. Educators can manage assignment timelines, instructions, add resources to turn in, grade with rubrics, and more. They can also track class and individual student progress in the Grades tab.

[Learn more about Assignments and Grades in Teams for Education](https://support.office.com/article/microsoft-teams-5aa4431a-8a3c-4aa5-87a6-b6401abea114?ui=en-US&rs=en-IE&ad=IE#ID0EAABAAA=Assignments).

> [!Note]
> For details about Teams assignments on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

## Assignments integrations in the Microsoft Teams admin center

Using the admin settings in the Microsoft Teams admin center, you can turn features on or off for educators within your organization and their students.

To view and manage Assignment settings, go to <a href="https://admin.teams.microsoft.com/education/assignments-settings" target="_blank">**Education** > **Assignment settings**</a> in the Teams admin center.

The following are settings related to Assignments:

<a name="#bkemaildigest"> </a>

### Weekly guardian email digest

Guardian emails are sent each weekend to parents or guardians. The email contains information about assignments from the previous week and for the upcoming week. The Parent and Guardian Sync can be setup using [School Data Sync](/schooldatasync/parent-contact-sync).

1. Import parent contact information via Parent and Guardian Sync in SDS. For instructions on how to enable Parent and Guardian Sync, see [Enabling Parent and Guardian Sync](/schooldatasync/parent-contact-sync#enabling-parent-and-guardian-sync).

2. Turn on the Guardian Setting in the Microsoft Teams admin center, as the setting is turned off by default. This will enable teachers to send out a weekly digest.

   > [!NOTE]
   > Teachers can opt-out of the digest by deselecting the setting inside their own personal class team (**Assignment Settings > Parent/Guardian Emails**).

To verify that Parents will get the email, the following three items must be true:

- Email address attached to the student profile in SDS and tagged as _Parent_ or _Guardian_. For details, see [Parent and Guardian Sync File Format](/schooldatasync/parent-contact-sync-file-format).

- Students belong to at least one class in which e-mail isn't disabled by the teacher in [assignment settings](https://support.microsoft.com/office/adjust-assignment-settings-in-your-class-team-05bb3b89-1cdf-415a-b6c7-44add0376a77).

- The emails will contain information about assignments that have a due date from the previous week or in the upcoming week.

Default setting for this feature is - **Off**.

<a name="bkmakecode"> </a>

### MakeCode

Microsoft MakeCode is a block-based coding platform that brings computer science to life for all students.

MakeCode is a Microsoft product that is subject to the Microsoft [terms of use](https://go.microsoft.com/fwlink/?LinkID=206977) and [privacy](https://go.microsoft.com/fwlink/?LinkId=521839) policies.

Default setting for this feature is - **Off**.

To enable MakeCode assignments in Teams, go to the **Teams Admin Center**, navigate to the **Assignments** section, and turn the MakeCode toggle option to **On**. Select **Save**. Allow a few hours for these settings to take effect.

For more information on how this feature works, watch this [video demonstration](https://makecode.com/blog/teams/teams-assignments).

[Learn more about MakeCode](https://aka.ms/makecode).

<a name="#turnitin"> </a>

### Turnitin

[Turnitin](https://www.turnitin.com/) is an academic integrity service. This is a third-party service that is subject to its own terms and privacy policy. You're responsible for your use of any third-party products and services.

Default setting for this feature is - **Off**.

To enable Turnitin for your organization, you'll need a Turnitin subscription. Then, you can input the following information, which can be found in your Turnitin admin console:

- **TurnitinApiKey**: This is a 32-character GUID found in the admin console under Integrations.
- **TurnitinApiUrl**: This is the HTTPS URL of your Turnitin admin console.

Here are some instructions to help you obtain this information.

The **TurnitinApiUrl** is the host address of your admin console.
Example: `https://your-tenant-name.turnitin.com`

The admin console is where you can create an integration and an API key associated with the integration.

Select **Integrations** from the side menu, then select **Add Integration** and give the integration a name.

![Screenshot showing adding a new integration.](./educationImages/Assignments_mopo_turnitin2.png)

The **TurnitinApiKey** will be given to you after you follow the prompts.
Copy the API key and paste it into the Microsoft Teams admin center.  This is the only time you can view the key.

![Screenshot showing copying the API key.](./educationImages/Assignments_mopo_turnitin3.png)

Upon clicking the **Save** button in the admin center for this setting, allow a few hours for these settings to take effect.

## Assignments data

Assignments stores information that is generated both by teachers and students. All the data is co-shared between teacher and the specific student for which the information is intended in class. There are two stores of this data, SharePoint and outside of SharePoint.

>[!NOTE]
>The same rules also apply to first-party integrations such as Reading Progress.

### Assignments data in SharePoint document libraries

Students' files associated with a Submission for Assignment are stored in a document library (named: *Student Work*). Files associated with Assignments that are created by teachers and accessible by Students are stored in another document library (named: *Class Files*) in the corresponding Class Team SharePoint site. First-party integrations may also store Assignments data in the same corresponding Class Team SharePoint site (named: *Assignments title + time stamp*).

#### Files associated with the student

IT admins can use the Content Search tool to search for student files (*Student Work*, *Class Files*, or other 1st-party integration files) that are related to assignment submissions and files that are related to assignments. For example, an admin could search all SharePoint sites in the organization and use the student's name and class or assignment name in the search query to find data relevant to a data subject request (DSR).

#### Files associated with the teacher

IT admins can use the Content Search tool to search for teacher files (*Student Work*, *Class Files*, or other 1st-party integration files) that are related to assignments and files distributed to students by the teachers within a class on assignments. For example, an admin could search all SharePoint sites in the organization and use the teacher's name and class or assignment name in the search query to find data relevant to a DSR.

### Assignments data outside of SharePoint document libraries

Some data related to Assignments isn't stored in the class team SharePoint site, which means it's not discoverable with Content Search. This includes:

- Student grades and feedback from the teacher
- The list of documents submitted for an assignment by each student
- Assignment details like Due Date, etc.
- First-party integration data like Reading Progress passages or student pronunciation data

For this type of data, an IT admin or data owner, such as a teacher, may have to go into the assignment in the class team to find data relevant to a DSR. The admin can add themselves as an owner to the class and view all the assignments for that class team.

>[!NOTE]
>If a student is no longer part of the class, their data might still be present in the class as *no longer enrolled*. The student will have to provide the tenant admin the list of such classes that they were ever a part of.

### Bulk Export assignment data outside of SharePoint document libraries

#### For a student

To bulk export a single student's data, before removing the student from the classes they're part of, [run the script](/microsoft-365/education/deploy/configure-assignments-for-teams) and provide the ``userId``. If the student has been removed from the site, either the admin can add the student back to the class before running the script, or the admin can provide the ``userId`` and the ``classId`` that the student was ever a part of.

The data about the student submissions will be exported.

#### For a teacher

Bulk Export assignment data works the same way for a student, but all submissions that the teacher has access to will be exported.

### Bulk Delete assignment data outside of SharePoint document libraries

#### For a student

To bulk delete a single student's data, before removing the student from the classes they're part of, [run the script](/microsoft-365/education/deploy/configure-assignments-for-teams) and provide the ``userId``. If the student has been removed from the site, either the admin can add the student back to the class before running the script, or the admin can provide the ``userId`` and the ``classId`` that the student was ever a part of.

Providing a ``ClassId`` will allow the admin to only delete information about the student from a specific class.

#### For a teacher

Since an assignment's data for a teacher is shared across the class, there's no bulk delete option. Instead the admin can add themselves to the class, go to the app, and delete the assignment.

For more information, see [Configure assignments for Teams](/microsoft-365/education/deploy/configure-assignments-for-teams).

## Removing Assignments and Grades

You can also use Teams policies to remove Assignments and Grades for a specific user or for your entire tenant.

To remove Assignments and Grades for an individual user, go to **Teams Admin Center** and navigate to **Teams apps > Permission policies** to create a new app permission policy definition.  When creating the new policy definition, set the **Microsoft apps** policy to _Block specific apps and allow all others_ and add **Assignments** and **Grades** to the list of blocked applications. Once your new policy definition is saved, assign it to the appropriate users.

To remove Assignments and Grades for your entire tenant, go to **Teams Admin Center**, navigate to **Teams apps > Manage apps**, and search for and select **Assignments** and **Grades** from the application list. Change the status setting within the applications' settings page to _Blocked_.

## Assignments diagnostic tool for users

Microsoft Support has created a tool to collect diagnostic data for the Microsoft engineering team to investigate issues related to the Assignments feature.

This tool can be accessed inside of Assignments on any screen the users experience an issue.

To pull up the diagnostic tool in Teams, users can:

- **On desktop and web:**
  - Select Ctrl+/
- **On mobile devices:**
  - Touch the screen with two fingers and rotate fingers 45 degrees, or
  - Tap on the screen with three fingers for 15 seconds

Once the diagnostic tool pops up, users will see a list of data that may be needed by Microsoft technical support.

The data pulled may include:

- Group ID
- Tenant ID
- Session ID
- Assignment ID
- Submission ID
- User ID

This data isn't automatically sent to Microsoft. Users need to copy and paste the data to a Microsoft support agent regarding a support ticket.

If a user pulls up the diagnostic tool then closes it, no data is sent.

When the data is sent to a Microsoft support agent, it's handled as Support Data under your organization's Microsoft 365 service agreements.

For instructions on using this diagnostic tool that you can share with educators and students, see [Get diagnostic data to troubleshoot Assignments](https://support.microsoft.com/topic/b40793f5-dbae-4c8a-841a-6baa7f232e2e).
