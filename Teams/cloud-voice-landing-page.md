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

Cloud voice provides Private Branch Exchange (PBX) capabilities, and options for connecting to the Public Switched Telephone Network (PSTN).

This article helps you decide whether you need to change any of the default cloud voice settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups starting with the core set of [changes you are more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, based on your organization's needs.

We recommend that all organizations work through the core decisions and then, if your organization has additional requirements, review the following material.

## Learn more about cloud voice

The following articles provide more information about deploying and using cloud voice features in Teams:

- [Phone System in Office 365](what-is-phone-system-in-office-365.md)
- [Quick start guide - Configuring Calling Plans in Microsoft Teams](configuring-teams-calling-quickstartguide.md)
- [Cloud voice deployment](cloud-voice-deployment.md)
- [Microsoft telephony solutions](https://docs.microsoft.com/en-us/SkypeForBusiness/hybrid/msft-telephony-solutions)


## Core deployment decisions

These are the settings that most organizations want to change (if the Teams default settings don't work for the organization).

## Phone System (Office 365)

Phone System is Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Office 365 cloud. With Phone System, users can make business-related calls from their computers and mobile devices.

Phone System allows you to replace your existing Private Branch Exchange (PBX) system with a set of features directly delivered from Office 365 and tightly integrated into the company’s cloud productivity experience.


|Ask yourself|Action |
|------------|-------|
|<ul><li>In which user locations or offices will I implement Phone System? </li></ul>|<ul><li>For more information about Phone System, see [What is Phone System in Office 365](what-is-phone-system-in-office-365.md).</li></ul>|
|||

## Connection to the Public Switched Telephone Network (PSTN)

To connect Phone System to the Public Switched Telephone Network (PSTN) so that users can make phone calls around the world, you can use one of the following:

- Phone System with Calling Plans - to use Microsoft as your telephony carrier
- Phone System with Direct Routing -  to connect to your own telephony carrier

### Phone System with Calling Plans

With Calling Plans, Microsoft facilitates connectivity to the Public Switched Telephone Network (PSTN). To use Microsoft as your telephony carrier, you need to obtain Calling Plan licenses and assign them to your Phone System users. 

There are two types of Calling Plans available:

- Domestic Calling Plans 
- Domestic and International Calling Plans

|Ask yourself|Action |
|------------|-------|
|<ul><li>Are Calling Plans available in my area?</li><li>Which user locations will have the Calling Plans service? </li><li>Do my users have Calling Plans licenses?</li><li>Do my users each have a direct inward dial (DID) phone number?</li></ul>|<ul><li> To find out if Calling Plans are available in your area, see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).</li><li>To buy and assign licenses, see [Step 2: Buy and assign licenses](set-up-calling-plans.md#step-2-buy-and-assign-licenses).</li><li>To get phone numbers, see [Step 3: Get phone numbers](set-up-calling-plans.md#step-3-get-phone-numbers). </li></ul>|
|||

**WHAT ABOUT QUESTIONS ABOUT WHICH TYPE OF PLAN?  DO I NEED INTERNATIONAL CALLING, ETC.?**

For more information, see [Make my service decisions - Phone System with Calling Plans](2-envision-make-my-service-decisions-phone-system.md)


#### Phone numbers and emergency locations

 With Calling Plans in Office 365, every user in your organization needs to have a unique direct inward dial (DID) phone number and a corresponding validated emergency address. You can also specify an emergency location within the emergency address (for example, an office number or floor number). 

|Ask yourself|Action |
|------------|-------|
|How detailed do I want the emergency address and location information to be? |For more information, see [What are emergency locations, addresses, and call routing?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-emergency-locations-addresses-and-call-routing)

### Phone System with Direct Routing

 With Direct Routing, you can use Phone System with virtually any telephony carrier.

|Ask yourself|Action |
|------------|-------|
|<ul><li>For which users will I enable Calling Plans or Direct Routing? </li><li>Do I have the required licenses for Direct Routing?</li></ul>|<ul><li>For more information about Direct Routing, see [Make my service decisions - Phone System Direct Routing](2-envision-make-my-service-decisions-direct-routing.md) and [Plan for Direct Routing](direct-routing-plan.md).</li></ul>|
|||

#### Session Border Controller (SBC) considerations

With Direct Routing, you connect your own Session Border Controller (SBC) directly to Phone System.  For a list of certified SBCs, see [Supported Session Border Controllers](direct-routing-plan.md#supported-session-border-controllers-sbcs).

|Ask yourself|Action |
|------------|-------|
| Where and how will I deploy SBCs? | For more information, see [Deploy and configure the SBC](direct-routing-sbc-multiple-tenants.md#deploy-and-configure-the-sbc).|
|||

#### Voice routing considerations

With Direct Routing, you'll need to configure Phone System to route the calls to the specific SBCs.

|Ask yourself|Action |
|------------|-------|
|<ul><li>What voice routing policies, PSTN usage, and voice routes do I need to create?</li><li>Which users will be assigned to the voice routing policy that I define?</li></ul> | For voice routing policy information, see [Configure Voice Routing](direct-routing-configure.md#configure-voice-routing).</li></ul> |
|||

#### Calling and interop policies

Direct Routing is only supported with Microsoft Teams. To place or receive PSTN calls through Direct Routing, you need to configure the necessary policies to ensure incoming calls are received in Teams. You can configure users to set Teams as their preferred client for calls by either configuring the user for Teams Only mode or configuring Teams as the preferred calling client by assigning the TeamsCallingPolicy and the TeamsInteropPolicy.

|Ask yourself|Action |
|------------|-------|
|How will I set Teams as the preferred client for calls? |For more information, see [Calling and interop policies](2-envision-make-my-service-decisions-direct-routing.md#calling-and-interop-policies). |
|||

## Additional deployment decisions

You may want to change settings for the following, based on your organization's needs and configuration:

- Voicemail
- Calling identity
- Phone numbers from Microsoft
- Dial plans

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

### Dial plans

A dial plan in the Phone System feature of Office 365 is a set of normalization rules that translate dialed phone numbers into an alternate format (typically E.164 format) for call authorization and call routing.

For more information about dial plans, see [What are dial plans?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-dial-plans)

|Ask yourself|Action |
|------------|-------|
|<ul><li>Does my organization need a customized dial plan?</li><li>Which users require a customized dial plan, and which tenant dial plan should be assigned to each user?</li></ul>|<ul><li>To help determine if you need a custom dial plan, see [Planning for tenant dial plans](what-are-dial-plans.md#planning-for-tenant-dial-plans)</li><li>To add users to a customized dial plan in PowerShell, see [Create and manage dial plans](create-and-manage-dial-plans.md).</ul></li> |
|||
