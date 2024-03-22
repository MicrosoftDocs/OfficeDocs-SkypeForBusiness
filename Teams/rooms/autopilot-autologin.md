---
title: Use Autopilot and auto-login to easily deploy Microsoft Teams Rooms consoles
author: tonysmit
ms.author: tonysmit
manager: pamgreen
ms.date: 03/20/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: itpro-rooms
audience: Admin
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier3
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to set up and use the AutoPilot and Auto-login features to deploy and provisioning Microsoft Teams Rooms on Windows conosles in your organization.
---

# Autopilot and Auto-login for Teams Rooms on Windows

You can use Windows Autopilot and Auto-login to deploy, provision, reset, redeploy, and recover Teams Rooms on Microsoft Teams Rooms on Windows consoles in your organization.

Windows Autopilot with Auto-login for Teams Rooms accelerates and simplifies the on-site deployment time for Teams Rooms consoles running Windows. The combination of these technologies removes the need for direct interaction with the Teams Rooms console during provisioning and deployment. After the physical installation of Teams Rooms for Windows on the device and turning it on, with AutoPilot and Auto-login, there isn't a need for someone to interact directly with the Teams Room console.

Instead, the Teams Rooms console will complete the Windows and Teams app installation automatically out-of-box, then sign-in to the Teams Room app without the need of someone to have to physcially access the device. Having these features greatly simplifies the Teams Rooms console lifecycle for IT, from it's initial deployment to it's end of life.

## Overview of steps

To be able to use Autopilot and auto-signin to provision and deploy Microsoft Teams Rooms consoles in your organization, you must perform these tasks:

- Step 1: [Verify that all prerequisites are met](#step-1-prerequisites)
- Step 2: [Register devices as Autopilot devices](#step-2-registering-device-through-windows-autopilot)
- Step 3: [Create a devicegroup](#step-3-create-a-group-for-teams-rooms)
- Step 4: [Deploy Teams Rooms app update tool](#step-8-set-up-auto-login-in-the-pro-management-portal)
- Step 5: [Create an Enrollment Status Page (ESP) profile](#step-5-create-an-enrollment-status-page-profile)
- Step 6: [Create and assign Autopilot profile](#step-6-create-an-autopilot-profile)
- Step 7: [Create and assign a Local Administrator Password Solution(LAPS) policy](/mem/intune protect/windows-laps-policy#create-a-laps-policy)
- Step 8: [Set up Auto-login in the Pro Management Portal](#step-8-set-up-auto-login-in-the-pro-management-portal)
- Step 9: [Deploy the device](#step-9-deploy-the-device)

## Step 1: Prerequisites

To ensure successful deployment of Microsoft Teams Rooms, ensure that these prerequisites are met.

1. You have bought enough Teams Rooms Pro licenses to cover the number of consoles you are provisioning and deploying. The Teams Rooms Pro license includes the correct Intune and Azure Active Directory (AAD) P1 licenses.
<!-- @Alvin - what is a P1 license? Also what specific Intune license does it include.-->
1. Verify that you have provisioned the correct permissions:

    a.  In Intune, verify that the account you are using has the Intune Administrator or Policy and Profile Manager permissions [Learn more](/autopilot/add-devices#required-permissions).
    b.  For the Teams Pro Portal, ensure the account you are using has the Teams Rooms Pro Manager permissions.

3. [Set up Windows automatic Intune enrollment](/autopilot/tutorial/self-deploying self-deploying-automatic-enrollment#set-up-windows-automatic-intune-enrollment)
4. You must set up the correct resource accounts.
<!-- @Alvin - we need a link here or more information on what type of resource accounts need to be set up. -->
5. Microsoft Teams Rooms on Windows
<!-- @Alvin - we need a link here or more information on what this is here. I have no clue what this is.-->

## Step 2: Registering device through Windows Autopilot

You can perform Windows Autopilot device registration within your organization by manually collecting the hardware identity of devices (hardware hashes) and uploading this information in a comma-separated-values (CSV) file to Intune. To do this, [Register devices as Autopilot
devices](/autopilot/tutorial/self-deploying/self-deploying-register-device).

> [!IMPORTANT]
> For Teams Rooms on Windows devices, it is required to ensure the GroupTag is formatted with the prefix **MTR-<customname>**. This can be done by adding the GroupTag to the .csv  described [here](/autopilot/add-devices#ensure-that-the-csv-file-meets-requirements) or having your partner enter the prefix and custom name when uploading using the Microsoft Partner Center in the **Group name** field.

This GroupTag field is critical for the Teams Pro Management Portal to distinguish Teams Rooms consoles from other Windows Autopilot registered devices. It is also useful for using dynamic device groups.

> [!Note]
> For testing, manual registration of the Autopilot devices in Intune is required. There are many methods, but all pre-requisites and instructions are detailed in this doc: [Manually register devices with Windows Autopilot](/autopilot/add-devices).

## Step 3: Create a Group for Teams Rooms

To create a Teams Rooms on Windows specific device group, see [Create a device
group](/autopilot/tutorial/self-deploying/self-deploying-device-group).

> [!Note]
> Intune's Group Tag field maps to the OrderID attribute on Microsoft Entra devices.

To create a dynamic device group that includes all Teams Rooms Autopilot devices, use the following query:

(device.devicePhysicalIds -any _ -startswith"[OrderID]:MTR-")

## **Step 4: Deploy Teams Room app update tool**

The update tool updates the Teams room app running on the device to a version that is Autopilot and Auto-login capable. The update tool needs to be downloaded and uploaded to you Intune instance and deployed to the Teams devices (ideally through the dynamic device group created in Step 3). During the Autopilot Enrollment Status Page (ESP), Intune will install the update tool to the device to update the Teams room appmbefore launching it.

To deploy the tool:

1. Download the update tool Win32 package [here](https://mmrprodglobstor.blob.core.windows.net/public/softwareupdates/onboarding/MTRPUpdater/ProvisioningToolInstaller.intunewin).
2. In the Microsoft Intune Admin center, navigate to **Apps** and under **By platform** select **Windows**.
3. Select **Add**. In the **Select app type** detail pane, select **Windows app (Win32)** in the drop-down menu.
4. Select the update tool app package file downloaded in Step 1.
5. In the configurator, most fields are automatically populated. For the preview build of the update tool, you must type in **Microsoft** as the publisher. Select **Next.**
6. Under **Program**, select **Next**
7. Under **Requirements** set the following:
    a.  **Operating system architecture:** Select **32-bit** and **64-bit**
    b.  **Minimum operating system:** Select **Windows 10 21H2**
8. Under **Detection rules**, set the following:
    a.  **Rules format: Manually configure detection rules**
    b.  Select **Add**
    c.  In the **Detection rule** detail pane, select **MSI** in the **Rule type**. The **MSI product code** should autofill.
    d.  Set **MSI product version check** to **No**
    e.  Select **OK**
    f.  Select **Next**
9. Under **Dependencies**, select **Next**
10. Under **Supersedence**, select **Next**
11. Under **Assignments**, select **Add group** under the **Required** section. In the **Select groups** detail pane, choose the group created for the Microsoft Teams Rooms being deployed with Windows Autopilot. Select **Next.**
12. On the **Review + create** page, review the configurations. If satisfied, select **Create.**

Going through these steps enables Intune to push the update tool to the Teams Rooms enrolling through Autopilot. The update tool will then automatically update the client app on the device so that it can perform Teams room auto-login.

For more details on Win32 app deployment in Intune, refer to [Add and assign Win32 apps to Microsoft Intune](/mem/intune/apps/apps-win32-add#add-a-win32-app-to-intune)

## Step 5: Create an Enrollment Status Page profile

Create an enrollment status page profile for your Teams Room on Windows deployment by using the steps outlined here  [Configure and assign Autopilot Enrollment Status Page (ESP)](/autopilot/tutorial/self-deploying/self-deploying-esp).

The required settings for ESP on Teams Rooms are:
+-------------------------------------------------------------+--------+
| Show app and profile configuration progress                 | Yes    |
+=============================================================+========+
| Block device use until all apps and profiles are installed  | Yes    |
+-------------------------------------------------------------+--------+
| Turn on log collection and diagnostics page for end users   | Yes    |
+-------------------------------------------------------------+--------+
| Only show page to devices provisioned by out-of-box         | Yes    |
| experience (OOBE)                                           |        |
+-------------------------------------------------------------+--------+
| Block device use until all apps and profiles are installed  | Yes    |
+-------------------------------------------------------------+--------+
| Allow users to reset device if installation error occurs    | Yes    |
+-------------------------------------------------------------+--------+
| Allow users to use device if installation error occurs      | No     |
+-------------------------------------------------------------+--------+
| Block device use until required apps are installed if they  | Se     |
| are assigned to the user/device                             | lected |
+-------------------------------------------------------------+--------+

> [!Note]
> Setting this to Selected helps to complete the ESP faster.

Under **Blocking apps**, select the MTRP Provisioning Tool. Set **Only fail selected blocking apps in technician phase** to **Yes**.
<!-- @Alvin - We need to spell out MTRP unless this is a UX setting. If it is a setting that's named that way, we need to bold it.-->

Assign the ESP to the previously created device group in [Step 3](#step-3-create-a-group-for-teams-rooms).

## Step 6: Create an Autopilot Profile

For Teams Rooms devices, create a Self-deploying Autopilot profile, use:[Create and assign Autopilot
profile](/autopilot/tutorial/self-deploying/self-deploying-autopilot-profile).

Assign the Autopilot profile to the previously created device group in [Step 3](#step-3-create-a-group-for-teams-rooms).

## Step 7: Create and assign a Local Administrator Password Solution (LAPS) policy

For Teams Rooms, it is highly recommended to create and assign a LAPS policy as a good security practice. This may also be required in certain jurisdictions to meet requirements by law.

To configure a LAPS policy, do the following: [LAPS authentication on Teams Rooms with Windows](/microsoftteams/rooms/laps-authentication#laps-deployment)

## Step 8: Set up Auto-login in the Pro Management Portal

After the Endpoint Manager portal configuration is complete, assign resource accounts to the Autopilot devices. This will let the Teams Rooms consoles automatically login when they are deployed.

> [!IMPORTANT]
> Only Teams Rooms devices that are running Windows 11 will be able to auto-login. Windows 10 devices are currently unsupported.

1. In the left navigation of the Microsoft Teams Rooms Pro Management portal, go to **Planning > Autopilot devices**
2. On the **Windows Autopilot devices** page, select **Sync** to populate the device list.

To assign an account to an Autopilot device, the device must have an Autopilot profile assigned. This is shown in the **Profile assignment status** column and should show as **Assigned**.

1. Select a device from the list.
2. Select **Assign account**
3. On the **Device selection** page, the device is pre-selected. Select **Next**
4. On the **Account selection** page, select the account you want to associate to this device. Select **Next**.
5. On the **Configuration** page, configure:
    - Enter the credentials if manual selected
    - Generate password automatically sets a password for the account.

> [!Note]
> Generate password requires Exchange Admin privileges to work. This option won't work with Hybrid resource accounts.

6. On the **Review** page, select **Finish** to complete theassociation of the resource account to Autopilot device. On the corresponding device, the **Provisioning status** will show as **Ready**.

> [!Note]
> The association is valid for up to 90 days.

When the device is unboxed, during the Out-of-Box-experience (OOBE), after Windows has completed provisioning and enrollment of the device, the Teams app will automatically login to the associated account. When the device successfully completes Auto-login, the **Provisioning status** will change to **Consumed.**

**Auto-login if you are resetting a Teams Room**

When resetting a Teams Room for Autopilot and Autologin, ensure that there is a resource account assigned to the Autopilot device with the **Provisioning status** showing as **Ready**. If the status is **Consumed,** you must re-assign an account to the Autopilot device being reset.

## Step 9: Deploy the device

Once all the configurations for Windows Autopilot self-deploying deployment and Auto-login have been completed in Intune and the Pro Management Portal, the next step is to start the deployment process on the device.

To start the Autopilot deployment process on the device, select a device that is Autopilot registered, and has a resource account assigned.

1. If a wired network connection is available, connect the device to
    the wired network connection.
2. Power on the device.
3. Once the device boots up, one of two things occurs depending on the
    state of network connectivity:

    - If the device is connected to a wired network and has network
        connectivity, the device may reboot to apply critical security
        updates (if available or applicable). After the reboot to apply
        critical security updates, the Autopilot process begins.

    - If the device isn't connected to a wired network or if it
        doesn't have network connectivity, it prompts to connect to a
        network. Connectivity to the Internet is required:

        a.  OOBE (out of box experience) begins and a screen asking for
            a country or region appears. Select the appropriate country
            or region, and then select **Yes**.

        b.  The keyboard screen appears to select a keyboard layout.
            Select the appropriate keyboard layout, and then
            select **Yes**.

        c.  An additional keyboard layouts screen appears. If needed,
            select additional keyboard layouts via **Add layout**, or
            select **Skip** if no additional keyboard layouts are
            needed.

        > [!Note]
        > When there's no network connectivity, the device can't downloaded the Autopilot profile to know what country/region and keyboard settings to use. For this reason, when there's no network connectivity, the country/region and keyboard screens appear even if these screens have been set to hidden in the Autopilot profile. These settings need to be specified in these screens in order for the network connectivity screens that follow to work properly.

        d.  The **Let's connect you to a network** screen appears. At this screen, either plug the device into a wired network (if available), or select and connect to a wireless Wi-Fi network.

        e.  Once network connectivity is established, the **Next** button should become available. Select **Next**.

        f.  At this point, the device may reboot to apply critical security updates (if available or applicable). After the reboot to apply critical security updates, the Autopilot process begins.

4. The Enrollment Status Page (ESP) appears displays progress during the provisioning process across two phases:

    - **Device preparation** (Device ESP)
    - **Device setup** (Device ESP)

    The first two phases of **Device preparation** and **Device setup** are part of the Device ESP while the final phase of **Account setup** is part of the User ESP. For Windows Autopilot self-deploying mode, only the Device ESP and its related two related phases (**Device preparation** and **Device setup**) run.

> [!Note]
> User ESP and **Account setup** are not recommended for Teams Rooms deployments.

5. During **Device setup** the Teams Rooms app update tool will run and update the app. When the device ESP process completes, the Windows Autopilot self-deploying deployment is complete, and the Teams Rooms Out-of-box experience starts.

6. At this point, the Teams Room app will detect the Autopilot profile and initiate Auto-login. The credentials for the Resource Account assigned to this Autopilot device will be retrieved securely and provisioned. When this is complete, the device will automatically login and be ready to facilitate meetings.

## Frequently Asked Questions

**Question** Why aren't my Autopilot devices syncing into the Pro Management portal?

**Answer** On the Autopilot device page in the Teams Pro Management portal, select **Sync** to initiate an update to the device list. Check the "Last synced" time on the page to see if it corresponds to the time the last sync was initiated. If it isn't, check your Intune permissions. The user initiating the sync must have, at minimum, read permissions to devices in Intune.

**Question** Can I use Autopilot to EntraID join the device into one tenant and manually login the Teams Room app to a resource account from another tenant?

**Answer** No. This is not a supported scenario and is likely to cause login to fail as the device is registered to a different domain than the resource account.
