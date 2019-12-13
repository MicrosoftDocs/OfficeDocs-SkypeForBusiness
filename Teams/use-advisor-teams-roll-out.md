---
title: Use Advisor for Teams (preview) to help you roll out Microsoft Teams
author: lolajacobsen
ms.author: lolaj
ms.reviewer: brandber
manager: serdars
ms.topic: article
ms.service: msteams
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
search.appverid: MET150
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Priority
f1keywords: 
- ms.teamsadmincenter.deploymentadvisor.overview
ms.custom:
description: "Use Advisor for Teams (preview) to help you plan and complete your Microsoft Teams deployment."
---

# Use Advisor for Teams to help you roll out Microsoft Teams

[!INCLUDE [preview-feature](includes/preview-feature.md)]

Advisor for Teams (preview) walks you through your Microsoft Teams rollout. It assesses your Office 365 tenant environment and identifies the most common configurations that you may need to update or modify before you can successfully roll out Teams. Then, Advisor for Teams creates a Deployment team (in Teams), with channels for each workload you want to roll out. Each workload in the Deployment team comes with a comprehensive Planner plan that includes all the rollout tasks for each workload.  Using this Planner plan, you'll assign tasks to the people responsible for each phase of the rollout - including the project manager, Teams and Office 365 admins, support people, and your adoption and user readiness team. Each rollout task contains all the guidance and resources you need to successfully complete the task.

Advisor for Teams is part of the [Teams admin center](https://admin.teams.microsoft.com) and assumes an active subscription in your tenant of Office 365 Business Essentials or greater to support Forms and Planner capabilities. To begin using Advisor for Teams, click the **Start** button in the **Deploying Teams workload** widget on the Dashboard. Or go to **Planning** > **Advisor**.

> [!IMPORTANT]
> Advisor for Teams isn't available for Microsoft 365 Government - GCC High or DoD deployments.

For a guided overview of the Advisor for Teams experience, check out the [Deploy & Configure Microsoft Teams](https://youtu.be/o2mlsUubIO4?t=50) Microsoft Mechanics video.

## Using Advisor for Teams (preview)

You don't have to be a Teams admin to use Advisor for Teams - anybody in your organization can use it. We've set up special permissions so non-admin users can get to Advisor for Teams, even though it's in the Teams admin center. You DO have to be a Teams admin, Teams Service Administrator, or Global Administrator to open the tenant readiness assessments as a standard user does not have access to many of the required Microsoft Graph APIs needed to successfully run.

The first time you use Advisor for Teams, it'll create a Deployment team for you in Teams. It adds a channel for each workload you want select to roll out.

> [!IMPORTANT]
> If a Deployment Team has already been created and a different standard user was to try and create a Deployment Advisor team, a message is provided asking them to contact your support team. This was done to prevent unintentional disclosure of information about the Team and users within it.

## Available Advisor for Teams plans

While Advisor for Teams is in preview, we're providing the following two plans:

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
Each plan includes a tenant readiness assessment that you can use to quickly identify areas that may need remediate in your environment before you roll out Teams. The assessments themselves are composed of both pre-requisites and best practices. Each assessment test will either have a green check mark or an orange warning triangle. 

- A green check mark means your tenant passed the specific test. 
- A orange warning triangle means follow-up is suggested to determine if action is needed (e.g. a Office 365 Group expiration policy is recommended, however not required).

> [!IMPORTANT]
> Once a user with an Administrative role starts the Advisor for Teams experience, all assessments tests are run in the background. Should there be an assessment test that is remediated shortly after, its status may not be reflected for up to 24hrs. This will be changed as part once Advisor for Teams reached General Availability.

The sections below will describe key assessment details such as differentiation between pre-requisites and best practices, what each assessment checks is doing and why. Finally, provide guidance for remediation as needed.

### Assessment test applied to all plans

|Assessment Test  |What it tells you  |
|---------|---------|
|Vanity domain configured     |Whether there's a non-@onmicrosoft.com domain configured for your tenant. While a @onmicrosoft.com domain is perfectly fine to primarily use, customers have requested that you'd like us to check Microsoft 365 fundamentals. For more information on adding a domain to Office 365, please reference this [article](https://docs.microsoft.com/office365/admin/setup/add-domain).    |
|Teams licenses     |This is a pre-requisite test. Through querying the Microsoft Graph this test will analyze the subscriptions associated within your tenant and validate if the subscriptions contains an eligible [service plan](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference) for Teams and the availability to assign is greater than zero. For more information on licensing for Teams, please reference this [article](https://docs.microsoft.com/microsoftteams/office-365-licensing).    |
|Exchange Online licenses     |Whether you have an active subscription with available Exchange Online licenses. While Exchange is no longer required for basic Teams functionality, integration with Exchange provides an optimal Teams experience. Through querying the Microsoft Graph this step will analyze the subscriptions associated within your tenant and validate if of the subscriptions contain a eligible serviceType for Exchange Online and the availability to assign is greater than zero. For more on how Exchange Online integrates with Teams, please reference this [article](https://docs.microsoft.com/microsoftteams/exchange-teams-interact).    |
|SharePoint Online licenses     |Whether you have an active subscription with available SharePoint Online licenses. This is specifically recommended to be enabled per-user to provide OneDrive for Business storage for file storage in chats. Through querying the Microsoft Graph this test will analyze the subscriptions associated within your tenant and validate if the subscriptions contains an eligible [service plan](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference) for SharePoint Online and the availability to assign is greater than zero. For more information, please reference this [article](https://docs.microsoft.com/microsoftteams/sharepoint-onedrive-interact).    |
|Guest access enabled     |Whether [guest access](https://docs.microsoft.com/en-us/microsoftteams/guest-access), which extends your organizations collaboration reach is turned on in Teams. Use the [Microsoft Teams guest access checklist](https://docs.microsoft.com/microsoftteams/guest-access-checklist) to walk through enabling this feature in Teams and granular configuration within Azure AD.    |
|External access configured     |Whether [external access](https://docs.microsoft.com/microsoftteams/manage-external-access) is enabled. By default, it is enabled with open federation. For more information and how to configure, please reference this [article](https://docs.microsoft.com/microsoftteams/manage-external-access)

### Chat, teams, channels, and apps

|Assessment Test  |What it tells you  |
|---------|---------|
|Office 365 Group naming policy configured     |Whether naming standards have been configured for Office 365 Groups. Office 365 Groups Naming Policy enables your organization to apply a consistent naming strategy to user created teams and also applies to other groups workloads (like Outlook, SharePoint, Planner, Yammer, etc.). This test queries Azure AD via Microsoft Graph to check for the existence of naming policies that apply to Office 365 Groups. For more information and how to enable Office 365 Group Naming Policies, please reference this [article](https://docs.microsoft.com/office365/admin/create-groups/groups-naming-policy).    |
|Office 365 Group Expiration Policy configured     |Whether a Group expiration policy has been defined for Office 365 Groups. This enables your organization to automatically remove inactive Teams. It is off by default. This test queries Azure AD via Microsoft Graph to validate if the value has been modified from the default. For more information and how to configure OFfice 365 Group Expiration Policies, please reference this [article](https://docs.microsoft.com/en-us/office365/admin/create-groups/office-365-groups-expiration-policy?view=o365-worldwide).    |

### Meetings and conferencing

|Assessment Test  |What it tells you  |
|---------|---------|
|Audio conferencing licenses    |Whether you have an active subscription with Audio conferencing licenses. This is a pre-requisite should Audio conferencing bridges be needed. Through querying the Microsoft Graph this test will analyze the subscriptions associated within your tenant and validate if the subscriptions contains an eligible [service plan](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference) for Audio Conferencing and the license availability is greater than zero. For more information on licensing for Audio Conferencing, please reference this [article](https://docs.microsoft.com/microsoftteams/teams-add-on-licensing/microsoft-teams-add-on-licensing).    |
|Stream licenses     |Whether you have an active subscription with Stream licenses. This is a pre-requisite should Meeting Recording be desired. Through querying the Microsoft Graph this test will analyze the subscriptions associated within your tenant and validate if the subscriptions contains an eligible [service plan](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference) for Stream and the license availability is greater than zero. For more information on Stream and how to enable for cloud meeting recording, please reference this [article](https://docs.microsoft.com/microsoftteams/cloud-recording).

### Advisor for Teams bot

Once Advisor for Teams creates your Deployment team, the Advisor bot delivers the following message in the General Channel.

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
> The Advisor for Teams bot is enabled by default. Do not disable it if you use or plan on using Advisor for Teams.

## Frequently asked questions
### What are the licensing requirements for Advisor for Teams?
Office 365 Business Essentials is required to leverage content Advisor for Teams provides via Teams integration with Forms and Planner. 

### Can I delete the Deployment team?
After Advisor for Teams has created your Deployment team, manage the team like any other team - including the ability to delete it. Be aware that, if you don't delete the team by using the Teams admin center, it will appear that the team stills exists only in the Teams admin center. This will be addressed as Advisor for Teams reached General Availability.

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
