---
title: "Deploy Microsoft Teams Rooms"
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.reviewer: davgroom
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Admin
- M365-voice
ms.custom:
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
description: "Read this article to learn about deploying Microsoft Teams Rooms."
---

# Deployment overview

Deployment of Microsoft Teams Rooms essentially breaks down into phases:

- Confirming that your deployment locations (rooms) meet the deployment dependencies
- Creating Microsoft Teams or Skype for Business and Exchange accounts and assigning them to the console devices (see [Configure accounts for Microsoft Teams Rooms](room-systems-v2-configure-accounts.md))
- Reimaging Microsoft Surface tablets to work as Microsoft Teams Rooms consoles (see [Configure a Microsoft Teams Rooms console](console.md) or [Deploy Microsoft Teams Rooms mass deployment guide](room-systems-scale.md))
- (Optional) Setting up Microsoft Operations Management Suite for your systems (see [Deploy Microsoft Teams Rooms management with Azure Monitor](azure-monitor-deploy.md)
- Setting up consoles in meeting rooms and connecting the peripheral devices you need (see the OEM documentation for your set of devices)

AV techs can be used for the last task, but your organization's IT department will need to do the other parts of the process. 


## Site readiness 

While the ordered devices are being delivered to your organization, work with your networking and facilities and AV teams to make sure that deployment dependencies are met and each site and room is ready in terms of power, networking, and display. In addition, make sure the physical installation requirements are met. For physical installation considerations, please visit the vendor’s site and leverage the experience of your AV team when installing and mounting screens and running cabling.

You can find out more about these dependencies in the planning guidance links below:

-   [Check network availability](srs-v2-prep.md#check-network-availability) 
-   [Certificates](srs-v2-prep.md#certificates)
-   [Proxy](srs-v2-prep.md#proxy)

**Pro Tip** - If you intend to use proxy servers to provide access to Microsoft Teams or Skype for Business Online, first [review this article](https://docs.microsoft.com/skypeforbusiness/optimizing-your-network/proxy-servers-for-skype-for-business-online). Note that when it comes to Skype for Business traffic over proxy servers, we recommend bypassing proxy servers altogether. Skype for Business traffic is already encrypted, so proxy servers don’t make it more secure. As part of your wider deployment, we recommend that you follow the guidance in [Evaluate my environment](https://docs.microsoft.com/MicrosoftTeams/3-envision-evaluate-my-environment#network-readiness) for bandwidth planning and assessing your network’s suitability for real-time traffic. For all bandwidth planning, use the [MyAdvisor Network Planner](https://myadvisor.fasttrack.microsoft.com/CloudVoice/NetworkPlanner). (We recommend that you create a Microsoft Teams Rooms persona to reflect the intended Microsoft Teams Rooms usage [video, screen sharing, audio] and assign a number of users that matches the number of Microsoft Teams Rooms units to be deployed to each site.) 

|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Confirm that your sites meet the key requirements for Microsoft Teams Rooms.</li><li>Confirm that you've provided sufficient bandwidth for each site.</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment and configuration.</li></ul>| 

**Pro Tip -** From a site-by-site planning perspective, you might find the following assets useful. They cover more than just Microsoft Teams Rooms and can be used in a full rollout of Skype for Business Online:

-   [Site Rollout/Migration Planning Delivery
    Guide](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_1_0_24)

-   [Site Rollout and Migration Planning -
    Playbook](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_1_0_16)

    > [!NOTE]
    > In the playbook, complete the tasks in the section “4.3 – > Conference Rooms” under the “4-Endpoints” sheet for each site where you’re planning to deploy Microsoft Teams Rooms devices. This will enable you to use the bulk account provisioning script later in the process. 

## Service readiness

To prepare for your Microsoft Teams Rooms deployment, do the following key, central tasks:

-   Define Microsoft Teams Rooms service account features.
-   Prepare an organizational unit and Active Directory group to hold your Microsoft Teams Rooms machine and service accounts, and—optionally—prepare Group Policy objects (GPOs) to enable PowerShell remoting.

### Define Microsoft Teams Rooms service account features 

Depending on the collaboration scenarios that you’ve decided to enable with your Microsoft Teams Rooms deployment, you’ll need to determine the features and capabilities that you assign to each Microsoft Teams Rooms service account that you enable.

| **Scenario** | **Description** | **Microsoft Teams Rooms service account feature** |
|---------- |------------- | --- |
| Interactive meetings            | Using voice, video, and screen sharing; making the Microsoft Teams Rooms a bookable resource                     | Enabled for Skype for Business, enabled for Exchange (Resource Mailbox) |
| Dial-in conferencing            | Enable meetings started *directly* from the Microsoft Teams Rooms console with dial-in conferencing coordinates | Enabled for Audio Conferencing                                          |
| Outbound/inbound PSTN Calling | Enable the Microsoft Teams Rooms console to make and receive PSTN calls                                         | Enabled for Phone System                                                |

For more information about Microsoft Teams Rooms accounts, see [Configure accounts for Microsoft Teams Rooms](room-systems-v2-configure-accounts.md).


|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide which scenarios you’ll support, and identify licensing requirements for your Microsoft Teams Rooms service accounts.</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Prepare to host machine and service accounts.</li></ul>| 


_Sample Microsoft Teams Rooms service account planning table_

| **Site**  | **Room name** | **Room type** | **Future room capabilities**                                                 | **Microsoft Teams Rooms account features**                                                                                         |
|-----------|---------------|---------------|------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| London HQ | Curie         | Medium        | 1 screen, audio and video plus presentation <br>Dial-in conferencing access<br> PSTN access  | Enabled for Skype for Business, enabled for Exchange (Resource Mailbox) <br>Enabled for Audio Conferencing <br>Enabled for Phone System |
| Sydney HQ | Hill          | Large         | 2 Screens, audio and video plus presentation<br>Dial-in conferencing access<br> PSTN access  | Enabled for Skype for Business, enabled for Exchange (Resource Mailbox)<br> Enabled for Audio Conferencing <br>Enabled for Phone System |


### Prepare to host Microsoft Teams Rooms machine and service accounts (optional)

To enable you to manage and report on your Microsoft Teams Rooms machine and service accounts, prepare your on-premises Active Directory or Azure Active Directory (Azure AD). 

Define an on-premises Active Directory or Azure AD group to add all Microsoft Teams Rooms service (user) accounts to, and then create usage reports by using the Get-CSUserSession PowerShell cmdlet across your Microsoft Teams Rooms deployment. For example, create a group named SkypeRoomSystemsv2-Service-Accounts. 


Define one organizational unit in your on-premises Active Directory or Azure AD hierarchy to hold all Microsoft Teams Rooms machine accounts (if they’re joined to the domain) and one organizational unit to hold all the Microsoft Teams Rooms user accounts. If you do create an organizational unit for the Microsoft Teams Rooms machine accounts, consider disabling inheritance to ensure that you apply only the policies you intended to apply to the domain-joined Microsoft Teams Rooms. 

Create a Group Policy object assigned to the organization unit that contains your Microsoft Teams Rooms computer accounts. Use this to: 

-   [Set power and local account settings](room-systems-v2-operations.md#configuring-group-policy-for-microsoft-teams-rooms).
-   Enable Windows Update.
-   Enable PowerShell remoting. You can configure a start-up script to run a  simple script: Enable-PSRemoting -Force

You can use PowerShell to perform a number of remote management activities, including getting and setting configuration information. PowerShell remoting must be enabled *before* any PowerShell remote management can take place and should be considered as part of your deployment processes or configured via Group Policy. For more information about these capabilities and enabling them, see [Maintenance and operations](room-systems-v2-operations.md#remote-management-using-powershell). 


## Configuration and deployment 

Planning for configuration and deployment covers the following key areas:

-   Account provisioning
-   Device software installation
-   Device deployment
-   Microsoft Teams Rooms application and peripheral device configuration
-   Testing
-   Asset management

### Account provisioning 

Each Microsoft Teams Rooms device requires a dedicated and unique resource account that must be enabled for both Microsoft Teams or Skype for Business and Exchange. This account must have a room mailbox hosted on Exchange and be enabled as a meeting room in the Teams or Skype for Business deployment. On the Exchange side, calendar processing must be configured so that the device can automatically accept incoming meeting requests. For more information about creating these accounts, see [Configure accounts for Microsoft Teams Rooms](room-systems-v2-configure-accounts.md). 

**Pro Tip** – Make the display names for these accounts descriptive and easy to understand. These are the names that users will see when searching for and adding Microsoft Teams Rooms systems to meetings. Some organizations use the convention *Site*-*Room Name*(*Max Room Capacity*)-RS, so for example Curie—a 12-person conference room in London—might have the display name LON-CURIE(12)-RS. 

If your organization has many conference rooms that require multiple, provisioned accounts, you might want to use [Skype Room Systems Accounts Provisioning Scripts](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_2_0_4,5_2_0_5) to bulk-provision multiple service accounts in an automated fashion.


|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide the naming convention for your Microsoft Teams Rooms accounts.</li><li>Decide whether you’ll create individual accounts or use bulk-provisioning scripts.</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment.</li></ul>| 


### Device software installation 

When planning to deploy Microsoft Teams Rooms, you have a number of options to consider to install the required software. Common scenarios and approaches are described in the following table. 

| **Scenario**            | **Approach**         |
|-------------------------|-----------------------|   
|Deploying a small number of Microsoft Teams Rooms devices (<10). | If using Surface Pro–based Microsoft Teams Rooms, follow the [installation instructions for a per-device install](console.md). [This handy video walks you through the process.](https://content.cloudguides.com/guides/Configure%20the%20Skype%20Room%20Systems%20console) If using an integrated solution, deploy by using the vendor image and configure settings as required. |
| Deploying between 10 and 50 devices from a single vendor.     | Create a WIM-based image, pause after [step 6 in the guidance](console.md), and capture a distribution image to be used with your cloning distribution technology.    |
| Deploying more than 50 Microsoft Teams Rooms devices, deploying devices from more than one vendor, or requiring organization-specific agents as part of the deployment. | Use a task sequencer–based software build and distribution platform, such as [System Center Configuration Manager](room-systems-scale.md).  |

**Pro Tip** - Each Microsoft Teams Rooms must have a valid and unique machine name on your network. Many monitoring and alerting systems display the machine name as a key identifier, so it’s important to develop a naming convention for Microsoft Teams Rooms deployments that allows support personnel to easily locate the Microsoft Teams Rooms that has been flagged as requiring an action. An example might be using a pattern of MTR-*Site*-*Room Name* (MTR-LON-CURIE). 

As part of the deployment, you’ll also need to consider your strategy for managing and configuring the [local accounts](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/clients-and-devices/skype-room-systems-v2-0#local-accounts) that are created by the Microsoft Teams Rooms application installer.

We provide guidance on how to use the [Microsoft Azure Monitor](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/clients-and-devices/azure-monitor) to monitor the Microsoft Teams Rooms deployment and report on availability, hardware/software errors, and Microsoft Teams Rooms application version. If you decide to use Microsoft Operations Management Suite, you should install the Operations Management Suite agent as part of the software installation process and configure the workspace connection information for your workspace. 

An additional consideration is whether the Microsoft Teams Rooms will be domain-joined. Information about the benefits of domain joining can be found in [Skype Room System domain joining considerations](domain-joining-considerations.md). 

|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide the Microsoft Teams Rooms device-naming convention to be used during your deployment.</li><li>Decide whether you’ll join Microsoft Teams Rooms devices to your domain, and how to manage and configure local accounts. </li><li>Decide whether you’ll use Operations Management Suite to monitor the Microsoft Teams Rooms deployment.</li><li>Decide which method you’ll use to deploy the software and agents to the Microsoft Teams Rooms system in preparation for the device deployment. </li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment approach.</li></ul>| 


### Device deployment

After you’ve deployed your software to the Microsoft Teams Rooms units, create your plan to ship the devices and their assigned peripheral devices to your rooms, and then proceed to installation and configuration. 


|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide who will manage the site-by-site deployment.</li><li> Identify the resources who will install the Microsoft Teams Rooms devices on site and undertake the configuration and testing.</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start device testing.</li></ul>| 

_Sample deployment table_

| **Site**  | **Room name** | **Room type** | **Microsoft Teams Rooms system**  | **Peripheral devices**  | **Microsoft Teams Rooms computer name**  | **Microsoft Teams Rooms resource account**  |
|-----------|---------------|---------------|-----------------------------------|------------------|------------------------------------------|---------------------------------------------|
| London HQ | Curie         | Medium        |                                   |                  |                                          |                                             |
| Sydney HQ | Hill          | Large         |                                   |                  |                                          |                                             |

### Microsoft Teams Rooms application and peripheral device configuration 

After each Microsoft Teams Rooms system has been physically deployed and the supported peripheral devices connected, you’ll need to configure the Microsoft Teams Rooms application to assign the Microsoft Teams Rooms resource account and password created earlier, to enable the Microsoft Teams Rooms system to sign in to Microsoft Teams or Skype for Business and Exchange. It's key to leverage certified USB audio and video peripherals linked elsewhere in the document. Not doing so can result in unpredictable behavior. 

You can manually configure each Microsoft Teams Rooms system. Alternatively, you can use a centrally stored, per–Microsoft Teams Rooms XML configuration file to manage the application settings and leverage a start-up GPO script to reapply the configuration you want, each time the Microsoft Teams Rooms system boots. 

For more information about how to use the XML configuration file, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md). 

You can use [remote PowerShell](room-systems-v2-operations.md#remote-management-using-powershell) to pull the Microsoft Teams Rooms configuration for reporting needs. 

|    |     |
|-----------|------------|
| ![](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide whether you’ll manually configure each Microsoft Teams Rooms system or use a central XML file (one per Microsoft Teams Rooms device).</li></ul>| 
| ![](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Define your remote management approach.</li></ul>| 

### Testing

After the Microsoft Teams Rooms system has been deployed, you should test it. Check that the capabilities listed in [Microsoft Teams Rooms help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2) are working on the deployed device. We highly recommend that the deployment team verify that the Microsoft Teams Rooms is logging to Microsoft Operations Management Suite (if used). It’s also important that you make a number of test calls and meetings to check quality. For more information, see this [useful deployment checklist](console.md#microsoft-teams-rooms-deployment-checklist).

We recommend that as part of the general Teams or Skype for Business rollout, you configure building files for Call Quality Dashboard (CQD), monitor quality trends, and engage in the Quality of Experience Review process. For more information, see the [Quality of Experience Review Guide](https://aka.ms/qerguide). 

**Pro Tip** – The [Testing Matrix](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=5_1_0_21) available from [MyAdvisor](https://myadvisor.fasttrack.microsoft.com/) contains a tab with a number of Microsoft Teams Rooms tests that you should review using as part of your testing. 

### Asset management 

As part of the deployment, you’ll want to update your asset register with the room name, Microsoft Teams Rooms device name, signed-in Microsoft Teams Rooms resource account, and assigned peripheral devices (and which USB ports they use). 

_Sample asset table_

| **Site**  | **Room name** | **Room type** | **Microsoft Teams Rooms serial no.**  | **Peripheral devices/ Serial nos./ Ports**  | **Microsoft Teams Rooms computer name**  | **Microsoft Teams Rooms service account**  | **Date deployed** |
|-----------|---------------|---------------|------------------------------------------|------------------------------------------|------------------------------------------|--------------------------------------------|-------------------|
| London HQ | Curie         | Medium        |                                          |                                          |                                          |                                            |                   |
| Sydney HQ | Hill          | Large         |                                          |                                          |                                          |                                            |                   |


