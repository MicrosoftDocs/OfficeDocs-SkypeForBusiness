
---
title: "Deploy Skype Room Systems v2"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 5/4/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Priority
ms.collection: 
- Strat_SB_Admin
ms.custom:
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
description: "Read this topic to learn about Skype Room Systems v2 and how it integrates with Exchange and Skype for Business Server 2015."
---

## Site readiness 

While the ordered devices are being delivered to your organization, work with
your networking and facilities teams to make sure that every deployment
dependency has been met and each site is ready in terms of power, networking,
and display. In addition, make sure the physical installation requirements are
met. For physical installation considerations, please visit the vendor’s site
and leverage the experience of your AV team when installing and mounting screens
and running cabling.

You can find out more about these dependencies in the planning guidance links
below:

-   [Network](https://docs.microsoft.com/en-gb/skypeforbusiness/plan-your-deployment/clients-and-devices/skype-room-systems-v2-0#check-network-availability)

-   [Certificates](https://docs.microsoft.com/en-gb/skypeforbusiness/plan-your-deployment/clients-and-devices/skype-room-systems-v2-0#certificates)

-   [Proxy](https://docs.microsoft.com/en-gb/skypeforbusiness/plan-your-deployment/clients-and-devices/skype-room-systems-v2-0#proxy)

**Pro Tip** - If you intend to use proxy servers to provide access to Skype for
Business Online, first [review this
article](https://docs.microsoft.com/en-us/skypeforbusiness/optimizing-your-network/proxy-servers-for-skype-for-business-online).
Note that when it comes to Skype for Business traffic over proxy servers, we
recommend bypassing proxy servers altogether. Skype for Business traffic is
already encrypted, so proxy servers don’t make it more secure. As part of your
wider Skype for Business deployment, we recommend that you follow the guidance
in [Evaluate my
environment](https://docs.microsoft.com/en-us/MicrosoftTeams/3-envision-evaluate-my-environment#network-readiness)
for bandwidth planning and assessing your network’s suitability for real-time
traffic. For all bandwidth planning, use the [MyAdvisor Network
Planner](https://myadvisor.fasttrack.microsoft.com/CloudVoice/NetworkPlanner).
(We recommend that you create a Skype Room Systems persona to reflect the
intended usage [video, screen sharing, audio] and assign a number of users that
matches the number of Skype Room Systems units to be deployed to each site.)

| Decision points | Confirm that your sites meet the key requirements for Skype Room Systems v2. |
|-----------------|------------------------------------------------------------------------------|


-   Confirm that you have provided sufficient bandwidth for each site.

| Next steps | Start to plan your device deployment and configuration. |   |
|------------|---------------------------------------------------------|---|


**Pro Tip -** From a site-by-site planning perspective, you might find the
following assets useful. They cover more than just Skype Room Systems v2 and can
be used in a full rollout of Skype for Business Online:

-   [Site Rollout/Migration Planning Delivery
    Guide](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_1_0_24)

-   [Site Rollout and Migration Planning -
    Playbook](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_1_0_16)

>   **Note** In the playbook, complete the tasks in the section “4.3 –
>   Conference Rooms” under the “4-Endpoints” sheet for each site where you’re
>   planning to deploy Skype Room Systems v2 devices. This will enable you to
>   use the bulk account provisioning script later in the process.

## Service readiness

To prepare for your Skype Room Systems deployment, do the following key, central
tasks:

-   Define Skype Room Systems service account features.

-   Plan for operations: define who will manage the Skype Room Systems units,
    define helpdesk queues, and provide an FAQ for the helpdesk.

-   Prepare an organizational unit and Active Directory group to hold your Skype
    Room Systems machine and service accounts, and—optionally—prepare Group
    Policy objects (GPOs) to enable PowerShell remoting.

### Define Skype Room Systems service account features 

Depending on the collaboration scenarios that you’ve decided to enable from your
Skype Room Systems devices, you’ll need to determine the features and
capabilities that you assign to each Skype Room Systems service account that you
enable.

| **Scenario**                    | **Description**                                                                                              | Skype Room Systems **service account feature**                          |
|---------------------------------|--------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| Interactive Meetings            | Using voice, video and screen sharing, making the Skype Room Systems a bookable resource                     | Enabled for Skype for Business, enabled for Exchange (Resource Mailbox) |
| Dial in Conferencing            | Enable meetings started *directly* from the Skype Room Systems console with dial-in conferencing coordinates | Enabled for Audio Conferencing                                          |
| Outbound / Inbound PSTN Calling | Enable the Skype Room Systems console to make and receive PSTN calls                                         | Enabled for Phone System                                                |

For more information about Skype Room Systems accounts, see [Deploy Skype Room
Systems
v2](https://docs.microsoft.com/en-us/skypeforbusiness/deploy/deploy-clients/room-systems-v2).

| Decision points | Decide which scenarios you’ll support and identify licensing requirements for your Skype Room Systems service accounts. |
|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| Next steps      | Plan for operations.                                                                                                    |

Sample Skype Room Systems service account planning table

| **Site**  | **Room Name** | **Room Type** | **Future Room Capabilities**                                                 | Skype Room Systems **Account Features**                                                                                         |
|-----------|---------------|---------------|------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| London HQ | Curie         | Medium        | 1 Screen, audio and video plus presentation Dial in Conf Access PSTN Access  | Enabled for Skype for Business, enabled for Exchange (Resource Mailbox) Enabled for Audio Conferencing Enabled for Phone System |
| Sydney HQ | Hill          | Large         | 2 Screens, audio and video plus presentation Dial in Conf Access PSTN Access | Enabled for Skype for Business, enabled for Exchange (Resource Mailbox) Enabled for Audio Conferencing Enabled for Phone System |

### Plan for operations 

Your organization must execute monitoring, administration, and management tasks
on an ongoing basis, and it’s key to agree who will undertake these tasks.

Many organizations have an AV team or partner who manages their conference rooms
and devices. This team should be involved in agreeing who will manage the Skype
Room Systems devices going forward to monitor performance, and deploy software
updates and hotfixes.

Consider which helpdesk queue you’ll route Skype Room Systems֪–related calls to,
and provide an FAQ to the helpdesk team so they can better understand how to use
Skype Room Systems and the key troubleshooting steps they can take.

| Decision points | Decide who will manage Skype Room Systems. |
|-----------------|--------------------------------------------|


-   Decide which helpdesk queue to route Skype Room Systems–related calls to.

| Next steps | Prepare to host accounts. |   |
|------------|---------------------------|---|


### Prepare to host Skype Room Systems machine and service accounts (optional)

To manage and report on your Skype Room Systems machine and service accounts,
it’s a good idea to prepare your on-premises Active Directory or Azure Active
Directory (Azure AD).

Define an on-premises Active Directory or Azure AD group to add all Skype Room
Systems service (user) accounts to, and then create usage reports by using the
Get-CSUserSession PowerShell cmdlet across all of your Skype Room Systems
systems. For example, create a group named SkypeRoomSystems-Service-Accounts.

Define one organizational unit in your on-premises Active Directory or Azure AD
hierarchy to hold all Skype Room Systems machine accounts (if they’re joined to
the domain) and one organizational unit to hold all the Skype Room Systems user
accounts. If you do create an organizational unit for the Skype Room Systems
machine accounts, consider disabling inheritance to ensure that you apply only
the policies you intended to apply to the domain-joined Skype Room Systems
systems.

Create a Group Policy object assigned to the organization unit that contains
your Skype Room Systems computer accounts. Use this to:

-   [Set power and local account
    settings](https://docs.microsoft.com/en-us/SkypeForBusiness/manage/skype-room-systems-v2/skype-room-systems-v2#configuring-group-policy-for-skype-room-systems-v2).

-   Enable Windows Update.

-   Enable PowerShell remoting. You can configure a start-up script to run a
    simple script: Enable-PSRemoting -Force

You can use PowerShell to perform a number of remote management activities,
including getting and setting configuration information. PowerShell remoting
must be enabled *before* any PowerShell remote management can take place and
should be considered as part of your deployment processes or configured via
Group Policy. For more information about these capabilities and enabling them,
see [Manage Skype Room Systems
v2](https://docs.microsoft.com/en-gb/skypeforbusiness/manage/skype-room-systems-v2/skype-room-systems-v2#remote-management-using-powershell).

## Configuration and deployment 

Planning for configuration and deployment covers the following key areas:

-   Account provisioning

-   Device software installation

-   Device deployment

-   Skype Room Systems application and peripheral device configuration

-   Testing

-   Asset management

### Account provisioning 

Each Skype Room Systems v2 device requires a dedicated and unique resource
account that must be enabled for both Skype for Business and Exchange. This
account must have a room mailbox hosted on Exchange and be enabled as a meeting
room in the Skype for Business deployment. On the Exchange side, calendar
processing must be configured so that the device can automatically accept
incoming meeting requests. For more information about these accounts, see
[Deploy Skype Room Systems
v2](https://docs.microsoft.com/en-gb/skypeforbusiness/deploy/deploy-clients/room-systems-v2).

**Pro Tip** – Make the display names for these accounts descriptive and easy to
understand. These are the names that users will see when searching for and
adding Skype Room Systems v2 systems to meetings. Some organizations use the
*Site*-*Room Name*(*Max Room Capacity*)-RS convention, so for example Curie—a
12-person conference room in London—might have the display name
LON-CURIE(12)-RS.

If your organization has many conference rooms that require multiple,
provisioned accounts, you might want to use [Skype Room Systems Accounts
Provisioning
Scripts](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_2_0_4,5_2_0_5)
to bulk-provision multiple service accounts in an automated fashion.

| Decision points | Decide the naming convention for your Skype Room Systems accounts. |
|-----------------|--------------------------------------------------------------------|


-   Decide whether you’ll create individual accounts or use bulk-provisioning
    scripts.

| Next steps | Start to plan your device deployment. |   |
|------------|---------------------------------------|---|


### Device software installation 

When planning to deploy the Skype Room Systems consoles, you have a number of
options to consider to install the required software. Common scenarios and
approaches are described in the following table.

| **Scenario**                                                                                                                                                         | **Approach**                                                                                                                                                                                                                                                                                           |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Deploying a small number of Skype Room Systems devices (\<10).                                                                                                       | If using Surface Pro–based Skype Room Systems, follow the [installation instructions for a per-device install](https://docs.microsoft.com/en-gb/skypeforbusiness/deploy/deploy-clients/console). If using an integrated solution, deploy by using the vendor image and configure settings as required. |
| Deploying between 10 and 50 devices from a single vendor.                                                                                                            | Create a WIM-based image, pause after [step 6 in the guidance](https://docs.microsoft.com/en-gb/skypeforbusiness/deploy/deploy-clients/console), and capture a distribution image by using cloning distribution technology.                                                                            |
| Deploying more than 50 Skype Room Systems devices, deploying devices from more than one vendor, or requiring organization-specific agents as part of the deployment. | Use a task sequencer–based software build and distribution platform, such as System Center Configuration Manager.                                                                                                                                                                                      |

**Pro Tip** - Each Skype Room Systems v2 system must have a valid and unique
machine name on your network. Many monitoring and alerting systems display the
machine name as a key identifier, so it’s important to develop a naming
convention for the Skype Room Systems devices that allows support personnel to
easily locate a Skype Room Systems system that has been flagged as requiring an
action. An example might be using a pattern of SRS-*Site*-*Room Name*
(SRS-LON-CURIE).

As part of the deployment, you’ll also need to consider your strategy for
managing and configuring the [local
accounts](https://docs.microsoft.com/en-gb/skypeforbusiness/plan-your-deployment/clients-and-devices/skype-room-systems-v2-0#local-accounts)
that are created by the Skype Room Systems application installer.

We provide guidance on how to use the [Microsoft Operations Management
Suite](https://docs.microsoft.com/en-us/skypeforbusiness/plan-your-deployment/clients-and-devices/oms-management)
to monitor the Skype Room Systems device and report on availability,
hardware/software errors, and Skype Room Systems application version. If you
decide to use Operations Management Suite, you should install the Operations
Management Suite agent as part of the software installation and configure the
workspace connection information for your workspace.

An additional consideration is whether the Skype Room Systems v2 systems will be
domain-joined. Information about the benefits of domain joining can be found in
[Skype Room System domain joining
considerations](https://docs.microsoft.com/en-us/skypeforbusiness/deploy/deploy-clients/domain-joining-considerations).

| Decision points | Decide the Skype Room Systems device-naming convention to be used during your deployment. |
|-----------------|-------------------------------------------------------------------------------------------|


-   Decide whether you’ll join Skype Room Systems v2 devices to your domain, and
    how to manage and configure local accounts.

    -   Decide whether you’ll use Operations Management Suite to monitor Skype
        Room Systems v2 devices.

        -   Decide which method you’ll use to deploy the software and agents to
            the Skype Room Systems v2 system in preparation for the device
            deployment.

| Next steps | Start to plan your device deployment approach. |   |   |   |
|------------|------------------------------------------------|---|---|---|


### Device deployment

After you’ve deployed your software to the Skype Room Systems v2 units, create
your plan to ship the devices and their assigned peripheral devices to your
rooms, and then proceed to installation and configuration.

| Decision points | Decide who will manage the site-by-site deployment. |
|-----------------|-----------------------------------------------------|


-   Identify the resources who will install the Skype Room Systems v2 devices on
    site and undertake the configuration and testing.

| Next steps | Start device testing. |   |
|------------|-----------------------|---|


Sample deployment table

| **Site**  | **Room Name** | **Room Type** | Skype Room Systems v**2 System**  | **Peripherals**  | Skype Room Systems v**2 Computer Name**  | Skype Room Systems v**2 Resource Account**  |
|-----------|---------------|---------------|-----------------------------------|------------------|------------------------------------------|---------------------------------------------|
| London HQ | Curie         | Medium        |                                   |                  |                                          |                                             |
| Sydney HQ | Hill          | Large         |                                   |                  |                                          |                                             |

### Skype Room Systems application and peripheral device configuration 

After each Skype Room Systems system has been physically deployed and the
peripheral devices connected, you’ll need to configure the Skype Room Systems
application to assign the Skype Room Systems resource account and password
created earlier, to enable the Skype Room Systems v2 system to sign in to Skype
for Business and Exchange.

You can manually configure each Skype Room Systems v2 system. Alternatively, you
can use a centrally stored, per–Skype Room Systems XML configuration file to
manage the application settings and leverage a start-up GPO script to reapply
the configuration you want, each time that the Skype Room Systems system boots.

For more information about how to use the XML configuration file, see [Manage a
Skype Room Systems v2 console settings remotely with an XML configuration
file](https://docs.microsoft.com/en-gb/skypeforbusiness/manage/skype-room-systems-v2/xml-config-file).

You can use [remote
PowerShell](https://docs.microsoft.com/en-us/skypeforbusiness/manage/skype-room-systems-v2/skype-room-systems-v2#remote-management-using-powershell)
to pull the Skype Room Systems v2 configuration for reporting needs.

| Decision points | Decide whether you’ll manually configure each Skype Room Systems system or use a central XML file (one per Skype Room Systems device). |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------|
| Next steps      | Define your remote management approach.                                                                                                |

### Testing

After the Skype Room Systems system has been deployed, you should test it. Check
that the capabilities listed in [Skype Room Systems v2
help](https://support.office.com/en-us/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)
are working on the deployed device. We highly recommend that the deployment team
verify that the Skype Room Systems system is logging to Operations Management
Suite (if used). It’s also important that you make a number of test calls and
meetings to check quality. For more information, see this [useful deployment
checklist](https://docs.microsoft.com/en-gb/skypeforbusiness/deploy/deploy-clients/console#skype-room-systems-v2-deployment-checklist).

We recommend that as part of the general Skype for Business rollout, you
configure building files for Call Quality Dashboard (CQD), monitor quality
trends, and engage in the Quality of Experience Review process. For more
information, see the [Quality of Experience Review
Guide](https://aka.ms/qerguide).

**Pro Tip** – The [Testing
Matrix](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_1_0_21)
available from [MyAdvisor](https://myadvisor.fasttrack.microsoft.com/) contains
a tab with a number of Skype Room Systems v2 tests that you might want to
consider using as part of your commissioning testing.

### Asset management 

As part of the deployment, you’ll want to update your asset register with the
room name, Skype Room Systems device name, signed-in Skype Room Systems resource
account, and assigned peripheral devices (and which USB ports they use).

Sample Asset Table

| **Site**  | **Room Name** | **Room Type** | Skype Room Systems v**2 System Serial**  | **Peripherals / Serial Numbers/ Ports**  | Skype Room Systems v**2 Computer Name**  | Skype Room Systems v**2 Service Account**  | **Date Deployed** |
|-----------|---------------|---------------|------------------------------------------|------------------------------------------|------------------------------------------|--------------------------------------------|-------------------|
| London HQ | Curie         | Medium        |                                          |                                          |                                          |                                            |                   |
| Sydney HQ | Hill          | Large         |                                          |                                          |                                          |                                            |                   |

<!-- Begin copied content from room-systems-v2 -->

# Deploy Skype Room Systems v2
 
Read this topic to learn about Skype Room Systems v2 and how it integrates with Exchange and Skype for Business Server 2015.
  
This topic introduces how to create accounts used by Skype Room Systems v2 in Microsoft Exchange and Skype for Business Server 2015. Deployment instructions for Skype Room Systems v2 devices is covered in [Configure a Skype Room Systems v2 console](console.md). Your infrastructure will likely fall into one of the following configurations:
  
- Online deployment: Your organization's environment is deployed entirely on Office 365. For more information, see [Deploy Skype Room Systems v2 with Office 365](with-office-365.md).
    
- On-premises deployment: Your organization has servers that it controls, where Active Directory, Exchange, and Skype for Business Server 2015 are hosted. For more information, see [Deploy Skype Room Systems v2 with Skype for Business Server 2015](with-skype-for-business-server-2015.md)
    
- Hybrid deployment: Your organization has a mix of services, with some hosted on premises and some hosted online through Office 365. With Skype Room Systems v2, the following hybrid scenarios are supported: 
    
  - Exchange Online with Skype for Business Server 2015 on premises. For more information, see [Deploy Skype Room Systems v2 with Exchange Online (Hybrid)](with-exchange-online.md).
    
  - Exchange on premises with Skype for Business Online. For more information, see [Deploy Skype Room Systems v2 with Exchange on premises (Hybrid)](with-exchange-on-premises.md).
    
Which configuration you have will affect how you prepare for device setup.
  
Skype Room Systems v2 needs to be assigned a "User account" in Active Directory, Exchange, and Skype for Business. The account is used to access its meeting calendar and establish Skype for Business connectivity. People can book this account by scheduling a meeting with it. Skype Room Systems v2 will be able to join that meeting and provide various features to the meeting attendees.
  
> [!IMPORTANT]
> Without a user account, none of these features will work. 
  
Every user account is unique to a single Skype Room Systems v2 device, and requires some setup:
  
- The user account must be configured correctly.
    
- Your infrastructure must be configured to allow Skype Room Systems v2 to validate the user account, and to reach the appropriate Microsoft services.
    
> [!IMPORTANT]
> It is highly recommended that account creation be done well in advance of actual hardware installation. Ideally, account preparation is started two to three weeks before installation. 
  
You can think of a user account as the resource account that people recognize as a conference room's or meeting space's account. When you want to schedule a meeting using that conference room, you invite the account to that meeting. In order to use Skype Room Systems v2 most effectively, you do the same with the user account that's assigned to each one.
  
If you already have a resource mailbox account set up for the meeting space where you're installing Skype Room Systems v2, you can change that resource account into a user account. Once that's done, all you need to do is add the user account to a Skype Room Systems v2 device. See user account setup examples provided below.
  
With additional configuration, remote management is possible using Microsoft Operations Management Suite (OMS) as described in [Plan Skype Room Systems v2 management with OMS](../../plan-your-deployment/clients-and-devices/oms-management.md), [Deploy Skype Room Systems v2 management with OMS](with-oms.md), and [Manage Skype Room Systems v2 devices with OMS](../../manage/skype-room-systems-v2/oms.md). 
  
## Basic Configuration

These properties represent the minimum configuration for a user account to work with Skype Room Systems v2. Your user account may require further setup.
  
|**Property**|**Purpose**|
|:-----|:-----|
|Exchange mailbox (Exchange 2013 SP1 or later, or Exchange Online)  <br/> |Enabling the account with an Exchange mailbox gives the user account the capability to receive and send both mail and meeting requests, and to display a meetings calendar on the Skype Room Systems v2 device. The Skype Room Systems v2 mailbox must be a room mailbox.  <br/> |
|Skype for Business is enabled  <br/> |Skype for Business must be enabled in order to use various conferencing features, like video calls, IM, and screen-sharing. Both Skype for Business Online and Skype for Business Server are supported.  <br/> |
|Password-enabled  <br/> |The user account must be enabled with a password, or it cannot authenticate with either Exchange or Skype for Business Server.  <br/> |
   
## Advanced Configuration

While the properties for the basic configuration will allow the user account to be set up in a simple environment, it is possible your environment has other restrictions on directory accounts that must be met in order for Skype Room Systems v2 to successfully use the user account.
  
|**Property**|**Purpose**|
|:-----|:-----|
|Certificate-based authentication  <br/> |Certificates may be required for both Exchange and Skype for Business Server. To deploy certificates, you can load them when logged in as Admin.  <br/> |
   
The best way to set up user accounts is to configure them using remote Windows PowerShell. [Microsoft provides scripts](https://go.microsoft.com/fwlink/?linkid=870105) that will help create new user accounts, or validate existing resource accounts you have in order to help you turn them into compatible Skype Room Systems v2 user accounts.
  
If you prefer to use the Office 365 UI over Windows PowerShell cmdlets, some steps can be performed manually. See [Creating a device account using Office 365](https://technet.microsoft.com/en-us/itpro/surface-hub/create-a-device-account-using-office-365).
  
## See also

[Plan for Skype Room Systems v2](../../plan-your-deployment/clients-and-devices/skype-room-systems-v2-0.md)
  
[Configure a Skype Room Systems v2 console](console.md)
  
[Manage Skype Room Systems v2](../../manage/skype-room-systems-v2/skype-room-systems-v2.md)

