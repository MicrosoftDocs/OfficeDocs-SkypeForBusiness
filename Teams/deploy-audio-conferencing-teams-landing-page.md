---
title: Audio Conferencing in Microsoft Teams
ms.reviewer: 
description: Use these deployment resources to help you roll out audio conferencing as part of the meetings workload in Microsoft Teams.
ms.topic: article
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 01/28/2019
ms.service: msteams
ms.collection:  
- Teams_ITAdmin_Help
- M365-collaboration
- M365-voice
localization_priority: Priority
search.appverid: MET150
appliesto: 
- Microsoft Teams
---
# Audio Conferencing in Microsoft Teams

Audio Conferencing is the ability to join a Teams meeting from a regular phone and dial out from a meeting to a phone number. Be sure you've reviewed [Meetings rollout](deploy-meetings-microsoft-teams-landing-page.md) as part of rolling out Audio Conferencing in your organization.

## Audio Conferencing deployment decisions

This article helps you decide whether to change any of the default Audio Conferencing settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups, starting with the core set of [changes you're more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, based on your organization's needs.

You only need to set up Audio Conferencing for people who plan to schedule or lead meetings. Meeting attendees who dial in don't need any licenses assigned to them or any other setup. Dialing in (calling in) to meetings is very useful for users who are on the road and can't attend a meeting using the Skype for Business or Teams app on their laptops or mobile devices. 


## Audio Conferencing prerequisites 

Before you can roll out Audio Conferencing for Teams, consider the following:

|Ask yourself|Action |
|------------|-------|
|Is Audio Conferencing available for my country/region?|To find out if Audio Conferencing is available for your country/region, see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).|
|Do my users have the proper licensing for Teams Audio Conferencing?|Audio Conferencing licenses are available as part of an Office 365 E5 subscription or as an add-on service for an Office 365 E1 or Office 365 E3 subscription. <ul><li>To get and assign licenses, see [Try or purchase Audio Conferencing in Office 365](https://docs.microsoft.com/SkypeForBusiness/audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365) and [Assign or remove licenses for Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</li><li> To learn more, read [Microsoft Teams add-on licensing](teams-add-on-licensing/microsoft-teams-add-on-licensing.md). </li><li>To see what cloud features are included in each Office 365 plan, see the [License options based on your plan](teams-add-on-licensing/office-365-business-premium.md) articles.</li></ul>|
|Do I need to purchase Communications Credits for the users who are assigned Audio Conferencing licenses?|To learn more, read [What are Communications Credits](what-are-communications-credits.md), then check out the [Communications Credits](#communications-credits) section below.|
|||


## Core deployment decisions

After you meet the Audio Conferencing prerequisites, complete the following tasks to configure Audio Conferencing for your users.


### Teams administrators

Teams provides a set of custom administrator roles that can be used to manage Teams for your organization. The roles provide various capabilities to administrators. 

| Ask yourself | Action |
|--------------|--------|
|Who will be assigned the Teams Communications Administrator role?|To learn more about Teams administrator roles see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md).|
|Who will be assigned the Teams Communications Support Engineer role?|To assign admin roles, see [Assign administrator and non-administrator roles to users with Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).|
|Who will be assigned the Teams Communications Support Specialist role?||
|||

### Conferencing bridges and phone numbers

Conferencing bridges let people dial into meetings using a phone. You can use the default settings for a conferencing bridge or change the phone numbers (toll and toll-free) and other settings, such as the PIN or the languages that are used.

See [Audio Conferencing in Office 365](audio-conferencing-in-office-365.md) to learn more.

|Ask yourself|Action |
|------------|-------|
|Do I need to add new conferencing bridge numbers?| To add new numbers, see [Getting service phone numbers](/microsoftteams/getting-service-phone-numbers).|
|Will I need to modify the bridge settings?|To modify the bridge settings, see [Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md).|
|Do I need to port numbers to use with audio conferencing?|To learn about porting phone numbers, read [Transfer phone numbers to Office 365](transfer-phone-numbers-to-office-365.md).|
|||


### Default and alternate languages

Teams Audio Conferencing lets you set up default and alternate languages for a conferencing bridge.

|Ask yourself|Action |
|------------|-------|
| Which languages should I choose for auto attendant greetings? | To choose languages, see [Set auto attendant languages for Audio Conferencing](https://docs.microsoft.com/SkypeForBusiness/audio-conferencing-in-office-365/set-auto-attendant-languages-for-audio-conferencing?toc=/MicrosoftTeams/toc.json&bc=/microsoftteams/breadcrumb/toc.json).|
|||

### Conferencing bridge settings 

After setting up your conferencing bridge, including default and alternate languages, you should verify that the default settings such as entry/exit notifications and PIN length are the ones you want to use. If they're not, you can change them. 

|Ask yourself|Action |
|------------|-------|
| Will attendees hear a notification when a user joins or exits a meeting? | To change these settings, see [Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md).|
|What is the required length of the PIN that a meeting organizer uses to start the meeting?||
|||

### Dial-in phone number settings for users who lead meetings

After you create your Audio Conferencing bridge, you need to set the toll and/or toll-free numbers that users who lead meetings will use.

|Ask yourself|Action |
|------------|-------|
| Which conference bridge numbers will I assign to each user who leads meetings? | To assign a dial-in phone number to a user, see [Step 7: Assign dial-in phone numbers for users who lead meetings](set-up-audio-conferencing-in-teams.md#step-7-assign-dial-in-phone-numbers-for-users-who-lead-meetings). |
|||

### Communications Credits

To provide toll-free conference bridge phone numbers and to support conferencing dial-out to international phone numbers, you must set up Communications Credits for your organization. To learn more about Communications Credits, see [What are Communications Credits?](what-are-communications-credits.md).

|Ask yourself|Action |
|------------|-------|
|Are Communications Credits required for my Audio Conferencing implementation? |To find out if you need to set up Communications Credits, see [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).|
|If they're required, how much should I purchase?|To determine the Communications Credits amount, see [Recommended funding amounts](what-are-communications-credits.md#recommended-funding-amounts).|
|Do I want to configure an auto-recharge amount?|To configure an auto-recharge amount, see [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).|
|||



## Additional deployment decisions

You may want to change these settings, based on your organization's needs and configuration.

### Outbound calling restriction policies 

As an administrator, you can use outbound call controls to restrict the type of audio conferencing and end user PSTN calls that can be made by users in your organization.

|Ask yourself|Action |
|------------|-------|
| Will I limit the type of outbound calls that are allowed? | To restrict outbound calls, see [Outbound calling restriction policies for Audio Conferencing and user PSTN calls](https://docs.microsoft.com/SkypeForBusiness/audio-conferencing-in-office-365/outbound-calling-restriction-policies?toc=/MicrosoftTeams/toc.json&bc=/microsoftteams/breadcrumb/toc.json).|
|||


### Dial plans

A dial plan, as part of Phone System in Office 365, is a set of normalization rules that translate dialed phone numbers into an alternate format (typically E.164 format) for call authorization and call routing.

For more information about dial plans, see [What are dial plans?](what-are-dial-plans.md)

|Ask yourself|Action |
|------------|-------|
|Does my organization need a customized dial plan?|To help determine if you need a custom dial plan, see [Planning for tenant dial plans](what-are-dial-plans.md#planning-for-tenant-dial-plans). |
|Which users require a customized dial plan, and which tenant dial plan should be assigned to each user?|To add users to a customized dial plan using PowerShell, see [Create and manage dial plans](create-and-manage-dial-plans.md).|
|||

### Troubleshoot meeting and call quality 

Teams gives you two ways to monitor and troubleshoot call quality problems: [Call Analytics and Call Quality Dashboard](difference-between-call-analytics-and-call-quality-dashboard.md). Call Analytics shows detailed information about the devices, networks, and connectivity related to the specific calls and meetings for each user. Call Analytics is designed to help admins and helpdesk agents troubleshoot call quality problems with specific calls, whereas the Call Quality Dashboard is designed to help admins and network engineers optimize a network. Call Quality Dashboard shifts focus from specific users and instead looks at aggregate information for an entire Teams organization. 

|Ask yourself|Action |
|------------|-------|
| Who will be responsible for monitoring and troubleshooting call quality issues? | See [Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md) for information about permission levels required to troubleshoot call quality issues.|
|||


## Next steps
- [Drive adoption](adopt-microsoft-teams-landing-page.md) of audio conferencing in your organization.
- [Roll out cloud voice](cloud-voice-landing-page.md)
- Include featured apps - such as Planner - in your initial Teams rollout. Add other [apps, bots, & connectors](deploy-apps-microsoft-teams-landing-page.md) as you drive Teams adoption.
