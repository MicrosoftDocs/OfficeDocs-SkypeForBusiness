---
title: Cloud voice in Microsoft Teams
author: lolajacobsen
ms.author: lolaj
manager: serdars
ms.date: 01/07/2019
ms.topic: article
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
ms.reviewer: crowe
search.appverid: MET150
description: Landing page to deploying cloud voice in Teams
appliesto: 
- Microsoft Teams
---

# Cloud voice in Microsoft Teams


You've completed the [Quick start](get-started-with-teams-quick-start.md). You've rolled out Teams with [chat, teams, channels, & apps](deploy-chat-teams-channels-microsoft-teams-landing-page.md) across your organization. Maybe you've deployed [Meetings & conferencing](deploy-meetings-microsoft-teams-landing-page.md). Now you're ready to add cloud voice workloads. 

This article helps you decide whether you need to change any of the default cloud voice settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups starting with the core set of [changes you are more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, based on your organization's needs.

We recommend that all organizations work through the core decisions and then, if your organization has additional requirements, review the following material.

### Learn more about cloud voice

The following articles provide more information about deploying and using cloud voice features in Teams:

- [Cloud voice deployment](cloud-voice-deployment.md)
- [Audio Conferencing in Office 365](audio-conferencing-in-office-365.md)
- [Tutorial: Audio conferencing in Microsoft Teams](tutorial-audio-conferencing.yml)
- [Quick start guide - Configuring Calling Plans in Microsoft Teams](configuring-teams-calling-quickstartguide.md)
- [Phone System in Office 365](what-is-phone-system-in-office-365.md)

## Core deployment decisions

These are the settings that most organizations want to change (if the Teams default settings don't work for the organization).

### Audio Conferencing 

Audio Conferencing provides organizations with additional entry points to any meeting (ad hoc or scheduled) by allowing meeting participants to join via public switched telephone network (PSTN) by dialing in using a traditional landline, private branch exchange (PBX), or mobile phones. <br>

Before you plan your implementation of Audio Conferencing in Teams, review the availability of the Audio Conferencing service; see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).

Audio Conferencing licenses are available as part of an Office 365 E5 subscription or as an add-on service for an Office 365 E1 or Office 365 E3 subscription. 

|Ask yourself|Action |
|------------|-------|
|<ul><li>Which user locations or offices will implement the Audio Conferencing service?</li><li>Do I have the required licenses in place?</li></ul> |<ul><li>To see what cloud features are included in each Office 365 plan, see the [License options based on your plan](https://docs.microsoft.com/skypeforbusiness/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/office-365-business-premium-plan) articles.</li><li>For more information about Teams add-on licensing, see [Skype for Business and Microsoft Teams add-on licensing](https://docs.microsoft.com/skypeforbusiness/skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing).</li></ul>|
|||

### Audio conferencing bridge phone numbers

An audio conferencing bridge answers calls for people who are using a phone to dial in to a meeting. Bridge phone numbers can be dedicated (only used for dialing in to meetings) or shared (available for other tasks). You can set up toll and toll-free phone numbers as bridge phone numbers. You can obtain new phone numbers from Microsoft or you can transfer existing phone numbers. Also, you'll need to choose a default conferencing bridge phone number for your tenant.

For more information, see [Set up Audio Conferencing](https://docs.microsoft.com/en-us/SkypeForBusiness/audio-conferencing-in-office-365/set-up-audio-conferencing) and [Make my service decisions - Audio Conferencing](2-envision-make-my-service-decisions-audio-conferencing.md).

|Ask yourself|Action |
|------------|-------|
|<ul><li>Who in my organization needs a dedicated audio conferencing bridge phone number? </li><li>Will I obtain audio conferencing bridge phone numbers from Microsoft or will I transfer existing phone numbers?</li><li> Which number will be the tenant default conference bridge number?</li></ul>|<ul><li> To configure dedicated conferencing bridge phone numbers, see [How do you get dedicated phone numbers?](https://docs.microsoft.com/en-us/MicrosoftTeams/audio-conferencing-in-office-365#how-do-you-get-dedicated-phone-numbers) </li><li> To obtain conferencing bridge phone numbers from Microsoft, see [Assign Microsoft as the audio conferencing provider](https://docs.microsoft.com/SkypeForBusiness/audio-conferencing-in-office-365/assign-microsoft-as-the-audio-conferencing-provider?toc=/MicrosoftTeams/toc.json&bc=/microsoftteams/breadcrumb/toc.json).</li><li> To transfer existing phone numbers, see [Transfer phone numbers to Office 365](https://docs.microsoft.com/microsoftteams/transfer-phone-numbers-to-office-365?toc=/skypeforbusiness/toc.json&bc=/skypeforbusiness/breadcrumb/toc.json).</li><li> To set up a default conferencing bridge phone number, see step 2 in [Change the phone numbers on your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md#step-2---change-the-default-phone-number-of-your-conference-bridge-optional).</li></ul>|
|||

### Communications Credits 

To provide toll-free conference bridge phone numbers and to support conferencing dial-out to international phone numbers, you must set up Communications Credits for your organization. To learn more about Communications Credits, see [What are Communications Credits?](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/what-are-communications-credits).

|Ask yourself|Action |
|------------|-------|
|<ul><li>Are Communications Credits required for my Audio Conferencing implementation?</li><li>If they are required, how much should I purchase?</li><li>Do I want to configure an auto-recharge amount?</li></ul> |<ul><li> To find out if you need to set up Communications Credits, see [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).</li><li>To determine the Communications Credits amount, see [Recommended funding amounts](what-are-communications-credits.md#recommended-funding-amounts).</li><li>To configure an auto-recharge amount, see [Set up Communications Credits for your organization](what-are-communications-credits.md#recommended-funding-amounts).</li></ul> |
|||

## Phone System with Calling Plans

Phone System with Calling Plans (“Calling Plans”) gives organizations a way to modernize their workplace by enabling users to make business-related phone calls from their computers and mobile devices. To use Microsoft as your telecommunications service provider, you need to obtain Calling Plan licenses and assign them to your Phone System users. With Calling Plans, Microsoft facilitates connectivity to the PSTN. 

There are two types of Calling Plans available: Domestic Calling Plans and Domestic and International Calling Plans. For more information, see [Make my service decisions - Audio Conferencing](2-envision-make-my-service-decisions-audio-conferencing.md).

|Ask yourself|Action |
|------------|-------|
|<ul><li>Are Calling Plans available in my area?</li><li>Which user locations will have the Calling Plans service? </li><li>Do my users have Calling Plans licenses?</li><li>Do my users each have a direct inward dial (DID) phone number?</li></ul>|<ul><li> To find out if Calling Plans are available in your area, see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).</li><li>To buy and assign licenses, see [Step 2: Buy and assign licenses](set-up-calling-plans.md#step-2-buy-and-assign-licenses).</li><li>To get phone numbers, see [Step 3: Get phone numbers](set-up-calling-plans.md#step-3-get-phone-numbers). </li></ul>|
|||

### Phone numbers and emergency locations

 With Calling Plans in Office 365, every user in your organization needs to have a unique direct inward dial (DID) phone number and a corresponding validated emergency address. You can also specify an emergency location within the emergency address (for example, an office number or floor number). 

|Ask yourself|Action |
|------------|-------|
|How detailed do I want the emergency address and location information to be? |For more information, see [What are emergency locations, addresses, and call routing?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-emergency-locations-addresses-and-call-routing)

### Phone System Direct Routing

For Teams users to be able to place and receive PSTN calls, they need to be enabled for Phone System, a feature in Office 365. You can use Direct Routing to enable connectivity to the PSTN and allow people in your organization to make and receive phone calls outside of the organization over the PSTN.

|Ask yourself|Action |
|------------|-------|
|<ul><li>In which user locations or offices will I implement Phone System? </li><li>For which users will I enable Calling Plans or Direct Routing? </li><li>Do I have the required licenses for Direct Routing?</li></ul>|<ul><li>For more information about Phone System, see [What is Phone System in Office 365](what-is-phone-system-in-office-365.md).</li><li>For more information about Direct Routing, see [Make my service decisions - Phone System Direct Routing](2-envision-make-my-service-decisions-direct-routing.md).</li></ul>|
|||

### SBC considerations

You need to use certified and supported session border controllers (SBCs) that need to be paired with the Direct Routing service to provide PSTN connectivity for your users. For a list of certified SBCs, see [Supported Session Border Controllers](direct-routing-plan.md#supported-session-border-controllers-sbcs).

|Ask yourself|Action |
|------------|-------|
| Where and how will I deploy SBCs? | For more information, see [Deploy and configure the SBC](direct-routing-sbc-multiple-tenants.md#deploy-and-configure-the-sbc).|
|||

### Voice routing

You'll need to configure Phone System to route the calls to the specific SBCs for Direct Routing.

|Ask yourself|Action |
|------------|-------|
|<ul><li>What voice routing policies, PSTN usage, and voice routes do I need to create?</li><li>Which users will be assigned to the voice routing policy that I define?</li></ul> | For voice routing policy information, see [Configure Voice Routing](direct-routing-configure.md#configure-voice-routing).</li></ul> |
|||

### Calling and interop policies

Direct Routing is only supported with Microsoft Teams. To place or receive PSTN calls through Direct Routing, you need to configure the necessary policies to ensure incoming calls are received in Teams. You can configure users to set Teams as their preferred client for calls by either configuring the user for Teams Only mode or configuring Teams as the preferred calling client by assigning the TeamsCallingPolicy and the TeamsInteropPolicy.

|Ask yourself|Action |
|------------|-------|
|How will I set Teams as the preferred client for calls? |For more information, see [Calling and interop policies](2-envision-make-my-service-decisions-direct-routing.md#calling-and-interop-policies). |
|||

## Additional deployment decisions

You may want to change these settings, based on your organization's needs and configuration.

### Voicemail

Phone System voicemail, powered by Azure Voicemail services, supports voicemail deposits to Exchange mailboxes only and doesn’t support third-party email systems. Phone System voicemail includes voicemail transcription, which is enabled for all users in your organization by default. Your business needs might require that you disable voicemail transcription for specific users or everyone throughout the organization.

|Ask yourself|Action |
|------------|-------|
|<ul><li>Do I want to enable Phone System voicemail in my Calling Plans implementation?</li><li>Do I want to enable voicemail transcription for some or all of my users?</li></ul>|<ul><li>For voicemail setup procedures, see [Set up Phone System voicemail](set-up-phone-system-voicemail.md).</li><li>To turn off voicemail transcription, see [Setting voicemail policies in your organization](set-up-phone-system-voicemail.md#setting-voicemail-policies-in-your-organization).</li></ul>|
|||

### Calling identity

By default, all outbound calls use the assigned phone number as calling identity (caller ID). The recipient of the call can quickly identify the caller and decide whether to accept or reject the call.

|Ask yourself|Action |
|------------|-------|
|Do I want to mask or disable caller ID? | To change or block the caller ID, see [Set the caller ID for a user](https://docs.microsoft.com/skypeforbusiness/what-are-calling-plans-in-office-365/set-the-caller-id-for-a-user). |
|||

### Phone numbers from Microsoft

Microsoft has two types of telephone numbers available: *subscriber* (user) numbers, which can be assigned to users in your organization, and *service* numbers, available as toll and toll-free service numbers, which have higher concurrent call capacity than subscriber numbers and can be assigned to services such as Audio Conferencing, Auto Attendants, or Call Queues.

|Ask yourself|Action |
|------------|-------|
|<ul><li>Which user locations need new phone numbers from Microsoft?</li><li>Which type of telephone number (subscriber or service) do I need?</li></ul>|<ul><li> For information about getting phone numbers, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) and [Getting phone numbers for your users](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/getting-phone-numbers-for-your-users).</li><li>To help you pick the type of phone number you need, see [Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md).</li></ul>|
|||

## Dial plans

A dial plan in the Phone System feature of Office 365 is a set of normalization rules that translate dialed phone numbers into an alternate format (typically E.164 format) for call authorization and call routing.

For more information about dial plans, see [What are dial plans?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-dial-plans)

|Ask yourself|Action |
|------------|-------|
|<ul><li>Does my organization need a customized dial plan?</li><li>Which users require a customized dial plan, and which tenant dial plan should be assigned to each user?</li></ul>|<ul><li>To help determine if you need a custom dial plan, see [Planning for tenant dial plans](what-are-dial-plans.md#planning-for-tenant-dial-plans)</li><li>To add users to a customized dial plan in PowerShell, see [Create and manage dial plans](create-and-manage-dial-plans.md).</ul></li> |
|||



