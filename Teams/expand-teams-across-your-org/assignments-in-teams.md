---
title: Assignments for Teams
author: cichur
ms.author: v-cichur
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
localization_priority: Normal
appliesto: 
  - Microsoft Teams
---

# Assignments in Teams for Education

The Assignments and Grades features in Teams for Education allow educators to assign tasks, work, or quizzes to their students. Educators can manage assignment timelines, instructions, add resources to turn in, grade with rubrics, and more. They can also track class and individual student progress in the Grades tab.

[Learn more about Assignments and Grades in Teams for Education](https://support.office.com/article/microsoft-teams-5aa4431a-8a3c-4aa5-87a6-b6401abea114?ui=en-US&rs=en-IE&ad=IE#ID0EAABAAA=Assignments).

> [!Note]
> For details about Teams assignments on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

## Assignments integrations in the Microsoft Teams admin center

Using the admin settings in the Microsoft Teams admin center, you can turn features on or off for educators within your organization and their students. The following are settings related to Assignments:

<a name="#bkemaildigest"> </a>
### Weekly guardian email digest


Guardian emails are sent each weekend to parents or guardians. The email contains information about assignments from the previous week and for the upcoming week. The Parent and Guardian Sync can be setup using [School Data Sync](/schooldatasync/parent-contact-sync).

1. Import parent contact information via Parent and Guardian Sync in SDS. For instructions on how to enable Parent and Guardian Sync, see [Enabling Parent and Guardian Sync](/schooldatasync/parent-contact-sync#enabling-parent-and-guardian-sync).

2. Turn on the Guardian Setting in the Microsoft Teams admin center, as the setting is turned off by default. This will enable teachers to send out a weekly digest.

   > [!NOTE]
   > Teachers can opt-out of the digest by deselecting the setting inside their own personal class team (**Assignment Settings > Parent/Guardian Emails**).

To verify that Parents will get the email the following three items must be true:

 - Email address attached to the student profile in SDS and tagged as _Parent_ or _Guardian_. For details, see [Parent and Guardian Sync File Format](/schooldatasync/parent-contact-sync-file-format).

 - Students belong to at least one class in which e-mail is not disabled by the teacher in [assignment settings](https://support.microsoft.com/office/adjust-assignment-settings-in-your-class-team-05bb3b89-1cdf-415a-b6c7-44add0376a77).

 - The emails will contain information about assignments that had a due date in the previous week or in the upcoming week.

Default setting for this feature is - **Off**.


<a name="bkmakecode"> </a>
### MakeCode
Microsoft MakeCode is a block-based coding platform that brings computer science to life for all students. 

MakeCode is a Microsoft product that is subject to the Microsoft [terms of use](https://go.microsoft.com/fwlink/?LinkID=206977) and [privacy](https://go.microsoft.com/fwlink/?LinkId=521839) policies.

Default setting for this feature is - **Off**.

To enable MakeCode assignments in Teams, go to the **Teams Admin Center**, navigate to the **Assignments** section, and turn the MakeCode toggle option to **On**. Click **Save**. Allow a few hours for these settings to take effect.

For more information on how this feature works, see this [video demonstration](https://makecode.com/blog/teams/teams-assignments).

[Learn more about MakeCode](https://aka.ms/makecode).

<a name="#turnitin"> </a>
### Turnitin

[Turnitin](https://www.turnitin.com/) is an academic integrity service. This is a third-party product or service that is subject to its own terms and privacy policy. You are responsible for your use of any third-party products and services.

Default setting for this feature is - **Off**..

To enable Turnitin for your organization, you will need a Turnitin subscription. Then you can input the following information, which can be found in your Turnitin admin console:

  * **TurnitinApiKey**: This is a 32-character GUID found in the admin console under Integrations.
  * **TurnitinApiUrl**: This is the HTTPS URL of your Turnitin admin console.

Here are some instructions to help you obtain this information.

The **TurnitinApiUrl** is the host address of your admin console.
Example: `https://your-tenant-name.turnitin.com`

The admin console is where you can create an integration and an API key associated with the integration.

Select **Integrations** from the side menu, then select **Add Integration** and give the integration a name.

![Screenshot showing adding a new integration](./educationImages/Assignments_mopo_turnitin2.png)

The **TurnitinApiKey** will be given to you after you follow the prompts. 
Copy the API key and paste it into the Microsoft Teams admin center.  This is the only time you can view the key.

![Screenshot showing copying the API key](./educationImages/Assignments_mopo_turnitin3.png)

Upon clicking the **Save** button in the admin center for this setting, allow a few hours for these settings to take effect.

### Removing Assignments and Grades
You can use Teams policies to remove Assignments and Grades for a specific user or for your entire tenant. 

To remove Assignments and Grades for an individual user go to **Teams Admin Center**, navigate to **Teams apps > Permission policies** to create a new app permission policy definition.  When creating the new policy definition set the **Microsoft apps** policy to _Block specific apps and allow all others_ and add **Assignments** to the list of blocked applications. Once your new policy definition is saved, assign it to the appropriate users.

To remove Assignments and Grades for your entire tenant, go to **Teams Admin Center**, navigate to **Teams apps > Manage apps**, and search for and select **Assignments** from the application list. Change the status setting within the Assignment application settings page to _Blocked_. 
