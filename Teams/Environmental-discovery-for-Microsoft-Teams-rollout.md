Environmental discovery for Microsoft Teams rollout
===================================================

Discovery is one of the very first and key steps that you should take when
planning for your journey to Microsoft Teams.

You should perform a detailed discovery of your environment to better understand
the current state and to reveal any difficulties or even further, possible
blockers to the execution of your Teams rollout.

Discovery Questionnaire
=======================

The sample questionnaire below walks you through a set of questions to confirm
readiness of your organization to the successful rollout of Audio Conferencing
and Phone System with Calling Plans capabilities in Teams.

All matters related to existing collaboration infrastructure and Office 365
Tenant, networking, endpoints, operations and, adoption and readiness are
included as part of the environmental discovery questionnaire.

The questionnaire is broken down into multiple sections to confirm readiness for
your Microsoft Teams deployment. Work with your project team to provide the
requested information as detailed as possible to facilitate the planning
activities.

You may start with copying the questionnaire into a Microsoft Word document. Try
to answer all questions and capture all the details as you move through.

Project Team
------------

Capture detailed information about the key stakeholders of the Teams rollout
project. Please note that one person can play several roles throughout the
project.

| Role                                  | Name, Email Address, Phone Number | Location, Time Zone | Comments |
|---------------------------------------|-----------------------------------|---------------------|----------|
| Executive Sponsor                     |                                   |                     |          |
| Project Lead                          |                                   |                     |          |
| Collaboration Lead/Architect          |                                   |                     |          |
| Consultant                            |                                   |                     |          |
| Project Manager                       |                                   |                     |          |
| Change Management/Adoption Specialist |                                   |                     |          |
| Network Lead                          |                                   |                     |          |
| Security Lead                         |                                   |                     |          |
| Telephony Lead                        |                                   |                     |          |
| Desktop Lead                          |                                   |                     |          |
| Support/Help Desk Lead                |                                   |                     |          |
| Deployment Lead                       |                                   |                     |          |
| Service Owner                         |                                   |                     |          |
| Facilities Lead                       |                                   |                     |          |
| Video Team Lead                       |                                   |                     |          |
| In scope Business Unit Leads          |                                   |                     |          |

Office 365 Tenant Details
-------------------------

It is highly recommended to have an active Office 365 tenant as you work with
this questionnaire. If you do not have Office 365 tenant activated or configured
yet, visit [Plan your setup of Office 365 for
business](https://support.office.com/article/plan-your-setup-of-office-365-for-business-eb926624-018b-4486-bf11-5fba6ee4d645).

Use the following table and capture the Office 365 Tenant details.

| Question                                                                                                                                                                 | Answer                                                                                                                                                                                          | Comments                          |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------|
| Does your organization already have a production O365 Tenant? Note: If there is more than one tenant associated with your organization, capture all the IDs.             | Yes No                                                                                                                                                                                          | Tenant Name: Tenant ID:           |
| In what region(s) are the tenant(s) deployed?                                                                                                                            |                                                                                                                                                                                                 |                                   |
| Is/are these tenant(s) O365 Multitenant or Dedicated?                                                                                                                    | Multitenant Dedicated                                                                                                                                                                           |                                   |
| Which Microsoft Online products are in use today? Note: Capture the number of users enabled for each service in the comments column.                                     | Microsoft Teams Skype for Business Online Exchange Online SharePoint Online OneDrive for Business Yammer Other                                                                                  |                                   |
| What License level is enabled for Skype Online users?                                                                                                                    | E1/G1 E2/G2 E3/G3 E4/G4 E5                                                                                                                                                                      | The number of users for each SKU: |
| What is the current Active Directory forest functional level in the environment? Note: If there is more than one Forest, please note the details in the comments column. | Windows Server 2000 Windows Server 2003 Windows Server 2008 Windows Server 2008 R2 Windows Server 2012 Windows Server 2012 R2 Windows Server 2016                                               |                                   |
| What is being used for Directory Synchronization today?                                                                                                                  | No sync (Cloud Only) Azure AD Connect Other (Specify in the comments column)                                                                                                                    |                                   |
| Is federated identity currently deployed? (ADFS or 3rd party)                                                                                                            | Yes No                                                                                                                                                                                          |                                   |
| If federated identity is used, what is the federation infrastructure?                                                                                                    | Windows 2008 R2 AD FS Windows 2012 AD FS Windows 2012 R2 AD FS Windows 2016 AD FS 3rd party federation gateway (please describe in comments column)                                             |                                   |
| If you currently maintain an active Office 365 tenant, is the SMTP/SIP domain of your targeted users associated with the tenant?                                         | N/A – No Office 365 tenant in place No, users’ SMTP/SIP domain is not associated with any tenants in Office 365 Yes, users’ SMTP/SIP domain is associated with an existing tenant in Office 365 |                                   |
| Do user UPNs match their Primary SMTP address?                                                                                                                           | Yes No Inconsistently                                                                                                                                                                           |                                   |

Existing Collaboration Platform Summary
---------------------------------------

Use the following table and capture existing collaboration platform deployment
details.

| Question                                                                                                                                          | Answer                                                                                                                                                                         | Comments              |
|---------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|
| Is Microsoft Teams deployed?                                                                                                                      | Yes No                                                                                                                                                                         |                       |
| Is Skype for Business deployed? Note: For on-premises and hybrid deployments, make sure you capture the version and CU details in the comments.   | Yes, Office 365 Yes, Hybrid (with Office 365) Yes, On Premises Yes, Online, Dedicated (Microsoft) Yes, Hosted, Dedicated (3rd party) Yes, Hosted, Shared (3rd party) No, other |                       |
| Is Exchange deployed? Note: For on-premises and hybrid deployments, make sure you capture the version and CU details in the comments.             | Yes, Office 365 Yes, Hybrid (with Office 365) Yes, On Premises Yes, Online, Dedicated (Microsoft) Yes, Hosted, Dedicated (3rd party) Yes, Hosted, Shared (3rd party) No, other |                       |
| Is SharePoint deployed? Note: For on-premises and hybrid deployments, make sure you capture the version and CU details in the comments.           | Yes, Office 365 Yes, Hybrid (with Office 365) Yes, On Premises Yes, Online, Dedicated (Microsoft) Yes, Hosted, Dedicated (3rd party) Yes, Hosted, Shared (3rd party) No, other |                       |
| Is Office 365 OneDrive for Business Online deployed?                                                                                              | Yes No                                                                                                                                                                         |                       |
| Do you have any other 3rd party platforms deployed and in use today? If so, note the number of users using these platforms and the usage details. | Cisco WebEx Slack Other (please specify in the comments column)                                                                                                                | No of users: Details: |
| Are you planning to move users from these 3rd party platforms to Microsoft Teams?                                                                 | Yes No                                                                                                                                                                         |                       |
| What is the current telephony and conferencing solution of the users who are in scope for this initiative?                                        |                                                                                                                                                                                |                       |

Collaboration Platform Deployment Details
-----------------------------------------

### Microsoft Teams (if applicable)

If applicable, capture the details of your Teams deployment using the sample
table below. Skip this section, if Teams is not enabled on your tenant.

| Question                                                                                             | Answer                                                                                                                                                                                                                                                                                                                                                     | Comments |
|------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| What types of users are enabled for Teams?                                                           | All users in the organization Specific users/user groups (Capture the details in the comments column)                                                                                                                                                                                                                                                      |          |
| Which Teams features, and modalities are in use?                                                     | Channel based conversations Private chat Guest Access Channel Meetings Private Meetings Private Calling Ad-hoc channel meetup Videos in meetings Screen Sharing in meetings Audio Conferencing Applications (Apps) Tabs Bots Connectors Custom cloud storage integration (Box, Dropbox, ShareFile, Google Drive) Channel email integration Other (specify) |          |
| What applications have been deployed to Teams?                                                       |                                                                                                                                                                                                                                                                                                                                                            |          |
| Have you specifically blocked any Teams capabilities? Note: If Yes, capture details in the comments. | Yes (Describe the details) No                                                                                                                                                                                                                                                                                                                              |          |
| Which Teams clients are in use?                                                                      | Web Windows Mac iOS Android Windows Mobile                                                                                                                                                                                                                                                                                                                 |          |
| Who has permissions to create teams?                                                                 | Everyone in the organization (This is the default setting) Specific people (specify)                                                                                                                                                                                                                                                                       |          |
| Are you using security and compliance features in Teams?                                             | Yes No                                                                                                                                                                                                                                                                                                                                                     |          |

### Skype for Business Online (if applicable)

If applicable, capture the details of your Skype for Business Online deployment
using the sample table below. Skip this section, if you have no Skype for
Business Online deployment.

| Question                                                                                                                        | Answer                                                                                                                                                                                                                                                           | Comments |
|---------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| What types of users are enabled for Skype for Business Online?                                                                  | All users in the organization Specific users/user groups (Capture the details)                                                                                                                                                                                   |          |
| What modalities and features are currently in use today?                                                                        | Instant Messaging and Presence (IM/P) Conferencing Federation Meeting Recording Microsoft Audio Conferencing 3rd Party Audio Conferencing (Capture the details in the comments) Calling Plans (formerly PSTN calling) Organizational Auto Attendants Call Queues |          |
| Have you specifically blocked any Skype for Business Online capabilities? Note: If Yes, provide details in the Comments column. | Yes No                                                                                                                                                                                                                                                           |          |
| What method is being used or is planned to connect the Phone System (formerly Cloud PBX) to the PSTN? (check all that apply)    | Calling Plans (formerly PSTN calling) On-premises PSTN Connectivity (leveraging existing Skype for Business 2015 / Lync Server 2013 Deployment) On-premises PSTN Connectivity (using Cloud Connector)                                                            |          |
| Have you ported any phone numbers to Microsoft? (applicable to Calling Plans and Audio Conferencing)                            | Yes No                                                                                                                                                                                                                                                           |          |

### Skype for Business On-Premises (if applicable)

If applicable, capture the details of your Skype for Business deployment using
the sample table below. Skip this section, if you have no Skype for Business
deployment on your premises.

| Question                                                                                                                                            | Answer                                                                                                                                                                                                                                                                                                                                                                                                                                             | Comments |
|-----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| What versions of Lync/Skype for Business currently are deployed on-premises?                                                                        | OCS 2007 “R1” OCS 2007 R2 Lync Server 2010 Lync Server 2013 Skype for Business Server 2015 Skype for Business Cloud Connector Edition                                                                                                                                                                                                                                                                                                              |          |
| Is hybrid with Skype for Business Online configured?                                                                                                | Yes No                                                                                                                                                                                                                                                                                                                                                                                                                                             |          |
| Is this environment hosted and managed by a 3rd party, if so please provide details in the comments?                                                | Yes No                                                                                                                                                                                                                                                                                                                                                                                                                                             |          |
| What modalities and features are currently in use today?                                                                                            | Instant Messaging and Presence (IM/P) Conferencing Federation Meeting Recording Persistent Chat / Group Chat Microsoft Audio Conferencing (formerly Dial in Conferencing) on your on-premises Lync/Skype for Business deployment 3rd Party Audio Conferencing (Please provide details in the comments column) Enterprise Voice using on-premises PSTN connectivity Calling Plans (formerly PSTN calling) via Hybrid with Skype for Business Online |          |
| Which version(s) of Edge Server do you have deployed?                                                                                               | OCS 2007 “R1” OCS 2007 R2 Lync Server 2010 Lync Server 2013 Skype for Business Server 2015                                                                                                                                                                                                                                                                                                                                                         |          |
| Do you have Lync / Skype for Business Edge deployed into more than one data center? If yes, capture the details.                                    | Yes No                                                                                                                                                                                                                                                                                                                                                                                                                                             |          |
| Select services that your Edge role provides today                                                                                                  | External User Access (corporate users) Remote User Access (anonymous external meeting participants) Federation Media Relay                                                                                                                                                                                                                                                                                                                         |          |
| Which of the following Voice calling features do you currently have dependencies on? Note: Capture additional dependencies in the comments section. | Busy options Call park Call Pickup / Group Call Pickup Common Area Phones / Hot Desking Response Groups / Hunt Groups Shared Line Appearance Private Line Voice Mail Call via work Emergency/Information numbers (911, 811, 411) Extension dialing Auto Attendant Subscriber Access Analog Devices Fax Caller ID Masking/Altering Location Based Routing Least Cost Routing Elevator Phone                                                         |          |

### Networking / Access to Office 365 Services

Use the following table and capture organization’s networking details and, how
your users are/will be connected to Office 365 services.

| Question                                                                                                                                                                                         | Answer                                                                                                      | Comments |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|----------|
| How do/will the users in scope for migration access Microsoft Teams when in the office? (Check all that apply)                                                                                   | Routed NAT connection Proxy Server Public Wi-Fi Managed (not public) Wi-Fi ExpressRoute (Microsoft Peering) |          |
| If access to O365 is via a Proxy server is there an ability to bypass the Proxy?                                                                                                                 | Yes No                                                                                                      |          |
| Is ExpressRoute being used today?                                                                                                                                                                | Yes No No, but it is being planned                                                                          |          |
| Have you performed Network Readiness Assessment? For more information see [Network Readiness Assessment](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Offers?pageState=NetworkReadiness) | Yes No                                                                                                      |          |
| Are users required to utilize a VPN when connecting to corporate resources remotely?                                                                                                             | Yes No                                                                                                      |          |
| If a VPN is used can Microsoft Teams traffic be excluded from the VPN to access O365 Services directly?                                                                                          | Yes No                                                                                                      |          |
| Does your network support QoS?                                                                                                                                                                   | Yes No                                                                                                      |          |
| Can you prioritize Microsoft Teams audio and video traffic to drive a high-quality experience?                                                                                                   | Yes No                                                                                                      |          |
| Do all locations within a region have internet egress, or is internet egress centralized for the entire region?                                                                                  | Regional access to internet Centralized access to internet                                                  |          |

Note: To calculate the amount of bandwidth and network requirements for your
cloud voice deployment, depending your organization’s details and estimated
usage, visit [Network
Planner](https://myadvisor.fasttrack.microsoft.com/CloudVoice/NetworkPlanner) in
[MyAdvisor](https://myadvisor.fasttrack.microsoft.com/).

### Endpoints

Use the following table and capture the details of the clients and endpoints in
use.

| Question                                                                                                           | Answer                                                                                                                  | Comments |
|--------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|----------|
| What desktop OS are the users using?                                                                               | XP Windows 7 Windows 8 Windows 10 Mac (Specify version in comments) Other (Capture the details in the comments)         |          |
| What version of Microsoft Office is deployed to these devices?                                                     | Office 2003 Office 2007 Office 2010 Office 2013 Office 2016 Mac Office 2011 Mac Office 2016 Other (capture the details) |          |
| Which Office deployment technology is in use within your organization?                                             | MSI Click-to-Run                                                                                                        |          |
| What are the allowed / supported mobile platforms in use? (select all that apply)                                  | Windows Mobile iOS Android Other (capture the details)                                                                  |          |
| How are mobile devices provided? (select all that apply)                                                           | Corporate devices BYOD                                                                                                  |          |
| What devices do users currently use to access voice and conferencing services (handsets, headsets, phones, video)? |                                                                                                                         |          |

### Operations

Use the following table and capture the details of the operational aspects of
the environment.

| Question                                                                                                                                       | Answer                                                             | Comments |
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|----------|
| What is your operations model for your Lync Server/ Skype for Business Server or Office 365 today?                                             |                                                                    |          |
| Can you outline the current support arrangement for Lync Server/ Skype for Business Server or Office 365?                                      |                                                                    |          |
| If deploying to multiple countries or regions, do each country have its own IT/Telephony staff to work with or will this be managed centrally? | Regional operations and support Centralized operations and support |          |
| Are you following the Call Quality Methodology?                                                                                                | Yes No                                                             |          |
| Have you assigned an individual or a team as the Quality Champion of the collaboration platform in use?                                        | Yes No                                                             |          |
| How do you monitor your Lync Server/ Skype for Business Server or Office 365 deployment?                                                       |                                                                    |          |
| Do you experience call quality issues?                                                                                                         | Yes No                                                             |          |
| How and when do you provide training to your Helpdesk on new services and capabilities?                                                        |                                                                    |          |

### Adoption and Readiness

Use the following table and capture the current adoption and readiness state of
your organization.

| Question                                                                                                    | Answer                                                                                                                                                                                                                                                                                          | Comments |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| What is your current active usage of SFB?                                                                   | \___\_ % total active users vs enabled users                                                                                                                                                                                                                                                    |          |
| How is your organization using SFB? Verify numbers on available usage reports                               | 1:1 conversations                                                                                                                                                                                                                                                                               |          |
| Does your organization have a User Adoption and Change Management team?                                     | Yes No                                                                                                                                                                                                                                                                                          |          |
| How do you currently measure success for technology rollouts like Skype for Business?                       |                                                                                                                                                                                                                                                                                                 |          |
| What % of your user base would you consider adopted on Skype for Business?                                  |                                                                                                                                                                                                                                                                                                 |          |
| What is user sentiment around Skype for Business?                                                           |                                                                                                                                                                                                                                                                                                 |          |
| Which of the following best describes the rollout strategy utilized for your Skype for Business deployment? | **Broad-Reach**: Email campaign with links to training **Expanded:** Broach-reach plus a variety of awareness (e.g. posters, events, champions) and training (videos, user guides, in-person) **Tailored:** Expanded, plus targeted messaging and training by persona **Other:** Please explain |          |

-   IM

-   Calling

-   Sharing

Meetings

-   Conferencing

-   Sharing

>   Calling
