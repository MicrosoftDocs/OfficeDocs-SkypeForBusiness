Environmental discovery for Microsoft Teams rollout
===================================================

Discovery is one of the very first, key steps that you take when planning for
your journey to Microsoft Teams.

You perform a detailed discovery of your environment to better understand its
current state and to reveal any difficulties or—even further—possible blockers
to the execution of your Teams rollout.

Discovery Questionnaire
=======================

The sample questionnaire below walks you through a set of questions to confirm
that your organization is ready for the successful rollout of Audio Conferencing
and Phone System with Calling Plans capabilities in Teams.

All matters related to your existing collaboration infrastructure and Office 365
tenant, networking, endpoints, operations, and adoption and readiness are
included as part of the environmental discovery questionnaire.

The questionnaire is divided into multiple sections to confirm your
organization’s readiness for your Teams deployment in several major areas. Work
with your project team to provide the requested information with as much detail
as possible to facilitate your planning activities.

> [!TIP]
> You can start by copying the questionnaire into a Microsoft Word document. Try to answer all questions and capture all details as you move through.

Project team
------------

Capture detailed information about the key stakeholders of your Teams rollout
project. Note that one person can play several roles throughout the project.

| Role                                  | Name, email address, phone number | Location, time zone | Comments      |
|---------------------------------------|-----------------------------------|---------------------|---------------|
| Executive Sponsor                     |                                   |                     |               |
| Project Lead                          |                                   |                     |               |
| Collaboration Lead/Architect          |                                   |                     |               |
| Consultant                            |                                   |                     |               |
| Project Manager                       |                                   |                     |               |
| Change Management/Adoption Specialist |                                   |                     |               |
| Network Lead                          |                                   |                     |               |
| Security Lead                         |                                   |                     |               |
| Telephony Lead                        |                                   |                     |               |
| Desktop Lead                          |                                   |                     |               |
| Support/Help Desk Lead                |                                   |                     |               |
| Deployment Lead                       |                                   |                     |               |
| Service Owner                         |                                   |                     |               |
| Facilities Lead                       |                                   |                     |               |
| Video Team Lead                       |                                   |                     |               |
| Business Unit Leads                   |                                   |                     |               |

Office 365 tenant details
-------------------------

We highly recommend that you have an active Office 365 tenant as you work with
this questionnaire. If you haven’t activated or configured an Office 365 tenant
yet, see [Plan your setup of Office 365 for business](https://support.office.com/article/plan-your-setup-of-office-365-for-business-eb926624-018b-4486-bf11-5fba6ee4d645).

- [ ] Use the following table to capture information about the Office 365 tenant.

| Question                                                                                                                                                   | Answer                                                                                                                                                                                         | Comments                          |
|------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------|
| Does your organization already have a production Office 365 tenant? <br/>If you have more than one tenant associated with your organization, note all the IDs.  | <ul><li> [ ] Yes</li></ul> <br/> No                                                                                                                                                                                        | Tenant Name: Tenant ID:           |
| In what regions are the tenants deployed?                                                                                                                  |                                                                                                                                                                                                |                                   |
| Are these tenants Office 365 Multitenant or Dedicated?                                                                                                     | Multitenant Dedicated                                                                                                                                                                          |                                   |
| Which Microsoft Online products are in use today? Note the number of users enabled for each service in the Comments column.                                | Microsoft Teams Skype for Business Online Exchange Online SharePoint Online OneDrive for Business Yammer Other                                                                                 |                                   |
| What license level is enabled for Skype for Business Online users?                                                                                         | E1/G1 E2/G2 E3/G3 E4/G4 E5                                                                                                                                                                     | The number of users for each SKU: |
| What is the current Active Directory forest functional level in the environment? If there’s more than one forest, note the details in the Comments column. | Windows Server 2000 Windows Server 2003 Windows Server 2008 Windows Server 2008 R2 Windows Server 2012 Windows Server 2012 R2 Windows Server 2016                                              |                                   |
| What are you using for directory synchronization today?                                                                                                    | No sync (cloud only) Azure Active Directory Connect Other (Specify in the Comments column.)                                                                                                    |                                   |
| Is federated identity currently deployed? (Active Directory Federation Service or third-party)                                                             | Yes No                                                                                                                                                                                         |                                   |
| If you’re using federated identity, what is the federation infrastructure?                                                                                 | Windows 2008 R2 AD FS Windows 2012 AD FS Windows 2012 R2 AD FS Windows 2016 AD FS Third-party federation gateway (Note the details in the Comments column.)                                    |                                   |
| If you currently maintain an active Office 365 tenant, is the SMTP/SIP domain of your targeted users associated with the tenant?                           | N/A – No Office 365 tenant in place No, users’ SMTP/SIP domain isn’t associated with any tenants in Office 365 Yes, users’ SMTP/SIP domain is associated with an existing tenant in Office 365 |                                   |
| Do user UPNs match their primary SMTP address?                                                                                                             | Yes No Inconsistently                                                                                                                                                                          |                                   |

Existing collaboration platform summary
---------------------------------------

Use the following table to capture information about your existing collaboration
platform deployment.

| Question                                                                                                                                                                | Answer                                                                                                                                                                             | Comments                  |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------|
| Is Microsoft Teams deployed?                                                                                                                                            | Yes No                                                                                                                                                                             |                           |
| Is Skype for Business deployed? For on-premises and hybrid deployments, make sure you note the version and cumulative update (CU) details in the Comments column.       | Yes, Office 365 Yes, hybrid (with Office 365) Yes, on-premises Yes, online, dedicated (Microsoft) Yes, hosted, dedicated (third party) Yes, hosted, shared (third party) No, other |                           |
| Is Exchange deployed? For on-premises and hybrid deployments, make sure you note the version and CU details in the Comments column.                                     | Yes, Office 365 Yes, hybrid (with Office 365) Yes, on-premises Yes, online, dedicated (Microsoft) Yes, hosted, dedicated (third party) Yes, hosted, shared (third party) No, other |                           |
| Is SharePoint deployed? For on-premises and hybrid deployments, make sure you note the version and CU details in the Comments column.                                   | Yes, Office 365 Yes, hybrid (with Office 365) Yes, on-premises Yes, online, dedicated (Microsoft) Yes, hosted, dedicated (third party) Yes, hosted, shared (third party) No, other |                           |
| Is Office 365 OneDrive for Business deployed?                                                                                                                           | Yes No                                                                                                                                                                             |                           |
| Do you have any other third-party platforms deployed and in use today? If so, note the number of users of these platforms and the usage details in the Comments column. | Cisco WebEx Slack Other (Specify in the Comments column.)                                                                                                                          | Number of users: Details: |
| Are you planning to move users from these third-party platforms to Teams?                                                                                               | Yes No                                                                                                                                                                             |                           |
| What is the current telephony and conferencing solution of the users who are in scope for this initiative?                                                              |                                                                                                                                                                                    |                           |

Collaboration platform deployment details
-----------------------------------------

### Microsoft Teams (if applicable)

If applicable, capture the details of your Teams deployment by using the sample
table below. If you haven’t deployed Teams, skip this section.

| Question                                                                                               | Answer                                                                                                                                                                                                                                                                                                                                                                             | Comments |
|--------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| What types of users are enabled for Teams?                                                             | All users in the organization Specific users/user groups (Specify in the Comments column)                                                                                                                                                                                                                                                                                          |          |
| Which Teams features and modalities are in use?                                                        | Channel-based conversations Private chat Guest access Channel meetings Private meetings Private calling Ad-hoc channel meetup Videos in meetings Screen sharing in meetings Audio conferencing Applications (apps) Tabs Bots Connectors Custom cloud storage integration (Box, Dropbox, ShareFile, Google Drive) Channel email integration Other (Specify in the Comments column.) |          |
| What applications have you deployed to Teams?                                                          |                                                                                                                                                                                                                                                                                                                                                                                    |          |
| Have you specifically blocked any Teams capabilities? If Yes, note the details in the Comments column. | Yes No                                                                                                                                                                                                                                                                                                                                                                             |          |
| Which Teams clients are in use?                                                                        | Web Windows Mac iOS Android Windows Mobile                                                                                                                                                                                                                                                                                                                                         |          |
| Who has permissions to create teams?                                                                   | Everyone in the organization (This is the default setting) Specific people (Specify in the Comments column.)                                                                                                                                                                                                                                                                       |          |
| Are you using security and compliance features in Teams?                                               | Yes No                                                                                                                                                                                                                                                                                                                                                                             |          |

### Skype for Business Online (if applicable)

If applicable, capture the details of your Skype for Business Online deployment
by using the sample table below. If you haven’t deployed Skype for Business
Online deployment, skip this section.

| Question                                                                                                                   | Answer                                                                                                                                                                                                                                                                  | Comments |
|----------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| What types of users are enabled for Skype for Business Online?                                                             | All users in the organization Specific users/user groups (Specify in the Comments column)                                                                                                                                                                               |          |
| What modalities and features are currently in use today?                                                                   | Instant Messaging and Presence (IM/P) Conferencing Federation Meeting Recording Microsoft Audio Conferencing Third-party audio conferencing (Note the details in the Comments column.) Calling Plans (formerly PSTN calling) Organizational Auto Attendants Call Queues |          |
| Have you specifically blocked any Skype for Business Online capabilities? If Yes, note the details in the Comments column. | Yes No                                                                                                                                                                                                                                                                  |          |
| What method are you using or plan to use to connect Phone System (formerly Cloud PBX) to the PSTN? Select all that apply.  | Calling Plans (formerly PSTN calling) On-premises PSTN connectivity (leveraging existing Skype for Business 2015 or Lync Server 2013 deployment) On-premises PSTN connectivity (using Cloud Connector)                                                                  |          |
| Have you ported any phone numbers to Microsoft? This is applicable to Calling Plans and Audio Conferencing features.       | Yes No                                                                                                                                                                                                                                                                  |          |

### Skype for Business on-premises (if applicable)

If applicable, capture the details of your Skype for Business deployment by
using the sample table below. If you haven’t deployed Skype for Business
on-premises, skip this section.

| Question                                                                                                                                      | Answer                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Comments |
|-----------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| What versions of Lync or Skype for Business currently are deployed on-premises?                                                               | Office Communications Server 2007 “R1” Office Communications Server 2007 R2 Lync Server 2010 Lync Server 2013 Skype for Business Server 2015 Skype for Business Cloud Connector Edition                                                                                                                                                                                                                                                                  |          |
| Is hybrid with Skype for Business Online configured?                                                                                          | Yes No                                                                                                                                                                                                                                                                                                                                                                                                                                                   |          |
| Is this environment hosted and managed by a third party? If Yes, note the details in the Comments column.                                     | Yes No                                                                                                                                                                                                                                                                                                                                                                                                                                                   |          |
| What modalities and features are currently in use today?                                                                                      | Instant Messaging and Presence (IM/P) Conferencing Federation Meeting Recording Persistent Chat / Group Chat Microsoft Audio Conferencing (formerly Dial in Conferencing) on your on-premises Lync Server or Skype for Business deployment Third-party audio conferencing (Note the details in the Comments column) Enterprise Voice using on-premises PSTN connectivity Calling Plans (formerly PSTN calling) via Hybrid with Skype for Business Online |          |
| Which version(s) of Edge Server do you have deployed?                                                                                         | Office Communications Server 2007 “R1” Office Communications Server 2007 R2 Lync Server 2010 Lync Server 2013 Skype for Business Server 2015                                                                                                                                                                                                                                                                                                             |          |
| Do you have Lync or Skype for Business Edge deployed into more than one datacenter? If Yes, note the details in the Comments column.          | Yes No                                                                                                                                                                                                                                                                                                                                                                                                                                                   |          |
| Select services that your Edge role provides today                                                                                            | External user access (corporate users) Remote user access (anonymous external meeting participants) Federation Media relay                                                                                                                                                                                                                                                                                                                               |          |
| Which of the following voice calling features do you currently have dependencies on? Note any additional dependencies in the Comments column. | Busy options Call park Call pickup or group call pickup Common area phones, or “hot desking” Response groups or hunt groups Shared line appearance Private line Voicemail Call via work Emergency or information numbers (911, 811, 411) Extension dialing Auto Attendant Subscriber access Analog devices Fax Caller ID masking or altering Location-based routing Least-cost routing Elevator phone                                                    |          |

### Networking and access to Office 365 services

Use the following table to capture your organization’s networking details and
how your users are (or will be) connected to Office 365 services.

| Question                                                                                                                                                                                            | Answer                                                                                                      | Comments |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|----------|
| How do (or how will) the users in scope for migration access Teams when they’re in the office? Select all that apply.                                                                               | Routed NAT connection Proxy server Public Wi-Fi Managed (not public) Wi-Fi ExpressRoute (Microsoft peering) |          |
| If access to Office 365 is through a proxy server, is there any way to bypass the proxy?                                                                                                            | Yes No                                                                                                      |          |
| Is ExpressRoute being used today?                                                                                                                                                                   | Yes No No, but it’s being planned                                                                           |          |
| Have you performed a Network Readiness Assessment? For more information see [Network Readiness Assessment](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Offers?pageState=NetworkReadiness). | Yes No                                                                                                      |          |
| Are users required to use a VPN when connecting to corporate resources remotely?                                                                                                                    | Yes No                                                                                                      |          |
| If a VPN is used, can Teams traffic be excluded from the VPN to access Office 365 Services directly?                                                                                                | Yes No                                                                                                      |          |
| Does your network support QoS?                                                                                                                                                                      | Yes No                                                                                                      |          |
| Can you prioritize Teams audio and video traffic to drive a high-quality experience?                                                                                                                | Yes No                                                                                                      |          |
| Do all locations within a region have internet egress, or is internet egress centralized for the entire region?                                                                                     | Regional access to the internet Centralized access to the internet                                          |          |

Note: To calculate the amount of bandwidth and other network requirements for
your cloud voice deployment, depending your organization’s details and estimated
usage, visit [Network
Planner](https://myadvisor.fasttrack.microsoft.com/CloudVoice/NetworkPlanner) in
[MyAdvisor](https://myadvisor.fasttrack.microsoft.com/).

### Endpoints

Use the following table to capture the details of the clients and endpoints in
use.

| Question                                                                                                           | Answer                                                                                                                                       | Comments |
|--------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|----------|
| What desktop OS are the users using?                                                                               | Windows XP Windows 7 Windows 8 Windows 10 Mac (Specify the version in the Comments column.) Other (Note the details in the Comments column.) |          |
| What version of Microsoft Office is deployed to these devices?                                                     | Office 2003 Office 2007 Office 2010 Office 2013 Office 2016 Mac Office 2011 Mac Office 2016 Other (Note the details in the Comments column.) |          |
| Which Office deployment technology is in use in your organization?                                                 | MSI Click-to-Run                                                                                                                             |          |
| What are the allowed and supported mobile platforms in use? Select all that apply.                                 | Windows Mobile iOS Android Other (Note the details in the Comments column.)                                                                  |          |
| How are mobile devices provided? Select all that apply.                                                            | Corporate devices Bring your own device                                                                                                      |          |
| What devices do users currently use to access voice and conferencing services (handsets, headsets, phones, video)? |                                                                                                                                              |          |

### Operations

Use the following table to capture the details of the operational aspects of
your environment.

| Question                                                                                                                                                        | Answer                                                             | Comments |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|----------|
| What is your operations model for your Lync Server, Skype for Business Server, or Office 365 deployment today?                                                  |                                                                    |          |
| Can you outline the current support arrangement for Lync Server, Skype for Business Server, or Office 365?                                                      |                                                                    |          |
| If you’re deploying to multiple countries or regions, does each country/region have its own IT/telephony staff to work with, or will this be managed centrally? | Regional operations and support Centralized operations and support |          |
| Are you following the Call Quality Methodology?                                                                                                                 | Yes No                                                             |          |
| Have you assigned an individual or team to the Quality Champion role for the collaboration platform in use?                                                     | Yes No                                                             |          |
| How do you monitor your Lync Server, Skype for Business Server, or Office 365 deployment?                                                                       |                                                                    |          |
| Do you experience call quality issues?                                                                                                                          | Yes No                                                             |          |
| How and when do you provide training to your helpdesk on new services and capabilities?                                                                         |                                                                    |          |

### Adoption and readiness

Use the following table and capture the current adoption and readiness state of
your organization.

| Question                                                                                                | Answer                                                                                                                                                                                                                                                                                                         | Comments |
|---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| What is your current active usage of Skype for Business?                                                | \___\_ % total active users versus enabled users                                                                                                                                                                                                                                                               |          |
| How is your organization using Skype for Business?                                                      | 1:1 conversations                                                                                                                                                                                                                                                                                              |          |
| Does your organization have a User Adoption and Change Management team?                                 | Yes No                                                                                                                                                                                                                                                                                                         |          |
| How do you currently measure success for technology rollouts like Skype for Business?                   |                                                                                                                                                                                                                                                                                                                |          |
| What percentage of your user base would you say has adopted Skype for Business?                         |                                                                                                                                                                                                                                                                                                                |          |
| What is user sentiment around Skype for Business?                                                       | Good Neutral Bad                                                                                                                                                                                                                                                                                               |          |
| Which of the following best describes the rollout strategy used for your Skype for Business deployment? | Broad reach: Email campaign with links to training Expanded: Broad reach plus a variety of awareness campaigns (posters, events, champions) and training (videos, user guides, in-person) Tailored: Expanded, plus targeted messaging and training by persona Other (Note the details in the Comments column.) |          |

-   IM

-   Calling

-   Sharing

Meetings

-   Conferencing

-   Sharing

>   Calling
