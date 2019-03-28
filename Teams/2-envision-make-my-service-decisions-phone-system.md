---
title: Make Phone System with Calling Plans service decisions - Microsoft Teams
author: rmw2890
ms.author: MyAdvisor
manager: serdars
ms.date: 03/13/2018
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.reviewer: rowille
description: Choose from calling plans and licensing, configure emergency locations and features like voicemail and caller ID, acquire or transfer phone numbers. 
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Make my service decisions

To plan for the technical implementation of Phone System with Calling Plans, you must make a series of service decisions ahead of time to better prepare your organization to implement a solution that meets your defined business requirements.

## Calling in Teams

With Microsoft Teams, your users can place and receive phone calls to or from the public switched telephone network (PSTN). Your users can use their own dedicated phone numbers for placing and receiving domestic and international phone calls from Teams client applications, with advanced features that include voicemail.

> [!NOTE]
> The latest Teams roadmap for identifying Teams Phone System with Calling Plan features in scope for your deployment can be found at <https://aka.ms/O365Roadmap>.

## Phone System in Teams

For Teams users to be able to place and receive PSTN calls, they need to be enabled for Phone System, a feature in Office 365.

To enable connectivity to the PSTN, your organization can use Microsoft as its telecommunications service provider. Eventually, you’ll also have the option to “bring your own” telecommunications service provider to enable connectivity to PSTN for Phone System.

> [!IMPORTANT]
> The ability to use your own telecommunications service provider for Phone System with your Teams deployment is also available with Phone System Direct Routing. To learn more about Direct Routing, please review the [Direct Routing guidance](2-envision-make-my-service-decisions-direct-routing.md).

## Phone System with Calling Plans

To use Microsoft as your telecommunications service provider, you need to obtain Calling Plan licenses and assign them to your Phone System users.

There are two major types of calling plans:

-   Domestic calling plan

-   Domestic and international calling plan

Each type of calling plan allocates a certain number of call minutes per month to each user who has been assigned the license. When the call minutes allocation is exhausted, the user won’t be able to place outbound calls—except for emergency calls—until the next month’s billing cycle. If you want users to be able to continue to place outbound call even after they’ve exhausted their
allocation of call minutes, or to let users who have a domestic calling plan place international calls, you can set up Communications Credits for your organization.

<!--ENDOFSECTION-->

## Availability of Calling Plans

Before you plan for the implementation of Calling Plans in Teams, verify that the Calling Plans service is available in your area by reviewing [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).

> [!IMPORTANT]
> Due to legal constraints, for Calling Plans to be available to multinational organizations, the contract for Office 365 subscriptions must be based in a country or region where the Calling Plans service is available, or where the Calling Plans service can be purchased.

> [!NOTE]
> If Calling Plans are not available in your area, you can use [Phone System Direct Routing](2-envision-make-my-service-decisions-direct-routing.md) to enable your users using Teams with PSTN capabilities.

After confirming that your organization can obtain the Calling Plans service, compile the list of user locations or offices where you’ll be implementing the Calling Plans service, based on the list of available countries and regions.

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide which user locations or offices you’ll implement the Calling Plans service in.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the user locations or offices to be enabled for the Calling Plans service.</li></ul>|

> [!TIP]
> Below is an example of a Phone System with Calling Plans site enablement list.
> 
> | **Office**                     | **Location**   | **Phone System service** |
> |--------------------------------|----------------|--------------------------|
> | One Epping Road                | Australia      | Legacy PSTN service |
> | 100 Cyberport Road             | Hong Kong SAR  | Phone System Direct Routing |
> | One Marina Boulevard           | Singapore      | Phone System Direct Routing |
> | 32 London Bridge Street        | United Kingdom | Phone System with Calling Plans |
> | 39 quai du Président Roosevelt | France         | Phone System with Calling Plans |

<!--ENDOFSECTION-->

## Phone numbers and emergency locations

With Calling Plans in Office 365, every user in your organization needs to have a unique direct inward dialing (DID) phone number and a corresponding validated emergency address. Review [Manage cloud voice telephone numbers](2-envision-make-my-service-decisions-phone-system.md#manage-cloud-voice-telephone-numbers) to plan the phone number acquisition for your Calling Plans implementation.

When you’re configuring phone numbers for Calling Plans, you must assign an emergency address to each telephone number before you assign the number to a user. This is required to support emergency calling. The emergency address must be validated to ensure that it’s in the correct format to be used by emergency response services.

> [!IMPORTANT]
> Emergency Services calling operates differently in the Calling Plans service than in traditional telephone services. It’s important that you understand these differences and communicate them to all users. See [Emergency Calling Terms and Conditions](emergency-calling-terms-and-conditions.md) for more details.

In addition to supplying a validated emergency address, you can define emergency locations and associate them with the validated emergency address to give a more exact location within an address. An emergency location is typically a building number, floor, building wing, or office number where the user is located.

To learn more about emergency locations in relation to Calling Plans, review the following articles:

-   [What are emergency locations, addresses and call routing?](what-are-emergency-locations-addresses-and-call-routing.md)

-   [Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide the granularity of emergency location information to be collected for user locations or offices in scope for the Calling Plans implementation.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the detailed emergency address and emergency locations for each user location or office in scope for the Calling Plans implementation.</li></ul>|

> [!TIP]
> You can use the following template to document the details of phone numbers and emergency location details.
> 
> |User |Emergency location and address |Phone number |
> |-----|-------------------------------|-------------|
> |Emily Braun |1034/32 London Bridge Street, London, SE1, United Kingdom |+44 23 4567 8901 |
> |Lidia Holloway |1065/32 London Bridge Street, London, SE1, United Kingdom |+44 23 4567 89112 |
> |Louis Lahr |1023/32 London Bridge Street, London, SE1, United Kingdom |+44 23 4567 8921 |
> |Marcel Beauchamp |07E15D/39 quai du Président Roosevelt, 92130 Issy-les-Moulineaux, France | TBA |
> |Rachelle Cormier |07N15D/39 quai du Président Roosevelt, 92130 Issy-les-Moulineaux, France | TBA |
> |Isabell Potvin |07F05E/39 quai du Président Roosevelt, 92130 Issy-les-Moulineaux, France | TBA |

<!--ENDOFSECTION-->

## Voicemail

Cloud Voicemail, powered by Azure Voicemail services, supports voicemail deposits to Exchange mailboxes only and doesn’t support third-party email systems.

By default, Cloud Voicemail works with Exchange Online; however it has a minimum supported Exchange on-premises version and deployment model to allow delivery of voicemail messages to user mailboxes in the on-premises Exchange deployment.

Cloud Voicemail includes voicemail transcription, which is enabled for all users in your organization by default. Your business needs might require that you disable voicemail transcription for specific users or everyone throughout the organization. If your organization decided to keep voicemail transcription enabled, you need to also consider whether voicemail transcription profanity masking need to be enabled. See [Setting voicemail policies in your organization](set-up-phone-system-voicemail.md) for more details.

>[!NOTE]
> A fallback mechanism has been implemented so that Cloud Voicemail can resend messages by using SMTP, which means users who have a mailbox on a third-party email system will receive their voicemail messages. This mechanism doesn’t include guaranteed service uptime or other voicemail
features, such as changing voicemail greeting.

For more information about voicemail in a Phone System implementation, see [Phone System with Calling Plans](calling-plan-landing-page.md).

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide whether you’ll enable Cloud Voicemail in your Calling Plans implementation.</li><li>If using Exchange on-premises and your existing deployment doesn’t meet your requirements to support Cloud Voicemail, choose from the available options (upgrade and setup for Cloud Voicemail support, migrate to Exchange Online, or leverage the fallback mechanism described earlier).</li><li>Decide whether you’ll enable or disable voicemail transcription and voicemail transcription profanity masking throughout the organization or for specific users.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>If applicable, document the Exchange decision points to support Cloud Voicemail.</li><li>If you’ll enable/disable voicemail, voicemail transcription, and voicemail transcription profanity masking only for specific users, document that list of users.</li></ul>|

> [!TIP]
> Cloud Voicemail details for the Phone System with Calling Plans implementation can be documented as the following.
> 
> |User |Exchange mailbox |Enable voicemail? |Voicemail transcription |Voicemail transcription profanity masking |
> |------------------|------------------|-------------------|----------|----------|
> |Emily Braun      |Online      |Yes |Enabled |Enabled |
> |Lidia Holloway   |Online      |Yes |Enabled |Disabled |
> |Louis Lahr       |On-premises |Yes |Enabled |Enabled |
> |Marcel Beauchamp |On-premises |Yes |Disabled |N/A |
> |Rachelle Cormier |Online      |Yes |Disabled |N/A |
> |Isabell Potvin   |On-premises |Yes |Disabled |N/A |

<!--ENDOFSECTION-->

## Calling identity

By default, all outbound calls use the assigned phone number as calling identity (Caller ID). The recipient of the call can quickly identify the caller and decide whether to accept or reject the call. In some cases, there are legitimate business requirements to mask the Caller ID to protect the identity of callers by using the office main line number—this is typically a service number serviced by the Auto Attendant configuration—as Caller ID, or to block Caller ID presentation altogether.

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide whether Caller ID manipulation is required for your Calling Plans implementation.</li><li>If applicable, decide the types of Caller ID manipulation (mask with service number or anonymize) to be implemented.</li><li>If applicable, decide which users require Caller ID manipulation and the type of Caller ID manipulation to be assigned to each user.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the users to be assigned Caller ID manipulation and the type of Caller ID manipulation to assign.</li></ul>|

> [!TIP]
> The following is an example of Caller ID masking details documentation.
> 
> |User  |Enable outbound Caller ID masking  |Caller ID masking type  |Allow user override  | Enable inbound Caller ID masking  |
> |---------|---------|---------|---------|---------|
> |Emily Braun|No|N/A|Yes|No|
> |Lidia Holloway|Yes|Service number (OrgAA, +44 20 7946 0000)|No|Yes|
> |Louis Lahr|No|N/A|Yes|No|
> |Marcel Beauchamp|Yes|Service number (OrgAA, TBA)|No|Yes|
> |Rachelle Cormier|Yes|Anonymize|Yes|No|
> |Isabell Potvin|Yes|Service number (OrgAA, TBA)|No|Yes|

<!--ENDOFSECTION-->

## Licensing for cloud voice capabilities

Audio Conferencing and Phone System are features in Office 365. They can be licensed separately as add-on services for existing customers who have Office 365 E3 or E1 subscription plans; they’re already included as part of the Office 365 E5 subscription plan.

Calling Plans is an add-on to the Phone System feature in Office 365, so you must have a Phone System licensed enabled to use Calling Plans.

To support for additional Audio Conferencing and Calling Plans use cases (international conference dial-out, external calling after Calling Plan minute allocations are exhausted, and so on), you can set up Communications Credits for your organization.

## Licensing for Calling Plans

If your organization intends to use Microsoft as telecommunications service provider, you need to obtain Calling Plan add-ons appropriate to your users’ business requirements. Generally, not everybody in an organization needs to place international calls, so you can provision most users with domestic Calling Plan licenses.

There are two types of Calling Plan licenses:

-   Domestic Calling Plan

-   International and Domestic Calling Plan

> [!NOTE]
> What is considered “domestic” for a specific user is determined by the user’s assigned Office 365 usage location.

Each Calling Plan type provides an allocation of calling minutes that users can use per month, either to make domestic calls or international calls. The Domestic Calling Plan costs less compared to the International and Domestic Calling Plan.

The flexibility of subscribing and assigning the most appropriate Calling Plan type for individual users’ business requirements helps your organization control the costs of its Calling Plans implementation.

For each Office 365 tenant, the combined number of calling minutes are pooled by country or region, and per Calling Plan type. When the monthly calling minutes cap for the tenant is reached, Calling Plans service (except for emergency calling) will be suspended for the remainder of the month. The Calling Plans service will resume automatically on the first day of the next calendar month.

You can set up Communications Credits for your organizations to enable users to make outbound calls after the allocation of calling minutes is exhausted without having to wait until the next month billing cycle. Additionally, Communications Credits give users assigned the Domestic Calling Plan the ability to make international calls, which are then charged by using a “pay-per-minute” model.

To learn more about Phone System and Calling Plans, review the following articles:

-   [Phone System](https://products.office.com/en-us/skype-for-business/phone-system)

-   [Calling Plans](https://products.office.com/en-us/skype-for-business/calling-plans)

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>If your organization doesn’t have the required Phone System license, decide whether you’ll acquire the Phone System license by stepping up your existing Office 365 subscriptions or by acquiring the Phone System add-on service.</li><li>Decide which users require a Domestic Calling Plan license and which require a Domestic and International Calling Plan license.</li><li>Decide whether you’ll need Communications Credits for your Calling Plans implementation.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the division, department, office, or user groups you’ll assign a Phone System license with Domestic Calling Plan or Domestic and International Calling Plan.</li></ul>|

> [!TIP]
> You can use the following example to document the license assignment for Phone System with Calling Plans users.
> 
> |User |Office |Office 365 License |Calling Plan |
> |----|----|----|----|
> |Emily Braun |32 London Bridge Street |Office 365 E5 |International and Domestic Calling Plan |
> |Lidia Holloway |32 London Bridge Street |Office 365 E5 |Domestic Calling Plan |
> |Louis Lahr |32 London Bridge Street |Office 365 E5 |Domestic Calling Plan |
> |Marcel Beauchamp |39 quai du Président Roosevelt |Office 365 E3, Phone System add-on |Domestic Calling Plan |
> |Rachelle Cormier |39 quai du Président Roosevelt |Office 365 E5 |International and Domestic Calling Plan |
> |Isabell Potvin |39 quai du Président Roosevelt |Office 365 E3, Phone System add-on |Domestic Calling Plan |

<!--ENDOFSECTION-->

## Communications Credits

Using Communications Credits, your users can dial out from an Audio Conferencing meeting to add someone else from anywhere in the world (outside of the originating country of the meeting organizer). You can set up Communications Credits for your organization to enable users to make outbound calls after they’ve exhausted their allocation of calling minutes, without having to wait
until the next month’s billing cycle. Additionally, Communications Credits give users assigned with the Domestic Calling Plan the ability to make international calls, which are then charged by using a “pay-per-minute” model.

The first consideration to make when implementing Communications Credits is to decide the initial amount of funds to be purchased. If your organization chooses to use auto-recharge, you’ll determine the optimal amount by measuring actual usage. Monitor your Communications Credits usage over time, and adjust your recharge amount as required.

For your Calling Plans implementation, you can control the use of Communications Credits on a per-user basis, which helps you ensure that you’ve assigned these credits in alignment with your business needs.

To learn more about Communications Credits, review [What are Communications Credits?](what-are-communications-credits.md).

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide whether you need Communications Credits for your Audio Conferencing or Calling Plans implementation.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the division, department, office, or user groups you’ll enable Communications Credits for.</li><li>Document your Communications Credits plan for your Audio Conferencing or Calling Plans implementation.</li></ul>|

> [!TIP]
> You use the following example to document the Communications Credits assignment list for Calling Plans users.
> 
> |User |Office |Calling Plan |Communications Credits |
> |----|----|----|----|
> |Emily Braun |32 London Bridge Street |International and Domestic Calling Plan |Enabled |
> |Lidia Holloway |32 London Bridge Street |Domestic Calling Plan |Disabled |
> |Louis Lahr |32 London Bridge Street |Domestic Calling Plan |Enabled |
> |Marcel Beauchamp |39 quai du Président Roosevelt |Domestic Calling Plan |Disabled |
> |Rachelle Cormier |39 quai du Président Roosevelt |International and Domestic Calling Plan |Enabled |
> |Isabell Potvin |39 quai du Président Roosevelt |Domestic Calling Plan |Disabled |

<br>

> [!TIP]
> Your Communications Credits planning numbers can be documented as in the following example.
>
> |         |         |
> |---------|---------|
> |Initial amount|$ 1,000|
> |Trigger amount|$ 400|
> |Auto-recharge amount|TBA|

<!--ENDOFSECTION-->

## Manage cloud voice telephone numbers

If you implement Phone System by bringing your own telecommunications service provider, telephone number management will remain as-is.

For Audio Conferencing and Calling Plans implementations, you can choose to acquire new telephone numbers or transfer (port) existing telephone numbers.

To let users dial phone numbers the way they’re accustomed to—such as omitting area codes for local calls, omitting country code for domestic calls, or even using short-digit dialing when performing conference dial-out or calling other users in the organization—you can configure a customized dial plan and assign it to users.

## Acquire new telephone numbers

The two types of telephone numbers in Microsoft cloud voice solutions are:

-   Subscriber (user) numbers, which can be assigned to users in your organization.

-   Service numbers, available as toll and toll-free service numbers, which have higher concurrent call capacity than subscriber numbers and can be assigned to services such as Audio Conferencing, Auto Attendants, or Call Queues.

For more information about the types of telephone numbers, see [Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md).

The total count of telephone numbers that you can obtain depend on the type of telephone number and the number of licenses you’ve bought and assigned to your users.

For more information about the total count of telephone numbers that you can obtain, see [How many phone numbers can you get?](how-many-phone-numbers-can-you-get.md)

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide the user locations or offices where new telephone numbers will be acquired from Microsoft.</li><li>Decide the type of telephone numbers to be acquired from Microsoft.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the user locations or offices where new telephone numbers will be acquired from Microsoft.</li><li>Document the type of telephone numbers to be acquired from Microsoft.</li></ul>|

## Transfer existing telephone numbers

If your organization wants to transfer (or port) existing telephone numbers to Microsoft, you can do so by submitting a port order request to Microsoft.

You can transfer all your existing telephone numbers at once (full port), and—in some markets—you can transfer a subset of your existing telephone numbers (partial port). A partial port can be useful in cases where you just want to gradually move your users to Phone System with Calling Plans.

A single port order can only transfer the telephone numbers to a single telephone number type. If you need to transfer some of your telephone numbers as subscriber numbers and some as service numbers, we recommend that you first complete the transfer to Microsoft and then perform the conversion as soon as the numbers are in Microsoft’s control.

As an alternative (if partial port is supported), you can submit multiple port requests, one port request at a time. However, this alternative approach will prolong your contract with your existing telecommunications service provider.

Telephone number porting is a complex topic and requires thorough planning, coordination, and adequately managing your stakeholders’ expectations. To learn more, see the following articles:

-   [Transferring phone numbers to Office 365](transfer-phone-numbers-to-office-365.md)

-   [Transferring phone numbers common questions](transferring-phone-numbers-common-questions.md)

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide the user locations or offices where existing telephone numbers will be transferred to Microsoft.</li><li>Decide the type of telephone numbers to be transferred to Microsoft.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the user locations or offices where existing telephone numbers will be transferred to Microsoft.</li><li>Document the type of telephone numbers to be transferred to Microsoft.</li></ul>|

<!--ENDOFSECTION-->

## Dial plans

A Dial Plan in the Phone System feature of Office 365 is a set of normalization rules that translate dialed phone numbers into an alternate format (typically E.164 format) for call authorization and call routing. The Audio Conferencing service leverages the same capabilities used by Phone System to translate dialed phone numbers in conference dial-out scenarios (for example, invite participants via PSTN and dial back, “call me” feature).

In the Phone System feature of Office 365, there are two types of dial plans:

-   **Service dial plan:** This is the default dial plan that’s applied to users based on their Office 365 usage location, and it can’t be modified.

-   **Tenant dial plan:** This is a customizable dial plan within a tenant, which is further divided into two types:

    -   **Tenant-global dial plan:** The dial plan that applies to all users in the tenant.

    -   **Tenant-user dial plan:** The dial plan that applies only to specific users.

The effective dial plan assigned to users is the combination of the service dial plan (based on a user’s Office 365 usage location) and tenant dial plan (which can be either a tenant-global dial plan or tenant-user dial plan).

![Table shows three combinations of service and tenant dial plans.](media/audio_conferencing_image8.png "Table shows three combinations of service and tenant dial plans.")

> [!IMPORTANT]
> There can be a maximum of 25 normalization rules in each tenant dial plan; therefore, it’s important to avoid duplicating normalization rules that are already available as part of the service dial plan.

For more information about dial plans, see [What are dial plans?](what-are-dial-plans.md)

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide whether your organization requires customized dial plans (business requirements, adoption requirements, and so on).</li><li>If applicable, decide the scope of the tenant dial plan (tenant-global or tenant-user) to support your requirements for customized dial plans.</li><li>If applicable, decide the tenant dial plans that you’ll create to support user locations or offices in scope for the cloud voice implementation.</li><li>If applicable, decide which users require a customized dial plan and the tenant dial plan to be assigned for each user.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the customized dial plans and the associated normalization rules to be configured as part of cloud voice implementation.</li><li>Document the users to be assigned a customized dial plan and the tenant dial plan to be assigned for each user.</li></ul>|

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

-   Phone System with Calling Plans site enablement list

-   License assignment for Phone System with Calling Plans users

-   Communications Credits planning numbers

-   Phone number acquisition, phone numbers, and emergency location details

-   Voicemail configuration details

-   Caller ID masking configuration details

-   Tenant dial plans

-   Dial plan assignments

<!--ENDOFSECTION-->