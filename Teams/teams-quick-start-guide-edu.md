---
title: Quick start - Set up Microsoft Teams for Education
description: IT administrators at education institutions can use this quick start guide to deploy Microsoft Teams for Education across their organization.
author: DaniEASmith
ms.author: danismith
manager: serdars
audience: admin
level: Intermediate
displayType: one-column
ms.date: 08/30/2018
ms.reviewer: ninadara
ms.service: msteams
ms.topic: tutorial
ms.localizationpriority: medium
search.appverid: MET150
ms.collection:
  - M365-collaboration
f1.keywords:
  - CSH
ms.custom:
  - NewAdminCenter_Update
  - seo-marvel-mar2020
appliesto: 
  - Microsoft Teams
---

# Quick start - Set up Teams for Education

This guide is for **IT admins in education**, including admins who haven't yet deployed Teams.

[Microsoft Teams](https://support.office.com/article/Video-What-is-Microsoft-Teams-b98d533f-118e-4bae-bf44-3df2470c2b12) is a digital hub that brings conversations, meetings, files, and apps together in one place. Because it’s built on Microsoft 365, schools benefit from integration with their familiar Office apps and services.

It delivers enterprise-grade security and compliance that is extensible and customizable to fit the needs of every school.

With Microsoft Teams, your school or institution can:

- Create collaborative classrooms.
- Connect in professional learning communities.
- Communicate with school staff.
- Coordinate research across institutions.
- Easily facilitate student life efforts like clubs or extracurricular activities.

This guide will help you get started with:

- Turning on Teams for students.
- Learning what kind of controls are available to manage Teams within your school.
- Finding partner services through references to external documentation.

If you've already deployed Teams (as a pilot or full deployment) and are looking for pointers on how to use Teams, see [Microsoft Teams for Education](https://support.office.com/article/Microsoft-Teams-5aa4431a-8a3c-4aa5-87a6-b6401abea114).

# [Before you begin](#tab/begin)

## Before you begin

1. [Deploy School Data Sync](/SchoolDataSync) to make it easier for educators to automatically create Teams. Contact [https://aka.ms/sdssupport](https://aka.ms/sdssupport) for deployment assistance.
2. Configure the correct ports and protocols for Teams. See [Office 365 URLs and IP address ranges](office-365-urls-ip-address-ranges.md).
3. [Prepare your school's network for Teams](prepare-network.md).
4. Choose a team type. Teams for Education offers three new types of teams (for a total of four). To understand the differences and use cases of each, see [Choose a team type to collaborate in Teams](https://support.office.com/article/Choose-a-team-type-to-collaborate-in-Microsoft-Teams-0a971053-d640-4555-9fd7-f785c2b99e67).

# [Planning guide](#tab/planning)

## Teams Planning guide

### Step 1: Get your people together

Assemble a group of individuals from staff, educators, and the educator community to act as the stakeholder & decision-making group for your Teams deployment.

### Step 2:  Prioritize your scenarios

Pick the most relevant scenarios for your organization instead of talking about features and functions.

Check out the [Microsoft 365 FastTrack Productivity Library](https://fasttrack.microsoft.com/microsoft365/productivitylibrary) for examples to help you define scenarios for your school.

Successful Teams deployments often center around highly collaborative teams that work closely together, such as classrooms, professional learning communities, and extracurricular student groups.

> [!TIP]
> **Plan Teams with Teams** Customers who use Teams to plan their deployment ease their key stakeholders into using Teams. Consider creating a team called Microsoft 365 Deployment and creating channels for the various workloads you want to deploy.
>
> Teams channels you may want to create include:
>
> - Exchange.
> - Microsoft Teams.
> - Pilot Feedback.
> - SharePoint.
> - Training and Adoption.

### Step 3: Conduct pilots and deploy Teams

You’ll want to conduct an initial Teams pilot with your educators, both champions and early adopters. A pilot gives you valuable information about how Microsoft 365 and Teams are received in your school.

Select an interested group of users and a prioritized education scenario to get started.

You can create teams for:

- Classes.
- PLCs.
- Staff members.
- Anyone.

Once your pilots are complete, you’ll have the feedback you need to plan your broad Teams deployment.

Be sure your deployment plan accounts for your prioritized scenarios, ensuring your school is getting the most from Microsoft 365 and Teams.

### Step 4: Measure usage, manage satisfaction, and drive adoption

To successfully drive adoption of Microsoft 365 and Teams, stay focused on your educators' experience.

Here’s a quick checklist of our best practices to get you started.

1. **Read the [Microsoft 365 Adoption Guidance]( https://aka.ms/office365adoptionguide)** for best practices. Also available to you is our supplemental content for [creating a change management strategy for Microsoft Teams](change-management-strategy.md) to document your approach.

2. **Study [Microsoft 365 activity reports](teams-activity-reports.md)** to understand usage across your school. If you aren’t a Microsoft 365 admin, ask your admin to give you Reports Reader permissions so you can access activity reports.

3. **Capture feedback from your educators** on their experience with Microsoft 365 and Teams. Use a channel in Teams when your school has fewer than 5000 individuals. Use a public group in Yammer when your school is larger than the membership limit in Teams.

4. **Nurture your champions and highlight your wins.** Reward educators for embracing these new tools and using them in innovative ways. This ensures continued use of Microsoft 365 and Teams.

# [Turn on or off Teams licenses](#tab/licenses)

## Turn on or off Teams licenses

Once an educator or student has a valid license and Teams has been enabled, they can run the desktop, web, and mobile Teams clients.

They can install these clients themselves. The IT admin doesn't need to deploy these clients.

You can manage individual user licenses for Microsoft Teams by using the Microsoft 365 Admin Center or by using PowerShell. See [Microsoft 365 licensing for Teams](/teams-edu-licensing) for information about both methods.

# [Configure Teams](#tab/configure)

## Configure Teams for your school

You can easily manage all Teams policies in the [Microsoft Teams admin center](https://admin.teams.microsoft.com/) by signing in with your admin credentials.

[!INCLUDE [policy-wizard-edu](includes/policy-wizard-edu.md)]

We suggest that you define different policies to manage which capabilities are available to your varying user groups, like educators, students, and staff.

**To configure a policy:**

1. In the left navigation of the Teams admin center, expand the Teams feature you want to configure. For example, **Teams**, **Meetings**, or **Teams apps**.
2. Find and select the policy page from the expanded menu.
3. Select the policy you want to configure and change its settings.
4. Select **Save**.

With policies, you can turn on and off features at the per-user level. Here’s how policy assignments work:

- By default, every new user will get the Global policy (tenant-level settings).
- A user can be assigned a pre-defined user policy created by Microsoft, if it meets your requirements. These pre-defined policies aren't editable by admins. If you want to manage these policies in the future, create new custom policies, and assign the custom policies to users.
- A custom policy can be assigned to any user. To create a new custom policy, click **Add**, choose the settings you want for the policy, and click **Save**. Then, assign the custom policy to a user by going to **Users** in the Teams admin center or using a PowerShell script.

### Allow different policies for faculty and students

To have custom settings for faculty and students (for example, Chat is turned on for faculty but not for students), there are two methods to create and assign them:

- Use the PowerShell module to run a script to create, and assign multiple policies. See the [Appendix](#appendix) for script examples and documentation.
- In the Teams admin center, create a new custom policy, and assign the policy to users on the **Users** tab.

> [!NOTE]
> Until a custom policy is assigned to a user, the user will be using the Global policy setting.
>
> This means that if Chat is turned in the Global policy and turned off in the custom Student policy, until the custom policy is assigned to the student, the student can use Chat.
>
> In this case, it may be easier to turn off Chat globally and use custom policies to allow Chat for faculty.

### Use policies and settings to enforce student safety measures

To maintain student safety, you should use administrative policies to control who can use private chat and private calling, who can schedule meetings, and what content types can be shared.  

View [Keeping students safe while using Teams for distance learning](https://support.office.com/article/f00fa399-0473-4d31-ab72-644c137e11c8) for more details on what policies and setting updates you need to make it safe for students.

### Appendix

#### Create and assign a messaging policy

1. See whether any of the available policies in your tenants suit your requirements by running Get-CsTeamsMessagingPolicy.
2. If not, create a new policy by running New-CsTeamsMessagingPolicy -Identity &lt;policy name&gt; -&lt;parameter name&gt; -&lt;parameter value&gt;.

For more information, see [Set-CsTeamsMessagingPolicy](/powershell/module/skype/set-csteamsmessagingpolicy)

#### Sample script

See [PowerShell script sample - Create and assign a messaging policy](./scripts/powershell-script-teams-messaging-policy-edu.md).

# [Distribute clients](#tab/distribute)

## Distribute clients

Teams has clients available for web, desktop, and mobile. These clients all require an active internet connection and don't support an offline mode.

To get the latest details on the functionality and methods of distribution of each client, check out our topic to [Get clients for Teams](get-clients.md).

### Download clients

The setup file for the Teams client is an executable file that can be downloaded by anyone from the [Teams downloads page](https://teams.microsoft.com/downloads).

Educators and students on desktops can install the application if they have the appropriate privileges. IT Admins can also distribute the installer through their existing client distribution tools.

End users with mobile devices can download the Microsoft Teams app from the mobile platform’s app store.

### Operating system requirements

|Windows |macOS |Linux |iOS |Android |
|--------|------|------|----|--------|
|7 and later |10.10 and later |DEB or RPM |10 or later |4.4 and later |

### Internet browser support

[!INCLUDE [browser-support](includes/browser-support.md)]

# [Resources and support](#tab/resources)

## Resources, feedback, and support

For more information on getting set up with Microsoft 365, aiding Teams adoption, providing feedback, or contacting support, see these articles:

[Microsoft 365 Education deployment overview](/microsoft-365/education/deploy/)

[Share Teams adoption resources](resources-teams-edu.md)

[Send a suggestion](https://aka.ms/eduuservoice)

[Contact support](https://aka.ms/o365portal)

---
