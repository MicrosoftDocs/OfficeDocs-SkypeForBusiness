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

Advisor for Teams (preview) walks you through your Microsoft Teams rollout. It assesses your Office 365 tenant environment and identifies anything that you need to update or modify before you can successfully roll out Teams. Then, Advisor for Teams creates a Deployment team (in Teams), with channels for each workload you want to roll out. Each workload in the Deployment team comes with a comprehensive Planner plan that includes all the rollout tasks for each workload.  Using this Planner plan, you'll assign tasks to the people responsible for each phase of the rollout - including the project manager, Teams and Office 365 admins, support people, and your adoption and user readiness team. Each rollout task contains all the guidance and resources you need to successfully complete the task.

Advisor for Teams is part of the [Teams admin center](https://admin.teams.microsoft.com). To use Advisor for Teams the first time, click the **Start** button in the **Deploying Teams workload** widget on the Dashboard. Or go to **Org-wide settings** > **Advisor**.

> [!IMPORTANT]
> Advisor for Teams isn't available for Microsoft 365 Government - GCC High or DoD deployments.

## Using Advisor for Teams (preview)

You don't have to be a Teams admin to use Advisor for Teams - anybody in your organization can use it. We've set up special permissions so non-admin users can get to Advisor for Teams, even though it's in the Teams admin center. You DO have to be a Teams admin, Teams Service Administrator, or Global Administrator to open the tenant readiness assessments.

The first time you use Advisor for Teams, it'll create a Service Management team for you in Teams. It adds channels for each workload you want to roll out. 


## Available Advisor for Teams plans

While Advisor for Teams is in preview, we're providing three plans:

1. Chat, teams, channels, and apps
    - Tenant assessment
    - Planner plan, including adoption tasks
    - Forms user survey
1. Meetings and conferencing
    - Tenant assessment
    - Planner plan, including adoption tasks
    - Forms user survey

We recommend that you start with the Chat, teams, channels, and apps plan. When you're done deploying that workload, go back to Advisor and click **Add channel** to start the next workload. 

## Tenant assessment
The workload rollout plans include a tenant readiness assessment that you can use to remediate any deficiencies in your environment before you roll out Teams. Here's what each assessment checks:

### Chat, teams, channels, and apps


|Assessment  |What it tells you  |
|---------|---------|
|Teams licenses     |Whether you have an active subscription with available Teams licenses |
|Exchange licenses     |Whether you have an active subscription with available Exchange Online licenses. While Exchange isn't required for basic Teams functionality, integration with Exchange provides an optimal Teams experience.         |
|SharePoint Online licenses     | Whether you have an active subscription with available SharePoint Online licenses. You need one SharePoint Online license per user for file storage, channel collaboration, and chat. 
|Guest access enabled     |If guest access is turned on in Teams. Azure Active Directory settings for guest access are not reviewed.   |
|Vanity domain configured     |Whether there's a non-@onmicrosoft.com domain configured for your tenant  |
|Office 365 Group naming standard configured     | Whether naming standards have been configured for Office 365 Groups        |
|Office 365 Group expiration configured     |  Whether a Group expiration policy has been defined for Office 365 Groups. If not, the value is set to never.        |
|External access configured     |If external access is turned on so you can communicate with external organizations in Teams.          |

### Meetings and conferencing


|Assessment  |What it tells you  |
|---------|---------|
|Teams licenses     |Whether you have an active subscription with available Teams licenses |
|Exchange licenses     |Whether you have an active subscription with available Exchange Online licenses. While Exchange isn't required for basic Teams functionality, integration with Exchange provides an optimal Teams experience. |
|Audio conferencing licenses    |Whether you have an active subscription with Audio conferencing licenses |
|Stream licenses     |Whether you have an active subscription with Stream licenses, which can used should Meeting Recording be desired. |
|Guest access     |If guest access is turned on in Teams. Azure Active Directory settings for guest access are not reviewed.|
|Vanity domain     |Whether there's a non-@onmicrosoft.com domain configured for your tenant.  |
|External access     |If external access is turned on so you can communicate with external organizations in Teams. |


### Advisor bot
Once Advisor creates your Deployment team, the Advisor bot delivers the following message.

>**Welcome to your Deployment team for Microsoft Teams!**
>  
>The purpose of this team is to walk you through your organization's Teams rollout by giving you all the resources you need and providing a collaboration space for the project team. Each channel created using Advisor for Teams includes a step-by-step Planner plan and other resources such as a Forms users survey that can be used throughout your rollout. At any point, you can you go back and review the tenant readiness assessment or add additional workload plans using the Teams admin center. If you have any questions about the tasks, @mention me and I'll do my best to answer your question.
> 
>**Call to action** 
>- If you're new to Teams or Planner, check out our [Teams walkthrough](http://teamsdemo.office.com/) and watch the [Planner quick-start videos](https://support.office.com/article/microsoft-planner-video-training-4d71390f-08d8-4db0-84ea-92fb078687c7). 
>- Head over to your Deployment team in Teams. Select your workload channel (for example, Chat, teams, channels, and apps), and select the **Planner** tab to get started.
> 
>To learn more about Advisor for Teams, read [Use Advisor for Teams to roll out Microsoft Teams](use-advisor-teams-roll-out.md).
>
> [!IMPORTANT]
> Advisor for Teams Bot doesn't collect any data.

## Frequently asked questions
### What are the licensing requirements for Advisor for Teams?
There are no additional licensing requirements other than being licensed for Teams.

### Can I delete the Service Management team?
After Advisor for Teams has created your Service Management team, manage the team like any other team - including the ability to delete it. Be aware that, if you don't delete the team by using the Teams admin center, it will be reported that the team exists.

### Can I add or remove channels in the Service Management team?
Yes, once the Service Management team has been created, you'll manage the channels the same way as any other team.

### Can I add or remove project team members in the Service Management team?
Yes, once the Service Management team has been created, you'll manage it the same way as any other team.

### Can I modify the Planner plans?
Yes, after Advisor for Teams has created your Service Management team, you should update the Planner plan so it best supports your Teams rollout. You can modify anything - buckets, tasks, task details - just like any other Planner plan.

### Can I modify the PowerBI dashboard?
Yes, after Advisor for Teams has created your Service Management team, you can modify the PowerBI dashboard as needed.

### Can I modify the Forms Pro survey?
Yes, after Advisor for Teams has created your Service Management team, you can modify the Forms Pro survey as needed.

### What information is Advisor for Teams collecting about my organization?
Advisor for Teams requests your agreement to collecting non-EUII (end user identifying information). The information that is collected is in the form of telemetry that provides feedback to Microsoft on how well Advisor for Teams is driving successful outcomes and where it may need to be improved. This same data is used to identify opportunities for Microsoft to proactively engage with your organization in an effort to assist with your deployment.

### Can I use Advisor for Teams with FastTrack?
Yes, FastTrack leverages Advisor for Teams for all customers looking to deploy Teams. They can assist with the initial setup of your Service Management team using Advisor for Teams (if required) and also provide as-needed support on specific topics during your Teams rollout.

### Can I use Advisor for Teams with a partner?
Yes, you can use Advisor for Teams while also using a deployment partner for your Teams deployment. If your partner is a CSP and manages your tenant on your behalf, they can use Advisor for Teams to create your Service Management team and assist you with executing the overall project. Additionally, you can work with any partner by adding those individuals as guests in your Service Management team, to allow them to participate as a member of the overall project team.

### How do I use Planner?
Check out [Microsoft Planner help](https://support.office.com/article/Microsoft-Planner-help-4a9a13c6-3adf-4a60-a6fc-15c0b15e16fc) and the [Planner quick-start videos](https://support.office.com/article/microsoft-planner-video-training-4d71390f-08d8-4db0-84ea-92fb078687c7). 

### How do I use Forms?
Go to the [Forms help center](https://support.office.com/forms).

## Related topics

[How to roll out Teams](How-to-roll-out-teams.md)