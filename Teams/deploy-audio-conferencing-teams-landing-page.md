---
title: Plan for Audio Conferencing in Microsoft Teams
ms.reviewer: 
description: Use these deployment resources to help you roll out Audio Conferencing for Microsoft Teams meetings.
ms.topic: article
ms.author: jenz
author: jenzamora
manager: pamgreen
audience: admin
ms.date: 2/21/2024
ms.service: msteams
ms.subservice: teams-audio-conferencing
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - M365-collaboration
  - Tier1
  - m365initiative-meetings
ms.custom: 
  - seo-marvel-mar2020
f1.keywords: 
  - NOCSH
ms.localizationpriority: high
search.appverid: MET150
appliesto: 
  - Microsoft Teams
---
# Plan for Audio Conferencing in Microsoft Teams

This article is for administrators and IT professionals who are evaluating Audio Conferencing for Teams meetings. 

Audio Conferencing enables users to join a Teams meeting from a phone using a Public Switched Telephone Network (PSTN) phone number. Audio Conferencing is sometimes called dial-in conferencing or PSTN conferencing. Audio Conferencing allows up to 1,000 phone attendees.

Audio Conferencing requires an additional Teams add-on license for each person in your organization who is going to schedule/host an Audio Conferencing meeting. (Audio Conferencing does not require a Teams Phone license.) For more information, see [Audio Conferencing prerequisites](#audio-conferencing-prerequisites).   **ADD LINK TO ADD-ON LICENSING AFTER IT'S UPDATED**

This article describes Audio Conferencing concepts and scenarios, and helps you decide whether to change any of the default Audio Conferencing settings, based on your organization's profile and business requirements.  When you're ready to deploy Audio Conferencing, see [Set up Audio Conferencing](set-up-audio-conferencing-in-teams.md).


## Audio Conferencing scenarios

Calling in (dialing in) to meetings is useful for users who are on the road and can't attend a meeting using the Microsoft Teams app on their laptops or mobile devices. But there are other scenarios in which using a phone to attend a Teams meeting can be a better option than using an app on a computer:
  
- Internet connectivity is limited.
- A meeting is audio only.
- The person tried to join a Teams meeting and it failed.
- The call quality is better when dialing in.
- People can join a meeting "hands free" using Bluetooth devices.
- People find it's easier and more convenient for their situation.

You only need to set up Audio Conferencing for people who plan to schedule or lead meetings. Meeting attendees who dial in don't need any licenses assigned to them or other setup.

After attendees join the meeting, they can also dial out and invite other callers into a Teams meeting.
For more information, see [Dial out from a Teams meeting so other people can join it](dialing-out-from-a-teams-meeting-so-other-people-can-join-it.md).




## Audio Conferencing numbers and pricing

With Audio Conferencing, your users can use toll and toll-free phone numbers to dial in to meetings. Toll (service) numbers are automatically assigned as shared Audio Conferencing numbers to organizations when they're enabled for Audio Conferencing. Dedicated toll and toll-free numbers can be assigned to your organization from other cities.

Toll-free phone numbers (service numbers) are available, but only in some countries/regions. To see what is available in your country or region, see [Country and region availability for Audio Conferencing](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).

For pricing info, see [Pricing for Audio Conferencing](https://go.microsoft.com/fwlink/?linkid=799762&clcid=0x409).



## Audio Conferencing prerequisites

Before you can roll out Audio Conferencing for Teams, consider these questions:

|Ask yourself|Action |
|------------|-------|
|Is Audio Conferencing available for my country/region?|To find out if Audio Conferencing is available for your country/region, see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).|
|Do my users have the proper licensing for Audio Conferencing?|Audio Conferencing licenses are available as part of a Microsoft 365 or Office 365 E5 . Audio conferencing licenses are also available as an add-on service for a Microsoft 365 Business Standard, E1, or E3 subscription. <ul><li>To get and assign licenses, see [Assign or remove licenses for Microsoft 365 Apps for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</li><li> To learn more, read [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md). </li><li>To see what cloud features are included in each plan, see the [License options based on your plan](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md) articles.</li></ul>|
|Do I need to purchase Communications Credits for the users who are assigned Audio Conferencing licenses?|To learn more, read [What are Communications Credits](what-are-communications-credits.md), then check out the [Communications Credits](#communications-credits) section.|
|||


## Audio Conferencing bridges

When you're setting up Audio Conferencing for Teams, you get an audio conferencing bridge. A conferencing bridge can contain one or more phone numbers. The phone number you set is included on the meeting invites for Teams apps. You can [change the phone numbers on your conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md), and you can also [change other audio conferencing bridge settings](change-the-settings-for-an-audio-conferencing-bridge.md).

The audio conferencing bridge answers a call for people who are dialing in to a meeting using a phone. It answers the caller with voice prompts from an Auto attendant, and then, depending on your settings, can play notifications and ask callers to record their name. **Microsoft bridge settings** allow you to change the settings for meeting notifications and the meeting join experience, and set the length of the PINs that are used by meeting organizers [in Microsoft Teams](set-the-pin-length-for-audio-conferencing-meetings-in-teams.md). Meeting organizers use PINs to start meetings if they can't join the meeting using the Teams app.

You can use the default settings for a conferencing bridge. You can also change the phone numbers (toll and toll-free) and other settings, such as the PIN or the languages that are used.

|Ask yourself|Action |
|------------|-------|
|Do I need to add new conferencing bridge numbers?| To add new numbers, see [Getting service phone numbers](./getting-service-phone-numbers.md).|
|Will I need to modify the bridge settings?|To modify the bridge settings, see [Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md).|
|Do I need to port numbers to use with audio conferencing?|To learn about porting phone numbers, read [Transfer phone numbers to Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md).|
|||


### Phone numbers for Audio Conferencing bridges

There are two types of phone numbers that can be assigned to your conferencing bridge: 

- [**Dedicated numbers**](#dedicated-phone-numbers) available only to users with your organization
- [**Shared numbers**](#shared-phone-numbers) that can be shared wiht users in other Microsoft 365 organizations

The default audio conferencing number assigned to an organizer is included only in the meeting invite. However, a caller can use any of the phone numbers assigned to your conferencing bridge to join a meeting. You can find the list of phone numbers available for joining a meeting using the **Find a local number** link included on every meeting invite.

For more information, see [Phone numbers for Audio Conferencing in Microsoft Teams](phone-numbers-for-audio-conferencing-in-teams.md).

#### Dedicated phone numbers
  
Dedicated phone numbers are service numbers that are only available to users within your organization. You can change the languages that are used when someone calls in to one of these numbers.

You can get dedicated toll and toll-free phone numbers for your conferencing bridges in one of three ways:

- **Use the Teams admin center.** For some countries/regions, you can get numbers for your conference bridges using the Teams admin center. See [Getting service phone numbers](./getting-service-phone-numbers.md).

- **Port your existing numbers.** You can port or transfer existing numbers from your current service provider or phone carrier to Microsoft 365. for more information on porting existing numbers, see [Transfer phone numbers to Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md) or [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).
  
- **Use a request form for new numbers.** Sometimes (depending on your country/region) you aren't able to get your new phone numbers using the Teams admin center, or you need specific phone numbers or area codes. If so, you need to download a form and send it back to us. For more information, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).



#### Shared phone numbers
  
Shared phone numbers are those phone numbers that can be shared with other Microsoft 365 organizations. You can't change the languages that are used when someone calls in to one of these numbers.

Shared phone numbers are automatically assigned to organizations when they're enabled for Audio Conferencing. When the phone numbers are assigned, a phone number is assigned as the default phone number of the conferencing bridge. The phone number assigned as the default number of the bridge is one from the country/region of the organization.

> [!NOTE]
> The country or region location of your organization can be found by signing in to the **Microsoft 365 admin center** and looking under **Organization Profile**.

> [!CAUTION]
> Due to limited availability of toll phone numbers in Venezuela, Indonesia, and United Arab Emirates (UAE), organizations from these countries/regions won't have an Audio Conferencing toll number automatically assigned to them. Toll-free numbers from these locations are available depending on available inventory.

To see a list of those countries/regions that have phone numbers automatically assigned to organizations, see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).
  

### Default and alternate languages for Audio Conferencing bridges

Audio Conferencing lets you set up default and alternate languages for a conferencing bridge. For more information, see [Set auto attendant languages for Audio Conferencing in Microsoft Teams](set-auto-attendant-languages-for-audio-conferencing-in-teams.md).

## Dial-in phone number settings for users who lead meetings

After you create your Audio Conferencing bridge, you need to set the toll and/or toll-free numbers that users who lead meetings will use. For more information, see [Assign dial-in phone numbers for users who lead meetings](set-up-audio-conferencing-in-teams.md#step-7-assign-dial-in-phone-numbers-for-users-who-lead-meetings). 

## Communications Credits

To provide toll-free conference bridge phone numbers and to support conferencing dial-out to international phone numbers, you must set up Communications Credits for your organization. To learn more about Communications Credits, see [What are Communications Credits?](what-are-communications-credits.md).

|Ask yourself|Action |
|------------|-------|
|Are Communications Credits required for my Audio Conferencing implementation? |To find out if you need to set up Communications Credits, see [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).|
|If they're required, how much should I purchase?|To determine the Communications Credits amount, see [Recommended funding amounts](what-are-communications-credits.md#recommended-funding-amounts).|
|Do I want to configure an auto-recharge amount?|To configure an auto-recharge amount, see [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).|
|||

## Other deployment decisions

You might want to change these settings based on your organization's needs and configuration.

### Outbound calling restriction policies

You can use outbound call controls to restrict the type of Audio Conferencing and Public Switched Telephone Network (PSTN) calls that users in your organization can make. For more information, see [Outbound calling restriction policies for Audio Conferencing and user PSTN calls](outbound-calling-restriction-policies.md).

### Dial plans

**DOES THIS APPLY TO AUDIO CONFERENCING?**  OR NUKE THIS SECTION ALTOGETHER?

A dial plan in Teams Phone is a set of normalization rules that translate dialed numbers into another format (typically E.164 format) for call authorization and routing.

For more information about dial plans, see [What are dial plans?](what-are-dial-plans.md)

|Ask yourself|Action |
|------------|-------|
|Does my organization need a customized dial plan?|To help determine if you need a custom dial plan, see [Planning for tenant dial plans](what-are-dial-plans.md#planning-for-tenant-dial-plans). |
|Which users require a customized dial plan, and which tenant dial plan should be assigned to each user?|To add users to a customized dial plan using PowerShell, see [Create and manage dial plans](create-and-manage-dial-plans.md).|
|||

### Troubleshoot meeting and call quality

Teams gives you two ways to monitor and troubleshoot call quality problems: [Call Analytics and Call Quality Dashboard](monitor-call-quality-qos.md). Call Analytics shows detailed information about the devices, networks, and connectivity related to the specific calls and meetings for each user. Call Analytics is designed to help admins and help desk agents troubleshoot call quality problems with specific calls. The Call Quality Dashboard is designed to help admins and network engineers optimize a network. Call Quality Dashboard shifts focus from specific users and instead looks at aggregate information for an entire Teams organization.


## Next steps

- [Drive adoption of Audio Conferencing in your organization](adopt-microsoft-teams-landing-page.md)
- [Roll out cloud voice](cloud-voice-landing-page.md)
- Include featured apps - such as Planner - in your initial Teams rollout. Add other [Teams apps](apps-in-teams.md) as you drive Teams adoption.







