#Make my service decisions

To plan for the technical implementation of Audio Conferencing, you must make a
series of service decisions ahead of time to better prepare your organization to
implement a solution that meets your defined business requirements.

As part of defining required Audio Conferencing features in Microsoft Teams, one
of the first steps is to evaluate the latest public roadmap to determine:

-   Which Audio Conferencing features in Teams that will be deployed for users
    in scope.

-   Expected user functionality requirements for Audio Conferencing in Teams.

-   Confirmation that Audio Conferencing features in Teams described in the
    latest public roadmap meet your user, functionality, and scope requirements,
    within the timeline of your deployment.

[!TIP] The latest Teams roadmap for identifying Teams Audio Conferencing
features in scope for your deployment can be found at
<https://aka.ms/skype2teamsroadmap>.

##Meetings in Teams

Teams gives your users the capability to schedule and join online meetings by
using HD video, voice over IP (VoIP), and PSTN dial-in conferencing options.

Meetings can be scheduled as private meetings (only invited parties can join) or
channel meetings (open for all users having access to the channel), and your
users can also start impromptu meetings within channels.

[!NOTE] To learn more about the features of meetings in Teams, see the [Skype
for Business to Microsoft Teams Capabilities
Roadmap](https://aka.ms/skype2teamsroadmap).

Meeting participants can join your Teams meetings by dialing in to the toll or
toll-free dial-in conference bridge phone numbers via landlines or mobile
phones. In addition, users can let the Audio Conferencing service initiate the
“call me” feature so they can participate in a meeting by having the conference
bridge call their phones (useful when the data connection isn’t reliable), or
let meeting organizers invite meeting participants by dialing out to their
phones.

[!IMPORTANT] Audio Conferencing in Teams doesn’t support third-party audio
conferencing providers.

##Availability of Audio Conferencing

Before you plan for the implementation of Audio Conferencing in Teams, you need
to review the availability of the Audio Conferencing service as detailed in
[Country and region availability for Audio Conferencing and Calling
Plans](https://docs.microsoft.com/SkypeForBusiness/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans).

[!IMPORTANT] Due to legal constraints, for Audio Conferencing to be available to
multinational organizations, the contract for Office 365 subscriptions must be
sourced from countries and regions where the Audio Conferencing service is
commercially available.

After confirming your organization is eligible to obtain the Audio Conferencing
service, compile the list of user locations or offices where you’ll implement
the Audio Conferencing service, based on the list of available countries and
regions.

| [./media/image1.png](./media/image1.png) |
|------------------------------------------|


~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image7.png

    Decision points

    Decide which user locations or offices will implement the Audio Conferencing
    service.

| [./media/image2.png](./media/image2.png) | Next steps | Document the user locations or offices to be enabled for the Audio Conferencing service. |   |
|------------------------------------------|------------|------------------------------------------------------------------------------------------|---|


~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image9.png

Below is an example of Audio Conferencing site enablement list template.

| **Office**                     | **Location**   | **PSTN conference service** |
|--------------------------------|----------------|-----------------------------|
| One Epping Road                | Australia      | Audio Conferencing          |
| 100 Cyberport Road             | Hong Kong SAR  | Legacy PSTN conferencing    |
| One Marina Boulevard           | Singapore      | Audio Conferencing          |
| 32 London Bridge Street        | United Kingdom | Audio Conferencing          |
| 39 quai du Président Roosevelt | France         | Audio Conferencing          |

##Licensing for Audio Conferencing

An [Audio Conferencing
license](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing)
is available as part of Office 365 E5 subscription plans, or as an add-on
service to Office 365 E1 or Office 365 E3 subscription plans.

[!NOTE]PSTN or dial-in conferencing in Teams doesn’t support third-party audio
conferencing providers (ACPs).  
If you already use Skype for Business Online PSTN Conferencing today, you can
immediately take advantage of Audio Conferencing in Teams.

To provide toll-free conference bridge phone numbers and to support conferencing
dial-out to international phone numbers, you must set up [Communications
Credits](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/what-are-communications-credits)
for your organization.

[!IMPORTANT] Some countries are serviced by toll-free conference bridge phone
numbers only. To support dial-in in these countries, you must use Communications
Credits.

The first consideration when implementing Communications Credits is to decide
the initial amount of funds you want to purchase. For recommended funding
amounts, see [Communications
Credits](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/what-are-communications-credits).

If your organization chooses to use auto-recharge, you can find a recommendation
for the trigger (lowest amount of funds) in [Communications
Credits](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/what-are-communications-credits).
Your actual usage will determine the auto-recharge amount. You should monitor
your Communications Credits usage over time and adjust the recharge amount as
necessary.

| [./media/image1.png](./media/image1.png) | Decision points | If your organization hasn’t already purchased the required Audio Conferencing licensing, decide whether you’ll acquire Audio Conferencing licenses by stepping up existing Office 365 subscriptions or by acquiring Audio Conferencing add-on licenses. |
|------------------------------------------|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [./media/image2.png](./media/image2.png) | Next steps      | Document the users who will be assigned Audio Conferencing licenses.                                                                                                                                                                                    |

~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image7.png

-   Decide whether Communications Credits are required for your Audio
    Conferencing implementation. If so, decide the initial amount of funds to be
    purchased. Where applicable, decide the trigger amount and auto-recharge
    amount.

~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image9.png

-   Document the Communications Credits plan (initial amount, trigger amount,
    auto-recharge amount)

[!TIP] You can document the license assignment list for Audio Conferencing users
by using the following example.

| User             | Office                         | Office 365 License                       |
|------------------|--------------------------------|------------------------------------------|
| Adele Vance      | One Epping Road                | Office 365 E5                            |
| Alex Wilber      | One Epping Road                | Office 365 E3, Audio Conferencing add-on |
| Ben Walters      | One Epping Road                | Office 365 E3, Audio Conferencing add-on |
| Christie Cline   | One Marina Boulevard           | Office 365 E3, Audio Conferencing add-on |
| Debra Berger     | One Marina Boulevard           | Office 365 E5                            |
| Lee Gu           | One Marina Boulevard           | Office 365 E5                            |
| Emily Braun      | 32 London Bridge Street        | Office 365 E5                            |
| Lidia Holloway   | 32 London Bridge Street        | Office 365 E5                            |
| Pradeep Gupta    | 32 London Bridge Street        | Office 365 E5                            |
| Marcel Beauchamp | 39 quai du Président Roosevelt | Office 365 E3, Audio Conferencing add-on |
| Rachelle Cormier | 39 quai du Président Roosevelt | Office 365 E5                            |
| Isabell Potvin   | 39 quai du Président Roosevelt | Office 365 E3, Audio Conferencing add-on |

[!TIP] Your Communications Credits planning numbers can be documented as in the
following example.

| Initial amount       | \$1,000 |
|----------------------|---------|
| Trigger amount       | \$400   |
| Auto-recharge amount | TBA     |

##Conference bridge phone numbers

The Audio Conferencing service in Office 365 includes:

-   Multiple types of conference bridge phone numbers (toll and toll-free)

-   Multiple categories of conference bridge phone numbers (dedicated and
    shared)

-   Support for multiple languages for the conference bridge (primary and
    secondary)

-   A default phone number for the tenant

[!NOTE] Dedicated conference bridge phone numbers count toward the limit of
phone numbers that can be acquired per tenant, based on the number of applicable
licenses. Toll-free conference bridge phone numbers require Communications
Credits.

If you must transfer existing conference bridge phone numbers to the Audio
Conferencing service—assuming they meet country-specific requirements—you can
transfer these existing conference bridge phone numbers to Microsoft.

[!NOTE] The complexity of transferring phone numbers to Microsoft varies greatly
depending on country or region, carrier, number of circuits involved, and many
other contributing factors. Work with your current provider to investigate how
long this is likely to take to help ensure that you start the process early
enough to meet your timelines.

To learn more about conference bridge phone numbers, review the following
articles:

-   [Set up Audio Conferencing for Skype for Business and Microsoft
    Teams](https://docs.microsoft.com/SkypeForBusiness/audio-conferencing-in-office-365/set-up-audio-conferencing)

-   [Phone numbers for Audio
    Conferencing](https://docs.microsoft.com/SkypeForBusiness/audio-conferencing-in-office-365/phone-numbers-for-audio-conferencing)

-   [Getting service phone
    numbers](https://docs.microsoft.com/SkypeForBusiness/what-is-phone-system-in-office-365/getting-service-phone-numbers)

-   [Transfer phone numbers to Office
    365](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/transfer-phone-numbers-to-office-365)

| [./media/image1.png](./media/image1.png) |
|------------------------------------------|


    ~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image7.png

        Decision points

        Decide whether your organization needs dedicated conference bridge phone
        numbers.

        -   Decide how the dedicated conference bridge phone numbers will be
            obtained for user locations or offices in-scope for the Audio
            Conferencing implementation (that is, obtain from Microsoft or
            transfer existing phone numbers).

            -   If you choose to obtain them from Microsoft, decide the method
                to use (form submission or automated) for user locations or
                offices in-scope for the Audio Conferencing implementation.

            -   Decide the language preferences to set up for each dedicated
                conference bridge phone number.

            -   Decide the tenant default conference bridge phone number.

| [./media/image2.png](./media/image2.png) | Next steps | Document the master plan for phone number acquisition, detailing how phone numbers will be obtained for each user location or office in scope for the Audio Conferencing implementation. |   |   |   |   |   |
|------------------------------------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|---|---|


~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image9.png

-   If applicable, complete the New Telephone Number Request form—one form for
    each location or office.

-   Document the detailed conference bridge phone number configurations (shared
    and dedicated conference bridge phone numbers, language preferences for each
    dedicated conference bridge phone number, tenant default conference bridge
    phone number).

Below is an example of a template you can use to capture conference bridge
details.

| Office                         | Bridge number acquisition and bridge type | Bridge number     | Bridge language                                    |
|--------------------------------|-------------------------------------------|-------------------|----------------------------------------------------|
| One Epping Road                | Acquire new, dedicated                    | TBA               | English (Australia)                                |
| One Marina Boulevard           | Acquire new, shared                       | TBA               | English (United States), Chinese (Simplified, PRC) |
| 32 London Bridge Street        | Port existing, dedicated                  | \+44 20 7946 0001 | English (United Kingdom)                           |
| 39 quai du Président Roosevelt | Acquire new, dedicated                    | TBA               | French (France), English (United Kingdom)          |

##Conference bridge settings

To further tailor the user experience, you can configure organization-wide
options for joining Audio Conferencing meetings (meeting entry and exit
notification and caller name recording), the meeting organizer’s PIN length, and
email notification:

-   Meeting entry and exit notifications are available in the form of recorded
    name, phone number, and tones.

-   PIN length is configurable from 4 to 12 digits, with a 5-digit PIN as the
    default.

-   Notification emails sent on enablement of the Audio Conferencing license or
    any other admin-driven change are enabled by default. You can disable this
    feature and take control of your organization’s user communications.

For users who are assigned an Audio Conferencing license, the default
toll/toll-free numbers, shown in the Audio Conferencing coordinates, can be
configured to use:

-   The tenant-level default.

-   The automatically assigned conference bridge phone numbers.

-   A conference bridge phone numbers configured manually for each user.

User-specific conference bridge phone numbers are typically useful in global or
nationwide organizations where users are distributed and must provide local
numbers as the default conference bridge phone numbers in their meeting
invitations.

Participants joining from different cities or overseas can look up additional
numbers configured at the tenant level, but these numbers don’t appear directly
in the meeting invitations. The meeting invitations provide a link that takes
participants to the **Teams Conference Dial-in Numbers** page for them to look
up the conference bridge phone number closest to their location.

You can also configure how unauthenticated callers are handled by each
individual meeting organizer—whether to require the meeting organizer to start
the meeting before unauthenticated callers can be admitted, or allow
unauthenticated callers to start a meeting.

You can also apply additional configurations for each user to control the use of
toll-free conference bridge phone numbers and dial-out from a conference.

[!NOTE] These cost-related controls are currently available for preview
customers only. You can enroll your organization in the preview program from
https://www.skypepreview.com.

With these controls, you can decide whether meeting organizers can provide
toll-free conference bridge phone numbers for meetings organized by them, and
whether participants can dial out from the meetings they organized. The level of
dial-out control spans from completely preventing dial out, to only allowing
dial out to domestic numbers, to allowing dial out to both domestic and
international numbers.

| [./media/image1.png](./media/image1.png) |
|------------------------------------------|


~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image7.png

    Decision points

    Decide whether your organization requires entry and exit notifications,
    and—if it does—the type of notification to be implemented (tones, phone
    number, or recorded name).

    -   Decide the Audio Conferencing PIN length that meets your organizational
        security requirements.

        -   Decide whether your organization wants to take control of user
            communications related to the Audio Conferencing service.

            -   Decide the conference bridge phone numbers to be assigned to
                each meeting organizer.

            -   Decide whether some meeting organizers need to use toll-free
                conference bridge phone numbers for their meetings.

            -   Decide whether some meeting organizers need to allow
                unauthenticated callers to start a meeting.

            -   Decide whether some meeting organizers need conference dial-out
                to be controlled.

| [./media/image2.png](./media/image2.png) | Next steps | Document the detailed conference bridge settings (entry and exit notifications, PIN length, configuration change email notification) |   |   |   |   |   |   |   |
|------------------------------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------|---|---|---|---|---|---|---|


~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image9.png

-   Document the conference bridge phone numbers to be assigned to each meeting
    organizer and the corresponding setting to control the policy for
    unauthenticated callers, and toll-free and dial out controls.

Your conference bridge settings can be documented as in the following example.

| Setting                                                             | Configuration |
|---------------------------------------------------------------------|---------------|
| Enable meeting entry and exit notifications                         | Enabled       |
| Entry/exit announcement type                                        | Tones         |
| Ask callers to record their name before joining the meeting         | Disabled      |
| PIN length                                                          | 5             |
| Automatically send emails to users if their dial-in settings change | Disabled      |

You can document the conference bridge settings assignment list for Audio
Conferencing users by using the following example.

| User             | Office                         | Default toll number | Default toll-free number | Allow toll-free | Unauthenticated callers bypass lobby | Conference dial out        |
|------------------|--------------------------------|---------------------|--------------------------|-----------------|--------------------------------------|----------------------------|
| Adele Vance      | One Epping Road                | TBA                 | TBA                      | Yes             | Enabled                              | International and domestic |
| Alex Wilber      | One Epping Road                | TBA                 | N/A                      | No              | Disabled                             | Not allowed                |
| Ben Walters      | One Epping Road                | TBA                 | N/A                      | No              | Disabled                             | Not allowed                |
| Christie Cline   | One Marina Boulevard           | TBA                 | TBA                      | Yes             | Disabled                             | Domestic                   |
| Debra Berger     | One Marina Boulevard           | TBA                 | TBA                      | Yes             | Enabled                              | Domestic                   |
| Lee Gu           | One Marina Boulevard           | TBA                 | TBA                      | Yes             | Enabled                              | Domestic                   |
| Emily Braun      | 32 London Bridge Street        | \+44 20 7946 0001   | TBA                      | Yes             | Enabled                              | Not allowed                |
| Lidia Holloway   | 32 London Bridge Street        | \+44 20 7946 0001   | TBA                      | Yes             | Disabled                             | Not allowed                |
| Pradeep Gupta    | 32 London Bridge Street        | \+44 20 7946 0001   | TBA                      | Yes             | Disabled                             | Not allowed                |
| Marcel Beauchamp | 39 quai du Président Roosevelt | TBA                 | N/A                      | No              | Disabled                             | Domestic                   |
| Rachelle Cormier | 39 quai du Président Roosevelt | TBA                 | TBA                      | Yes             | Enabled                              | International and domestic |
| Isabell Potvin   | 39 quai du Président Roosevelt | TBA                 | N/A                      | No              | Disabled                             | Domestic                   |

##Manage cloud voice telephone numbers

For Audio Conferencing implementation, you can choose to acquire new telephone
numbers or transfer/port existing telephone numbers.

To allow users to dial phone numbers the way they’re accustomed to—such as
omitting area codes for local calls, omitting country code for domestic calls,
or even using short digit dialing when performing conference dial out—you can
configure a customized dial plan and assign it to users.

##Acquire new telephone numbers

The two types of telephone numbers within Microsoft cloud voice solutions are:

-   Subscriber (user) numbers, which can be assigned to users in your
    organization.

-   Service numbers, available as toll and toll-free service numbers, which have
    higher concurrent call capacity than subscriber numbers and can be assigned
    to services such as Audio Conferencing, Auto Attendants, or Call Queues.

For more information about these types of telephone numbers, see [Different
kinds of phone numbers used for Calling
Plans](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/different-kinds-of-phone-numbers-used-for-calling-plans).

The total count of telephone numbers that you can obtain depend on the telephone
number types and the number of licenses you have bought and assigned to your
users.

When it comes to service numbers, you need to carefully plan your Audio
Conferencing implementation. Evaluate whether your business requires dedicated
conference bridge phone numbers; if not, your organization can opt to use shared
conference bridge phone numbers.

For more information about the total count of telephone numbers that you can
obtain, see [How many phone numbers can you
get?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/how-many-phone-numbers-can-you-get)

| [./media/image1.png](./media/image1.png) |
|------------------------------------------|


~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image7.png

    Decision points

    Decide the user locations or offices where new telephone numbers will be
    acquired from Microsoft.

    -   Decide the type of telephone numbers to be acquired from Microsoft.

| [./media/image2.png](./media/image2.png) | Next steps | Document the user locations or offices where new telephone numbers will be acquired from Microsoft. |   |   |
|------------------------------------------|------------|-----------------------------------------------------------------------------------------------------|---|---|


~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image9.png

-   Document the type of telephone numbers to be acquired from Microsoft.

##Transfer existing telephone numbers

If your organization wants to transfer (or port) existing telephone numbers to
Microsoft, you can do so by submitting a port order request to Microsoft.

You can transfer all your existing telephone numbers at once (full port), and—in
some markets—you can transfer a subset of your existing telephone numbers
(partial port). A partial port can be useful in cases where you just want to
move your dial-in conference bridge to Audio Conferencing service.

A single port order can only transfer the telephone numbers to a single
telephone number type. If you need to transfer some of your telephone numbers as
subscriber numbers and some as service numbers, we recommend that you first
complete the transfer to Microsoft and then perform the conversion as soon as
the numbers are within Microsoft’s control.

As an alternative, if partial port is supported, you can submit multiple port
requests, one port request at a time. However, this alternative approach will
prolong your contract with your existing telecommunications service provider.

Telephone number porting is a complex topic and requires thorough planning,
coordination, and adequately managing your stakeholders’ expectations. To learn
more, see the following articles:

-   [Transferring phone numbers to Office
    365](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/transfer-phone-numbers-to-office-365)

-   [Transferring phone numbers common
    questions](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/transferring-phone-numbers-common-questions)

| [./media/image1.png](./media/image1.png) |
|------------------------------------------|


    ~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image7.png

        Decision points

        Decide the user locations or offices where existing telephone numbers
        will be transferred to Microsoft.

        -   Decide the type of telephone numbers to be transferred to Microsoft.

| [./media/image2.png](./media/image2.png) | Next steps | Document the user locations or offices where existing telephone numbers will be transferred to Microsoft. |   |   |
|------------------------------------------|------------|-----------------------------------------------------------------------------------------------------------|---|---|


~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image9.png

-   Document the type of telephone numbers to be transferred to Microsoft.

##Dial plans

A Dial Plan in the Phone System feature of Office 365 is a set of normalization
rules that translates dialed phone numbers into an alternate format (typically
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
plan (based on a user’s Office 365 usage location) and tenant dial plan (can be
either tenant-global dial plan or tenant-user dial plan).

![Diagram describing the effective dial plan applied to users based on tenant dial-plan components. ](media/925581d6f2b12ccc77595722be469e02.png)

**[!Important]** There can be a maximum of 25 normalization rules in each tenant
dial plan; therefore, it’s important to avoid duplicating normalization rules
that are already available as part of the service dial plan.

To learn more about dial plans, see [What are dial
plans?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-dial-plans)

| [./media/image1.png](./media/image1.png) |
|------------------------------------------|


~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image7.png

    Decision points

    Decide whether your organization requires customized dial plans (business
    requirements, adoption requirements, and so on).

    -   If applicable, decide the scope of tenant dial plan (tenant-global or
        tenant-user) to support the requirements for customized dial plans.

        -   If applicable, decide the tenant dial plans that you’ll create to
            support user locations or offices in-scope for the cloud voice
            implementation.

            -   If applicable, decide which users require a customized dial plan
                and the tenant dial plan to be assigned for each user.

| [./media/image2.png](./media/image2.png) | Next steps | Document the customized dial plans and the associated normalization rules to be configured as part of your cloud voice implementation. |   |   |   |   |
|------------------------------------------|------------|----------------------------------------------------------------------------------------------------------------------------------------|---|---|---|---|


~   https://docs.microsoft.com/en-us/MicrosoftTeams/media/audio_conferencing_image9.png

-   Document the users to be assigned a customized dial plan and the tenant dial
    plan to be assigned for each user.

If it’s applicable to your project, you can use the following template to
document the tenant dial plan configurations.

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
| Pradeep Gupta    | 32 London Bridge Street        | Service dial plan | N/A                  |
| Marcel Beauchamp | 39 quai du Président Roosevelt | Tenant dial plan  | FR-Paris-Issy-30qdPR |
| Rachelle Cormier | 39 quai du Président Roosevelt | Tenant dial plan  | FR-Paris-Issy-30qdPR |
| Isabell Potvin   | 39 quai du Président Roosevelt | Tenant dial plan  | FR-Paris-Issy-30qdPR |

##Document service decisions 

Use the information from the previous sections of this article to document your
service decisions. In general, this documentation will contain the following
main sections:

-   Audio Conferencing service site enablement list

-   License assignment list for Audio Conferencing meeting organizers

-   Communications Credits planning numbers

-   Conference bridge details

-   Conference bridge settings

-   Conference bridge settings assignments

-   Tenant dial plans

-   Dial plan assignments
