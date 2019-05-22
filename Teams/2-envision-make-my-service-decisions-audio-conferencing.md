---
title: Make Audio Conferencing service decisions - Microsoft Teams
author: rmw2890
ms.author: Rowille
manager: serdars
ms.date: 12/28/2018
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.reviewer: rowille
description: Learn about meetings, licensing and availability, configuring conference bridge settings, acquiring or transfering phone numbers, and choosing tenant dial plans. 
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Make my service decisions

To plan for the technical implementation of Audio Conferencing, you must make a series of service decisions ahead of time to better prepare your organization to implement a solution that meets your defined business requirements.

## Audio Conferencing in Teams

As part of defining required Audio Conferencing features in Microsoft Teams, one of the first steps is to evaluate the latest public roadmap to determine:

-   Which Audio Conferencing features in Teams that will be deployed for users in scope.

-   Expected user functionality requirements for Audio Conferencing in Teams.

-   Confirmation that Audio Conferencing features in Teams described in the latest public roadmap meet your user, functionality, and scope requirements, within the timeline of your deployment.

> [!NOTE]
> The latest Teams roadmap for identifying Teams Audio Conferencing features in scope for your deployment can be found at <https://aka.ms/O365Roadmap>.

## Meetings in Teams

Teams gives your users the capability to schedule and join online meetings by using HD video, voice over IP (VoIP), and PSTN dial-in conferencing options.

Meetings can be scheduled as private meetings (only invited parties can join) or channel meetings (open for all users having access to the channel), and your users can also start impromptu meetings within channels.

> [!NOTE]
> To learn more about the features of meetings in Teams, see the [Microsoft 365 Roadmap](https://aka.ms/O365Roadmap).

Meeting participants can join your Teams meetings by dialing in to the toll or toll-free dial-in conference bridge phone numbers via landlines or mobile phones. In addition, users can let the Audio Conferencing service initiate the “call me” feature so they can participate in a meeting by having the conference bridge call their phones (useful when the data connection isn’t reliable), or let meeting organizers invite meeting participants by dialing out to their phones.

> [!IMPORTANT]
> Audio Conferencing in Teams doesn’t support third-party audio conferencing providers (ACPs).

<!--ENDOFSECTION-->

## Availability of Audio Conferencing

Before you plan for the implementation of Audio Conferencing in Teams, you need to review the availability of the Audio Conferencing service as detailed in [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).

> [!IMPORTANT]
> Due to legal constraints, for Audio Conferencing to be available to multinational organizations, the contract for Office 365 subscriptions must be sourced from countries and regions where the Audio Conferencing service is commercially available.

After confirming your organization is eligible to obtain the Audio Conferencing service, compile the list of user locations or offices where you’ll implement the Audio Conferencing service, based on the list of available countries and regions.

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide which user locations or offices will implement the Audio Conferencing service.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the user locations or offices to be enabled for the Audio Conferencing service.</li></ul>|

> [!TIP]
> Below is an example of an Audio Conferencing site enablement list template:
> 
> |Office   |Location |PSTN Conference Service  |
> |---------|---------|---------|
> |One Epping Road|Australia|Audio Conferencing|
> |100 Cyberport Road|Hong Kong SAR|Legacy PSTN Conferencing|
> |One Marina Boulevard|Singapore|Audio Conferencing|
> |32 London Bridge Street|United Kingdom|Audio Conferencing|
> |39 quai du Président Roosevelt|France|Audio Conferencing|

<!--ENDOFSECTION-->

## Licensing for Audio Conferencing

An [Audio Conferencing license](teams-add-on-licensing/microsoft-teams-add-on-licensing.md) is available as part of Office 365 E5 subscription plans, or as an add-on service to Office 365 E1 or Office 365 E3 subscription plans.

> [!NOTE]
> PSTN or dial-in conferencing in Teams doesn’t support third-party audio conferencing providers (ACPs).
> <br>If you already use Skype for Business Online PSTN Conferencing today, you can
immediately take advantage of Audio Conferencing in Teams.

To provide toll-free conference bridge phone numbers and to support conferencing
dial-out to international phone numbers, you must set up [Communications Credits](what-are-communications-credits.md) for your organization.

> [!IMPORTANT]
> Some countries are serviced by toll-free conference bridge phone numbers only. To support dial-in in these countries, you must use Communications Credits.

The first consideration when implementing Communications Credits is to decide
the initial amount of funds you want to purchase. If your organization chooses to use auto-recharge, you need to decide the trigger amount (lowest amount of funds) and the auto-recharge amount. Your actual usage will determine the auto-recharge amount. You should monitor your Communications Credits usage over time and adjust the recharge amount as necessary.

You can learn more about Communications Credits [here](what-are-communications-credits.md).

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>If your organization hasn’t already purchased the required Audio Conferencing licensing, decide whether you’ll acquire Audio Conferencing licenses by stepping up existing Office 365 subscriptions or by acquiring Audio Conferencing add-on licenses.</li><li>Decide whether Communications Credits are required for your Audio Conferencing implementation. If so, decide the initial amount of funds to be purchased. Where applicable, decide the trigger amount and auto-recharge amount.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the users who will be assigned Audio Conferencing licenses.</li><li>Document the Communications Credits plan (initial amount, trigger amount,auto-recharge amount)</li></ul>|

> [!TIP]
> You can document the license assignment list for Audio Conferencing users by using the following example.
> 
> |User  |Office  |Office 365 License  |
> |---------|---------|---------|
> |Adele Vance|One Epping Road|Office 365 E5|
> |Alex Wilber|One Epping Road|Office 365 E3, Audio Conferencing add-on|
> |Ben Walters|One Epping Road|Office 365 E3, Audio Conferencing add-on|
> |Christie Cline|One Marina Boulevard|Office 365 E3, Audio Conferencing add-on|
> |Debra Berger|One Marina Boulevard|Office 365 E5|
> |Lee Gu|One Marina Boulevard|Office 365 E5|
> |Emily Braun|32 London Bridge Street|Office 365 E5|
> |Lidia Holloway|32 London Bridge Street|Office 365 E5|
> |Louis Lahr|32 London Bridge Street|Office 365 E5|
> |Marcel Beauchamp|39 quai du Président Roosevelt|Office 365 E3, Audio Conferencing add-on|
> |Rachelle Cormier|39 quai du Président Roosevelt|Office 365 E5|
> |Isabell Potvin|39 quai du Président Roosevelt|Office 365 E3, Audio Conferencing add-on|

<br>

> [!TIP]
> Your Communications Credits planning numbers can be documented as the following:
>
> |         |         |
> |---------|---------|
> |Initial amount|$ 1,000|
> |Trigger amount|$ 400|
> |Auto-recharge amount|TBA|
> 
<!--ENDOFSECTION-->

## Conference bridge phone numbers

The Audio Conferencing service in Office 365 includes:

-   Multiple types of conference bridge phone numbers (toll and toll-free)

-   Multiple categories of conference bridge phone numbers (dedicated and shared)

-   Support for multiple languages for the conference bridge (primary and secondary)

-   A default phone number for the tenant

> [!NOTE]
> Dedicated conference bridge phone numbers count toward the limit of phone numbers that can be acquired per tenant, based on the number of applicable licenses. Toll-free conference bridge phone numbers require Communications Credits.

If you must transfer existing conference bridge phone numbers to the Audio Conferencing service—assuming they meet country-specific requirements—you can transfer these existing conference bridge phone numbers to Microsoft.

> [!NOTE]
> The complexity of transferring phone numbers to Microsoft varies greatly depending on country or region, carrier, number of circuits involved, and many other contributing factors. Work with your current provider to investigate how long this is likely to take to help ensure that you start the process early enough to meet your timelines.

To learn more about conference bridge phone numbers, review the following articles:

-   [Set up Audio Conferencing for Microsoft Teams](set-up-audio-conferencing-in-teams.md)

-   [Phone numbers for Audio Conferencing](https://docs.microsoft.com/SkypeForBusiness/audio-conferencing-in-office-365/phone-numbers-for-audio-conferencing)

-   [Getting service phone numbers](getting-service-phone-numbers.md)

-   [Transfer phone numbers to Office 365](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/transfer-phone-numbers-to-office-365)

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide whether your organization needs dedicated conference bridge phone numbers.</li><li>Decide how the dedicated conference bridge phone numbers will be obtained for user locations or offices in-scope for the Audio Conferencing implementation (that is, obtain from Microsoft or transfer existing phone numbers).</li><li>If you choose to obtain them from Microsoft, decide the method to use (form submission or automated) for user locations or offices in-scope for the Audio Conferencing implementation.</li><li>Decide the language preferences to set up for each dedicated conference bridge phone number.</li><li>Decide the tenant default conference bridge phone number.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the master plan for phone number acquisition, detailing how phone numbers will be obtained for each user location or office in scope for the Audio Conferencing implementation.</li><li>If applicable, complete the New Telephone Number Request form—one form for each location or office.</li><li>Document the detailed conference bridge phone number configurations (shared and dedicated conference bridge phone numbers, language preferences for each dedicated conference bridge phone number, tenant default conference bridge phone number).</li></ul>|

Below is an example of a template you can use to capture conference bridge details.

> [!TIP]
> Below is an example of a template to capture conference bridge details:
> 
> |Office   |Bridge Number Acquisition and Bridge Type |Bridge Number  |Bridge Language|
> |---------|---------|---------|---------|
> |One Epping Road|Acquire new, dedicated|TBA|English (Australia)|
> |One Marina Boulevard|Acquire new, shared|TBA|English (United States), Chinese (Simplified, PRC)|
> |32 London Bridge Street|Port existing, dedicated|+44 20 7946 0001|English (United Kingdom)|
> |39 quai du Président Roosevelt|Acquire new, dedicated|TBA|French (France), English (United Kingdom)|

<!--ENDOFSECTION-->

## Conference bridge settings

To further tailor the user experience, you can configure organization-wide options for joining Audio Conferencing meetings (meeting entry and exit notification and caller name recording), the meeting organizer’s PIN length, and email notification:

-   Meeting entry and exit notifications are available in the form of recorded name, phone number, and tones.

-   PIN length is configurable from 4 to 12 digits, with a 5-digit PIN as the default.

-   Notification emails sent on enablement of the Audio Conferencing license or any other admin-driven change are enabled by default. You can disable this feature and take control of your organization’s user communications.

For users who are assigned an Audio Conferencing license, the default toll/toll-free numbers, shown in the Audio Conferencing coordinates, can be configured to use:

-   The tenant-level default.

-   The automatically assigned conference bridge phone numbers.

-   A conference bridge phone numbers configured manually for each user.

User-specific conference bridge phone numbers are typically useful in global or nationwide organizations where users are distributed and must provide local numbers as the default conference bridge phone numbers in their meeting invitations.

Participants joining from different cities or overseas can look up additional numbers configured at the tenant level, but these numbers don’t appear directly in the meeting invitations. The meeting invitations provide a link that takes participants to the **Teams Conference Dial-in Numbers** page for them to look up the conference bridge phone number closest to their location.

You can also configure how unauthenticated callers are handled by each individual meeting organizer—whether to require the meeting organizer to start the meeting before unauthenticated callers can be admitted, or allow unauthenticated callers to start a meeting.

You can also apply additional configurations for each user to control the use of toll-free conference bridge phone numbers and dial-out from a conference.

> [!NOTE]
> These cost-related controls are currently available for preview customers only. You can enroll your organization in the preview program from https://www.skypepreview.com.

With these controls, you can decide whether meeting organizers can provide toll-free conference bridge phone numbers for meetings organized by them, and whether participants can dial out from the meetings they organized. The level of dial-out control spans from completely preventing dial out, to only allowing dial out to domestic numbers, to allowing dial out to both domestic and international numbers.

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide whether your organization requires entry and exit notifications, and—if it does—the type of notification to be implemented (tones, phone number, or recorded name).</li><li>Decide the Audio Conferencing PIN length that meets your organizational security requirements.</li><li>Decide whether your organization wants to take control of user communications related to the Audio Conferencing service.</li><li>Decide the conference bridge phone numbers to be assigned to each meeting organizer.</li><li>Decide whether some meeting organizers need to use toll-free conference bridge phone numbers for their meetings.</li><li>Decide whether some meeting organizers need to allow unauthenticated callers to start a meeting.</li><li>Decide whether some meeting organizers need conference dial-out to be controlled.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the detailed conference bridge settings (entry and exit notifications, PIN length, configuration change email notification)</li><li>Document the conference bridge phone numbers to be assigned to each meeting organizer and the corresponding setting to control the policy for unauthenticated callers, and toll-free and dial out controls.</li></ul>|

> [!TIP]
> Your conference bridge settings can be documented as in the following example.
> 
> |         |         |
> |---------|---------|
> |Enable meeting entry and exit notifications|Enabled|
> |Entry/exit announcement type|Tones|
> |Ask callers to record their name before joining the meeting|Disabled|
> |PIN length|5|
> |Automatically send emails to users if their dial-in settings change|Disabled|

<br>

> [!TIP]
> You can document the conference bridge settings assignment list for Audio Conferencing users by using the following example.
>
> |User  |Office  |Default toll number  |Default toll-free number  |Allow toll-free  |Unauthenticated callers bypass lobby  |Conference dial out  |
> |---------|---------|---------|---------|---------|---------|---------|
> |Adele Vance|One Epping Road|TBA|TBA|Yes|Enabled|International and domestic|
> |Alex Wilber|One Epping Road|TBA|TBA|No|Disabled|Not allowed|
> |Ben Walters|One Epping Road|TBA|TBA|No|Disabled|Not allowed|
> |Christie Cline|One Marina Boulevard|TBA|TBA|Yes|Disabled|Domestic|
> |Debra Berger|One Marina Boulevard|TBA|TBA|Yes|Enabled|Domestic|
> |Lee Gu|One Marina Boulevard|TBA|TBA|Yes|Enabled|Domestic|
> |Emily Braun|32 London Bridge Street|+44 20 7946 0001|TBA|Yes|Enabled|Not allowed|
> |Lidia Holloway|32 London Bridge Street|+44 20 7946 0001|TBA|Yes|Disabled|Not allowed|
> |Louis Lahr|32 London Bridge Street|+44 20 7946 0001|TBA|Yes|Disabled|Not allowed|
> |Marcel Beauchamp|39 quai du Président Roosevelt|TBA|TBA|No|Disabled|Domestic|
> |Rachelle Cormier|39 quai du Président Roosevelt|TBA|TBA|Yes|Enabled|International and domestic|
> |Isabell Potvin|39 quai du Président Roosevelt|TBA|TBA|No|Disabled|Domestic|

<!--ENDOFSECTION-->

## Manage cloud voice telephone numbers

For Audio Conferencing implementation, you can choose to acquire new telephone numbers or transfer/port existing telephone numbers.

To allow users to dial phone numbers the way they’re accustomed to—such as omitting area codes for local calls, omitting country code for domestic calls, or even using short digit dialing when performing conference dial out—you can configure a customized dial plan and assign it to users.

## Acquire new telephone numbers

The two types of telephone numbers within Microsoft cloud voice solutions are:

-   Subscriber (user) numbers, which can be assigned to users in your organization.

-   Service numbers, available as toll and toll-free service numbers, which have higher concurrent call capacity than subscriber numbers and can be assigned to services such as Audio Conferencing, Auto Attendants, or Call Queues.

For more information about these types of telephone numbers, see [Different kinds of phone numbers used for Calling Plans](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/different-kinds-of-phone-numbers-used-for-calling-plans).

The total count of telephone numbers that you can obtain depend on the telephone number types and the number of licenses you have bought and assigned to your users.

When it comes to service numbers, you need to carefully plan your Audio Conferencing implementation. Evaluate whether your business requires dedicated conference bridge phone numbers; if not, your organization can opt to use shared conference bridge phone numbers.

For more information about the total count of telephone numbers that you can obtain, see [How many phone numbers can you get?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/how-many-phone-numbers-can-you-get)

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide the user locations or offices where new telephone numbers will be acquired from Microsoft.</li><li>Decide the type of telephone numbers to be acquired from Microsoft.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the user locations or offices where new telephone numbers will be acquired from Microsoft.</li><li>Document the type of telephone numbers to be acquired from Microsoft.</li></ul>|

## Transfer existing telephone numbers

If your organization wants to transfer (or port) existing telephone numbers to Microsoft, you can do so by submitting a port order request to Microsoft.

You can transfer all your existing telephone numbers at once (full port), and—in some markets—you can transfer a subset of your existing telephone numbers (partial port). A partial port can be useful in cases where you just want to move your dial-in conference bridge to Audio Conferencing service.

A single port order can only transfer the telephone numbers to a single telephone number type. If you need to transfer some of your telephone numbers as subscriber numbers and some as service numbers, we recommend that you first complete the transfer to Microsoft and then perform the conversion as soon as the numbers are within Microsoft’s control.

As an alternative, if partial port is supported, you can submit multiple port requests, one port request at a time. However, this alternative approach will prolong your contract with your existing telecommunications service provider.

Telephone number porting is a complex topic and requires thorough planning, coordination, and adequately managing your stakeholders’ expectations. To learn more, see the following articles:

-   [Transferring phone numbers to Office 365](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/transfer-phone-numbers-to-office-365)

-   [Transferring phone numbers common questions](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/transferring-phone-numbers-common-questions)

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide the user locations or offices where existing telephone numbers will be transferred to Microsoft.</li><li>Decide the type of telephone numbers to be transferred to Microsoft.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the user locations or offices where existing telephone numbers will be transferred to Microsoft.</li><li>Document the type of telephone numbers to be transferred to Microsoft.</li></ul>|

<!--ENDOFSECTION-->

## Dial plans

A Dial Plan in the Phone System feature of Office 365 is a set of normalization rules that translates dialed phone numbers into an alternate format (typically E.164 format) for call authorization and call routing. The Audio Conferencing service leverages the same capabilities used by Phone System to translate dialed phone numbers in conference dial-out scenarios (for example, invite participants via PSTN and dial back, “call me” feature).

In the Phone System feature of Office 365, there are two types of dial plans:

-   **Service dial plan:** This is the default dial plan that’s applied to users based on their Office 365 usage location, and it can’t be modified.

-   **Tenant dial plan:** This is a customizable dial plan within a tenant, which is further divided into two types:

    -   **Tenant-global dial plan:** The dial plan that applies to all users in the tenant.

    -   **Tenant-user dial plan:** The dial plan that applies only to specific users.

The effective dial plan assigned to users is the combination of the service dial plan (based on a user’s Office 365 usage location) and tenant dial plan (can be either tenant-global dial plan or tenant-user dial plan).

![Table shows three combinations of service and tenant dial plans.](media/audio_conferencing_image8.png "Table shows three combinations of service and tenant dial plans.")

> [!Important]
> There can be a maximum of 25 normalization rules in each tenant dial plan; therefore, it’s important to avoid duplicating normalization rules that are already available as part of the service dial plan.

To learn more about dial plans, see [What are dial plans?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-dial-plans)

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide whether your organization requires customized dial plans (business requirements, adoption requirements, and so on).</li><li>If applicable, decide the scope of tenant dial plan (tenant-global or tenant-user) to support the requirements for customized dial plans.</li><li>If applicable, decide the tenant dial plans that you’ll create to support user locations or offices in-scope for the cloud voice implementation.</li><li>If applicable, decide which users require a customized dial plan and the tenant dial plan to be assigned for each user.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the customized dial plans and the associated normalization rules to be configured as part of your cloud voice implementation.</li><li>Document the users to be assigned a customized dial plan and the tenant dial plan to be assigned for each user.</li></ul>|

> [!TIP]
> If it’s applicable to your project, you can use the following template to document the tenant dial plan configurations.
> 
> |Tenant Dial Plan Name<br>_Description_  |Normalization Rules Name<br>_Description_  |Pattern<br>Translation<br>IsInternalExtension  |
> |---------|---------|---------|
> |**AU-NSW-NorthRyde-OER**<br>_One Epping Road North Ryde, NSW, AU Dial Plan_|**AU-NSW-NorthRyde-OER-Internal**<br>_Internal number (x7000 - x7999) for One Epping Road office, North Ryde, NSW, Australia_|^(7\d{3})$<br>+6125550$1<br>True|
> ||**AU-NSW-Local**<br>_Local number normalization for NSW, Australia_|^([2-9]\d{7})$<br>+612$1<br>False|
> ||**AU-TollFree**<br>_Toll Free number normalization for Australia_|^(1[38]\d{4,8})\d*$<br>+61$1<br>False|
> ||**AU-Service**<br>_Service number normalization for Australia_|^(000\|1[0125]\d{1,8})$<br>$1<br>False|
> |**SG-Singapore-OMB**<br>_OMB Singapore, SG Dial Plan_|**SG-OMB-Internal**<br>_Internal number (x8000 â€“ x8999) for OMB office, Singapore_|^(8\d{3})$<br>+656888$1<br>True|
> ||**SG-TollFree**<br>_Toll Free number normalization for Singapore_|^(1?800\d{7})\d*$<br>+65$1<br>False|
> ||**SG-Service**<br>_Service number normalization for Singapore_|^(1\d{3,4}\|9\d{2})$<br>$1<br>False|
> |**FR-Paris-Issy-39qdPR**<br>_39 quai du Président Roosevelt Issy-les-Moulineaux, France Dial Plan_|**FR-39qdPR-Internal**<br>_Internal number (x7000 â€“ x7999) for 39 quai du Président Roosevelt office, Issy-les-Moulineaux, France_|^(7\d{3})$<br>+3319999$1<br>True|
> ||**FR-TollFree**<br>_Toll Free number normalization for France_|^0?(80\d{7})\d*$<br>+33$1<br>False|
> ||**FR-Service**<br>_Service number normalization for France_|^(1\d{1,2}\|11[68]\d{3}\|10\d{2}\|3\d{3})$<br>$1<br>False|

<br>

> [!TIP]
> The example template below can be leveraged to document dial plan assignments to support your project:
>
> |User  |Office  |Dial Plan Type  |Dial Plan Name  |
> |---------|---------|---------|---------|
> |Adele Vance|One Epping Road|Tenant dial plan|AU-NSW-NorthRyde-OER|
> |Alex Wilber|One Epping Road|Tenant dial plan|AU-NSW-NorthRyde-OER|
> |Ben Walters|One Epping Road|Tenant dial plan|AU-NSW-NorthRyde-OER|
> |Christie Cline|One Marina Boulevard|Tenant dial plan|SG-Singapore-OMB|
> |Debra Berger|One Marina Boulevard|Tenant dial plan|SG-Singapore-OMB|
> |Lee Gu|One Marina Boulevard|Tenant dial plan|SG-Singapore-OMB|
> |Emily Braun|32 London Bridge Street|Service dial plan|N/A|
> |Lidia Holloway|32 London Bridge Street|Service dial plan|N/A|
> |Louis Lahr|32 London Bridge Street|Service dial plan|N/A|
> |Marcel Beauchamp|39 quai du Président Roosevelt|Tenant dial plan|FR-Paris-Issy-30qdPR|
> |Rachelle Cormier|39 quai du Président Roosevelt|Tenant dial plan|FR-Paris-Issy-30qdPR|
> |Isabell Potvin|39 quai du Président Roosevelt|Tenant dial plan|FR-Paris-Issy-30qdPR|

<!--ENDOFSECTION-->

## Document service decisions 

Use the information from the previous sections of this article to document your service decisions. In general, this documentation will contain the following main sections:

-   Audio Conferencing service site enablement list

-   License assignment list for Audio Conferencing meeting organizers

-   Communications Credits planning numbers

-   Conference bridge details

-   Conference bridge settings

-   Conference bridge settings assignments

-   Phone numbers acquisition plans

-   Tenant dial plans

-   Dial plan assignments

<!--ENDOFSECTION-->