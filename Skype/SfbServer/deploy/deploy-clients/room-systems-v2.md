---
title: "Deploy Skype Room Systems v2"
ms.author: Turgayo
author: Turgayo
manager: serdars
ms.audience: ITPro
ms.reviewer: davgroom
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Admin
ms.custom:
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
description: "Read this article to learn about deploying Skype Room Systems v2."
---

# Deployment overview

Deployment of Skype Room Systems v2 essentially breaks down into phases:

- Confirming that your deployment locations (rooms) meet the deployment dependencies
- Creating Skype for Business and Exchange accounts and assigning them to the console devices (see [Configure accounts for Skype Room Systems v2](room-systems-v2-configure-accounts.md))
- Reimaging Microsoft Surface tablets to work as Skype Room Systems v2 consoles (see [Configure a Skype Room Systems v2 console](console.md) or [Deploy Skype Room Systems v2 mass deployment guide](room-systems-scale.md))
- (Optional) Setting up Microsoft Operations Management Suite for your systems (see [Deploy Skype Room Systems v2 management with Azure Monitor](azure-monitor.md))
- Setting up consoles in meeting rooms and connecting the peripheral devices you need (see the OEM documentation for your set of devices)

AV techs can be used for the last task, but your organization's IT department will need to do the other parts of the process. 


## Site readiness 

While the ordered devices are being delivered to your organization, work with your networking and facilities and AV teams to make sure that deployment dependencies are met and each site and room is ready in terms of power, networking, and display. In addition, make sure the physical installation requirements are met. For physical installation considerations, please visit the vendor’s site and leverage the experience of your AV team when installing and mounting screens and running cabling.

You can find out more about these dependencies in the planning guidance links below:

-   [Check network availability](../../plan-your-deployment/clients-and-devices/srs-v2-prep.md#check-network-availability) 
-   [Certificates](../../plan-your-deployment/clients-and-devices/srs-v2-prep.md#certificates)
-   [Proxy](../../plan-your-deployment/clients-and-devices/srs-v2-prep.md#proxy)

**Pro Tip** - If you intend to use proxy servers to provide access to Skype for Business Online, first [review this article](https://docs.microsoft.com/skypeforbusiness/optimizing-your-network/proxy-servers-for-skype-for-business-online). Note that when it comes to Skype for Business traffic over proxy servers, we recommend bypassing proxy servers altogether. Skype for Business traffic is already encrypted, so proxy servers don’t make it more secure. As part of your wider Skype for Business deployment, we recommend that you follow the guidance in [Evaluate my environment](https://docs.microsoft.com/MicrosoftTeams/3-envision-evaluate-my-environment#network-readiness) for bandwidth planning and assessing your network’s suitability for real-time traffic. For all bandwidth planning, use the [MyAdvisor Network Planner](https://myadvisor.fasttrack.microsoft.com/CloudVoice/NetworkPlanner). (We recommend that you create a Skype Room Systems v2 persona to reflect the intended Skype Room Systems v2 usage [video, screen sharing, audio] and assign a number of users that matches the number of Skype Room Systems units to be deployed to each site.) 

|    |     |
|-----------|------------|
| ![](../../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Confirm that your sites meet the key requirements for Skype Room Systems v2.</li><li>Confirm that you've provided sufficient bandwidth for each site.</li></ul>| 
| ![](../../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment and configuration.</li></ul>| 

**Pro Tip -** From a site-by-site planning perspective, you might find the following assets useful. They cover more than just Skype Room Systems v2 and can be used in a full rollout of Skype for Business Online:

-   [Site Rollout/Migration Planning Delivery
    Guide](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_1_0_24)

-   [Site Rollout and Migration Planning -
    Playbook](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_1_0_16)

    > [!NOTE]
    > In the playbook, complete the tasks in the section “4.3 – > Conference Rooms” under the “4-Endpoints” sheet for each site where you’re planning to deploy Skype Room Systems v2 devices. This will enable you to use the bulk account provisioning script later in the process. 

## Service readiness

To prepare for your Skype Room Systems deployment, do the following key, central tasks:

-   Define Skype Room Systems service account features.
-   Prepare an organizational unit and Active Directory group to hold your Skype Room Systems machine and service accounts, and—optionally—prepare Group Policy objects (GPOs) to enable PowerShell remoting.

### Define Skype Room Systems service account features 

Depending on the collaboration scenarios that you’ve decided to enable with your Skype Room Systems v2 deployment, you’ll need to determine the features and capabilities that you assign to each Skype Room Systems v2 service account that you enable.

| **Scenario** | **Description** | **Skype Room Systems v2 service account feature** |
|---------- |------------- | --- |
| Interactive meetings            | Using voice, video, and screen sharing; making the Skype Room Systems v2 a bookable resource                     | Enabled for Skype for Business, enabled for Exchange (Resource Mailbox) |
| Dial-in conferencing            | Enable meetings started *directly* from the Skype Room Systems v2 console with dial-in conferencing coordinates | Enabled for Audio Conferencing                                          |
| Outbound/inbound PSTN Calling | Enable the Skype Room Systems v2 console to make and receive PSTN calls                                         | Enabled for Phone System                                                |

For more information about Skype Room Systems accounts, see [Configure accounts for Skype Room Systems v2](room-systems-v2-configure-accounts.md).


|    |     |
|-----------|------------|
| ![](../../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide which scenarios you’ll support, and identify licensing requirements for your Skype Room Systems v2 service accounts.</li></ul>| 
| ![](../../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Prepare to host machine and service accounts.</li></ul>| 


_Sample Skype Room Systems v2 service account planning table_

| **Site**  | **Room name** | **Room type** | **Future room capabilities**                                                 | **Skype Room Systems v2 account features**                                                                                         |
|-----------|---------------|---------------|------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| London HQ | Curie         | Medium        | 1 screen, audio and video plus presentation <br>Dial-in conferencing access<br> PSTN access  | Enabled for Skype for Business, enabled for Exchange (Resource Mailbox) <br>Enabled for Audio Conferencing <br>Enabled for Phone System |
| Sydney HQ | Hill          | Large         | 2 Screens, audio and video plus presentation<br>Dial-in conferencing access<br> PSTN access  | Enabled for Skype for Business, enabled for Exchange (Resource Mailbox)<br> Enabled for Audio Conferencing <br>Enabled for Phone System |


### Prepare to host Skype Room Systems v2 machine and service accounts (optional)

To enable you to manage and report on your Skype Room Systems v2 machine and service accounts, prepare your on-premises Active Directory or Azure Active Directory (Azure AD). 

Define an on-premises Active Directory or Azure AD group to add all Skype Room Systems v2 service (user) accounts to, and then create usage reports by using the Get-CSUserSession PowerShell cmdlet across your Skype Room Systems v2 deployment. For example, create a group named SkypeRoomSystemsv2-Service-Accounts. 


Define one organizational unit in your on-premises Active Directory or Azure AD hierarchy to hold all Skype Room Systems v2 machine accounts (if they’re joined to the domain) and one organizational unit to hold all the Skype Room Systems v2 user accounts. If you do create an organizational unit for the Skype Room Systems v2 machine accounts, consider disabling inheritance to ensure that you apply only the policies you intended to apply to the domain-joined Skype Room Systems v2. 

Create a Group Policy object assigned to the organization unit that contains your Skype Room Systems computer accounts. Use this to: 

-   [Set power and local account settings](../../manage/skype-room-systems-v2/room-systems-v2-operations.md#configuring-group-policy-for-skype-room-systems-v2).
-   Enable Windows Update.
-   Enable PowerShell remoting. You can configure a start-up script to run a  simple script: Enable-PSRemoting -Force

You can use PowerShell to perform a number of remote management activities, including getting and setting configuration information. PowerShell remoting must be enabled *before* any PowerShell remote management can take place and should be considered as part of your deployment processes or configured via Group Policy. For more information about these capabilities and enabling them, see [Maintenance and operations](../../manage/skype-room-systems-v2/room-systems-v2-operations.md#remote-management-using-powershell). 


## Configuration and deployment 

Planning for configuration and deployment covers the following key areas:

-   Account provisioning
-   Device software installation
-   Device deployment
-   Skype Room Systems v2 application and peripheral device configuration
-   Testing
-   Asset management

### Account provisioning 

Each Skype Room Systems v2 device requires a dedicated and unique resource account that must be enabled for both Skype for Business and Exchange. This account must have a room mailbox hosted on Exchange and be enabled as a meeting room in the Skype for Business deployment. On the Exchange side, calendar processing must be configured so that the device can automatically accept incoming meeting requests. For more information about creating these accounts, see [Configure accounts for Skype Room Systems v2](room-systems-v2-configure-accounts.md). 

**Pro Tip** – Make the display names for these accounts descriptive and easy to understand. These are the names that users will see when searching for and adding Skype Room Systems v2 systems to meetings. Some organizations use the convention *Site*-*Room Name*(*Max Room Capacity*)-RS, so for example Curie—a 12-person conference room in London—might have the display name LON-CURIE(12)-RS. 

If your organization has many conference rooms that require multiple, provisioned accounts, you might want to use [Skype Room Systems Accounts Provisioning Scripts](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_2_0_4,5_2_0_5) to bulk-provision multiple service accounts in an automated fashion.


|    |     |
|-----------|------------|
| ![](../../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide the naming convention for your Skype Room Systems v2 accounts.</li><li>Decide whether you’ll create individual accounts or use bulk-provisioning scripts.</li></ul>| 
| ![](../../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment.</li></ul>| 


### Device software installation 

When planning to deploy Skype Room Systemsv2, you have a number of options to consider to install the required software. Common scenarios and approaches are described in the following table. 

| **Scenario**            | **Approach**         |
|-------------------------|-----------------------|   
|Deploying a small number of Skype Room Systems devices (<10). | If using Surface Pro–based Skype Room Systems v2, follow the [installation instructions for a per-device install](console.md). [This handy video walks you through the process.](https://content.cloudguides.com/guides/Configure%20the%20Skype%20Room%20Systems%20console) If using an integrated solution, deploy by using the vendor image and configure settings as required. |
| Deploying between 10 and 50 devices from a single vendor.     | Create a WIM-based image, pause after [step 6 in the guidance](console.md), and capture a distribution image to be used with your cloning distribution technology.    |
| Deploying more than 50 Skype Room Systems devices, deploying devices from more than one vendor, or requiring organization-specific agents as part of the deployment. | Use a task sequencer–based software build and distribution platform, such as [System Center Configuration Manager](room-systems-scale.md).  |

**Pro Tip** - Each Skype Room Systems v2 must have a valid and unique machine name on your network. Many monitoring and alerting systems display the machine name as a key identifier, so it’s important to develop a naming convention for Skype Room Systems v2 deployments that allows support personnel to easily locate the Skype Room Systems v2 that has been flagged as requiring an action. An example might be using a pattern of SRS-*Site*-*Room Name* (SRS-LON-CURIE). 


As part of the deployment, you’ll also need to consider your strategy for managing and configuring the [local accounts](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/clients-and-devices/skype-room-systems-v2-0#local-accounts) that are created by the Skype Room Systems application installer.

We provide guidance on how to use the [Microsoft Azure Monitor](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/clients-and-devices/azure-monitor) to monitor the Skype Room Systems v2 deployment and report on availability, hardware/software errors, and Skype Room Systems v2 application version. If you decide to use Microsoft Operations Management Suite, you should install the Operations Management Suite agent as part of the software installation process and configure the workspace connection information for your workspace. 

An additional consideration is whether the Skype Room Systems v2 will be domain-joined. Information about the benefits of domain joining can be found in [Skype Room System domain joining considerations](domain-joining-considerations.md). 

|    |     |
|-----------|------------|
| ![](../../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide the Skype Room Systems device-naming convention to be used during your deployment.</li><li>Decide whether you’ll join Skype Room Systems v2 devices to your domain, and how to manage and configure local accounts. </li><li>Decide whether you’ll use Operations Management Suite to monitor the Skype Room Systems v2 deployment.</li><li>Decide which method you’ll use to deploy the software and agents to the Skype Room Systems v2 system in preparation for the device deployment. </li></ul>| 
| ![](../../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment approach.</li></ul>| 


### Device deployment

After you’ve deployed your software to the Skype Room Systems v2 units, create your plan to ship the devices and their assigned peripheral devices to your rooms, and then proceed to installation and configuration. 


|    |     |
|-----------|------------|
| ![](../../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide who will manage the site-by-site deployment.</li><li> Identify the resources who will install the Skype Room Systems v2 devices on site and undertake the configuration and testing.</li></ul>| 
| ![](../../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start device testing.</li></ul>| 

_Sample deployment table_

| **Site**  | **Room name** | **Room type** | **Skype Room Systems v2 system**  | **Peripheral devices**  | **Skype Room Systems v2 computer name**  | **Skype Room Systems v2 resource account**  |
|-----------|---------------|---------------|-----------------------------------|------------------|------------------------------------------|---------------------------------------------|
| London HQ | Curie         | Medium        |                                   |                  |                                          |                                             |
| Sydney HQ | Hill          | Large         |                                   |                  |                                          |                                             |

### Skype Room Systems v2 application and peripheral device configuration 

After each Skype Room Systems v2 system has been physically deployed and the supported peripheral devices connected, you’ll need to configure the Skype Room Systems v2 application to assign the Skype Room Systems v2 resource account and password created earlier, to enable the Skype Room Systems v2 system to sign in to Skype for Business and Exchange. It's key to leverage Skype for Business certified USB audio and video peripherals linked elsewhere in the document. Not doing so can result in unpredictable behavior. 

You can manually configure each Skype Room Systems v2 system. Alternatively, you can use a centrally stored, per–Skype Room Systems XML configuration file to manage the application settings and leverage a start-up GPO script to reapply the configuration you want, each time the Skype Room Systems v2 system boots. 

For more information about how to use the XML configuration file, see [Manage a Skype Room Systems v2 console settings remotely with an XML configuration file](../../manage/skype-room-systems-v2/xml-config-file.md). 

You can use [remote PowerShell](../../manage/skype-room-systems-v2/room-systems-v2-operations.md#remote-management-using-powershell) to pull the Skype Room Systems v2 configuration for reporting needs. 

|    |     |
|-----------|------------|
| ![](../../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide whether you’ll manually configure each Skype Room Systems v2 system or use a central XML file (one per Skype Room Systems v2 device).</li></ul>| 
| ![](../../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Define your remote management approach.</li></ul>| 

### Testing

After the Skype Room Systems v2 system has been deployed, you should test it. Check that the capabilities listed in [Skype Room Systems v2 help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2) are working on the deployed device. We highly recommend that the deployment team verify that the Skype Room Systems v2 is logging to Microsoft Operations Management Suite (if used). It’s also important that you make a number of test calls and meetings to check quality. For more information, see this [useful deployment checklist](console.md#skype-room-systems-v2-deployment-checklist). 

We recommend that as part of the general Skype for Business rollout, you configure building files for Call Quality Dashboard (CQD), monitor quality trends, and engage in the Quality of Experience Review process. For more information, see the [Quality of Experience Review Guide](https://aka.ms/qerguide). 

**Pro Tip** – The [Testing Matrix](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_1_0_21) available from [MyAdvisor](https://myadvisor.fasttrack.microsoft.com/) contains a tab with a number of Skype Room Systems v2 tests that you should review using as part of your testing. 

### Asset management 

As part of the deployment, you’ll want to update your asset register with the room name, Skype Room Systems v2 device name, signed-in Skype Room Systems v2 resource account, and assigned peripheral devices (and which USB ports they use). 

_Sample asset table_

| **Site**  | **Room name** | **Room type** | **Skype Room Systems v2 serial no.**  | **Peripheral devices/ Serial nos./ Ports**  | **Skype Room Systems v2 computer name**  | **Skype Room Systems v2 service account**  | **Date deployed** |
|-----------|---------------|---------------|------------------------------------------|------------------------------------------|------------------------------------------|--------------------------------------------|-------------------|
| London HQ | Curie         | Medium        |                                          |                                          |                                          |                                            |                   |
| Sydney HQ | Hill          | Large         |                                          |                                          |                                          |                                            |                   |


