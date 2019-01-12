---
title: Deploy Audio Conferencing in Microsoft Teams
description: Use these deployment resources to help you roll out audio conferencing in Microsoft Teams.
ms.topic: article
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 01/07/2019
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
search.appverid: MET150
appliesto: 
- Microsoft Teams
---
# Deploy Audio Conferencing in Microsoft Teams

You've completed [Quick start](get-started-with-teams-quick-start.md). You've rolled out Teams with [chat, teams, channels, & apps](deploy-chat-teams-channels-microsoft-teams-landing-page.md) across your organization. Now you're ready to add the Audio Conferencing workload. Here's how.

## Audio Conferencing service decisions

Teams provides a great out-of-the-box collaboration experience for your organization, and most organizations find that the default settings work for them. This article helps you decide whether you need to change any of the default settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups starting with the core set of [changes you are more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, again based on your organization's needs.

Calling in (dialing in) to meetings is very useful for users who are on the road and can't attend a meeting using the Skype for Business or Microsoft Teams app on their laptops or mobile devices. 

You only need to set up Audio Conferencing for people who plan to schedule or lead meetings. Meeting attendees who dial in don't need any licenses assigned to them or other setup.

## Audio Conferencing prerequisites 

Before you can deploy audio conferencing for Teams, you need to consider the following.

|Ask yourself|Action |
|------------|-------|
|<ul><li> Is Audio Conferencing available for my country/region?</li><li>Do my users have the proper licensing for Teams Audio Conferencing?</li><li>Do I need to purchase Communications Credits for the users who are assigned Audio Conferencing licenses?</li></ul> |<ul><li> To find out if Audio Conferencing is available for your country/region, see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)</li><li>To get and assign licenses, see [Try or purchase Audio Conferencing in Office 365](https://docs.microsoft.com/SkypeForBusiness/audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365) and [Assign or remove licenses for Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc). </li><li>To assign Communications Credits, see [What are Communications Credits](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/what-are-communications-credits)</li></ul> |
|||

## Core deployment decisions

After you meet the Audio Conferencing prerequisites, you can complete the following tasks to configure Audio Conferencing for your users.

### Teams administrators

Teams provides a set of custom administrator roles that can be used to manage Teams for your organization. The roles provide various capabilities to administrators. To learn more about Teams administrator roles see [Use Microsoft Teams admin roles to manage Teams](https://docs.microsoft.com/MicrosoftTeams/using-admin-roles).

|Ask yourself|Action |
|------------|-------|
|<ul><li>Who will be assigned the Teams Communications Administrator role?</li><li>Who will be assigned the Teams Communications Support Engineer role?</li><li>Who will be assigned the Teams Communications Support Specialist role?</li></ul> |<ul><li> For more information about Teams admin roles, see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md).</li><li>To assign admin roles, see [Assign administrator and non-administrator roles to users with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).</li></ul>|
|||

### Conferencing bridges and phone numbers

Conferencing bridges let people dial into meetings using a phone. You can use the default settings for a conferencing bridge or change the phone numbers (toll and toll-free) and other settings, such as the PIN or the languages that are used.

See [Audio Conferencing in Office 365](https://docs.microsoft.com/microsoftteams/audio-conferencing-in-office-365?WT.mc_id=TeamsAdminCenterCSH) for more information.

|Ask yourself|Action |
|------------|-------|
|<ul><li> Do I need to add new bridge numbers? </li><li>Will I need to modify the bridge settings?</li></ul>|<ul><li> To add new numbers, see [Getting service phone numbers](https://docs.microsoft.com/SkypeForBusiness/what-is-phone-system-in-office-365/getting-service-phone-numbers).</li><li>To modify the bridge settings, see [Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md).
|||


### Default and alternate languages

Teams Audio Conferencing lets you set up default and alternate languages for a conferencing bridge.

|Ask yourself|Action |
|------------|-------|
| Which languages should I choose for auto attendant greetings? | To choose languages see [Set auto attendant languages for Audio Conferencing](https://docs.microsoft.com/SkypeForBusiness/audio-conferencing-in-office-365/set-auto-attendant-languages-for-audio-conferencing).|
|||

### Conferencing bridge settings 

After setting up your conference bridge and default and alternate languages, you should verify that the default settings such as entry/exit notifications and PIN length are the ones you want to use. If they're not, you can change them. 

|Ask yourself|Action |
|------------|-------|
| <ul><li>Will attendees hear a notification when a user joins or exits a meeting?</li><li> What is the required length of the PIN that a meeting organizser uses to start the meeting? | To change these settings, see [Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md).|
|||

### Dial-in phone number settings for users who lead meetings

After you create your Audio Conferencing bridge, you need to set the toll and/or toll-free numbers that users who lead meetings will use.

|Ask yourself|Action |
|------------|-------|
| Which conference bridge numbers will I assign to each user who leads meetings? | To assign a dial-in phone number to a user, see [Step 7: Assign dial-in phone numbers for users who lead meetings](https://docs.microsoft.com/skypeforbusiness/audio-conferencing-in-office-365/set-up-audio-conferencing#step-7-assign-dial-in-phone-numbers-for-users-who-lead-meetings). |
|||

## Additional deployment decisions

You may want to change these settings, based on your organization's needs and configuration.

### Outbound calling restriction policies 

As an administrator, you can use outbound call controls to restrict the type of audio conferencing and end user PSTN calls that can be made by users in your organization.

|Ask yourself|Action |
|------------|-------|
| Will I limit the type of outbound calls that are allowed? | To restrict outbound calls, see [Outbound calling restriction policies for Audio Conferencing and user PSTN calls](https://docs.microsoft.com/SkypeForBusiness/audio-conferencing-in-office-365/outbound-calling-restriction-policies?toc=/MicrosoftTeams/toc.json&bc=/microsoftteams/breadcrumb/toc.json).|
|||

### Call and meeting quality 

Microsoft Teams gives you two ways to monitor and troubleshoot call quality problems: Call Analytics and Call Quality Dashboard. Call Analytics shows detailed information about the devices, networks, and connectivity related to the specific calls and meetings for each user. Where Call Analytics is designed to help admins and helpdesk agents troubleshoot call quality problems with specific calls, the Call Quality Dashboard is designed to help admins and network engineers optimize a network. Call Quality Dashboard shifts focus from specific users and instead looks at aggregate information for an entire Teams organization.

See [Call Analytics and Call Quality Dashboard](https://docs.microsoft.com/MicrosoftTeams/difference-between-call-analytics-and-call-quality-dashboard)
for more information.

|Ask yourself|Action |
|------------|-------|
| Who will be responsible for monitoring and troubleshooting call quality issues? | See [Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md) for information about permission levels required to troubleshoot call quality issues.|
|||

### Operating your meetings service 

It’s important that you understand the overall health of the Microsoft Teams service so that you can proactively alert others in your organization of any event that affects the service.

The [Operate my service](https://docs.microsoft.com/MicrosoftTeams/1-drive-value-operate-my-service) articles provide in-depth guidance for service operations.

|Ask yourself|Action |
|------------|-------|
| Who in my organization will be responsible for managing the meetings service? | <need a link here> |
|||

