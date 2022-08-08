---
title: Manage Microsoft Teams configuration on Surface Hub
ms.author: dstrome
author: dstrome
ms.reviewer: rahulmi
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Rooms
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: Manage Microsoft Teams settings on Surface Hub using Microsoft Intune and Windows Configuration Designer
---

# Manage Microsoft Teams settings on Surface Hub

You can manage Microsoft Teams settings on a Surface Hub using Windows Configuration Designer or Microsoft Intune in Microsoft Endpoint Manager. Knowledge of Windows Configuration Designer or Microsoft Intune is required to make changes to Teams settings. For more information about these options, see the following articles:

- [Create a provisioning package for Windows 10](/windows/configuration/provisioning-packages/provisioning-create-package)
- [What is Microsoft Intune device management?](/mem/intune/remote-actions/device-management)

Windows Configuration Designer is a good option if you only have a few Surface Hub devices and you can access them easily. If you have many Surface Hubs, or if they're in remote locations, use Microsoft Intune in Microsoft Endpoint Manager if its deployed in your organization. Regardless of the method you choose, you need to create an XML configuration file to make changes to Teams settings on Surface Hub.

## Teams configuration file syntax

Teams configuration on a Surface Hub is defined using an XML file. The XML file contains all the settings that can be used to control how Teams works. Both Windows Configuration Designer and Microsoft Intune use the same XML syntax. Here's an example of the Teams configuration XML file:

```xml
<SurfaceHubSettings>
    <BluetoothAdvertisementEnabled>true</BluetoothAdvertisementEnabled>
    <AutoAcceptProximateMeetingInvitations>true</AutoAcceptProximateMeetingInvitations>
    <CoordinatedMeetings enabled="true"> 
        <TrustedAccounts>room@contoso.com</TrustedAccounts>
        <Settings> 
            <Audio default="false" enabled="false" />
            <Video default="false" enabled="true" /> 
        </Settings> 
    </CoordinatedMeetings>
</SurfaceHubSettings>
```

The following table describes all the configuration settings available in the configuration file:

| Parent                  | Element                                   | Attribute | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|-------------------------|-------------------------------------------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| None                    | `<SurfaceHubSettings>`                    |           | Contains all configuration elements for Teams configuration on a Surface Hub.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `<SurfaceHubSettings>`  | `<BluetoothAdvertisementEnabled>`         |           | Determines whether Surface Hub advertises that it's available for Bluetooth connections.<br>Accepted values: `true`, `false`                                                                                                                                                                                                                                                                                                                                                                                         |
| `<SurfaceHubSettings>`  | `<AutoAcceptProximateMeetingInvitations>` |           | Determines whether Teams will automatically accept proximity-based meetings.<br>Accepted values: `true`, `false`                                                                                                                                                                                                                                                                                                                                                                                                     |
| `<SurfaceHubSettings>`  | `<CoordinatedMeetings>`                   |           | Contains all configuration elements for Coordinated Meetings.                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|                         |                                           | `enabled` | Determines whether Teams is configured to participate in Coordinated Meetings with other devices.<br>Accepted values: `true`, `false`                                                                                                                                                                                                                                                                                                                                                                                |
| `<CoordinatedMeetings>` | `<TrustedAccounts>`                       |           | This is a comma-separated list of UPNs for each Teams Room device or Surface Hub that the device should accept meeting join requests from, or to which meeting join requests should be sent.<br>Accepted values: string                                                                                                                                                                                                                                                                                                                         |
| `<CoordinatedMeetings>` | `<Settings>`                              |           | Contains configuration audio and video configuration elements for Coordinated Meetings                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `<Settings>`            | `<Audio>`                                 |           | Controls audio configuration for Teams on a Surface Hub.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|                         |                                           | `default` | Determines on which device the microphone will be active when a meeting starts. Only one device (typically a Teams Rooms device) can have this field set to `true` while the rest of the devices must have this field set to `false` to avoid audio echo and feedback.<br>Accepted values: `true`, `false`                                                                                                                                                                                                           |
|                         |                                           | `enabled` | Determines whether participants in a meeting can toggle the microphone on or off. Devices on which **Audio default** is set to `false` should have this setting set to `false` so that participants can't accidentally turn on a microphone and cause audio echo or feedback.<p>If **Audio default** is set to `true`, this setting is ignored and participants can mute or unmute the microphone.<br>Accepted values: `true`, `false`                                                                               |
| `<Settings>`            | `<Video>`                                 |           | Controls video configuration for Teams on a Surface Hub.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|                         |                                           | `default` | Determines on which device the camera will be active when a meeting starts. For the best experience, we recommend that only the Teams Rooms device be set to `true` while all other devices are set to `false`.<br>Accepted values: `true`, `false`                                                                                                                                                                                                                                                                  |
|                         |                                           | `enabled` | Determines whether participants in a meeting can toggle the camera on or off. You can set this to `true` on any other devices in the event participants want to share different video perspectives (such as if a participant is using the Surface Hub whiteboard). If you don't want participants to turn a camera on or off on a device, set this to `false`.<p> If **Video default** is set to `true`, this setting is ignored and participants can turn the camera on or off.<br>Accepted values: `true`, `false` |

## Apply Teams settings to Surface Hub

Apply or update Teams configuration settings on Surface Hub using either Windows Configuration Designer or Microsoft Intune in Microsoft Endpoint Manager.

### Use Windows Configuration Designer

You can use Windows Configuration Designer to create a provisioning package that you can use to apply Teams settings to your Surface Hubs. You'll paste the XML file you created above into Windows Configuration Designer to create the provisioning package.

> [!IMPORTANT]
> If you've already applied Teams configuration to your Surface Hub using a provisioning package and want to change it, you need to remove the existing provisioning package first. For more information, see [Remove a provisioning package created by Windows Configuration Designer](#remove-a-provisioning-package-created-by-windows-configuration-designer).

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
5. Go to **Surface Hub**, **Device management**, **Add or remove a provisioning package**, and then **Add a package**
6. Under **Select a package**, select **Add** next to your provisioning package, and then restart your Surface Hub

### Use Microsoft Intune

If your Surface Hubs are managed using Microsoft Intune in Microsoft Endpoint Management, you can use it to apply Teams settings to your Surface Hubs. You'll create a new configuration profile and then paste the XML file you created above into it.

> [!IMPORTANT]
> Your Surface Hubs need to be in a device group so that the Microsoft Intune can identify which devices to apply the configuration profile to. For information about how to create a device group, see [Add groups to organize users and devices](/mem/intune/fundamentals/groups-add).

Do the following to create a configuration profile to apply Teams settings to your Surface Hubs:

1. Sign in to Microsoft Endpoint Manager by visiting https://endpoint.microsoft.com/
2. Navigate to **Devices** > **Configuration profiles** and select **Create profile**
3. Under **Platform**, select **Windows 10 and later**
4. Under **Profile**, select **Custom**, and then click **Create**
5. On the **Basics** tab, in **Name**, provide a descriptive name for your configuration profile and select **Next**
6. On the **Configuration settings** tab, select **Add**
7. In the **Add row** pane, do the following:
    1. Provide a descriptive name and, optionally, a description of the Teams setting you're adding
    2. In **OMA-URI**, enter `./Vendor/MSFT/SurfaceHub/InBoxApps/Teams/Configurations`
    3. In **Data type**, select **String (XML file)**
    4. Open the file browser, select the XML file you created above, and **Open**
8. Select **Add** and then **Next**
9. On the **Assignments** tab, make sure **Assign to** is set to **Selected groups**
10. Under **Selected groups**, select **Select groups to include** and choose the group that contains your Surface Hubs, and then select **Select**
11. Select **Next**, **Next**
12. On the **Review + create**, select **Create**

## Remove Teams settings from a Surface Hub

Remove Teams configuration settings on Surface Hub using either Windows Configuration Designer or Microsoft Intune in Microsoft Endpoint Manager.

### Remove a provisioning package created by Windows Configuration Designer

If you applied Teams settings to a Surface Hub using a provisioning package created by Windows Configuration Designer, use the following steps to remove the package and its settings:

1. On your Surface Hub, open the Start menu, select **All apps**, and then select **Settings**
2. Provide your admin username and password and then select **Yes**
3. Go to **Surface Hub**, **Device management** and then **Add or remove a provisioning package**
4. Next to the provisioning package you want to remove, select **Remove**
5. Go to **Surface Hub** and then **Apps & features**
6. Find **Microsoft Teams for Surface Hub** and then select **Advanced Options**
7. Select **Reset**, and then **Reset** again
8. Restart your Surface Hub

### Remove settings applied by Microsoft Intune

If you applied Teams settings to a Surface Hub using Microsoft Intune in Microsoft Endpoint Management, use the following steps to remove the configuration profile and its settings:

1. Sign in to Microsoft Endpoint Manager by visiting https://endpoint.microsoft.com/
2. Navigate to **Devices** > **Configuration profiles**
3. Select the configuration profile that contains the Coordinated Meeting settings you want to remove
4. On the configuration profile details page, select **Delete** and then **OK**

After you've removed configuration profile that contained the Coordinated Meeting settings for your Surface Hub, use the following steps to reset the Teams app on the Surface Hub:

1. On your Surface Hub, open the Start menu, select **All apps**, and then select **Settings**
2. Provide your admin username and password and then select **Yes**
3. Go to **Surface Hub** and then **Apps & features**
4. Find **Microsoft Teams for Surface Hub** and then select **Advanced Options**
5. Select **Reset**, and then **Reset** again
6. Restart your Surface Hub
