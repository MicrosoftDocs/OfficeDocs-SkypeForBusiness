---
title: Prepare to deploy Microsoft Teams cloud voice service
author: rmw2890
ms.author: MyAdvisor
manager: serdars
ms.date: 03/18/2019
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.reviewer: rowille
description: Use onboarding checklists to prepare Office 365 for Teams and configure Teams core capabilities, networking, and cloud voice workloads.
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Prepare my service

This article gives an overview of the requirements for preparing cloud voice services for your organization. By preparing properly, you can be sure you’re ready to provide cloud voice capabilities to your organization.

## Onboarding checklists for Microsoft Teams voice workloads

The following checklists walk you through the steps for implementing Audio Conferencing, Phone System with Calling Plans (“Calling Plans”), and Phone System Direct Routing (“Direct Routing”) capabilities in Microsoft Teams.

*  [Prepare Office 365 for Teams](onboarding-checklist-enable-office-365.md)

*  [Configure Teams core capabilities](onboarding-checklist-configure-microsoft-teams-core-capabilities.md)

*  [Configure networking](onboarding-checklist-configure-networking.md)

*  [Configure cloud voice workloads in Teams](onboarding-checklist-configure-cloud-voice-workloads-in-Microsoft-Teams.md)

*  [Configure Direct Routing in Teams](onboarding-checklist-configure-direct-routing-in-Microsoft-Teams.md)

The tasks and activities in these checklists are the core “to-do” items that
apply to every deployment of cloud voice capabilities with Teams. You can
customize the checklists to include the activities and tasks that are specific
to your own Teams journey.

>[!NOTE]
>This guidance focuses solely on Calling Plans, Audio Conferencing, and Direct Routing. If you’re new to Teams, review [Overview of Microsoft Teams](teams-overview.md). For general
guidance for planning your Teams deployment, start with [Deploy chat, teams, channels, and apps in Microsoft Teams](deploy-chat-teams-channels-microsoft-teams-landing-page.md).

Use the provided checklists to track the status of each individual activity and task, and to be sure you haven’t skipped any critical steps. Each activity includes a detailed description of required actions and references to additional information that you can use to complete that activity.

Although we recommend that you follow the checklists in order, the exact sequence will depend on the scope of your deployment and the configuration and complexity of your environment. They’re organized to support either a “greenfield” Teams deployment (one with no previous Skype for Business Online presence) or migrating from Skype for Business Online to Teams. If you’re migrating from Skype for Business Online, you might have already completed some of these activities and can ignore them now.

When you’re onboarding users on a per-site basis, we highly recommended that you use the [Site Enablement Playbook for Voice (Playbook)](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/site-enablement-playbook-for-voice-(playbook).xlsx?raw=true) as a supplementary guide to these checklists.

>[!NOTE]
>Most of the configuration settings are common between Teams and Skype for
Business Online. You use the Office 365 Admin Center and Microsoft Teams admin center to configure those settings.

<table>
<tr><td><img src="media/audio_conferencing_image7.png" alt=""/> <br/>Decision points</td><td><ul><li>Who will be responsible for overseeing the completion of the onboarding checklists?</li></ul></td></tr>
<tr><td><img src="media/audio_conferencing_image9.png" alt=""/><br/>Next steps</td><td><ul><li>Download the onboarding checklists.</li><li>Work through the onboarding checklist items step-by-step in accordance with your organization’s deployment plan.</li></ul></td></tr>
</table>

<!--ENDOFSECTION-->

## Continue onboarding

After you complete these checklists, you’ll have successfully added voice capabilities to your Teams deployment.

As the next step, use the [Site Enablement Playbook for Voice (Playbook)](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/site-enablement-playbook-for-voice-(playbook).xlsx?raw=true) to help you onboard your users on each site, and help ensure that you plan and execute important site-specific activities.

-   Ready Site by Site Rollout Plan

-   Establish Service Management Process

-   Execute Testing and Remediation

<!--ENDOFSECTION-->

## Test cloud voice workloads in Teams

After you’ve defined and documented your Teams cloud voice business success and technical implementation plans as part of the Envision phase and undertaken the configuration you want in the admin center, the next step is to validate that your organization’s expectations and requirements are met through feature, functionality, and usability. You should perform this validation step before you deploy a pilot or final deployment in your production environment.

You can leverage the business success plan you defined during the Envision phase to serve as the basis for determining the activities, expectations, feature/functionality test cases, and overall scope to be evaluated during the testing phase.

## Define your testing approach

In its simplest form, your testing approach is based on your reviewing the feature capabilities of the Audio Conferencing, Calling Plans, or Direct Routing service and developing a test plan to verify that your functionality requirements are met for users in scope. The following is an example test plan for the Onboard phase of an audio conferencing implementation.


| Audio Conferencing feature to test | Results summary | Additional notes |
|------------|-----------------|------------------|
| Schedule an ad-hoc Teams meeting that contains audio conferencing dial-in information | Pass/Fail   | TBD |
| Use a phone for meeting audio by dialing into a meeting from the PSTN with the dial-in information provided | Pass/Fail | TBD |
| Join other people to an existing meeting by dialing out via the PSTN | Pass/Fail | TBD |



| Calling Plans or Direct Routing feature to test | Results summary | Additional notes |
|----------------------------------------------------|-----------------|------------------|
| Make a PSTN call by dialing a PSTN number       | Pass/Fail       | TBD |
| Receive a PSTN call by dialing your PSTN number from an external line (mobile, landline) | Pass/Fail | TBD|
| Transfer a PSTN call from one Teams user to another | Pass/Fail | TBD |


>[!TIP]
>To assist with test-case creation as a starting point, see the list
of user guidance available at [Teams Meetings and calls](https://support.office.com/article/Meetings-and-calls-d92432d5-dd0f-4d17-8f69-06096b6b48a8#bkmk_havingmeetings).

<!--ENDOFSECTION-->

## Set up cloud voice workloads for Teams

Now that you’ve defined your testing approach, the next step is configuring your service environment and users in scope for Teams cloud voice features.

For additional information, see:

- [Technical Planning for Audio Conferencing](audio-conferencing.md#technical-planning-for-audio-conferencing)

- [Set up Audio Conferencing for Microsoft Teams](set-up-audio-conferencing-in-teams.md)

- [Technical Planning for Phone System with Calling Plans](calling-plan-landing-page.md)

- [Set up Calling Plans for Skype for Business and Microsoft Teams](https://docs.microsoft.com/skypeforbusiness/what-are-calling-plans-in-office-365/set-up-calling-plans)

- [Plan Direct Routing](https://docs.microsoft.com/microsoftteams/direct-routing-plan)

- [Configure Direct Routing](https://docs.microsoft.com/microsoftteams/direct-routing-configure)

### Execute the test plan

[//]: # (Edit okay? "User" seemed a bit ambiguous to me.)
After the user environment and the service have been configured, the last step of testing includes test plan execution with focus on feature and functionality validation. 

**Audio Conferencing testing prerequisites and assumptions for users and sites in scope:**

-   Business use case definition for the Audio Conferencing service has been completed.

-   Licensing required for Audio Conferencing is available and has been assigned.

-   The list of organizational sites and user groups have been identified.

-   The list of dedicated and shared audio conferencing dial in numbers with language preference have been identified and configured.

-   [Communications Credits](what-are-communications-credits.md) (if required) have been set up for your organization.

-   Audio Conferencing conference bridge settings have been identified and configured (PIN length, entry/exit notifications, enablement notification preference).

-   Tenant conferencing policies and dial plan settings that support Audio Conferencing dial-out scenarios have been identified, configured, and applied.

-   Audio Conferencing compliance requirements have been identified and configured.

**Calling Plans testing prerequisites and assumptions for users and sites in scope:**

-   Business use case definition for the Calling Plans service has been completed.

-   Licensing required for Calling Plans is available and has been assigned.

-   The list of organizational sites and user groups have been identified.

-   Phone numbers to be assigned to users have been acquired or ported to Microsoft and are available in the tenant portal.

-   [Communications Credits](what-are-communications-credits.md) (if required) have been set up for your organization.

-   Tenant user policies and dial plan settings that support Calling Plans scenarios have been identified, configured, and applied.

-   Calling Plans compliance requirements have been identified and configured.

**Direct Routing testing prerequisites and assumptions for users and sites in scope:**

-   Business use case definition for the Direct Routing service has been completed.

-   Licensing required for Direct Routing is available and has been assigned.

-   The list of organizational sites and user groups have been identified.

-   A [certified session border controller (SBC)](https://docs.microsoft.com/microsoftteams/direct-routing-plan#supported-session-border-controllers-sbcs) has been deployed, configured and paired with Phone System.

-   Enterprise voice has been enabled, and the phone numbers have been assigned.

-   Voice routing policies have been identified, configured, and assigned.

-   Microsoft Teams has been set as the preferred calling client for the users in scope.
 
-   Direct Routing compliance requirements have been identified and configured.

<table>
<tr><td><img src="media/audio_conferencing_image7.png" alt=""/> <br/>Decision points</td><td><ul><li>Decide which Audio Conferencing feature capabilities will be deployed (service decision).</li><li>Identify user functionality requirements for Audio Conferencing.</li><li>Identify service configuration requirements for Audio Conferencing.</li><br><li>Decide whether Direct Routing or Calling Plans will be deployed and configured.<li>Decide which Phone System feature capabilities will be deployed (service decision).</li><li>Identify user functionality requirements for Calling Plans or Direct Routing.</li><li>Identify service configuration requirement for Calling Plans or Direct Routing.</li></ul></td></tr>
<tr><td><img src="media/audio_conferencing_image9.png" alt=""/><br/>Next steps</td><td><ul><li>Develop and document your test plan approach.</li><li>Prepare your service environment and users in scope for Audio Conferencing features.</li><li>Prepare your service environment and users in scope for Calling Plans or Direct Routing features.</li><li>Execute test validation for the Audio Conferencing features that you want to enable.</li><li>Execute test validation for the Calling Plans or Direct Routing features that you want to enable.</li><li>For any test failures, confirm that your configuration is correct, review community articles, and—if required—raise a support case.</li></ul></td></tr>
</table>


For additional detailed guidance on how to perform testing for Audio Conferencing in Teams, see the [detailed testing guide for Audio Conferencing](onboarding-test-plan-for-enterprises-Audio-Conferencing.md).

For additional detailed guidance on how to perform testing for Calling Plans in Teams, see the [detailed testing guide for Phone System](onboarding-test-plan-for-enterprises-Phone-System.md).

<!--ENDOFSECTION-->
