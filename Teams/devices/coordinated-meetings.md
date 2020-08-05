---
title: "Set up coordinated meetings with Microsoft Teams Rooms and Surface Hub"
ms.author: dstrome
author: dstrome
ms.reviewer: rahulmi
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
localization_priority: Normal
description: "Configure Teams Rooms devices and Surface Hub to join meetings when one device or the other joins a meeting."
---

# Set up Coordinated Meetings with Microsoft Teams Rooms and Surface Hub

If you have one or more Microsoft Teams Rooms devices or Surface Hubs in a meeting room, you can set up Coordinated Meetings. Coordinated Meetings lets you set up your Teams Rooms devices and Surface Hubs so that when you join a meeting on one device, the other devices in the room are also joined to the same meeting. You can configure your cameras, speakers, and microphones so that the ones that give participants the best experience are enabled while others are disabled. This avoids the dreaded echo and feedback noise participants can experience when adding multiple devices to a meeting.

To set up Coordinated Meetings, you need to make sure your Teams Rooms devices and Surface Hubs are already correctly configured to participate in meetings. Most importantly, each device needs to have its own Exchange room mailbox. For information on how to set them up, see the following articles:

- [Deploy Microsoft Teams Rooms](../rooms/rooms-deploy.md)
- [Create Surface Hub 2S device account](https://docs.microsoft.com/surface-hub/surface-hub-2s-account)

After you've confirmed that your Teams Rooms devices and Surface Hubs can automatically accept meetings and join them successfully, you can set up Coordinated Meetings.

The following steps should be completed for each meeting room separately. Devices in one meeting room shouldn't be set up for Coordinated Meetings with devices in other meeting rooms.

## Step 1: Plan your Coordinated Meeting experience

Before you make any configuration changes, you need to decide which devices will do what in each meeting room. That is, for a given meeting room, you need to decide which device will have the active microphone, camera, and whiteboard. How you configure your devices depends on your specific environment, but here are some general recommendations to start with:

- **Microphone** Teams Rooms device
- **Camera** Teams Rooms device (on by default) and Surface Hub (off by default, but allowed to be turned on by participants)
- **Whiteboard** Surface Hub

> [!IMPORTANT]
> Make sure you enable the microphone only on one device. If you enable it on more than one device, you'll experience audio echo and feedback.

## Step 2: Get your devices' UPNs

When you set up a Coordinated Meeting experience in a meeting room, you need to tell the Teams Rooms devices and Surface Hubs in that room which devices to coordinate with. This is done by adding the user principal name (UPN) of the devices it should coordinate with to its configuration. If you don't know the UPNs for each of the devices you want to set up for Coordinated Meetings, you can find them using the Microsoft 365 admin center. 

You need to be assigned an admin role to access the Microsoft 365 admin center. For more information, see [About admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).

To get the UPNs of your Teams Rooms devices and Surface Hubs, do the following:

1. Sign in to the Microsoft 365 admin center by visiting https://admin.microsoft.com
2. Go to **Users** > **Active users**
3. Find the name of your Teams Rooms device or Surface Hub in the **Display name** column (you can use the **Search** box if you have many users)
4. Find the UPN in the **Username** column (it'll look something like alias@contoso.com or alias@contoso.onmicrosoft.com)
5. Repeat this for each device that will participate in Coordinated Meetings

## Step 3: Create a deployment worksheet

After you've planned your Coordinated Meeting experience and gathered a list of your devices' UPNs, it's a good idea to create a deployment worksheet. A deployment worksheet will help you visualize the configuration you want to set across all of your devices, allowing you to validate your choices and check for errors.

In a spreadsheet app, add rows for the following in the first column:

| Setting                | Description      |
|------------------------|-----------------|
| **Audio default**      | Determines on which device the microphone will be active when a meeting starts. Only one device (typically a Teams Rooms device) can have this field set to `true` while the rest of the devices must have this field set to `false` to avoid audio echo and feedback.          |
| **Audio enabled**      | Determines whether participants in a meeting can toggle the microphone on or off. Devices on which **Audio default** is set to `false` should have this setting set to `false` so that participants can't accidentally turn on a microphone and cause audio echo or feedback.<p>If **Audio default** is set to `true`, this setting is ignored and participants can mute or unmute the microphone.          |
| **Video default**      | Determines on which device the camera will be active when a meeting starts. For the best experience, we recommend that only the Teams Rooms device be set to `true` while all other devices are set to `false`.          |
| **Video enabled**      | Determines whether participants in a meeting can toggle the camera on or off. You can set this to `true` on any other devices in the event participants want to share different video perspectives (such as if a participant is using the Surface Hub whiteboard). If you don't want participants to turn a camera on or off on a device, set this to `false`.<p> If **Video default** is set to `true`, this setting is ignored and participants can turn the camera on or off.         |
| **Whiteboard default** | Determines whether the Teams Rooms device will display a whiteboard shared by one of the meeting participants. We recommend that you set this to `false` if you have a Surface Hub and `true` if you don't have one. This setting has no effect on Surface Hubs. Surface Hubs will always display a whiteboard shared by meeting participants.         |
| **Trusted accounts**   | This is a comma-separated list of UPNs for each Teams Room device or Surface Hub that the device should accept meeting join requests from, or to which meeting join requests should be sent. |

In subsequent columns, add each of your Teams Rooms devices and Surface Hubs. In each column, fill out the values that correspond to the experience you want for the meeting room. Here's an example with one Teams Rooms device and one Surface Hub:

- Teams device
  - Audio and video are turned **on** when a meeting starts. Participants **can** toggle audio and video on or off.
  - Displaying a shared whiteboard is turned off.
- Surface Hub
  - Audio is turned **off** when a meeting starts. Participants **can't** toggle audio on or off.
  - Video is turned **off** when a meeting starts. Participants **can** toggle video on or off.

| Setting                | Teams Room      | Surface Hub      |
|------------------------|-----------------|------------------|
| **Audio default**      | `true`          | `false`          |
| **Audio enabled**      | `true`          | `false`          |
| **Video default**      | `true`          | `false`          |
| **Video enabled**      | `true`          | `true`           |
| **Whiteboard default** | `false`         | Not applicable   |
| **Trusted accounts**   | hub@contoso.com | room@contoso.com |

## Step 4: Configure Teams Rooms device

You can either set up Coordinated Meetings on a Teams Rooms device using the device's touch screen or, if you need to set up many devices and want to do so from a central location, you can use an XML configuration file.

Use the worksheet you created in the previous step to help you set up your devices.

### Use the Teams Rooms device's touch screen

To set up Coordinated Meetings on a device, do the following:

1. Select **... More** > **Settings**
2. Enter the Administrator password and select **Yes**
3. Select **Coordinated Meetings**
4. Under **Options**, set **Coordinated Meeting** to on
5. If **Audio default** in your worksheet is `true`, set **Turn on this device's microphone** to on, otherwise leave it off
6. If **Audio enabled** in your worksheet is `true`, select **Let people enable when joining a meeting** under **Turn on this device's microphone**. This option can't be turned off if **Turn on this device's microphone** is set to on.
7. If **Video default** in your worksheet is `true`, set **Turn on this device's camera** to on, otherwise leave it off
8. If **Video enabled** in your worksheet is `true`, select **Let people enable when joining a meeting** under **Turn on this device's camera**. This option can't be turned off if **Turn on this device's camera** is set to on.
9. If **Whiteboard default** in your worksheet is `true`, set **Turn on whiteboarding on this device** to on, otherwise leave it off
10. Under **Trusted device accounts**, type each UPN listed in **Trusted accounts** in your worksheet. Separate multiple UPNs with commas.
11. Select **Save and exit**

After you select **Save and exit**, the device will restart and it'll be ready to participate in Coordinated Meetings.

### Use the Teams Rooms XML configuration file

Coordinated Meetings can be set up using the Teams Rooms device's `SkypeSettings.xml` XML configuration file. The `SkypeSettings.xml` file isn't a static file. When the Teams Rooms device start, it checks in `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState` for a file named `SkypeSettings.xml`. If the file exists, the device reads and applies the configuration specified in the file. After it's done applying the configuration, the file is deleted. For more information about the `SkypeSettings.xml` file, see [Manage console settings with an XML configuration file](../rooms/xml-config-file.md#manage-console-settings-with-an-xml-configuration-file).

The following is the syntax of the Coordinated Meetings settings in the configuration file:

```xml
<CoordinatedMeetings enabled="true">
    <Settings>
        <Audio default="true" enabled="true"/>
        <Video default="true" enabled="true"/>
        <Whiteboard default="false"/>
    </Settings>
    <TrustedAccounts>hub@contoso.com</TrustedAccounts>
</CoordinatedMeetings>
```

To set up Coordinated Meetings on a device, do the following:

1. In a text file editor, such as Visual Studio Code or Notepad, paste the above XML into a new file
2. Set each of the XML elements to the corresponding `true` or `false` value in your spreadsheet. For example, if **Audio default** is `true`, set `<Audio default="true">`.
3. Be sure to change `TrustedAccounts` to your list of UPNs
4. Save the file with the name `SkypeSettings.xml`
5. Place the file in the Teams Rooms device's `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState` folder. You can do this a few ways:
    - **Copy the file to your Teams Rooms device** You'll need to enable file sharing and create a network share before you can copy files to your device. After you do that, you can connect to network share and copy the file to the device. For more information, see [Microsoft Teams Rooms maintenance and operations](../rooms/rooms-operations.md).
    - **Use a Group Policy** Create a group policy to copy the file to device. For more information, see [Group Policy Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831791(v=ws.11)).
    - **Download the file on the Teams Rooms device** You can log into the device using Admin mode and then copy the file to the device from a network share or USB drive. For more information, see [Switching to Admin mode](../rooms/rooms-operations.md#switching-to-admin-mode-and-back-when-the-microsoft-teams-rooms-app-is-running).
6. Restart the device. You can do this a couple ways:
    - **Remote PowerShell** You can run the Shutdown command on the device using Remote PowerShell. For more information, see [Remote Management using PowerShell](../rooms/rooms-operations.md).
    - **Run Restart-Computer** You can run the `Restart-Computer` cmdlet on your local computer and specify the computer name of the device you want to restart. For more information, see [Restart-Computer](https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-7).

## Step 5: Configure Surface Hub

You can either set up Coordinated Meetings on a Surface Hub using Windows Configuration Designer or Microsoft Intune in Microsoft Endpoint Manager. Knowledge of Windows Configuration Designer or Microsoft Intune is required to complete these steps. For more information about these options, see the following articles:

- [Create a provisioning package for Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package)
- [What is Microsoft Intune device management?](https://docs.microsoft.com/mem/intune/remote-actions/device-management)

Windows Configuration Designer is a good option if you only have a few Surface Hub devices and you can access them easily. If you have many Surface Hubs, or if they're in remote locations, use Microsoft Intune in Microsoft Endpoint Manager if its deployed in your organization. Regardless of the method you choose, you need to create an XML configuration file for Coordinated Meetings on Surface Hub.

### Create Coordinated Meetings XML configuration file for Surface Hub

Both Windows Configuration Designer and Microsoft Intune are used to apply the Coordinated Meetings configuration to your Surface Hubs. The configuration is defined using XML. Before you go further, you need to create the XML that will be applied.

The following is the syntax of the Coordinated Meetings XML configuration file.

```xml
<SurfaceHubSettings>​
    <BluetoothAdvertisementEnabled>true</BluetoothAdvertisementEnabled>​
    <AutoAcceptProximateMeetingInvitations>true</AutoAcceptProximateMeetingInvitations>​
    <CoordinatedMeetings enabled="true"> ​
        <TrustedAccounts>​room@contoso.com</TrustedAccounts>​
        <Settings> ​
            <Audio default="false" enabled="false" />​
            <Video default="false" enabled="true" /> ​
        </Settings> ​
    </CoordinatedMeetings>​
</SurfaceHubSettings>
```

Do the following to prepare the XML for Windows Configuration Designer or Microsoft Intune:

1. In a text file editor, such as Visual Studio Code or Notepad, paste the above XML into a new file
2. Set each of the XML elements to the corresponding `true` or `false` value in your spreadsheet. For example, if **Audio default** is `true`, set `<Audio default="true">`.
3. Be sure to change `TrustedAccounts` to your list of UPNs
4. Windows Configuration Designer requires that the XML be on a single line. Remove all the line breaks between each line so that the XML looks like the following:

    ```xml
    <SurfaceHubSettings><BluetoothAdvertisementEnabled>true</BluetoothAdvertisementEnabled>...
    ```

5. Save the file on your computer

### Use Windows Configuration Designer

You can use Windows Configuration Designer to create a provisioning package that you can use to apply Coordinating Meetings settings to your Surface Hubs. You'll paste the XML file you created above into Windows Configuration Designer to create the provisioning package.

Do the following to create the provisioning package in Windows Configuration Designer:

1. Install Windows Configuration Designer from the Windows Store on your local computer and open it
2. Select **Provision Surface Hub devices** and then **Switch to advanced editor**
3. On the next screen, expand **WindowsTeamSettings** > **Teams** and select **Configurations**
4. In the field next to **Configurations** in the middle pane, paste the single line of XML you created above
5. Select **Export** > **Provisioning package**
6. Provide a name for the provisioning package in **Name** and select **Next** > **Next**
7. Specify a location to save the provisioning package and select **Next**
8. Select **Build** to create the provisioning package and then **Finish**

Finally, after you've created the provisioning package, do the following to apply the provisioning package to your Surface Hub:

1. Save the provisioning package you created above to a USB drive
2. Insert the USB drive into your Surface Hub
3. On your Surface Hub, open the Start menu, select **All apps**, and then select **Settings**
4. Provide your admin username and password and then select **Yes**
5. Select **Surface Hub**, **Device management**, **Add or remove a provisioning package**, and then **Add a package**
6. Under **Select a package**, select **Add** next to your provisioning package, and then restart your Surface Hub

### Use Windows Intune

If your Surface Hubs are managed using Microsoft Intune in Microsoft Endpoint Management, you can use it to apply Coordinated Meetings settings to your Surface Hubs. You'll create a new configuration profile and then paste the XML file you created above into it.

> [!IMPORTANT]
> Your Surface Hubs need to be in a device group so that the Microsoft Intune can identify which devices to apply the configuration profile to. For information about how to create a device group, see [Add groups to organize users and devices](https://docs.microsoft.com/mem/intune/fundamentals/groups-add).

Do the following to create a configuration profile to apply Coordinated Meetings configuration to your Surface Hubs:

1. Sign in to Microsoft Endpoint Manager by visiting https://endpoint.microsoft.com/
2. Navigate to **Devices** > **Configuration profiles** and select **Create profile**
3. Under **Platform**, select **Windows 10 and later**
4. Under **Profile**, select **Custom**, and then click **Create**
5. On the **Basics** tab, in **Name**, provide a descriptive name for your configuration profile and select **Next**
6. On the **Configuration settings** tab, select **Add**
7. In the **Add row** pane, do the following:
    1. Provide a descriptive name and, optionally, a description of the Coordinated Meetings setting you're adding
    2. In **OMA-URI**, enter `./Vendor/MSFT/SurfaceHub/InBoxApps/Teams/Configurations`
    3. In **Data type**, select **String (XML file)**
    4. Open the file browser, select the XML file you created above, and **Open**
8. Select **Add** and then **Next**
9. On the **Assignments** tab, make sure **Assign to** is set to **Selected groups**
10. Under **Selected groups**, select **Select groups to include** and choose the group that contains your Surface Hubs, and then select **Select**
11. Select **Next**, **Next**
12. On the **Review + create**, select **Create**
