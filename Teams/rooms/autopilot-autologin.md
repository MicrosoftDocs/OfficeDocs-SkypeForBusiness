---
title: Use Autopilot and Autologin to easily deploy Microsoft Teams Rooms consoles
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: altsou
ms.date: 03/20/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: itpro-rooms
audience: Admin
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to set up and use the Autopilot and Autologin features to deploy and provisioning Microsoft Teams Rooms on Windows consoles in your organization.
---

# Autopilot and Autologin for Teams Rooms on Windows

You can use Windows Autopilot and Autologin to deploy, provision, reset, redeploy, and recover Teams Rooms on Microsoft Teams Rooms on Windows consoles in your organization.

Windows Autopilot with Autologin for Teams Rooms simplifies and accelerates the on-site deployment time for Teams Rooms consoles running Windows. The combination of these technologies removes the need for direct interaction with the Teams Rooms console during provisioning and deployment. Using Autopilot and Autologin, there isn't a need for someone to physically interact with the Teams Room console to deploy it.

Instead, the Teams Rooms console completes the Windows and Teams app installation automatically out-of-box. Once installation is complete, it then signs in to the Teams Room app without the need for someone to have physical access to the device. The combinations of these features greatly simplify the Teams Rooms console lifecycle, from its initial deployment to its end of life.

## Overview of steps

To use Autopilot and Autologin to provision and deploy Microsoft Teams Rooms consoles in your organization, you must perform these tasks:

- Step 1: [Verify that all prerequisites are met](#step-1-prerequisites)
- Step 2: [Register devices as Autopilot devices](#step-2-registering-teams-rooms-consoles-using-windows-autopilot)
- Step 3: [Create a device group](#step-3-create-a-group-for-the-teams-rooms-consoles)
- Step 4: [Deploy Teams Rooms app update tool](#step-4-deploy-teams-room-app-update-tool)
- Step 5: [Create an Enrollment Status Page (ESP) profile](#step-5-create-an-autopilot-enrollment-status-page-esp-status-page-profile)
- Step 6: [Create and assign Autopilot profile](#step-6-create-an-autopilot-profile)
- Step 7: [Create and assign a Local Administrator Password Solution policy](#step-7-create-and-assign-a-local-administrator-password-solution-laps-policy)
- Step 8: [Set up Autologin in the Pro Management Portal](#step-8-set-up-autologin-in-the-teams-rooms-pro-management-portal)
- Step 9: [Deploy the device](#step-9-deploy-the-teams-rooms-console)

## Step 1: Prerequisites

To successfully deploy Microsoft Teams Rooms consoles, verify that these prerequisites are met.

1. You must buy enough Teams Rooms Pro licenses for each of the consoles you're provisioning and deploying. Teams Rooms Pro licenses include the correct Intune and Microsoft Entra ID P1 licenses. To see more information on the licensing requirements for Autopilot, see [Autopilot licensing requirements](/autopilot/licensing-requirements).

2. You must verify the account you're using to deploy the consoles has the correct permissions.
   1.  For Intune, verify that the account has the Intune Administrator or Policy and Profile Manager permissions, see [Learn more](/autopilot/add-devices#required-permissions).
   1. For the Teams Management Pro portal, the account has the Teams Rooms Pro Manager permissions.

3. You must [Set up Windows automatic Intune enrollment](/autopilot/tutorial/self-deploying/self-deploying-automatic-enrollment#set-up-windows-automatic-intune-enrollment).
4. You must Microsoft Entra join devices. Autopilot self-deploying mode is not supported for Microsoft Entra hybrid join devices.
5. You must create and set up the required resource accounts. See, [Create a resource account](/microsoftteams/rooms/create-resource-account).
6. You must be only deploying Microsoft Teams Rooms on Windows consoles with Windows 11 installed. See, [Teams Rooms Windows support](/microsoftteams/rooms/rooms-lifecycle-support).

## Step 2: Registering Teams Rooms consoles using Windows Autopilot

To register your Teams Rooms consoles for your organization, you can use Windows Autopilot device registration to collect the hardware identity of your consoles using hardware hashes and having this information in a comma-separated-values (CSV) file, and the uploading it to Intune. See [Register devices as Autopilot
devices](/autopilot/tutorial/self-deploying/self-deploying-register-device).

> [!IMPORTANT]
> For Teams Rooms on Windows consoles, it is required that the GroupTag has the prefix **MTR-ConsoleName**. You can easily do this by adding the GroupTag to the .csv file described [here](/autopilot/add-devices#ensure-that-the-csv-file-meets-requirements) or entering the prefix and console name in the **Group name** field by adding it using the Microsoft Partner Center.

This GroupTag field is critical for the Teams Pro Management portal so it can tell the difference between the Teams Rooms consoles and other devices that are registered with Windows Autopilot. The GroupTag field is also useful when you're using dynamic device groups.

> [!Note]
> To test Autopilot, you can manually register Autopilot devices in Intune. You can do this several different ways, see [Manually register devices with Windows Autopilot](/autopilot/add-devices).

## Step 3: Create a group for the Teams Rooms consoles

To create a Teams Rooms on Windows consoles device group, see [Create a device group](/autopilot/tutorial/self-deploying/self-deploying-device-group).

> [!Note]
> Intune's **Group Tag** field is the same as the **OrderID** attribute on Microsoft Entra devices.

To create a dynamic device group that includes all of the Teams Rooms consoles to use Autopilot, use the following query:

```odata
(device.devicePhysicalIds -any _ -startswith"[OrderID]:MTR-")
```

## Step 4: Deploy Teams Room app update tool

The Teams Rooms app update tool updates the Teams room app running on the device to a version that supports Autopilot and Autologin. The update tool needs to be first downloaded, then uploaded to Intune, and deployed to the Teams Rooms on Windows consoles. Although it's not required, use dynamic device groups. During the Autopilot Enrollment Status Page (ESP), Intune installs the update tool to the Teams Rooms console and updates the Teams room app before it starts.

Going through these steps enables Intune to push the update tool to the Teams Rooms enrolling through Autopilot. The update tool then automatically updates the Teams app on the console so it can automatically log in.

To deploy the Teams Rooms app update tool to your consoles:

1. To download the update tool Win32 package, see [here](https://aka.ms/mtrp/autopilot-tool).
2. In the Microsoft Intune Admin center, navigate to **Apps** and under **By platform** select **Windows**.
3. Select **Add**. In the **Select app type** detail pane, select **Windows app (Win32)** in the drop-down menu.
4. Browse to select the update tool app package file downloaded in Step 1.
5. On this page, most fields are automatically populated. To see the update tool in the list, put in **Microsoft** as the publisher, then select **Next**.
6. Under **Program**, select **Next**.
7. Under **Requirements** set the following:
   1.  Under **Operating system architecture**, select **32-bit** and **64-bit**.
   1.  Under **Minimum operating system**, select **Windows 10 21H2**.

8. Under **Detection rules**, set:
   1.  **Rules format: Manually configure detection rules**, select **Add**.
   1.  In the **Detection rule** detail pane, select **MSI** in the **Rule type**. The **MSI product code** should fill in automatically.
   1.  Select **No** for **MSI product version check**.
   1.  Select **OK**.
   1.  Select **Next**.

9. Under **Dependencies**, select **Next**.
10. Under **Supersedence**, select **Next**.
11. Under **Assignments**, select **Add group**.
12. Under the **Required** section, in the **Select groups** detail pane, choose the group created for the Microsoft Teams Rooms consoles being deployed with Windows Autopilot. Select **Next**.
13. On the **Review + create** page, review your settings. If everything is set correctly, select **Create**.

For more information on Win32 app deployment in Intune, see [Add and assign Win32 apps to Microsoft Intune](/mem/intune/apps/apps-win32-add#add-a-win32-app-to-intune).

## Step 5: Create an Autopilot Enrollment Status Page (ESP) status page profile

To create an enrollment status page profile for your Teams Room on Windows consoles, see [Configure and assign Autopilot Enrollment Status Page (ESP)](/autopilot/tutorial/self-deploying/self-deploying-esp).

The required settings for ESP on Teams Rooms are:

| Setting | Option |
|:-----|:-----|
| Show app and profile configuration progress                                                 | Yes         |
| Block device use until all apps and profiles are installed                                  | Yes         |
| Turn on log collection and diagnostics page for end users                                   | Yes         |
| Only show page to devices provisioned by out-of-box experience (OOBE)                       | Yes         |
| Block device use until all apps and profiles are installed                                  | Yes         |
| Allow users to reset device if installation error occurs                                    | Yes         |
| Allow users to use device if installation error occurs                                      | No          |
| Block device use until required apps are installed if they're assigned to the user/device   | Selected    |

> [!Note]
> Setting this to **Selected** helps to complete the ESP faster.

Under **Blocking apps**, select the Microsoft Teams Rooms Pro Provisioning (MTRP) tool. Set **Only fail selected blocking apps in technician phase** to **Yes**.

Then assign the ESP to the device group you created in [Step 3](#step-3-create-a-group-for-the-teams-rooms-consoles).

## Step 6: Create an Autopilot profile

For the Teams Rooms consoles, you must create a Self-deploying Autopilot profile. See [Create and assign Autopilot
profile](/autopilot/tutorial/self-deploying/self-deploying-autopilot-profile).

Then assign the Autopilot profile to the previously created device group in [Step 3](#step-3-create-a-group-for-the-teams-rooms-consoles).

## Step 7: Create and assign a Local Administrator Password Solution (LAPS) policy

For the Teams Rooms consoles, we recommended that you create and assign a LAPS policy as a best security practice. Also, because in some jurisdictions enhanced security is required by law.

To set up and configure a LAPS policy, see [LAPS authentication on Teams Rooms with Windows](/microsoftteams/rooms/laps-authentication#laps-deployment).

## Step 8: Set up Autologin in the Teams Rooms Pro Management portal

After the Endpoint Manager portal configuration is complete, you must assign the resource accounts for the consoles listed as Autopilot devices that let the Teams Rooms consoles automatically log in when they're deployed.

> [!IMPORTANT]
> Only Teams Rooms consoles that are running Windows 11 will be able to Autologin. Windows 10 devices aren't currently supported.

1. Go to the Microsoft Teams Rooms Pro Management portal and sign in.

2. In the left navigation of the Microsoft Teams Rooms Pro Management portal, go to **Planning > Autopilot devices**.

3. On the **Windows Autopilot devices** page, select **Sync** to populate the device list.

To assign an account to an Autopilot device, the device must have an Autopilot profile assigned. You can see the devices in the **Profile assignment status** column and they should be listed as **Assigned**.

1. Select a device from the list.
2. Select **Assign account**.
3. On the **Device selection** page, the device is preselected. Select **Next**.
4. On the **Account selection** page, select the account you want to use on this device, then elect **Next**.
5. On the **Configuration** page:
    - Enter the credentials if manual was selected.
    - Generate password automatically. This sets a password for the account.

      > [!Note]
      > Generate password requires Exchange Admin privileges to work. This option won't work with Hybrid resource accounts.

6. On the **Review** page, select **Finish** to link the resource account to Autopilot device.

When the console is ready to be provisioned, the **Provisioning status** shows as **Ready**.

> [!Note]
> The link and association is valid for up to 90 days.

When you take the console out of the box:
1. The Out-of-Box-experience (OOBE) runs.
2. Windows then completes the provisioning and enrollment of the console.
3. The Teams app will automatically log in.

   > [!Note]
   > When the device successfully completes Autologin, the **Provisioning status** changes to **Consumed**.

**Autologin if you are resetting a Teams Room**

When resetting a Teams Room for Autopilot and Autologin, verify there's a resource account assigned to the Autopilot device with the **Provisioning status** showing as **Ready**. If the status is **Consumed**, you must reassign the resource account to the Autopilot device for the console you're resetting.

## Step 9: Deploy the Teams Rooms console

Once all the configuration steps for Windows Autopilot self-deploying deployment and Autologin are completed, the next step is to start the deployment process for the console.

To start the Autopilot deployment process on the console that is Autopilot registered and has a resource account assigned.

1. If a wired network connection is available, connect the device to the wired network connection.
2. Turn on the device.
3. Once the device boots up, one of two things occurs depending on the state of network connectivity:

   > [!IMPORTANT]
   > Connectivity to the Internet is required.

   - If the device is connected to a wired network, the device may reboot to apply critical security updates if they're available. After the reboot to apply critical security updates, the Autopilot process begins.

   - If the device isn't connected to a wired network or if it doesn't have network connectivity, it prompts you to connect to a network.

   1. The OOBE (Out of Box Experience) begins and a screen asking for a country/region appears. Select the appropriate country or region, and then select **Yes**.

   1. The keyboard screen appears to select a keyboard layout. Select the appropriate keyboard layout, and then select **Yes**. If needed, you can select additional keyboard layouts by selecting **Add layout**, or select **Skip** if you don't want to add additional keyboard layouts.

      > [!Note]
      > When there's no network connectivity, the device can't download the Autopilot profile to identify the country/region and keyboard settings to use. This is why when there's no network connectivity, the country/region and keyboard screens appear and must be set to hidden in the Autopilot profile. These settings need to be set for the network connectivity screensto work properly.

   1. The **Let's connect you to a network** screen appears. At this screen, either plug the device into a wired network (if available), or select and connect to a wireless Wi-Fi network.

   1. Once network connectivity is established, the **Next** button is available. Select **Next**.

   1. The device may reboot to apply critical security updates if they're available. After the reboot to apply critical security updates, the Autopilot process begins.

4. The Enrollment Status Page (ESP) displays progress during the provisioning process in two phases:

    - **Device preparation** (Device ESP)
    - **Device setup** (Device ESP)

    The first two phases of **Device preparation** and **Device setup** are part of the Device ESP. The second phase of **Account setup** is part of the User ESP. For Windows Autopilot self-deploying mode, only the Device ESP and these two related phases (**Device preparation** and **Device setup**) run.

    > [!Note]
    > User ESP and **Account setup** aren't recommended for Teams Rooms deployments.

5. During **Device setup** the Teams Rooms app update tool runs and updates the Teams app. When the device ESP process completes, the Windows Autopilot self-deploying deployment is complete, and the Teams Rooms Out-of-box experience starts.

6. The Teams Room app now detects the Autopilot profile and initiates Autologin. The credentials for the resource account assigned to this Autopilot device are used. When this part is complete, the console will automatically log in and is ready for Teams meetings.

## Frequently asked questions

**Question** Why aren't my Autopilot devices syncing into the Teams Room Pro Management portal?

**Answer** In the Teams Pro Management portal on the Autopilot device page, select **Sync** to initiate an update to the device list. Check the "Last synced" time on the page to see if it corresponds to the time the last sync was initiated. If devices are still not syncing, check that the GroupTag is configured correctly with the prefix **MTR-ConsoleName**.

**Question** Why does the console not automatically login after resetting the console?

**Answer** If the console has not completed Windows Autopilot provisioing before, a Windows reset is required. It is recommended to reset to a factory image. A simple reset initiated through the Teams app will not reset Windows. 

If the device succesfully completed Windows Autopilot provisioning and the Teams app fails to login, check the respective device in the Pro Management portal and verify the **Provisioing status** shows as **Ready**.

**Question** Can I use Autopilot to EntraID join the device into one tenant and manually log in the Teams Room app to a resource account from another tenant?

**Answer** No. Using EntraID to join the device isn't a supported scenario. When the console attempts to log in, it fails because the device is registered to a different domain than the resource account.
