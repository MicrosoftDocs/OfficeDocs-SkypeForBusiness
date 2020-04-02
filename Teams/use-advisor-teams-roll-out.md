---
title: Use Advisor for Teams (public preview) to help you roll out Microsoft Teams
author: lolajacobsen
ms.author: lolaj
ms.reviewer: brandber
manager: serdars
ms.topic: article
ms.service: msteams
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
- remotework
search.appverid: MET150
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Priority
f1.keywords:
- CSH
ms.custom: 
- ms.teamsadmincenter.deploymentadvisor.overview
ms.custom:
description: "Use Advisor for Teams (public preview) to help you plan and complete your Microsoft Teams deployment."
---

# Use Advisor for Teams to help you roll out Microsoft Teams

[!INCLUDE [preview-feature](includes/preview-feature.md)]

Advisor for Teams (public preview) walks you through your Microsoft Teams rollout. It assesses your Office 365 tenant environment and identifies the most common configurations that you may need to update or modify before you can successfully roll out Teams. Then, Advisor for Teams creates a Deployment team (in Teams), with channels for each workload you want to roll out. Each workload in the Deployment team comes with a comprehensive Planner plan that includes all the rollout tasks for each workload.  Using this Planner plan, you'll assign tasks to the people responsible for each phase of the rollout - including the project manager, Teams and Office 365 admins, support people, and your adoption and user readiness team. Each rollout task contains all the guidance and resources you need to successfully complete the task.

Advisor for Teams is part of the [Teams admin center](https://admin.teams.microsoft.com). At a minimum, you'll need an Office 365 Business Essentials license so you can take advantage of the Advisor for Teams integration with Forms and Planner. To begin using Advisor for Teams, click the **Start** button in the **Deploying Teams workload** widget on the Dashboard. Or go to **Planning** > **Teams Advisor**.

> [!IMPORTANT]
> Advisor for Teams isn't available for Microsoft 365 Government - GCC High or DoD deployments.

For a guided overview of the Advisor for Teams experience, check out the [Deploy & Configure Microsoft Teams](https://youtu.be/o2mlsUubIO4?t=50) Microsoft Mechanics video.

## Using Advisor for Teams (public preview)

**Teams, Forms, and Planner licenses are required to use Advisor for Teams.** However, you don't have to be a Teams admin to use Advisor for Teams - anybody in your organization can use it. We've set up special permissions so non-admin users can get to Advisor for Teams, even though it's in the Teams admin center. You DO have to be a Teams admin, Teams Service Administrator, or Global Administrator to open the tenant readiness assessments (this is because the special non-admin roles don't have access to the Microsoft Graph APIs underlying the assessments).

> [!IMPORTANT]
> If **Teams Advisor** is missing under **Planning** in the Teams admin center, it means the user isn't licensed for Teams. This behavior will change in the future.

The first time you use Advisor for Teams, it'll create a Deployment team for you in Teams. It adds a channel for each workload you select.

> [!IMPORTANT]
> If a Deployment team has already been created and a different user tries to create it, they'll get an error telling them to contact the support team. This prevents Teams from unintentionally disclosing information about the existing team and its members. Ask the owner of the Deployment team to add you, or contact your support person for help.

## Available Advisor for Teams plans

While Advisor for Teams is in public preview, we're providing the following two plans:

1. Chat, teams, channels, and apps
    - Tenant assessment
    - Planner plan, including adoption tasks
    - Forms user survey
    - Advisor for Teams bot
1. Meetings and conferencing
    - Tenant assessment
    - Planner plan, including adoption tasks
    - Forms user survey
    - Advisor for Teams bot

We recommend that you start with the Chat, teams, channels, and apps plan. When you're done deploying that workload, go back to Advisor for Teams and click **Add channel** to start the next workload.

## Tenant assessment
Each plan includes a tenant readiness assessment that you can use to quickly identify aspects of your environment that may need remediation before you roll out Teams. The assessments include prerequisites and best practices. Each assessment test will have a green check mark or an orange warning triangle. 

- <sub><img src="media/use-advisor-teams-roll-out-image2.png" alt="Green check mark"/></img></sub>A green check mark means your tenant passed the specific test. 
- <sub><img src="media/use-advisor-teams-roll-out-image1.png" alt="Yellow alert mark"/></img></sub>An orange warning triangle means that we suggest you follow up to determine if any action is needed (for example, an Office 365 Group expiration policy is recommended but not required).

> [!IMPORTANT]
> Once a user with an Administrative role starts Advisor for Teams, all assessments run in the background. If you update or remediate something, it may not be reflected in your assessments for up to 24 hours. This is temporary - as soon as Advisor for Teams leaves the public preview and is generally available, the assessments will update in near real time.

The sections below describe each assessment, including whether something is a prerequisite or best practices, what each assessment checks is doing and why, and guidance for remediation as needed.

### Assessment tests for all workloads

|Assessment test  |What it tells you  |
|---------|---------|
|Vanity domain configured     |Whether there's a non-@onmicrosoft.com domain configured for your tenant (for example, @contoso.onmicrosoft.com). You can use the @onmicrosoft.com domain, of course, or you can configure a vanity domain - your choice. For more information, read [Add a domain to Office 365](https://docs.microsoft.com/office365/admin/setup/add-domain). |
|Teams licenses     |This is a prerequisite - you **must have** Teams licenses in order to roll out Teams. Queries the Microsoft Graph to see whether you have Teams licenses (with at least one license available to assign). For more information, read [Office 365 licensing for Teams](https://docs.microsoft.com/microsoftteams/office-365-licensing).    |
|Exchange Online licenses     |Whether you have an active subscription with available Exchange Online licenses. While Exchange isn't required for basic Teams functionality, integration with Exchange provides an optimal Teams experience. Queries the Microsoft Graph to analyze the subscriptions associated with your tenant and validate whether you have subscriptions with an eligible Exchange Online license (with at least one license available to assign). For more information, read [How Exchange and Teams interact](exchange-teams-interact.md).    |
|SharePoint Online licenses     |Whether you have an active subscription with available SharePoint Online licenses. We recommend per-user SharePoint Online licenses to provide OneDrive for Business for file storage in chats. Queries the Microsoft Graph to see whether you have SharePoint Online licenses (with at least one license available to assign). For more information, read [How SharePoint Online and OneDrive for Business interact with Teams](https://docs.microsoft.com/microsoftteams/sharepoint-onedrive-interact).    |
|Guest access enabled     |Whether [guest access](guest-access.md) is turned on. Guest access lets you invite external users to your join your teams. Use the [Teams guest access checklist](guest-access-checklist.md) to walk through turning on guest access in Teams; the checklist includes the required Azure AD configurations. |
|External access configured     |Whether [external access](manage-external-access.md) is turned on. By default, it's turned on, with open federation. |

### Assessments for chat, teams, channels, and apps

In addition to the [Assessment tests for all workloads](#assessment-tests-for-all-workloads), the following additional assessments are run for the chat, teams, channels, and apps workload:

|Assessment test  |What it tells you  |
|---------|---------|
|Office 365 Group naming policy configured     |Whether naming standards have been configured for Office 365 Groups. Office 365 Groups naming policy enables your organization to apply a consistent naming strategy to user-created teams and also applies to other Groups workloads (including Outlook, SharePoint, Planner, and Yammer). This test queries Azure AD via the Microsoft Graph to check for the existence of naming policies that apply to Office 365 Groups. For more information, read [Office 365 Group naming policy](https://docs.microsoft.com/office365/admin/create-groups/groups-naming-policy).    |
|Office 365 Group Expiration Policy configured     |Whether a Group Expiration Policy has been defined for Office 365 Groups. This enables your organization to automatically remove inactive Teams. It's turned off by default. This test queries Azure AD via the Microsoft Graph and reports whether the value has been modified from the default. For more information, read [Office 365 Group Expiration Policy](https://docs.microsoft.com/office365/admin/create-groups/office-365-groups-expiration-policy).    |

### Assessments for meetings and conferencing

In addition to the [Assessment tests for all workloads](#assessment-tests-for-all-workloads), the following additional assessments are run for the meetings and conferencing workload:

|Assessment test  |What it tells you  |
|---------|---------|
|Audio Conferencing licenses    |Whether you have an active subscription with Audio conferencing licenses. This is a prerequisite if you're deploying Audio conferencing bridges. Queries the Microsoft Graph to see whether you have Audio Conferencing licenses (with at least one license available to assign) For more information, read [Teams add-on licensing](teams-add-on-licensing/microsoft-teams-add-on-licensing.md).    |
|Stream licenses     |Whether you have an active subscription with Microsoft Stream licenses. This is a prerequisite if you want to turn on Meeting Recording. Queries the Microsoft Graph to see whether you have Microsoft Stream licenses (with at least one license available to assign). For more information on Stream and how to turn it on, read [Teams cloud meeting recording](cloud-recording.md).

### Advisor for Teams bot

Once Advisor for Teams creates your Deployment team, the Advisor bot delivers the following message in the General channel:

>**Welcome to your Deployment team for Microsoft Teams!**
>  
>The purpose of this team is to walk you through your organization's Teams rollout by giving you all the resources you need and providing a collaboration space for the project team. Each channel created using Advisor for Teams includes a step-by-step Planner plan and other resources such as a Forms users survey that can be used throughout your rollout. At any point, you can you go back and review the tenant readiness assessment or add additional workload plans using the Teams admin center.
> 
>**Call to action** 
>- If you're new to Teams or Planner, check out our [Teams walkthrough](https://teamsdemo.office.com/) and watch the [Planner quick-start videos](https://support.office.com/article/microsoft-planner-video-training-4d71390f-08d8-4db0-84ea-92fb078687c7). 
>- Head over to your Deployment team in Teams. Select your workload channel (for example, Chat, teams, channels, and apps), and select the **Planner** tab to get started.
> 
>To learn more about Advisor for Teams, read [Use Advisor for Teams to roll out Microsoft Teams](use-advisor-teams-roll-out.md).
>

> [!IMPORTANT]
> The Advisor for Teams Bot is only used to send a welcome message to your Deployment team. No additional data is collected.

> [!IMPORTANT]
> The Advisor for Teams bot is turned on by default. Don't turn it off if you use or plan on using Advisor for Teams.

## Frequently asked questions
### What are the licensing requirements for Advisor for Teams?
At a minimum, you'll need Office 365 Business Essentials so you can take advantage of the Advisor for Teams integration with Forms and Planner.

### Can I delete the Deployment team?
After Advisor for Teams has created your Deployment team, manage the team like any other team - including the ability to delete it. Be aware that, if you don't delete the team by using the Teams admin center, the Teams admin center will show that the team still exists. This is temporary - it'll be fixed when Advisor for Teams leaves the public preview period and becomes generally available.

### Can I add or remove channels in the Deployment team?
Yes, once the Deployment team has been created, you'll manage the channels the same way as any other team.

### Can I add or remove project team members in the Deployment team?
Yes, once the Deployment team has been created, you'll manage it the same way as any other team.

### Can I modify the Planner plans?
Yes, after Advisor for Teams has created your Deployment team, you should update the Planner plan so it best supports your Teams rollout. You can modify anything - buckets, tasks, task details - just like any other Planner plan.

### Can I modify the Forms survey?
Yes, after Advisor for Teams has created your Deployment team, you can modify the Forms survey as needed.

### What information is Advisor for Teams collecting about my organization?
Advisor for Teams requests your agreement to collecting non-EUII (end user identifying information). The information that is collected is in the form of telemetry that provides feedback to Microsoft on how well Advisor for Teams is driving successful outcomes and where it may need to be improved. This same data is used to identify opportunities for Microsoft to proactively engage with your organization in an effort to assist with your deployment.

### Can I use Advisor for Teams with FastTrack?
Yes, FastTrack leverages Advisor for Teams for all customers looking to deploy Teams. They can assist with the initial setup of your Deployment team using Advisor for Teams (if required) and also provide as-needed support on specific topics during your Teams rollout.

### Can I use Advisor for Teams with a partner?
Yes, you can use Advisor for Teams while also using a deployment partner for your Teams deployment. If your partner is a CSP and manages your tenant on your behalf, they can use Advisor for Teams to create your Deployment team and assist you with executing the overall project. Additionally, you can work with any partner by adding those individuals as guests in your Deployment team, to allow them to participate as a member of the overall project team.

### How do I use Planner?
Check out [Microsoft Planner help](https://support.office.com/article/Microsoft-Planner-help-4a9a13c6-3adf-4a60-a6fc-15c0b15e16fc) and the [Planner quick-start videos](https://support.office.com/article/microsoft-planner-video-training-4d71390f-08d8-4db0-84ea-92fb078687c7). 

### How do I use Forms?
Go to the [Forms help center](https://support.office.com/forms).

## Related topics

[How to roll out Teams](How-to-roll-out-teams.md)

[Best practices for organizing teams in Teams](best-practices-organizing.md)

[Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference
) 
