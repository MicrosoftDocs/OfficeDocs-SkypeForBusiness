#Make my service decisions

##Calling in Teams

With Microsoft Teams, your users can place and receive phone calls to or from
the public switched telephone network (PSTN). Your users can use their own
dedicated phone numbers for placing and receiving domestic and international
phone calls from Teams client applications, with advanced features that include
voicemail and emergency calling (enhanced 911).

**[!NOTE]** To learn more about the features for calling in Teams, review the
[Skype for Business to Microsoft Teams Capabilities
Roadmap](https://aka.ms/skype2teamsroadmap).

##Phone System in Teams

For Teams users to be able to place and receive PSTN calls, they need to be
enabled for Phone System, a feature in Office 365.

To enable connectivity to the PSTN, your organization can use Microsoft as its
telecommunications service provider. Eventually, you’ll also have the option to
“bring your own” telecommunications service provider to enable connectivity to
PSTN for Phone System.

**[!MPORTANT]** The ability to choose your own telecommunications service
provider for Phone System will be available in the future. To learn more about
the projected timeline, please review the [Skype for Business to Microsoft Teams
Capabilities Roadmap](https://aka.ms/skype2teamsroadmap).

##Phone System with Calling Plans

To use Microsoft as your telecommunications service provider, you need to obtain
Calling Plan licenses and assign them to your Phone System users.

There are two major types of calling plans:

-   Domestic calling plan

-   Domestic and international calling plan

Each type of calling plan allocates a certain number of call minutes per month
to each user who has been assigned the license. When the call minutes allocation
is exhausted, the user won’t be able to place outbound calls—except for
emergency calls—until the next month’s billing cycle. If you want users to be
able to continue to place outbound call even after they’ve exhausted their
allocation of call minutes, or to let users who have a domestic calling plan
place international calls, you can set up Communications Credits for your
organization.

##Availability of Calling Plans

Before you plan for the implementation of Calling Plans in Teams, verify that
the Calling Plans service is available in your area by reviewing [Country and
region availability for Audio Conferencing and Calling
Plans](https://docs.microsoft.com/SkypeForBusiness/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans).

**[!IMPORTANT]** Due to legal constraints, for Calling Plans to be available to
multinational organizations, the contract for Office 365 subscriptions must be
based in a country or region where the Calling Plans service is available, or
where the Calling Plans service can be purchased.

After confirming that your organization can obtain the Calling Plans service,
compile the list of user locations or offices where you’ll be implementing the
Calling Plans service, based on the list of available countries and regions.

| [./media/image1.png](./media/image1.png) |
|------------------------------------------|


~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image7.png

    Decision points

    Decide which user locations or offices you’ll implement the Calling Plans
    service in.

| [./media/image2.png](./media/image2.png) | Next steps | Document the user locations or offices to be enabled for the Calling Plans service. |   |
|------------------------------------------|------------|-------------------------------------------------------------------------------------|---|


~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image9.png

Below is an example of a Phone System with Calling Plans site enablement list.

| Office                         | Location       | PSTN system service             |
|--------------------------------|----------------|---------------------------------|
| One Epping Road                | Australia      | Legacy PSTN service             |
| 100 Cyberport Road             | Hong Kong SAR  | Legacy PSTN service             |
| One Marina Boulevard           | Singapore      | Legacy PSTN service             |
| 32 London Bridge Street        | United Kingdom | Phone System with Calling Plans |
| 39 quai du Président Roosevelt | France         | Phone System with Calling Plans |

##Phone numbers and emergency locations

With Calling Plans in Office 365, every user in your organization needs to have
a unique direct inward dialing (DID) phone number and a corresponding validated
emergency address. Review “Managing cloud voice telephone numbers, [Provide
Link]” to plan the phone number acquisition for your Calling Plans
implementation.

When you’re configuring phone numbers for Calling Plans, you must assign an
emergency address to each telephone number before you assign the number to a
user. This is required to support emergency calling. The emergency address must
be validated to ensure that it’s in the correct format to be used by emergency
response services.

**[!IMPORTANT**]Emergency Services calling operates differently in the Calling
Plans service than in traditional telephone services. It’s important that you
understand these differences and communicate them to all users. See [Emergency
Calling Terms and
Conditions](https://docs.microsoft.com/en-us/skypeforbusiness/what-are-calling-plans-in-office-365/emergency-calling-terms-and-conditions)
for more details.

In addition to supplying a validated emergency address, you can define emergency
locations and associate them with the validated emergency address to give a more
exact location within an address. An emergency location is typically a building
number, floor, building wing, or office number where the user is located.

To learn more about emergency locations in relation to Calling Plans, review the
following articles:

-   [What are emergency locations, addresses and call
    routing?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-emergency-locations-addresses-and-call-routing)

-   [Emergency calling terms and
    conditions](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/emergency-calling-terms-and-conditions)

| Decision points | Decide the granularity of emergency location information to be collected for user locations or offices in scope for the Calling Plans implementation. |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| Next steps      | Document the detailed emergency address and emergency locations for each user location or office in scope for the Calling Plans implementation        |

You can use the following template to document the details of phone numbers and
emergency location details.

| User             | Emergency location and address                                           | Phone number       |
|------------------|--------------------------------------------------------------------------|--------------------|
| Emily Braun      | 1034/32 London Bridge Street, London, SE1, United Kingdom                | \+44 23 4567 8901  |
| Lidia Holloway   | 1065/32 London Bridge Street, London, SE1, United Kingdom                | \+44 23 4567 89112 |
| Louis Lahr       | 1023/32 London Bridge Street, London, SE1, United Kingdom                | \+44 23 4567 8921  |
| Marcel Beauchamp | 07E15D/39 quai du Président Roosevelt, 92130 Issy-les-Moulineaux, France | TBA                |
| Rachelle Cormier | 07N15D/39 quai du Président Roosevelt, 92130 Issy-les-Moulineaux, France | TBA                |
| Isabell Potvin   | 07F05E/39 quai du Président Roosevelt, 92130 Issy-les-Moulineaux, France | TBA                |

##Voicemail

Phone System voicemail, powered by Azure Voicemail services, supports voicemail
deposits to Exchange mailboxes only and doesn’t support third-party email
systems.

By default, Phone System voicemail works with Exchange Online; however it has a
minimum supported Exchange on-premises version and deployment model to allow
delivery of voicemail messages to user mailboxes in the on-premises Exchange
deployment.

Phone System voicemail includes voicemail transcription, which is enabled for
all users in your organization by default. Your business needs might require
that you disable voicemail transcription for specific users or everyone
throughout the organization. See [Setting voicemail policies in your
organization](https://docs.microsoft.com/en-us/SkypeForBusiness/what-is-phone-system-in-office-365/phone-system-voicemail/set-up-phone-system-voicemail?ui=en-US&rs=en-US&ad=US#setting-voicemail-policies-in-your-organization)
for more details.

**[!NOTE]** A fallback mechanism has been implemented so that Phone System
voicemail can resend messages by using SMTP, which means users who have a
mailbox on a third-party email system will receive their voicemail messages.
This mechanism doesn’t include guaranteed service uptime or other voicemail
features, such as changing voicemail greeting.

For more information about voicemail in a Phone System implementation, see
[Azure PBX voicemail support for Exchange
Server](https://docs.microsoft.com/MicrosoftTeams/phone-system-with-calling-plans#licensing-for-calling-plans).

| Decision points | Decide whether you’ll enable Phone System voicemail in your Calling Plans implementation. |
|-----------------|-------------------------------------------------------------------------------------------|


-   If using Exchange on-premises and your existing deployment doesn’t meet your
    requirements to support Phone System voicemail, choose from the available
    options (upgrade and setup for Phone System voicemail support, migrate to
    Exchange Online, or leverage the fallback mechanism described earlier).

    -   Decide whether you’ll enable or disable voicemail transcription
        throughout the organization or for specific users.

| Next steps | If applicable, document the Exchange decision points to support Phone System voicemail. |   |   |
|------------|-----------------------------------------------------------------------------------------|---|---|


-   If you’ll enable voicemail and voicemail transcription only for specific
    users, document that list of users.

Phone System voicemail details for the Phone System with Calling Plans
implementation can be documented as the following:

| User             | Exchange mailbox | Enable voicemail? | Voicemail transcription |
|------------------|------------------|-------------------|-------------------------|
| Emily Braun      | Online           | Yes               | Enabled                 |
| Lidia Holloway   | Online           | Yes               | Enabled                 |
| Louis Lahr       | On-premises      | Yes               | Enabled                 |
| Marcel Beauchamp | On-premises      | Yes               | Disabled                |
| Rachelle Cormier | Online           | Yes               | Disabled                |
| Isabell Potvin   | On-premises      | Yes               | Disabled                |

##Calling identity

By default, all outbound calls use the assigned phone number as calling identity
(Caller ID). The recipient of the call can quickly identify the caller and
decide whether to accept or reject the call. In some cases, there are legitimate
business requirements to mask the Caller ID to protect the identity of callers
by using the office main line number—this is typically a service number serviced
by the Auto Attendant configuration—as Caller ID, or to block Caller ID
presentation altogether.

| Decision points | Decide whether Caller ID manipulation is required for your Calling Plans implementation. |
|-----------------|------------------------------------------------------------------------------------------|


-   If applicable, decide the types of Caller ID manipulation (mask with service
    number or anonymize) to be implemented.

    -   If applicable, decide which users require Caller ID manipulation and the
        type of Caller ID manipulation to be assigned to each user.

| Next steps | Document the users to be assigned Caller ID manipulation and the type of Caller ID manipulation to assign. |   |   |
|------------|------------------------------------------------------------------------------------------------------------|---|---|


The following is an example of Caller ID masking details documentation.

| User             | Enable outbound Caller ID masking | Caller ID masking type                   | Allow user override | Enable inbound Caller ID masking |
|------------------|-----------------------------------|------------------------------------------|---------------------|----------------------------------|
| Emily Braun      | No                                | N/A                                      | Yes                 | No                               |
| Lidia Holloway   | Yes                               | Service number (OrgAA, +44 20 7946 0000) | No                  | Yes                              |
| Louis Lahr       | No                                | N/A                                      | Yes                 | No                               |
| Marcel Beauchamp | Yes                               | Service number (OrgAA, TBA)              | No                  | Yes                              |
| Rachelle Cormier | Yes                               | Anonymize                                | Yes                 | No                               |
| Isabell Potvin   | Yes                               | Service number (OrgAA, TBA)              | No                  | Yes                              |

##Licensing for cloud voice capabilities

Audio Conferencing and Phone System are features in Office 365. They can be
licensed separately as add-on services for existing customers who have Office
365 E3 or E1 subscription plans; they’re already included as part of the Office
365 E5 subscription plan.

Calling Plans is an add-on to the Phone System feature in Office 365, so you
must have a Phone System licensed enabled to use Calling Plans.

To support for additional Audio Conferencing and Calling Plans use cases
(international conference dial-out, external calling after Calling Plan minute
allocations are exhausted, and so on), you can set up Communications Credits for
your organization.

##Licensing for Calling Plans

If your organization intends to use Microsoft as telecommunications service
provider, you need to obtain Calling Plan add-ons appropriate to your users’
business requirements. Generally, not everybody in an organization needs to
place international calls, so you can provision most users with domestic Calling
Plan licenses.

There are two types of Calling Plan licenses:

-   Domestic Calling Plan

-   International and Domestic Calling Plan

**[!NOTE]** What is considered “domestic” for a specific user is determined by
the user’s assigned Office 365 usage location.

Each Calling Plan type provides an allocation of calling minutes that users can
use per month, either to make domestic calls or international calls. The
Domestic Calling Plan costs less compared to the International and Domestic
Calling Plan.

The flexibility of subscribing and assigning the most appropriate Calling Plan
type for individual users’ business requirements helps your organization control
the costs of its Calling Plans implementation.

For each Office 365 tenant, the combined number of calling minutes are pooled by
country or region, and per Calling Plan type. When the monthly calling minutes
cap for the tenant is reached, Calling Plans service (except for emergency
calling) will be suspended for the remainder of the month. The Calling Plans
service will resume automatically on the first day of the next calendar month.

You can set up Communications Credits for your organizations to enable users to
make outbound calls after the allocation of calling minutes is exhausted without
having to wait until the next month billing cycle. Additionally, Communications
Credits give users assigned the Domestic Calling Plan the ability to make
international calls, which are then charged by using a “pay-per-minute” model.

To learn more about Phone System and Calling Plans, review the following
articles:

-   [Phone System](https://products.office.com/skype-for-business/phone-system)

-   [Calling
    Plans](https://products.office.com/skype-for-business/calling-plans)

| Decision points | If your organization doesn’t have the required Phone System license, decide whether you’ll acquire the Phone System license by stepping up your existing Office 365 subscriptions or by acquiring the Phone System add-on service. |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|


    -   Decide which users require a Domestic Calling Plan license and which
        require a Domestic and International Calling Plan license.

        -   Decide whether you’ll need Communications Credits for your Calling
            Plans implementation.

| Next steps | Document the division, department, office, or user groups you’ll assign a Phone System license with Domestic Calling Plan or Domestic and International Calling Plan. |   |   |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|


You can use the following example to document the license assignment for Phone
System with Calling Plans users.

| User             | Office                         | Office 365 License                 | Calling Plan                            |
|------------------|--------------------------------|------------------------------------|-----------------------------------------|
| Emily Braun      | 32 London Bridge Street        | Office 365 E5                      | International and Domestic Calling Plan |
| Lidia Holloway   | 32 London Bridge Street        | Office 365 E5                      | Domestic Calling Plan                   |
| Louis Lahr       | 32 London Bridge Street        | Office 365 E5                      | Domestic Calling Plan                   |
| Marcel Beauchamp | 39 quai du Président Roosevelt | Office 365 E3, Phone System add-on | Domestic Calling Plan                   |
| Rachelle Cormier | 39 quai du Président Roosevelt | Office 365 E5                      | International and Domestic Calling Plan |
| Isabell Potvin   | 39 quai du Président Roosevelt | Office 365 E3, Phone System add-on | Domestic Calling Plan                   |

##Communications Credits

Using Communications Credits, your users can dial out from an Audio Conferencing
meeting to add someone else from anywhere in the world (outside of the
originating country of the meeting organizer). You can set up Communications
Credits for your organization to enable users to make outbound calls after
they’ve exhausted their allocation of calling minutes, without having to wait
until the next month’s billing cycle. Additionally, Communications Credits give
users assigned with the Domestic Calling Plan the ability to make international
calls, which are then charged by using a “pay-per-minute” model.

The first consideration to make when implementing Communications Credits is to
decide the initial amount of funds to be purchased. If your organization chooses
to use auto-recharge, you’ll determine the optimal amount by measuring actual
usage. Monitor your Communications Credits usage over time, and adjust your
recharge amount as required.

For your Calling Plans implementation, you can control the use of Communications
Credits on a per-user basis, which helps you ensure that you’ve assigned these
credits in alignment with your business needs.

To learn more about Communications Credits, review [What are Communications
Credits?](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/what-are-communications-credits).

| Decision points | Decide whether you need Communications Credits for your Audio Conferencing or Calling Plans implementation. |
|-----------------|-------------------------------------------------------------------------------------------------------------|
| Next steps      | Document the division, department, office, or user groups you’ll enable Communications Credits for.         |

-   Document your Communications Credits plan for your Audio Conferencing or
    Calling Plans implementation.

You use the following example to document the Communications Credits assignment
list for Calling Plans users.

| User             | Office                         | Calling Plan                            | Communications Credits |
|------------------|--------------------------------|-----------------------------------------|------------------------|
| Emily Braun      | 32 London Bridge Street        | International and Domestic Calling Plan | Enabled                |
| Lidia Holloway   | 32 London Bridge Street        | Domestic Calling Plan                   | Disabled               |
| Louis Lahr       | 32 London Bridge Street        | Domestic Calling Plan                   | Enabled                |
| Marcel Beauchamp | 39 quai du Président Roosevelt | Domestic Calling Plan                   | Disabled               |
| Rachelle Cormier | 39 quai du Président Roosevelt | International and Domestic Calling Plan | Enabled                |
| Isabell Potvin   | 39 quai du Président Roosevelt | Domestic Calling Plan                   | Disabled               |

Your Communications Credits planning numbers can be documented as in the
following example.

| Initial amount       | \$1,000 |
|----------------------|---------|
| Trigger amount       | \$400   |
| Auto-recharge amount | TBA     |

##Manage cloud voice telephone numbers

If you implement Phone System by bringing your own telecommunications service
provider, telephone number management will remain as-is.

For Audio Conferencing and Calling Plans implementations, you can choose to
acquire new telephone numbers or transfer (port) existing telephone numbers.

To let users dial phone numbers the way they’re accustomed to—such as omitting
area codes for local calls, omitting country code for domestic calls, or even
using short-digit dialing when performing conference dial-out or calling other
users in the organization—you can configure a customized dial plan and assign it
to users.

##Acquire new telephone numbers

The two types of telephone numbers in Microsoft cloud voice solutions are:

-   Subscriber (user) numbers, which can be assigned to users in your
    organization.

-   Service numbers, available as toll and toll-free service numbers, which have
    higher concurrent call capacity than subscriber numbers and can be assigned
    to services such as Audio Conferencing, Auto Attendants, or Call Queues.

For more information about the types of telephone numbers, see [Different kinds
of phone numbers used for Calling
Plans](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/different-kinds-of-phone-numbers-used-for-calling-plans).

The total count of telephone numbers that you can obtain depend on the type of
telephone number and the number of licenses you’ve bought and assigned to your
users.

For more information about the total count of telephone numbers that you can
obtain, see [How many phone numbers can you
get?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/how-many-phone-numbers-can-you-get)

| Decision points | Decide the user locations or offices where new telephone numbers will be acquired from Microsoft. |
|-----------------|---------------------------------------------------------------------------------------------------|


-   Decide the type of telephone numbers to be acquired from Microsoft.

| Next steps | Document the user locations or offices where new telephone numbers will be acquired from Microsoft. |   |
|------------|-----------------------------------------------------------------------------------------------------|---|


-   Document the type of telephone numbers to be acquired from Microsoft.

##Transfer existing telephone numbers

If your organization wants to transfer (or port) existing telephone numbers to
Microsoft, you can do so by submitting a port order request to Microsoft.

You can transfer all your existing telephone numbers at once (full port), and—in
some markets—you can transfer a subset of your existing telephone numbers
(partial port). A partial port can be useful in cases where you just want to
gradually move your users to Phone System with Calling Plans.

A single port order can only transfer the telephone numbers to a single
telephone number type. If you need to transfer some of your telephone numbers as
subscriber numbers and some as service numbers, we recommend that you first
complete the transfer to Microsoft and then perform the conversion as soon as
the numbers are in Microsoft’s control.

As an alternative (if partial port is supported), you can submit multiple port
requests, one port request at a time. However, this alternative approach will
prolong your contract with your existing telecommunications service provider.

Telephone number porting is a complex topic and requires thorough planning,
coordination, and adequately managing your stakeholders’ expectations. To learn
more, see the following articles:

-   [Transferring phone numbers to Office
    365](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/transfer-phone-numbers-to-office-365)

-   [Transferring phone numbers common
    questions](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/transferring-phone-numbers-common-questions)

| Decision points | Decide the user locations or offices where existing telephone numbers will be transferred to Microsoft. |
|-----------------|---------------------------------------------------------------------------------------------------------|


    -   Decide the type of telephone numbers to be transferred to Microsoft.

| Next steps | Document the user locations or offices where existing telephone numbers will be transferred to Microsoft. |   |
|------------|-----------------------------------------------------------------------------------------------------------|---|


-   Document the type of telephone numbers to be transferred to Microsoft.

##Dial plans

A Dial Plan in the Phone System feature of Office 365 is a set of normalization
rules that translate dialed phone numbers into an alternate format (typically
E.164 format) for call authorization and call routing. The Audio Conferencing
service leverages the same capabilities used by Phone System to translate dialed
phone numbers in conference dial-out scenarios (for example, invite participants
via PSTN and dial back, “call me” feature).

In the Phone System feature of Office 365, there are two types of dial plans:

-   **Service dial plan:** This is the default dial plan that’s applied to users
    based on their Office 365 usage location, and it can’t be modified.

-   **Tenant dial plan:** This is a customizable dial plan within a tenant,
    which is further divided into two types:

    -   **Tenant-global dial plan:** The dial plan that applies to all users in
        the tenant.

    -   **Tenant-user dial plan:** The dial plan that applies only to specific
        users.

The effective dial plan assigned to users is the combination of the service dial
plan (based on a user’s Office 365 usage location) and tenant dial plan (which
can be either a tenant-global dial plan or tenant-user dial plan).

![Diagram describing the effective dial plan applied to users based on tenant dial-plan components. ](media/925581d6f2b12ccc77595722be469e02.png)

**[!IMPORTANT]** There can be a maximum of 25 normalization rules in each tenant
dial plan; therefore, it’s important to avoid duplicating normalization rules
that are already available as part of the service dial plan.

For more information about dial plans, see [What are dial
plans?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-dial-plans)

| Decision points | Decide whether your organization requires customized dial plans (business requirements, adoption requirements, and so on). |
|-----------------|----------------------------------------------------------------------------------------------------------------------------|


-   If applicable, decide the scope of the tenant dial plan (tenant-global or
    tenant-user) to support your requirements for customized dial plans.

    -   If applicable, decide the tenant dial plans that you’ll create to
        support user locations or offices in scope for the cloud voice
        implementation.

        -   If applicable, decide which users require a customized dial plan and
            the tenant dial plan to be assigned for each user.

| Next steps | Document the customized dial plans and the associated normalization rules to be configured as part of cloud voice implementation. |   |   |   |
|------------|-----------------------------------------------------------------------------------------------------------------------------------|---|---|---|


-   Document the users to be assigned a customized dial plan and the tenant dial
    plan to be assigned for each user.

If it’s applicable to your project, you can use the following example as a
template to document the tenant dial plans configurations.

| Tenant Dial Plan Name                                                                          | Normalization Rules Name                                                                                                       | Pattern                                                  |
| *Description*                                                                                  | *Description*                                                                                                                  | Translation                                              |
|                                                                                                |                                                                                                                                | IsInternalExtension                                      |
|------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| **AU-NSW-NorthRyde-OER**                                                                       | **AU-NSW-NorthRyde-OER-Internal**                                                                                              | \^(7\\d{3})\$                                            |
| *One Epping Road North Ryde, NSW, AU Dial Plan*                                                | *Internal number (x7000 - x7999) for One Epping Road office, North Ryde, NSW, Australia*                                       | +6125550\$1                                              |
|                                                                                                |                                                                                                                                | True                                                     |
|                                                                                                | **AU-NSW-Local**                                                                                                               | \^([2-9]\\d{7})\$                                        |
|                                                                                                | *Local number normalization for NSW, Australia*                                                                                | +612\$1                                                  |
|                                                                                                |                                                                                                                                | False                                                    |
|                                                                                                | **AU-TollFree**                                                                                                                | \^(1[38]\\d{4,8})\\d\*\$                                 |
|                                                                                                | *Toll Free number normalization for Australia*                                                                                 | +61\$1                                                   |
|                                                                                                |                                                                                                                                | False                                                    |
|                                                                                                | **AU-Service**                                                                                                                 | \^(000\|1[0125]\\d{1,8})\$                               |
|                                                                                                | *Service number normalization for Australia*                                                                                   | \$1                                                      |
|                                                                                                |                                                                                                                                | False                                                    |
| **SG-Singapore-OMB**                                                                           | **SG-OMB-Internal**                                                                                                            | \^(8\\d{3})\$                                            |
| *OMB Singapore, SG Dial Plan*                                                                  | *Internal number (x8000 – x8999) for OMB office, Singapore*                                                                    | +656888\$1                                               |
|                                                                                                |                                                                                                                                | True                                                     |
|                                                                                                | **SG-TollFree**                                                                                                                | \^(1?800\\d{7})\\d\*\$                                   |
|                                                                                                | *Toll Free number normalization for Singapore*                                                                                 | +65\$1                                                   |
|                                                                                                |                                                                                                                                | False                                                    |
|                                                                                                | **SG-Service**                                                                                                                 | \^(1\\d{3,4}\|9\\d{2})\$                                 |
|                                                                                                | *Service number normalization for Singapore*                                                                                   | \$1                                                      |
|                                                                                                |                                                                                                                                | False                                                    |
| **FR-Paris-Issy-39qdPR**                                                                       | **FR-39qdPR-Internal**                                                                                                         | \^(7\\d{3})\$                                            |
| *39 quai du Président Roosevelt Issy-les-Moulineaux, France Dial Plan*                         | *Internal number (x7000 – x7999) for 39 quai du Président Roosevelt office, Issy-les-Moulineaux, France*                       | +3319999\$1                                              |
|                                                                                                |                                                                                                                                | True                                                     |
|                                                                                                | **FR-TollFree**                                                                                                                | \^0?(80\\d{7})\\d\*\$                                    |
|                                                                                                | *Toll Free number normalization for France*                                                                                    | +33\$1                                                   |
|                                                                                                |                                                                                                                                | False                                                    |
|                                                                                                | **FR-Service**                                                                                                                 | \^(1\\d{1,2}\|11[68]\\d{3}\|10\\d{2}\|3\\d{3})\$         |
|                                                                                                | *Service number normalization for France*                                                                                      | \$1                                                      |
|                                                                                                |                                                                                                                                | False                                                    |

You can use the example below to document dial plan assignments to support your
project.

| User             | Office                         | Dial Plan Type    | Dial Plan Name       |
|------------------|--------------------------------|-------------------|----------------------|
| Adele Vance      | One Epping Road                | Tenant dial plan  | AU-NSW-NorthRyde-OER |
| Alex Wilber      | One Epping Road                | Tenant dial plan  | AU-NSW-NorthRyde-OER |
| Ben Walters      | One Epping Road                | Tenant dial plan  | AU-NSW-NorthRyde-OER |
| Christie Cline   | One Marina Boulevard           | Tenant dial plan  | SG-Singapore-OMB     |
| Debra Berger     | One Marina Boulevard           | Tenant dial plan  | SG-Singapore-OMB     |
| Lee Gu           | One Marina Boulevard           | Tenant dial plan  | SG-Singapore-OMB     |
| Emily Braun      | 32 London Bridge Street        | Service dial plan | N/A                  |
| Lidia Holloway   | 32 London Bridge Street        | Service dial plan | N/A                  |
| Louis Lahr       | 32 London Bridge Street        | Service dial plan | N/A                  |
| Marcel Beauchamp | 39 quai du Président Roosevelt | Tenant dial plan  | FR-Paris-Issy-30qdPR |
| Rachelle Cormier | 39 quai du Président Roosevelt | Tenant dial plan  | FR-Paris-Issy-30qdPR |
| Isabell Potvin   | 39 quai du Président Roosevelt | Tenant dial plan  | FR-Paris-Issy-30qdPR |
