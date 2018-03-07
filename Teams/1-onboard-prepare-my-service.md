---
title: Prepare to deploy Microsoft Teams cloud voice service
author: rmw2890
ms.author: MyAdvisor
manager: lehewe
ms.date: 03/13/2018
ms.topic: article
ms.service: msteams
ms.reviewer: rowille
description: Use onboarding checklists to prepare Office 365 for Teams and configure Teams core capabilities, networking, and cloud voice workloads.
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

# Prepare my service

## Onboarding checklists for Microsoft Teams voice workloads

The following checklists walk you through the steps for implementing Audio
Conferencing and Phone System with Calling Plans capabilities in Microsoft
Teams.

*  [Prepare Office 365 for Teams](https://docs.microsoft.com/MicrosoftTeams/onboarding-checklist-enable-office-365)

*  [Configure Teams core capabilities](https://docs.microsoft.com/MicrosoftTeams/onboarding-checklist-configure-microsoft-teams-core-capabilities)

*  [Configure networking](https://docs.microsoft.com/MicrosoftTeams/onboarding-checklist-configure-networking)

*  [Configure cloud voice workloads in Teams](https://docs.microsoft.com/MicrosoftTeams/onboarding-checklist-configure-cloud-voice-workloads-in-Microsoft-Teams)

The tasks and activities in these checklists are the core “to-do” items that
apply to every deployment of cloud voice capabilities with Teams. You can
customize the checklists to include the activities and tasks that are specific
to your own Teams journey.

>[!NOTE]
>This guidance focuses solely on Phone System with Calling Plans and
Audio Conferencing. If you’re new to Teams, review [Overview of Microsoft
Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview). For general
guidance for planning your Teams deployment, see the [Microsoft Teams Planning
Guide](https://docs.microsoft.com/MicrosoftTeams/quick-start-enable-teams).

Use the provided checklists to track the status of each individual activity and
task, and to be sure you haven’t skipped any critical steps. Each activity
includes a detailed description of required actions and references to additional
information that you can use to complete that activity.

Although we recommend that you follow the checklists in order, the exact
sequence will depend on the scope of your deployment and the configuration and
complexity of your environment. They’re organized to support either a
“greenfield” Teams deployment (one with no previous Skype for Business Online
presence) or migrating from Skype for Business Online to Teams. If you’re
migrating from Skype for Business Online, you might have already completed some
of these activities and can ignore them now.

When you’re onboarding users on a per-site basis, we highly recommended that you
use the [Site Enablement Playbook for Voice (Playbook)](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness-pr/blob/live/Teams/downloads/site-enablement-playbook-for-voice-(playbook).xlsx?raw=true) as a
supplementary guide to these checklists.

>[!NOTE]
>Most of the configuration settings are common between Teams and Skype for
Business Online. You use Office 365 Skype for Business Administration Center to
configure those settings.

<table>
<tr><td>![](media/audio_conferencing_image7.png) <br/>Decision points</td><td><ul><li>Who will be responsible for overseeing the completion of the onboarding checklists?</li></ul></td></tr>
<tr><td>![](media/audio_conferencing_image9.png)<br/>Next steps</td><td><ul><li>Download the onboarding checklists.</li><li>Work through the onboarding checklist items step-by-step in accordance with your organization’s deployment plan.</li></ul></td></tr>
</table>

<!--ENDOFSECTION-->

## Continue onboarding

After you complete this checklist, you’ll have successfully added voice
capabilities to your Teams deployment.

As the next step, use the [Site Enablement Playbook for Voice (Playbook)](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness-pr/blob/live/Teams/downloads/site-enablement-playbook-for-voice-(playbook).xlsx?raw=true) to help you onboard your users on each site, and help ensure that you plan
and execute important site-specific activities.

-   Ready Site by Site Rollout Plan

-   Establish Service Management Process

-   Execute Testing and Remediation

<!--ENDOFSECTION-->

## Test cloud voice workloads in Teams

After you’ve defined and documented your Teams cloud voice business success and
technical implementation plans as part of the Envision phase and undertaken the
configuration you want in the admin center, the next step is to validate that
your organization’s expectations and requirements are met through feature,
functionality, and usability. You should perform this validation step before you
deploy a pilot or final deployment in your production environment.

You can leverage the business success plan you defined during the Envision phase
to serve as the basis for determining the activities, expectations,
feature/functionality test cases, and overall scope to be evaluated during the
testing phase.

## Define your testing approach

In its simplest form, your testing approach is based on your reviewing the
feature capabilities of the Audio Conferencing or Phone System with
Calling Plans service and developing a test plan to verify that your
functionality requirements are met for users in scope. The following is an
example test plan for the Onboard phase of an audio conferencing implementation.

| Audio Conferencing feature to test | Results summary | Additional notes |
|------------|-----------------|------------------|
| Schedule an ad-hoc Teams meeting that contains audio conferencing dial-in information | Pass/Fail   | TBD |
| Use a phone for meeting audio by dialing into a meeting from the PSTN with the dial-in information provided | Pass/Fail | TBD |
| Join other people to an existing meeting by dialing out via the PSTN | Pass/Fail | TBD |


| Phone System with Calling Plans feature to test | Results summary | Additional notes |
|----------------------------------------------------|-----------------|------------------|
| Make a PSTN call to by dialing a PSTN number       | Pass/Fail       | TBD |
| Receive a PSTN call by dialing your PSTN number from an external line (mobile, landline) | Pass/Fail | TBD|
|Transfer a PSTN call from one Teams user to another | Pass/Fail | TBD |


>[!TIP]
>To assist with test-case creation as a starting point, see the list
of audio conferencing user guidance available at [Teams Meetings and
calls](https://support.office.com/article/Meetings-and-calls-d92432d5-dd0f-4d17-8f69-06096b6b48a8?ui=en-US&rs=en-US&ad=US#bkmk_havingmeetings).

<!--ENDOFSECTION-->

## Set up cloud voice workloads for Teams

Now that you’ve defined your testing approach, the next step is configuring your
service environment and users in scope for Teams cloud voice features. For
additional information, see [Technical Planning for Audio
Conferencing](https://docs.microsoft.com/microsoftteams/audio-conferencing#technical-planning-for-audio-conferencing)
and [Set up Audio Conferencing for Skype for Business and Microsoft
Teams](https://docs.microsoft.com/skypeforbusiness/audio-conferencing-in-office-365/set-up-audio-conferencing)
in addition to [Technical Planning for Phone System with Calling
Plans](https://docs.microsoft.com/microsoftteams/phone-system-with-calling-plans#technical-planning-for-phone-system-with-calling-plans)
and [Set up Calling Plans for Skype for Business and Microsoft
Teams](https://docs.microsoft.com/skypeforbusiness/what-are-calling-plans-in-office-365/set-up-calling-plans)

<!--ENDOFSECTION-->

### Execute the test plan

After the user and audio conferencing service environments have been configured,
the last step of testing includes test plan execution with focus on feature and
functionality validation. 

**Audio Conferencing testing prerequisites and assumptions for users and sites in
scope:**

-   Business use case definition for the Audio Conferencing service has
    been completed.

-   Licensing required for Audio Conferencing is available and has been
    assigned.

-   The list of organizational sites and user groups have been identified.

-   The list of dedicated and shared audio conferencing dial in numbers with
    language preference have been identified and configured.

-   [Communications
    Credits](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/what-are-communications-credits)
    (if required) have been set up for your organization.

-   Audio Conferencing conference bridge settings have been identified and
    configured (PIN length, entry/exit notifications, enablement notification
    preference).

-   Tenant conferencing policies and dial plan settings that support Audio
    Conferencing dial-out scenarios have been identified, configured, and
    applied.

-   Audio Conferencing compliance requirements have been identified and
    configured.

**Phone System with Calling Plans testing prerequisites and assumptions for users and
sites in scope:**

-   Business use case definition for the Phone System with Calling Plans
    service has been completed.

-   Licensing required for Phone System with Calling Plans is available and
    has been assigned.

-   The list of organizational sites and user groups have been identified.

-   Phone numbers to be assigned to users have been acquired or ported to
    Microsoft and are available in the tenant portal.

-   [Communications
    Credits](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/what-are-communications-credits)
    (if required) have been set up for your organization.

-   Tenant user policies and dial plan settings that support Phone System
    with Calling Plans scenarios have been identified, configured, and applied.

-   Phone System with Calling Plans compliance requirements have been
    identified and configured.

<table>
<tr><td>![](media/audio_conferencing_image7.png) <br/>Decision points</td><td><ul><li>Decide which Audio Conferencing feature capabilities will be deployed (service decision).</li><li>Identify user functionality requirements for Audio Conferencing.</li><li>Identify service configuration requirements for Audio Conferencing.</li><li>Decide which Phone System with Calling Plans feature capabilities will be deployed (service decision).</li><li>Identify user functionality requirements for Phone System with Calling Plans.</li><li>Identify service configuration requirement for Phone System with Calling Plans.</li></ul></td></tr>
<tr><td>![](media/audio_conferencing_image9.png)<br/>Next steps</td><td><ul><li>Develop and document your test plan approach.</li><li>Prepare your service environment and users in scope for Audio Conferencing features.</li><li>Prepare your service environment and users in scope for Phone System with Calling Plans features.</li><li>Execute test validation for the Audio Conferencing features that you want to enable.</li><li>Execute test validation for the Phone System with Calling Plans features that you want to enable.</li><li>For any test failures, confirm that your configuration is correct, review community articles, and—if required—raise a support case.</li></ul></td></tr>
</table>


For additional detailed guidance on how to perform testing for Audio Conferencing in Teams, see the [detailed testing guide for Audio Conferencing]  (https://docs.microsoft.com/MicrosoftTeams/onboarding-test-plan-for-enterprises-Audio-Conferencing).

For additional detailed guidance on how to perform testing for Phone System
with Calling Plans in Teams, see the [detailed testing guide for Phone System](https://docs.microsoft.com/MicrosoftTeams/onboarding-test-plan-for-enterprises-Phone-System).

<!--ENDOFSECTION-->