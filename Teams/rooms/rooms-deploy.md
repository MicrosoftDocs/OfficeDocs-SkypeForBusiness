---
title: Deploy Microsoft Teams Rooms
ms.author: dstrome
author: dstrome
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.service: msteams
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Rooms
ms.custom: seo-marvel-apr2020
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
description: Read this article to learn about how to deploy Microsoft Teams Rooms, including the deployment phases.
---

# Deployment overview

Deployment of Microsoft Teams Rooms essentially breaks down into phases:

- Confirming that your deployment locations (spaces) meet the deployment dependencies
- Creating Microsoft Teams or Skype for Business and Exchange accounts and assigning them to Teams Rooms (see [Configure accounts for Microsoft Teams Rooms](rooms-configure-accounts.md))
- (Optional) Setting up Azure Monitor for your systems (see [Deploy Microsoft Teams Rooms management with Azure Monitor](azure-monitor-deploy.md)
- Setting up Teams Rooms in meeting spaces and connecting the peripheral devices you need (see the OEM documentation for your set of devices)

## Site readiness 

While the ordered devices are being delivered to your organization, work with your networking, facilities, and AV teams to make sure that deployment dependencies are met and each site and space is ready in terms of power, networking, and display. In addition, make sure the physical installation requirements are met. For physical installation considerations, consult with your vendor and leverage the experience of your AV team when installing and mounting screens and running cabling.

You can find out more about these dependencies in the planning guidance links below:

-   [Check network availability](rooms-prep.md#check-network-availability)
-   [Certificates](rooms-prep.md#certificates)
-   [Proxy](rooms-prep.md#proxy)

**Pro Tip** - If you must use proxy servers to provide access to Teams, first [review this article](../proxy-servers-for-skype-for-business-online.md). When it comes to Microsoft Teams real-time media traffic over proxy servers, we recommend bypassing proxy servers altogether. Microsoft Teams traffic is already encrypted, so proxy servers don't make it more secure and they add latency to real-time traffic. As part of your wider deployment, we recommend that you follow the guidance in [Prepare your network for Teams](../prepare-network.md) for bandwidth planning and assessing your network's suitability for real-time traffic.

|  &nbsp;  | &nbsp;    |
|-----------|------------|
| ![confirm sites.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Confirm that your sites meet the key requirements for Microsoft Teams Rooms.</li><li>Confirm that you've provided sufficient bandwidth for each site.</li></ul>| 
| ![plan device deployment.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment and configuration.</li></ul>| 

## Service readiness

To prepare for your Microsoft Teams Rooms deployment, do the following key, central tasks:

-   Define Microsoft Teams Rooms resource accounts.
-   If joining Teams Rooms to Azure Active Directory, prepare an Azure AD group with dynamic membership to hold all of the Teams Rooms resource accounts. This will simplify future management, such as applying Conditional Access policies. In order to most easily leverage Azure AD dynamic groups, determine a naming convention that will uniquely identify your Teams Rooms resource accounts.
-   If joining Teams Rooms to Active Directory, prepare an organizational unit and Active Directory group to hold your Microsoft Teams Rooms machine and resource accounts, and—optionally—prepare Group Policy objects (GPOs) to enable PowerShell remoting.

### Define Microsoft Teams Rooms resource account features 

Depending on the collaboration scenarios that you've decided to enable with your Microsoft Teams Rooms deployment, you'll need to determine the features and capabilities that you assign to each Microsoft Teams Rooms that you enable.

| **Scenario** | **Description** | **Microsoft Teams Rooms service account feature** |
|---------- |------------- | --- |
| Interactive meetings            | Using voice, video, and screen sharing; making the Microsoft Teams Rooms a bookable resource                     | Enabled for Microsoft Teams or Skype for Business; enabled for Exchange (Resource Mailbox) |
| Dial-in conferencing            | Have an audio conferencing phone number when tapping "New meeting" on the console | Enabled for Audio Conferencing                                          |
| Outbound/inbound PSTN Calling | Enable the Microsoft Teams Rooms console to make and receive PSTN calls                                         | Enabled for Phone System                                                |

For more information about Microsoft Teams Rooms accounts, see [Configure accounts for Microsoft Teams Rooms](rooms-configure-accounts.md).


|  &nbsp;  |  &nbsp;   |
|-----------|------------|
| ![scenario support.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide which scenarios you'll support, and identify licensing requirements for your Microsoft Teams Rooms resource accounts.</li></ul>| 
| ![prepare host machine.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Prepare to host machine and resource accounts.</li></ul>| 


_Sample Microsoft Teams Rooms resource account planning table_

| **Site**  | **Room name** | **Room type** | **Future room capabilities**                                                 | **Microsoft Teams Rooms account features**                                                                                         |
|-----------|---------------|---------------|------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| London HQ | Curie         | Medium        | 1 screen, audio and video plus presentation <br>Dial-in conferencing access<br> PSTN access  | Enabled for Exchange (Resource Mailbox) <br>Enabled for Audio Conferencing <br>Enabled for Phone System |
| Sydney HQ | Hill          | Large         | 2 Screens, audio and video plus presentation<br>Dial-in conferencing access<br> PSTN access  | Enabled for Skype for Business <br>Enabled for Exchange (Resource Mailbox)<br> Enabled for Audio Conferencing <br>Enabled for Phone System |


### Prepare to host Microsoft Teams Rooms and resource accounts (optional)

To enable you to manage and report on your Microsoft Teams Rooms and resource accounts, prepare your on-premises Active Directory or Azure Active Directory (Azure AD). 

Define an on-premises Active Directory or Azure Active Directory group to add all Microsoft Teams Rooms resource accounts to. If using Azure Active Directory, consider using a dynamic group to automatically add and remove resource accounts from the group.

Define one organizational unit in your on-premises Active Directory hierarchy to hold all Microsoft Teams Rooms machine accounts (if they're joined to the domain) and one organizational unit to hold all the Microsoft Teams Rooms user accounts. Disable Group Policy inheritance to ensure that you apply only the policies you intended to apply to the domain-joined Microsoft Teams Rooms.

Create a Group Policy object assigned to the organization unit that contains your Microsoft Teams Rooms computer accounts. Use this to: 

-   [Set power and local account settings](rooms-operations.md#configuring-group-policy-for-microsoft-teams-rooms).
-   Enable Windows Update.
-   Enable PowerShell remoting. You can configure a start-up script to run a script: Enable-PSRemoting -Force

You can use PowerShell to perform several remote management activities, including getting and setting configuration information. PowerShell remoting must be enabled *before* any PowerShell remote management can take place and should be considered as part of your deployment processes or configured via Group Policy. For more information about these capabilities and enabling them, see [Maintenance and operations](rooms-operations.md#remote-management-using-powershell). 


## Configuration and deployment 

Planning for configuration and deployment covers the following key areas:

-   Resource account provisioning
-   Device software installation
-   Device deployment
-   Microsoft Teams Rooms application and peripheral device configuration
-   Testing
-   Asset management

### Resource account provisioning 

Each Microsoft Teams Rooms device requires a dedicated and unique resource account that must be enabled for both Microsoft Teams or Skype for Business, and Exchange. This account must have a room mailbox hosted on Exchange. Calendar processing must be configured so that the device can automatically accept incoming meeting requests. For more information about creating these accounts, see [Configure accounts for Microsoft Teams Rooms](rooms-configure-accounts.md). 

**Pro Tip** - Each Microsoft Teams Rooms must have a valid and unique machine name on your network. Many monitoring and alerting systems display the machine name as a key identifier, so it's important to develop a naming convention for Microsoft Teams Rooms deployments that allows support personnel to easily locate the Microsoft Teams Rooms that has been flagged as requiring an action. An example might be using a pattern of MTR-*Site*-*Room Name* (MTR-LON-CURIE). 

|  &nbsp;  | &nbsp;    |
|-----------|------------|
| ![decide naming convention.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide the naming convention for your Microsoft Teams Rooms resource accounts.</li><li>Decide whether you'll create individual accounts or use bulk-provisioning scripts.</li></ul>| 
| ![next steps.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment.</li></ul>| 


### Device software installation 

Teams Rooms comes pre-installed by the original equipment manufacturer (OEM).

We provide guidance on how to use [Microsoft Azure Monitor](/skypeforbusiness/plan-your-deployment/clients-and-devices/azure-monitor) to monitor the Microsoft Teams Rooms deployment and report on availability, hardware/software errors, and Microsoft Teams Rooms application version. If you decide to use Microsoft Operations Management Suite, you should install the Operations Management Suite agent as part of the software installation process and configure the workspace connection information for your workspace. 

An additional consideration is whether the Microsoft Teams Rooms will be domain-joined. Information about the benefits of domain joining can be found in [Configuring Group Policy for Microsoft Teams Rooms](rooms-operations.md#configuring-group-policy-for-microsoft-teams-rooms). 

| &nbsp;   |  &nbsp;   |
|-----------|------------|
| ![decision points device naming.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide the Microsoft Teams Rooms resource account naming convention to be used during your deployment.</li><li>Decide whether you'll join Microsoft Teams Rooms devices to your domain. </li><li>Decide whether you'll use Azure Monitor to monitor the Microsoft Teams Rooms deployment.</li> 
| ![next steps plan device.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start to plan your device deployment approach.</li></ul>| 


### Device deployment

After you've decided how to create and manage your Microsoft Teams Rooms resource accounts, create your plan to ship the devices and their assigned peripherals to your rooms, and then proceed to installation and configuration.


|  &nbsp;  |   &nbsp;  |
|-----------|------------|
| ![manage site-by-site deployment.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide who will manage the site-by-site deployment.</li><li> Identify the resources who will install Microsoft Teams Rooms on site and undertake the configuration and testing.</li></ul>| 
| ![start device testing.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start device testing.</li></ul>| 

_Sample deployment table_

| **Site**  | **Room name** | **Room type** | **Microsoft Teams Rooms system**  | **Peripheral devices**  | **Microsoft Teams Rooms computer name**  | **Microsoft Teams Rooms resource account**  |
|-----------|---------------|---------------|-----------------------------------|------------------|------------------------------------------|---------------------------------------------|
| London HQ | Curie         | Medium        |                                   |                  |                                          |                                             |
| Sydney HQ | Hill          | Large         |                                   |                  |                                          |                                             |

### Microsoft Teams Rooms application and peripheral device configuration 

After each Microsoft Teams Rooms system has been physically deployed and the supported peripheral devices connected, you'll need to configure the Microsoft Teams Rooms application to assign the Microsoft Teams Rooms resource account and password to enable Teams Rooms to sign in to Microsoft Teams or Skype for Business, and Exchange.

You can manually configure each Microsoft Teams Rooms system. Alternatively, you can use a centrally stored, per–Teams Rooms XML configuration file to manage the application settings.

For more information about how to use the XML configuration file, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md). 

You can use [remote PowerShell](rooms-operations.md#remote-management-using-powershell) to pull the Microsoft Teams Rooms configuration for reporting needs. 

| &nbsp;   |  &nbsp;   |
|-----------|------------|
| ![decision point configure.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide whether you'll manually configure each Microsoft Teams Rooms system or use a central XML file (one per Microsoft Teams Rooms device).</li></ul>| 
| ![next steps remote approach.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Define your remote management approach.</li></ul>| 

### Testing

After Teams Rooms has been deployed, you should test it. Check that the capabilities listed in [Microsoft Teams Rooms help](https://support.microsoft.com/en-us/office/microsoft-teams-rooms-help-e667f40e-5aab-40c1-bd68-611fe0002ba2?ui=en-us&rs=en-us&ad=us) are working on the deployed device. We highly recommend that the deployment team verify that Microsoft Teams Rooms is appearing in Teams admin center. It's also important that you make a number of test calls and meetings to check quality. For more information, see this [useful deployment checklist](console.md#microsoft-teams-rooms-deployment-checklist).

We recommend that as part of the general Teams or Skype for Business rollout, you configure building files for Call Quality Dashboard (CQD), monitor quality trends, and engage in the Quality of Experience Review process. For more information, see [Improve and monitor call quality for Teams](../monitor-call-quality-qos.md). 

### Asset management

As part of the deployment, you'll want to update your asset register with the room name, Microsoft Teams Rooms name, Microsoft Teams Rooms resource account, and assigned peripheral devices. 

_Sample asset table_

| **Site**  | **Room name** | **Room type** | **Microsoft Teams Rooms serial no.**  | **Peripheral devices/ Serial nos./ Ports**  | **Microsoft Teams Rooms computer name**  | **Microsoft Teams Rooms service account**  | **Date deployed** |
|-----------|---------------|---------------|------------------------------------------|------------------------------------------|------------------------------------------|--------------------------------------------|-------------------|
| London HQ | Curie         | Medium        |                                          |                                          |                                          |                                            |                   |
| Sydney HQ | Hill          | Large         |                                          |                                          |                                          |                                            |                   |
