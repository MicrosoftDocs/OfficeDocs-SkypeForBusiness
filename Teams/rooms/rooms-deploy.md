---
title: Microsoft Teams Rooms Deployment Overview
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: altsou
ms.date: 10/11/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.custom: seo-marvel-apr2020
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
description: Read this article to learn about how to deploy Microsoft Teams Rooms and Teams panels, including the deployment phases.
---

# Deployment overview

After completing planning for Teams Rooms (see [Planning for Teams Rooms](rooms-plan.md)), the next phase is deployment. Deploying Teams Rooms is broken down into a few phases:

1. Ordering equipment and confirming that your deployment locations (spaces) meet the deployment dependencies
2. Preparing your network environment and configuration steps to ensure your devices work on your corporate network
3. Creating resource accounts for your Microsoft Teams devices (see [Create and configure resource accounts for Teams devices](rooms-configure-accounts.md))
4. Enabling the Teams Rooms Pro Management Portal and assigning administrative roles (see [Accessing the Pro Management Portal](enrolling-mtrp-managed-service.md))
5. Configuring Intune for your Teams Rooms
6. Physically deploying your Teams Rooms devices and completing the initial setup steps

> [!TIP]
> As a companion to this article, we recommend using the [Microsoft Teams Rooms automated setup guide](https://go.microsoft.com/fwlink/?linkid=2224463) when signed in to the Microsoft 365 admin center. This guide will customize your experience based on your environment.  To review best practices without signing in and activating automated setup features, go to the [Microsoft 365 setup portal](https://go.microsoft.com/fwlink/?linkid=2222974).

## Ordering equipment and site readiness for a Teams Rooms deployment

Before ordering Teams Rooms equipment, review your physical meeting room spaces to determine the style of meetings that occur in the space and the equipment that fits the need. For more information, see [meeting room guidance](room-planning-guidance.md). Then, order your desired equipment from the [Teams devices store](/microsoftteams/devices/device-store) or from your reseller partner.

While waiting for the ordered devices to be delivered, work with your networking, facilities, and AV teams to make sure that deployment dependencies are met. Ensure each site and space is ready in terms of power, networking, and furniture. In addition, make sure the physical installation requirements are met. For physical installation considerations, consult with your vendor and use the experience of your AV team when installing and mounting screens and running cabling.

|  &nbsp;  | &nbsp;    |
|-----------|------------|
| ![confirm sites.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Select and order your Microsoft Teams Rooms equipment.</li><li>Confirm that your sites meet the physical installation requirements for Microsoft Teams Rooms.</li></ul>| 
| ![plan device deployment.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Prepare your network for Teams Rooms.</li></ul>|


## Preparing your corporate network for Teams Rooms

Teams Rooms devices have specific network requirements which may require adjustments to your corporate network from bandwidth, firewall & proxy, or installing certificates. All of these requirements are things you want to consider as you deploy Teams Rooms.  For more information on the networking requirements, see these links:

- [Preparing your network](rooms-prep.md)
- [Teams Rooms QoS](/microsoftteams/devices/qos-on-teams-devices)
- [Teams Rooms IPs and URLs](microsoftteams/rooms/security?tabs=Windows#network-security)
- [802.1x for Teams Rooms](microsoftteams/rooms/security?tabs=Windows#network-security)

## Creating resource accounts for your Microsoft Teams Rooms

Teams Rooms devices need resource accounts to be able to successfully sign into Teams and to be booked by end users to ensure join buttons appear on the rooms calendar. Each physical meeting room needs its own Teams Rooms resource account. Teams devices dedicated for that space can share the same resource account, meaning a Teams Room with two Teams panels at different doors can all share the same Teams Rooms resource account. This sharing ensures they're all in sync from a calendar perspective and automatic check-in/booking for meetings works correctly.

For each resource account, there are features an IT admin can enable for different business needs. You want to consider the features outlined here as you create your Teams Rooms resource accounts following this guide: [How to create and configure resource accounts for Teams devices](create-resource-account.md).

| Scenario | Description | Microsoft Teams Rooms service account feature |
|---------- |------------- | --- |
| Bookable for meetings           | Using voice, video, and screen sharing; making the Microsoft Teams Rooms a bookable resource                     | Enabled for Microsoft Teams; enabled for Exchange calendaring |
| Meet Now                        | Allowing a "Meet Now" from the Teams Rooms device                                                                | Configure a Teams Meeting policy allowing Meet Now            |
| Outbound/inbound PSTN Calling   | Enable the Microsoft Teams Rooms console to make and receive PSTN calls                                          | Enabled for Phone System                                      |

|  &nbsp;  |  &nbsp;   |
|-----------|------------|
| ![scenario support.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide which Teams Rooms scenarios you support.</li><li>Identify licensing requirements for your Microsoft Teams Rooms resource accounts.</li></ul>|
| ![prepare host machine.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Prepare the Pro Management Portal.</li></ul>|

## Enabling the Pro Management Portal

Teams Rooms devices are best managed in the Teams Rooms Pro Management Portal. Once you have a Teams Rooms Pro license available in your Microsoft 365 tenant, you can enable the Teams Rooms Pro Management Portal following the guidance here: [Accessing the Pro Management Portal](enrolling-mtrp-managed-service.md).

While in the Pro Management Portal it's important to define various administrative roles for your meeting room admins.  The Pro Management Portal supports granular role-based access control (RBAC), you can follow the steps here for how to configure RBAC: [Role-based access control in the Microsoft Teams Rooms Pro Management Portal](rooms-pro-rbac.md).


|  &nbsp;  |  &nbsp;   |
|-----------|------------|
| ![scenario support.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Activate the Pro Management Portal.</li><li>Define RBAC inside of the Pro Management Portal</li></ul>|
| ![prepare host machine.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Configuring Intune for your Teams Devices.</li></ul>|

## Configuring Intune for your Teams Devices

Teams Rooms on Windows devices can be managed in Intune to expand device management capabilities beyond what is available within the Teams Rooms Pro Management Portal and for Intune compliance assessments to ensure Teams Rooms on Windows devices are compliant with organizational requirements.  Teams Rooms on Android and Teams panels devices automatically enroll into Intune when they're logged in for the first time providing additional controls and Intune compliance assessments as well.

For Teams Rooms on Windows devices, Intune enrollment can be completed using [AutoPilot + AutoLogin](autopilot-autologin.mnd) or in one of several other manually [enrollment methods offered by Intune](/mem/intune/fundamentals/deployment-guide-enrollment-windows).

For Teams Rooms on Android and Teams panel devices, Intune enrollment is requirement for a successful sign in.  Teams Android devices use Android Device Administrator today as their enrollment method, for information on enabling Intune enrollment see these instructions: [Configure Intune to enroll Teams Android-based devices](/microsoftteams/devices/phones-panels-deploy#configure-intune-to-enroll-teams-android-based-devices).

|  &nbsp;  |  &nbsp;   |
|-----------|------------|
| ![scenario support.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Enabling Teams Rooms on Windows devices to enroll in Intune</li><li>Enabling Teams Rooms on Android and Teams panels to enroll in Intune</li></ul>|
| ![prepare host machine.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Physically deploying your Teams Rooms devices and completing the initial setup</li></ul>|

## Physically deploying and configuring your Teams Rooms devices

### Device deployment

After you created and enabled the management portal for your Microsoft Teams Rooms resource accounts and devices, create your plan to ship the devices and their assigned peripherals to your rooms, and then proceed to installation and configuration.

|  &nbsp;  |   &nbsp;  |
|-----------|------------|
| ![manage site-by-site deployment.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide who will manage the site-by-site deployment.</li><li> Identify the resources who will install Microsoft Teams Rooms on site and undertake the configuration and testing.</li></ul>| 
| ![start device testing.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Start device testing.</li></ul>| 

_Sample deployment table_

| Site | Room name | Room type | Microsoft Teams Rooms system | Peripheral devices | Microsoft Teams Rooms computer name | Microsoft Teams Rooms resource account |
|-----------|---------------|---------------|-----------------------------------|------------------|------------------------------------------|---------------------------------------------|
| London HQ | Curie         | Medium        |                                   |                  |                                          |                                             |
| Sydney HQ | Hill          | Large         |                                   |                  |                                          |                                             |

### Microsoft Teams Rooms application and peripheral device configuration

After each Microsoft Teams Rooms system has been physically deployed and the supported peripheral devices connected.  At initial power on of your Teams Rooms device, you need to configure the Microsoft Teams Rooms application to use the matching Microsoft Teams Rooms resource account and password to sign in to Microsoft Teams.

Once signed in, you can configure settings each Microsoft Teams Rooms system. For a Teams Rooms on Windows device, you can use a centrally stored, XML configuration file to manage the application settings. For more information about how to use the XML configuration file, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

| &nbsp;   |  &nbsp;   |
|-----------|------------|
| ![decision point configure.](../media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide whether you will manually configure each Microsoft Teams Rooms system or use a central XML file.</li></ul>|
| ![next steps remote approach.](../media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Test your new Teams Rooms devices.</li></ul>|

### Testing

After Teams Rooms has been deployed, you should test it. Check that the capabilities listed in [Microsoft Teams Rooms help](https://support.microsoft.com/office/microsoft-teams-rooms-help-e667f40e-5aab-40c1-bd68-611fe0002ba2?ui=en-us&rs=en-us&ad=us) are working on the deployed device. We highly recommend that the deployment team verify that Microsoft Teams Rooms is appearing in Teams Admin Center and in Teams Rooms Pro Management Portal. It's also important that you make several test calls and meetings to check quality.

### Asset management

As part of the deployment, you may want to update your asset register with the room name, Microsoft Teams Rooms name, Microsoft Teams Rooms resource account, and assigned peripheral devices.

_Sample asset table_

| Site | Room name | Room type | Microsoft Teams Rooms serial no. | Peripheral devices/ Serial nos./ Ports | Microsoft Teams Rooms computer name | Microsoft Teams Rooms service account | Date deployed |
|-----------|---------------|---------------|------------------------------------------|------------------------------------------|------------------------------------------|--------------------------------------------|-------------------|
| London HQ | Curie         | Medium        |                                          |                                          |                                          |                                            |                   |
| Sydney HQ | Hill          | Large         |                                          |                                          |                                          |                                            |                   |
