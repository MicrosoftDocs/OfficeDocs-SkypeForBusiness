---
title: Teams for Remote Desktop
author: cichur
ms.author: v-cichur
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: alivano
audience: admin
description: Learn how to run Microsoft Teams in a Remote Desktop environment.
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
appliesto: 
  - Microsoft Teams
---

# Teams for Remote Desktop environment

This article describes the requirements and limitations for using Microsoft Teams in a Remote Desktop environment (RDP).

## What is RDP?

RDP is virtualization technology that hosts a desktop operating system and applications on a centralized server in a data center. RDP enables a fully personalized desktop experience to users with a fully secured and compliant centralized source.

Microsoft Teams in a virtualized environment supports chat and collaboration. Teams in a virtualized environment supports multiple configurations.

Using Teams in a virtualized environment is different from using Teams in a non-virtualized environment. For example, some advanced features might not be available in a virtualized environment, and video resolution can differ.

To ensure an optimal user experience, follow the guidance in [How do you use Teams Remote Desktop?](https://support.microsoft.com/windows/how-to-use-remote-desktop-5fe128d5-8fb1-7a23-3b8a-41e636865e8c).

## Teams on RDP requirements

Using Teams in a virtualized environment requires the Teams desktop client app.

The Teams desktop app was validated with leading virtualization solution providers. With multiple market providers, we recommend that you consult your virtualization solution provider to ensure that you meet the minimum requirements.
  
#### Dedicated persistent setup

In a dedicated persistent setup, users' local operating system changes are retained after users sign out. For persistent setup, Teams supports both per-user and per-machine installation.

The following suggestions are the recommended minimum VM configuration.

|Parameter  |Workstation operating system  |Server operating system  |
|---------|---------|---------|
|vCPU   |    2 cores     |  4, 6, or 8<br>It's important to understand the underlying non-uniform memory access (NUMA) configuration and configure your VMs accordingly.     |
|RAM     |   4 GB      | 512 MB to 1024 MB per user        |
|Storage    | 8 GB        | 40 GB to 60 GB        |

#### Non-persistent setup

In a non-persistent setup, users' local operating system changes are not retained after users sign out. Such setups are commonly shared multi-user sessions. VM configuration varies based on the number of users and available physical box resources.

For a non-persistent setup, the Teams desktop app must be installed per-machine to the golden image. (To learn more, see the [Install or update the Teams desktop app on VDI](teams-for-vdi.md#install-or-update-the-teams-desktop-app-on-vdi) section.) This ensures an efficient launch of the Teams app during a user session.

Using Teams in a non-persistent setup also requires a profile-caching manager, for efficient Teams runtime data synchronization. Efficient data synchronization ensures that the appropriate user-specific information (such as a user's data, profile, or settings) is cached during the user's session. Make sure data in these two folders are synched:<br>

- C:\Users\username\AppData\Local\Microsoft\IdentityCache (%localAppdata%\Microsoft\IdentityCache)
- C:\Users\username\AppData\Roaming\Microsoft\Teams (%appdata%\Microsoft\Teams)

> [!NOTE]
> A roaming folder (or, if you are using folder redirection, a caching manager) is required to ensure that the Teams app has the runtime data and files required to run the application. This is necessary to mitigate network latency issues or network glitches, which would otherwise cause application errors and a slow experience due to unavailable data and files.

There are several caching manager solutions available. For example, [FSLogix](https://docs.microsoft.com/fslogix/overview). Consult your caching manager provider for specific configuration instructions.

##### Teams cached content exclusion list for non-persistent setup

Exclude the following data from the Teams caching folder, %appdata%/Microsoft/Teams. Excluding these items helps reduce the user caching size to further optimize your non-persistent setup.

- .txt files
- Media-stack folder
- meeting-addin\Cache (%appdata%\Microsoft\Teams\meeting-addin\Cache)

### Microsoft 365 Apps for enterprise considerations

Consider the following when you deploy Teams with Microsoft 365 Apps for enterprise on RDP.

#### New deployments of Teams through Microsoft 365 Apps for enterprise

Before you deploy Teams through Microsoft 365 Apps for enterprise, you must first uninstall any pre-existing Teams apps if they were deployed using per-machine installation.

#### Using Teams with per-machine installation and Microsoft 365 Apps for enterprise

Microsoft 365 Apps for enterprise doesn't support per-machine installations of Teams. To use per-machine installation, you must exclude Teams from Microsoft 365 Apps for enterprise. See the [Deploy the Teams desktop app to the VM](#deploy-the-teams-desktop-app-to-the-vm) and [How to exclude Teams deployment through Microsoft 365 Apps for enterprise](#how-to-exclude-teams-deployment-through-microsoft-365-apps-for-enterprise) sections.

#### How to exclude Teams deployment through Microsoft 365 Apps for enterprise

To learn more about Teams and Microsoft 365 Apps for enterprise, see [How to exclude Teams from new installations of Microsoft 365 Apps for enterprise](https://docs.microsoft.com/DeployOffice/teams-install#how-to-exclude-microsoft-teams-from-new-installations-of-office-365-proplus) and [Use Group Policy to control the installation of Teams](https://docs.microsoft.com/DeployOffice/teams-install#use-group-policy-to-control-the-installation-of-microsoft-teams).

### Deploy the Teams desktop app to the VM

1. Download the Teams MSI package that matches your RDP VM operating system using one of the following links:

    - [32-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&download=true)
    - [64-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true)

    > [!NOTE]
    > For government clouds, see [Install Microsoft Teams using Microsoft Endpoint Configuration Manager](msi-deployment.md) for the download links to the MSI files.

    The minimum version of the Teams desktop app that's required is version 1.3.00.4461. (PSTN hold isn't supported in earlier versions.)

2. Install the MSI to the RDP VM by running one of the following commands:

    - Per-user installation (default)
  
        ```console
        msiexec /i <path_to_msi> /l*v <install_logfile_name> ALLUSERS=1
        ```

        This process is the default installation, which installs Teams to the %AppData% user folder. At this point, the golden image setup is complete. Teams won't work properly with per-user installation on a non-persistent setup.

    - Per-machine installation

        ```console
        msiexec /i <path_to_msi> /l*v <install_logfile_name> ALLUSER=1 ALLUSERS=1
        ```

        This process installs Teams to the Program Files (x86) folder on a 64-bit operating system and to the Program Files folder on a 32-bit operating system. At this point, the golden image setup is complete. Installing Teams on each machine is required for non-persistent setups.

        The next interactive sign-in session starts Teams and asks for credentials.

        > [!NOTE]
        > These examples also use the **ALLUSERS=1** parameter. When you set this parameter, Teams Machine-Wide Installer appears in Programs and Features in Control Panel and in Apps & features in Windows Settings for all users of the computer. All users can then uninstall Teams if they have admin credentials.
        It's important to understand the difference between **ALLUSERS=1** and **ALLUSER=1**. The **ALLUSERS=1** parameter can be used in non-RDP and RDP environments, while the **ALLUSER=1** parameter is used only in RDP environments to specify a per-machine installation.

3. Uninstall the MSI from the RDP VM. There are two ways to uninstall Teams.

    - PowerShell script: You can use [this PowerShell script](scripts/powershell-script-deployment-cleanup.md) to uninstall Teams and remove the Teams folder for a user. Run the script for each user profile in which Teams was installed on the computer.
    - Command line: Run the following command.
  
      ```console
      msiexec /passive /x <path_to_msi> /l*v <uninstall_logfile_name>
      ```

      This process uninstalls Teams from the Program Files (x86) folder or Program Files folder, depending on the operating system environment.

### Network requirements

We recommend that you evaluate your environment to identify any risks and requirements that can influence your overall cloud voice and video deployment. Use the [Skype for Business Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) to test whether your network is ready for Teams.

To learn more about how to prepare your network for Teams, see [Prepare your organization's network for Teams](prepare-network.md).

### Teams on Chrome browser versus Teams desktop app for RDP

Teams on Chrome browser doesn't provide a replacement for the Teams desktop app for RDP with AV optimization. The chat and collaboration experience works as expected. When media is needed, there are some experiences that might not meet user expectations on the Chrome browser:

- The audio and video streaming experience might not be optimal. Users might experience delays or reduced quality.
- Device settings aren't available in browser settings.
- Device management is handled through the browser and requires multiple settings in browser site settings.
- Device settings might need to be set in Windows device management.

## Teams on RDP with chat and collaboration

If your organization wants to only use chat and collaboration features in Teams, you can set user-level policies to turn off calling and meeting functionality in Teams.

### Set policies to turn off calling and meeting functionality

You can set policies by using the Microsoft Teams admin center or PowerShell. It might take some time (a few hours) for the policy changes to propagate. If you don't see changes for a given account immediately, try again in a few hours.

[**Calling polices**](teams-calling-policy.md): Teams includes the built-in DisallowCalling calling policy, in which all calling features are turned off. Assign the DisallowCalling policy to all users in your organization who use Teams in a virtualized environment.

[**Meeting policies**](meeting-policies-in-teams.md): Teams includes the built-in AllOff meeting policy, in which all meeting features are turned off. Assign the AllOff policy to all users in your organization who use Teams in a virtualized environment.

#### Assign policies using the Microsoft Teams admin center

To assign the DisallowCalling calling policy and the AllOff meeting policy to a user:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**.

2. Select the user by clicking to the left of the user name, and then select **Edit settings**.

3. Do the following steps:

    a.  Under **Calling policy**, select **DisallowCalling**.

    b.  Under **Meeting policy**, select **AllOff**.

    c. Select **Apply**.

To assign a policy to multiple users at a time:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then search for the users or filter the view to show the users you want.

2. In the **&#x2713;** (check mark) column, select the users. To select all users, select the &#x2713; (check mark) at the top of the table.

3. Select **Edit settings**, make the changes that you want, and then select **Apply**.

Or, you can also do the following steps:

1. In the left navigation of the Microsoft Teams admin center, go to the policy you want to assign. For example:

    - Go to **Voice** > **Calling policies**, and then select **DisallowCalling**.
    - Go to **Meetings** > **Meeting policies**, and then select **AllOff**.

2. Select **Manage users**.

3. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.

4. When you're finished adding users, select **Save**.

#### Assign policies using PowerShell

The following example shows how to use the [Grant-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamscallingpolicy) to assign the DisallowCalling calling policy to a user.

```PowerShell
Grant-CsTeamsCallingPolicy -PolicyName DisallowCalling -Identity "user email id"
```

To learn more about using PowerShell to manage calling policies, see [Set-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamscallingpolicy).

The following example shows how to use the [Grant-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsmeetingpolicy) to assign the AllOff meeting policy to a user.

```PowerShell
Grant-CsTeamsMeetingPolicy -PolicyName AllOff -Identity "user email id"
```

To learn more about using PowerShell to manage meeting policies, see [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy).

## Migrate Teams on RDP with chat and collaboration to optimize Teams with calling and meetings

If you have an existing implementation of Teams on RDP with chat and collaboration in which you had set user-level policies to turn off calling and meeting functionality, and you're migrating to Teams with AV optimization, you must set policies to turn on calling and meeting functionality for those Teams on RDP users.

### Set policies to turn on calling and meeting functionality

You can use the Microsoft Teams admin center or PowerShell to set and assign calling and meeting policies to your users. It can take some time (a few hours) for policy changes to propagate. If you don't see changes for a given account immediately, try again after a few hours.

[**Calling polices**](teams-calling-policy.md): Calling policies in Teams control, which calling features are available to users. Teams includes the built-in AllowCalling calling policy, in which all calling features are turned on. To turn on all calling features, assign the AllowCalling policy. Or, create a custom calling policy to turn on the calling features that you want and assign it to users.

[**Meeting policies**](meeting-policies-in-teams.md): Meeting policies in Teams control the types of meetings that users can create and the features that are available to meeting participants that are scheduled by users in your organization. Teams includes the built-in AllOn meeting policy, in which all meeting features are turned on. To turn on all meeting features, assign the AllOn policy. Or, create a custom meeting policy to turn on the meeting features that you want and assign it users.

#### Assign policies using the Teams admin center

To assign the AllowCalling calling policy and the AllOn meeting policy to a user:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**.

2. Select the user by clicking to the left of the user name, and then select **Edit settings**.

3. Do the following steps:

    a.  Under **Calling policy**, select **AllowCalling**.

    b.  Under **Meeting policy**, select **AllOn**.

    c. Select **Apply**.

To assign a policy to multiple users at a time:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then search for the users or filter the view to show the users you want.

2. In the **&#x2713;** (check mark) column, select the users. To select all users, select the **&#x2713;** (check mark) at the top of the table.

3. Select **Edit settings**, make the changes that you want, and then select **Apply**.

Or, you can also do the following steps:

1. In the left navigation of the Microsoft Teams admin center, go to the policy you want to assign. For example:

    - Go to **Voice** > **Calling policies**, and then select **AllowCalling**.
    - Go to **Meetings** > **Meeting policies**, and then select **AllOn**.

2. Select **Manage users**.

3. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.

4. When you're finished adding users, select **Save**.

#### Assign policies with PowerShell

The following example shows how to use the [Grant-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamscallingpolicy) to assign the AllowCalling calling policy to a user.

```PowerShell
Grant-CsTeamsCallingPolicy -PolicyName AllowCalling -Identity "user email id"
```

To learn more about using PowerShell to manage calling policies, see [Set-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamscallingpolicy).

The following example shows how to use the [Grant-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsmeetingpolicy) to assign the AllOn meeting policy to a user.

```PowerShell
Grant-CsTeamsMeetingPolicy -PolicyName AllOn -Identity "user email id"
```

To learn more about using PowerShell to manage meeting policies, see [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy).

## Control fallback mode in Teams

When users connect from an unsupported endpoint, the users are in fallback mode, in which AV isn't optimized. You can disable or enable fallback mode by setting one of the following registry DWORD values:

- HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Teams\DisableFallback
- HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\Teams\DisableFallback

To disable fallback mode, set the value to **1**. To enable audio only, set the value to **2**. If the value isn't present or is set to **0** (zero), fallback mode is enabled.

This feature is available in Teams version 1.3.00.13565 and later.

## Known issues and limitations

### Client deployment, installation, and setup

- With per-machine installation, Teams on RDP isn't automatically updated in the way that non-RDP Teams clients are. You must uninstall the current version to update to a newer version.
- Teams should be deployed either per user or per machine. Deployment of Teams for concurrent per user and per machine is not supported. To migrate from either per machine or per user to one of these modes, follow the uninstall procedure and redeploy to either mode.

### Calling and meetings

The following calling and meeting features aren't supported:

- Enhanced emergency services
- HID buttons and LED controls between the Teams app and devices
- Background blur and effects
- Broadcast and live event producer and presenter roles
- Location-Based Routing (LBR)
- Call park
- Call queue
- Shared system audio/computer sound
- Media bypass for Direct Routing

> [!NOTE]
> We're working on adding calling and meeting features that are currently only available in non-RDP environments. These might include more admin control over quality, additional screen sharing scenarios, and advanced features recently added to Teams. Contact your Teams representative to learn more about upcoming features.

The following are known issues and limitations for calling and meetings:

Issues with Audio and Video:

1213011: Teams cannot find the local webcam when in RDP session.

1213014: Audio and Video settings do not work properly in RDP

1213000: No audio notifications from Teams in Remote Desktop Connection session

Issues with screen sharing

1215075: RDP controls overlap with Teams Meeting Screen share controls when Remote Desktop Client is in Full Screen

1213010: Presenting in RDP session: sharing screen Teams places a large black box around my cursor

1213292: Mouse cursor jumps around a lot when sharing in a Remote Desktop Connection session

For Teams known issues that aren't related to RDP, see [Support Teams in your organization](Known-issues.md).
