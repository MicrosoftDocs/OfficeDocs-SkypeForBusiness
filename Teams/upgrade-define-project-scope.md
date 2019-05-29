---
title: Project Scope Skype for Business to Microsoft Teams Adoption | Upgrade 
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: dearbeen
description: Scope your upgrade project by refining your vision and goals. 
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
MS.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

![Upgrade journey diagram, highlighting the Project Definition stage](media/upgrade-banner-project-definition.png "Stages of the upgrade journey, with emphasis on the Project Definition stage")

This article is part of the Project Definition stage of your upgrade journey, an activity you complete after you create a sponsorship coalition and project team from the stakeholders you’ve identified are key to your project’s success. Before proceeding, confirm that you’ve completed the following activities:

- [Enlisted project stakeholders](upgrade-enlist-stakeholders.md)

# Define your project scope

Taking time to define your project vision, scope, goals, and governance will help ensure all project stakeholders are aligned and working toward the same end results. This is especially critical given that the technical readiness team and user readiness team will be working independently to pull their respective pieces together. After you complete this section, refer to it throughout your project to ensure you’re on track to achieve the end state you wanted. Use the goals that you identify below to measure against your outcomes, and mitigate as needed.

| | |
|---|---|
| ![An icon depicting decision points](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>What do you want to accomplish with this project (in other words, why are you doing it)?</li><li>What does success look like?</li><li>What are the risks, and what’s your plan to mitigate those risks?</li></ul> |
| ![An icon depicting the next steps](media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Discuss the following sections with your project team and sponsors.</li><li>Document your vision, scope, goals, and risks for this project.</li><li>Revisit your project team to validate that you’ve engaged the right team.</li></ul>|

## Project vision

Your vision is the “big picture” or eventual end-state that answers the question, “Why are we doing this project?” An ideal vision addresses your organization’s business drivers and user value-add perspectives, as shown in the following examples:

- **Organization business driver**: Standardizing on Microsoft Teams aligns with our digital workplace transformation and enables us to drive operational efficiencies, eliminate redundant solutions, and save USD5 million.
- **User value-add**: Microsoft Teams (1) saves time by providing a single location for project notes, Office docs, team members, conversations, and meetings; (2) simplifies communication by using a centralized contact list and persistent chat tracking for quick access to your conversations, and (3) alleviates the frustration of trying to find that lost email attachment by storing and accessing files in one place.

Consider the following discussion points to help refine your vision:

- Description of the current business process

- Challenges with the existing business process

- How technology can help overcome these challenges

- The expected and measurable business outcomes if these challenges are overcome

> [!TIP]
> Identify use cases and personas to further refine your project vision.

## Project scope

Your vision might only be realized over time, through various phases. The project scope defines the focus of your project _at this time_ and serves to keep your project team focused on their current tasks, enabling you to realize your long-term vision. For example, your scope might call for you to run a pilot, deploy a specific workload such as voice or meetings, or enable Teams alongside Skype for Business as you plan for your upgrade over time. As part of the project scope, you should assess:

- [The various coexistence modes](https://aka.ms/SkypeToTeams-Coexist), and which would be optimal for your organization.
- The best way for Skype for Business and Teams to coexist before you move to Teams.
- Whether you should conduct a [pilot](https://aka.ms/SkypeToTeams-Pilot) to validate technical and user readiness in your organization.

## Project goals

Your goals define the outcome you want and enable you to measure the success of the project. Goals can be defined as _objectives and key results_ (OKRs), and the measures of project success can be defined as _key success indicators_ (KSIs). It’s essential that you get full participation from project stakeholders in defining OKRs and KSIs, to help ensure they feel a sense of ownership and align these measures of success to defined project tasks. Goals should include a mix of technical and user-focused success.

- **OKRs** contain the objectives you set at the beginning of the project and the key results you measure on a defined cadence (for example, monthly or quarterly). By reviewing your key results, you can ensure your project deliverables are on schedule, or identify and mitigate issues to get your project back on track. OKRs are typically categorized as “achieved” or “not achieved.”
- **KSIs** measure quality and success of the key results and complement the binary nature of OKRs by detailing good and/or bad results. When defining KSIs, we recommend that you use “specific, measurable, assignable, realistic, time-related” (SMART) criteria:
  - Specific: target a specific area for improvement
  - Measurable: quantify, or at least suggest an indicator of, progress
  - Assignable: specify who will do it
  - Realistic: state what results can realistically be achieved, given available resources
  - Time-related: specify when the results can be achieved

The following table shows examples of OKRs and KSIs for the initial phases of a Skype for Business to Teams upgrade project.

| Objective | Key result | To do |
|---|---|---|
| Pilot Teams alongside Skype for Business, in [collaboration-only mode](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md) | FY18Q2: 500-user pilot conducted and completed | <ul><li>Identify pilot users</li><li>Create a pilot test plan</li><li>Enable pilot users on Teams</li><li>Implement the pilot</li><li>Execute a pilot feedback survey</li><li>Measure pilot success</li></ul> |
| Successfully run collaboration-only mode for all users in the organization alongside Skype for Business | <ul><li>60% of Skype for Business users are using Teams within 30 days of rollout</li><li>User satisfaction with Teams is &#8805;80%</li></ul> | <ul><li>Design and execute a broad communications and training plan</li><li>Enable all users for Teams in collaboration-only mode</li><li>Track usage monthly</li><li>Gather user feedback</li><li>Monitor network health/quality</li><li>Mitigate as needed</li></ul> |

| Type | Key success indicator | How measured | Success criteria | Measured |
|---|---|---|---|---|
| **Network and quality** | Percentage of poor audio calls should be minimal | [Call Quality Dashboard (CQD)](https://aka.ms/sof-cqd) | \<3% of poor calls with Teams | Weekly, then monthly |
| **Usage and awareness** | The chat, meetings, and calling experience is equal to or better than Skype for Business | Survey | 80% agree or strongly agree | Weekly through pilot, post-rollout |
| **Usage and adoption** | Users actively use the solution | Office 365 reports or CQD | 90% participation from pilot users, better than the current solution | Weekly, then monthly |
| **Usage and training** | I had adequate training/help resources to successfully use Teams | Post-pilot survey | 80% agree or strongly agree | Post-pilot, post-rollout |
| **User satisfaction** | I would recommend Teams to others | [Net Promoter Score (NPS)](http://www.npscalculator.com/en) via post-pilot survey | NPS \> 0 | Post-pilot, post-rollout |
| **Business driver** | Cost savings | Accounts Payable | \$X million cost expenditure in third-party solutions | Six months, then one year, then five years post-rollout |

> [!TIP]
> To help ensure your project stays on track, consider defining smaller, short-term milestones in addition to bigger, long-term goals. This can include metrics that you’ll capture as part of your user pilot. When considering your timeline, use the [Microsoft 365 Roadmap](https://aka.ms/O365Roadmap) if you’re waiting for features that aren’t yet available in Teams.

## Risks and mitigation

 With any project, unforeseen events or other factors can arise and throw your project off track. It’s important to proactively assess potential risks and define a mitigation plan for overcoming the issues that might arise, so your project can continue toward your goals. A _risk register_ is an excellent tool for tracking project risks—along with how likely they are and their potential impact—and capturing your mitigation plan. The following table shows a sample risk register.

| Risk | Likelihood | Impact | Overall | Mitigation plan |
|---|---|---|---|-------|
| **Network quality** | Medium | High | High | Execute a network planning exercise. |
| **Low user adoption** | High | High | High | Proactively work with users during the pilot and deployment phases; implement a targeted awareness and training campaign to create desire. |
| | | | | |

## Timeline

As you scope your upgrade journey, be sure to set a timeline for key milestones (for example, enabling Teams alongside Skype for Business for all users) in addition to the completion date. A defined timeline helps your project team drive toward a consistent end state and informs the right work-back schedule, helping to ensure that your project stays on track. Consider a timeline that’s not too accelerated (where tasks might be overlooked) or too distant (where momentum might be lost). The ideal timeline accounts for:

- **Product readiness for compliance and user scenario requirements**: Refer to the [product roadmap](https://aka.ms/O365Roadmap) to gauge when Teams will be ready for your organization.
- **Upgrade groups**: Determine whether you’ll be enabling Teams or upgrading users by upgrade groups, which could affect the timeline of your overall upgrade journey.
- **Organizational factors such as change freeze, fiscal year end, deployment lifecycles**: Discuss and account for any internal processes that might influence your upgrade timeline.
- **Other changes that are occurring at or around the same time**: Consider bundling changes or spacing them out to facilitate a positive user experience and minimize any impact on productivity.
- **Resourcing**: Confirm resource allocation with your project stakeholders to ensure that the project team you’ve brought together has enough bandwidth to complete all necessary tasks.

As a reference point, a sample timeline is provided for the pre-upgrade, upgrade, and post-upgrade phases of the [Upgrade Pro journey](https://aka.ms/UpgradePro), which we encourage you to adjust as needed to align with the specific needs of your organization.

After you’ve completed the activities described above, you should have a solid foundation for your project. Continue with your [technical readiness](https://aka.ms/SkypeToTeams-TechnicalReadiness) and [organizational readiness](https://aka.ms/SkypeToTeams-UserReadiness) planning activities.
