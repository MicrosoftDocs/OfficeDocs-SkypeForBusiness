---
title: Teams for Virtualized Desktop Infrastructure
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: rafarhi, jmorrow
audience: admin
description: Learn how to run Microsoft Teams in a Virtualized Desktop Infrastructure (VDI) environment.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Teams for Virtualized Desktop Infrastructure

This article describes the requirements and limitations for using Microsoft Teams in a virtualized environment.

## What is VDI?

Virtual Desktop Infrastructure (VDI) is virtualization technology that hosts a desktop operating system and applications on a centralized server in a data center. This enables a fully personalized desktop experience to users with a fully secured and compliant centralized source.
 
Microsoft Teams in a virtualized environment supports chat and collaboration, and with the Citrix platform, calling and meeting functionality are also supported.

Teams in a virtualized environment supports multiple configurations. These include VDI, RDHS, dedicated, shared, persistent and non-persistent modes. Features are in continuous development and are added on a regular basis, and functionality will expand in the coming months and years.
 
Using Teams in a virtualized environment may be somewhat different from using Teams in a non-virtualized environment. For example, some advanced features may not be available in a virtualized environment and video resolution may differ. To ensure an optimal user experience, follow the guidance in this article.

## Teams on VDI components

Using Teams in a virtualized environment requires the following components.

- **Virtualization broker**: The resource and connection manager to the virtualization provider, such as Azure
- **Virtual desktop**: The Virtual Machine (VM) stack that runs Microsoft Teams
- **Thin client**: The endpoint that the user physically interfaces with
- **Teams desktop app**: This is the Teams desktop client app

## Teams on VDI requirements

### Virtualization provider requirements

The Teams desktop app was validated with leading virtualization solution providers. With multiple market providers, we recommend that you consult your virtualization solution provider to ensure minimum requirements are met.
  
Currently, Teams on VDI with audio/video (AV) optimization is certified with Citrix. Review the information in this section to ensure both Citrix and Teams requirements are met for proper functionality.

### Citrix Virtual Apps and Desktops requirements

Citrix Virtual Apps and Desktops (formerly known as XenApp and XenDesktop) provides AV optimization for Teams on VDI. With Citrix Virtual Apps and Desktops, Teams on VDI supports calling and meeting functionality in addition to chat and collaboration.

You can download the latest version of Citrix Virtual Apps and Desktops [here](https://www.citrix.com/downloads/citrix-virtual-apps-and-desktops/). (You'll need to sign in first.) The necessary components are bundled into the [Citrix Workspace app (CWA)](https://www.citrix.com/downloads/workspace-app/) and Virtual Delivery Agent (VDA) by default. You don't need to install any additional components or plugins on CWA or the VDA.

For the latest server and client requirements, see [this Citrix website](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html).

## Install the Teams desktop app on VDI

You can deploy the Teams desktop app for VDI using a per-machine installation or per-user installation using the MSI package. Deciding on which approach to use depends on whether you use a persistent or non-persistent setup and the associated functionality needs of your organization.
For a dedicated persistent setup, either approach would work.  However, for a non-persistent setup, per-machine installation is required for Teams to work efficiently. See the [Non-persistent setup](#non-persistent-setup) section.

With per-machine installation, automatic updates is disabled. This means that to update the Teams app, you must uninstall the current version to update to a newer version. With per-user installation, automatic updates is enabled. For most VDI deployments, we recommend you deploy Teams using per-machine installation.

#### Dedicated persistent setup

In a dedicated persistent setup, users' local operating system changes are retained after users log off.  For persistent setup, Teams support both per-user and per-machine installation.

The following is the recommended minimum VM configuration.

|Parameter  |Workstation operating system  |Server operation system  |
|---------|---------|---------|
|vCPU   |    2 cores     |  4,6, or 8<br>It's important to understand the underlying non-uniform memory access (NUMA) configuration and configure your VMs accordingly.     |
|RAM     |   4 GB      | 512 to 1024 MB per user        |
|Storage    | 8 GB        | 40 to 60 GB        |

#### Non-persistent setup

In a non-persistent setup, users' local operating system changes are not retained after users log off. Such setups are commonly shared multi-user sessions. VM configuration varies based on the number of users and available physical box resources.

For a non-persistent setup, the Teams desktop app must be installed per-machine to the golden image. This ensures an efficient launch of the Teams app during a user session. Using Teams with a non-persistent setup also requires a profile caching manager for efficient Teams runtime data sync. This ensures that the appropriate user-specific information (for example, user data, profile, and settings) are cached during the user session.  There are variety of caching manager solutions available. For example, [FSLogix](https://docs.microsoft.com/en-us/fslogix/overview). Consult your caching manager provider for specific configuration instructions.

##### Teams cached content exclusion list for non-persistent setup

Exclude the following from the Teams caching folder, %appdata%/Microsoft/Teams.  Excluding these help reduce the user caching size to further optimize your non-persistent setup.

- .txt files
- Media-stack folder

### Office 365 ProPlus considerations

Consider the following when you deploy Teams with Office 365 ProPlus on VDI.

#### New deployments of Teams through Office 365 ProPlus

Before you deploy Teams through Office 365 ProPlus, you must first uninstall any pre-existing Teams apps if they were deployed using per-machine installation.

Teams through Office 365 ProPlus is installed per-user. To learn more, see [Deploy Microsoft Teams with Office 365 ProPlus](https://docs.microsoft.com/deployoffice/teams-install).

#### Teams deployments through Office 365 ProPlus updates

Teams is also being added to existing installations of Office 365 ProPlus. Since Office 365 ProPlus installs Teams per-user only, see [Deploy Microsoft Teams with Office 365 ProPlus](https://docs.microsoft.com/deployoffice/teams-install).

#### Using Teams with per-machine installation and Office 365 ProPlus

Office 365 ProPlus doesn't support per-machine installations of Teams. To use per-machine installation, you must exclude Teams from Office 365 ProPlus. See the [Deploy the Teams desktop app to the VM](#deploy-the-teams-desktop-app-to-the-vm) and [How to exclude Teams deployment through Office 365 ProPlus](#how-to-exclude-teams-deployment-through-office-365-proplus) sections.

#### How to exclude Teams deployment through Office 365 ProPlus

To learn more about Teams and Office 365 ProPlus, see [How to exclude Teams from new installations of Office 365 ProPlus](https://docs.microsoft.com/en-us/DeployOffice/teams-install#how-to-exclude-microsoft-teams-from-new-installations-of-office-365-proplus) and [Use Group Policy to control the installation of Teams](https://docs.microsoft.com/en-us/DeployOffice/teams-install#use-group-policy-to-control-the-installation-of-microsoft-teams).

### Deploy the Teams desktop app to the VM

1. Download the Teams MSI package that matches your VDI VM operating system using one of the following links.

    - [32-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&download=true&managedInstaller=true)
    - [64-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&download=true&managedInstaller=true&arch=x64)

2. Install the MSI to the VDI VM by running one of the following commands:

    - Per-machine installation (recommended)

        ```
        msiexec /i <path_to_msi> /l*v <install_logfile_name> ALLUSER=1
        ```

        This installs Teams to the Program Files (x86) folder on a 64-bit operating system and to the Program Files folder on a 32-bit operating system. At this point, the golden image setup is complete. Installing Teams per-machine is required for non-persistent setups.
 
        The next interactive logon session starts Teams and asks for credentials.
   
   - Per-user installation  (default)
  
        ```
        msiexec /i <path_to_msi> /l*v <install_logfile_name>
        ```
    
        This is the default installation, which installs Teams to the %AppData% user folder. At this point, the golden image setup is complete. Teams will not work properly with per-user installation on a non-persistent setup.
    
3. Uninstall the MSI from the VDI VM by running the following command:

    ```
    msiexec /passive /x <path_to_msi> /l*v <uninstall_logfile_name>
    ```
    This uninstalls Teams from the Program Files (x86) folder or Program Files folder, depending on the operating system environment.

## Teams on VDI performance considerations

There are variety of virtualized setup configurations, each with a different focus for optimization. For example, user density. When planning, consider the following to help optimize your setup based on the workload needs of your organization:

- Minimum requirement: Some workloads may require a setup using resources that are above the minimum requirements. For example, workloads for developers who use applications that demand more computing resources.
- Dependencies: These include dependencies on infrastructure, workload, and other environmental considerations outside the Teams desktop app.
- Disabled features on VDI: Teams disables GPU-intensive features for VDI, which can help improve transient CPU utilization. The following features are disabled:
    - Teams CSS animation
    - Giphy auto-start

## Teams on VDI with calling and meetings

In addition to chat and collaboration, Teams on VDI with calling and meeting support is available with Citrix-based platforms. Supported features are based on the WebRTC media stack and Citrix-specific implementation. The following diagram provides an overview of the architecture.

These calling and meeting features are not supported:

- Enhanced emergency services
- HID buttons and LED controls between the Teams app and devices
- Background blur and effects
- Broadcast/live events
- Location-Based Routing (LBR)
- Call park
- Call queue

We're working on adding calling and meeting features that are currently only available in non-VDI environments. These may include more admin control over quality, additional screen sharing scenarios, and advanced features recently added to Teams. Contact your Teams representative to learn more about upcoming features.

### Network requirements

We recommend that you evaluate your environment to identify any risks and requirements that can influence your overall cloud voice and video deployment. Use the [Skype for Business Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) to test whether your network is ready for Teams.

To learn more about how to prepare your network for Teams, see [Prepare your organization's network for  Teams](prepare-network.md).

### Migrate from Skype for Business on VDI to Teams on VDI

If you're migrating from Skype for Business on VDI to Teams on VDI, besides the differences between the two applications, there are some differences when VDI is also implemented. Some capabilities that aren’t currently supported in Teams VDI that are in Skype for Business VDI are as follows:

- Control of VDI calling experiences with policies for limiting media bitrate
- Per-platform policy to disable some AV features in VDI
- Give and take control when app sharing
- Screen share from chat without audio
- Simultaneous video and screen sharing send and receive

### Teams on Chrome browser versus Teams desktop app for VDI

Teams on Chrome browser doesn't provide a replacement for the Teams desktop app for VDI with AV optimization. The chat and collaboration experience works as expected. When media is needed, there are some experiences that may not meet user expectations on the Chrome browser.

- The audio and video streaming experience may not be optimal. Users may experiences delays or reduced quality.
- Device settings aren't available in browser settings.
- Device management is handled through the browser and requires multiple settings in browser site settings.
- Device settings may also need to be set in Windows device management.

## Teams on VDI with chat and collaboration

If your organization wants to only use chat and collaboration features in Teams, you can set user-level policies to turn off calling and meeting functionality in Teams. This feature level doesn't require Citrix Virtual Apps and Desktops.

### Set policies to turn off calling and meeting functionality

You can set policies by using the Microsoft Teams admin center or PowerShell. It can take some time (a few hours) for the policy changes to propagate. If you don’t see changes for a given account immediately, try again in a few hours.

[**Calling polices**](teams-calling-policy.md): Teams includes the built-in DisallowCalling calling policy, in which all calling features are turned off. Assign the DisallowCalling policy to all users in your organization who use Teams in a virtualized environment. 

[**Meeting policies**](meeting-policies-in-teams.md): Teams includes the built-in AllOff meeting policy, in which all meeting features are turned off. Assign the AllOff policy to all users in your organization who use Teams in a virtualized environment. 

#### Assign policies using the Microsoft Teams admin center

To assign the DisallowCalling calling policy and the AllOff meeting policy to users, follow these steps:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**.
2. Select the user by clicking to the left of the user name, and then click **Edit settings**.
3. Do the following:
    1.  Under **Calling policy**, click **DisallowCalling**.
    2.  Under **Meeting policy**, click **AllOff**.
4. Click **Apply**.

To assign a policy to multiple users at a time, see [Edit Teams user settings in bulk](edit-user-settings-in-bulk.md).

Or, you can also do the following:

1. In the left navigation of the Microsoft Teams admin center, go to the policy you want to assign. For example:
    - Go to **Voice** > **Calling policies**, and then click **DisallowCalling**.
    - Go to **Meetings** > **Meeting policies**, and then click **AllOff**.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then click **Add**. Repeat this step for each user that you want to add.
5. When you're finished adding users, click **Save**.

#### Assign policies using PowerShell

The following example shows how to use the [Grant-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamscallingpolicy) to assign the DisallowCalling calling policy to a user.

```
Grant-CsTeamsCallingPolicy -PolicyName DisallowCalling -Identity “user email id”
```

To learn more about using PowerShell to manage calling policies, see [Set-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamscallingpolicy).

The following example shows how to use the [Grant-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsmeetingpolicy) to assign the AllOff meeting policy to a user.

```
Grant-CsTeamsMeetingPolicy -PolicyName AllOff -Identity “user email id”
```

To learn more about using PowerShell to manage meeting policies, see [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy).

## Migrate Teams on VDI with chat and collaboration to Citrix with calling and meetings

If you have an existing implementation of Teams on VDI with chat and collaboration in which you had set user-level policies to turn off calling and meeting functionality, and you're migrating to Citrix with AV optimization, you must set policies to turn on calling and meeting functionality for those Teams on VDI users.

### Set policies to turn on calling and meeting functionality

You can use the Microsoft Teams admin center or PowerShell to set and assign calling and meeting policies to your users. It can take some time (a few hours) for policy changes to propagate. If you don’t see changes for a given account immediately, try again after a few hours.

[**Calling polices**](teams-calling-policy.md): Calling policies in Teams control which calling features are available to users. Teams includes the built-in AllowCalling calling policy, in which all calling features are turned on. To turn on all calling features, assign the AllowCalling policy. Or, create a custom calling policy to turn on the calling features that you want and assign it to users. 

[**Meeting policies**](meeting-policies-in-teams.md): Meeting policies in Teams control the types of meetings that users can create and the features that are available to meeting participants that are scheduled by users in your organization. Teams includes the built-in AllOn meeting policy, in which all meeting features are turned on. To turn on all meeting features, assign the AllOn policy. Or, create a custom meeting policy to turn on the meeting features that you want and assign it users.

#### Assign policies using the Microsoft Teams admin center

To assign the AllowCalling calling policy and the AllOn meeting policy to users, follow these steps:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**.
2. Select the user by clicking to the left of the user name, and then click **Edit settings**.
3. Do the following:
    1.  Under **Calling policy**, click **AllowCalling**.
    2.  Under **Meeting policy**, click **AllOn**.
4. Click **Apply**.

To assign a policy to multiple users at a time, see [Edit Teams user settings in bulk](edit-user-settings-in-bulk.md).

Or, you can also do the following:

1. In the left navigation of the Microsoft Teams admin center, go to the policy you want to assign. For example:
    - Go to **Voice** > **Calling policies**, and then click **AllowCalling**.
    - Go to **Meetings** > **Meeting policies**, and then click **AllOn**.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then click **Add**. Repeat this step for each user that you want to add.
5. When you're finished adding users, click **Save**.

#### Assign policies using PowerShell

The following example shows how to use the [Grant-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamscallingpolicy) to assign the AllowCalling calling policy to a user.

```
Grant-CsTeamsCallingPolicy -PolicyName AllowCalling -Identity “user email id”
```

To learn more about using PowerShell to manage calling policies, see [Set-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamscallingpolicy).

The following example shows how to use the [Grant-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsmeetingpolicy) to assign the AllOn meeting policy to a user.

```
Grant-CsTeamsMeetingPolicy -PolicyName AllOn -Identity “user email id”
```

To learn more about using PowerShell to manage meeting policies, see [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy).

## Known issues and limitations

### Client deployment, installation, and setup

- With per-machine installation, Teams on VDI isn't automatically updated in the way that non-VDI Teams clients are. You have to update the VM image by installing a new MSI as described in the [Install the Teams desktop app on VDI](#install-the-teams-desktop-app-on-vdi) section. You must uninstall the current version to update to a newer version.
- MacOs and Linux-based clients are not supported by Citrix at this time.

### Calling and meetings

- Interoperability with Skype for Business is limited to audio calls, no video modality.
- Dual Tone Multi Frequency (DTMF) interaction with telephony systems  is currently not supported.
- Joining Teams meetings as an anonymous user isn't AV-optimized. The user can join the meeting and have a non-optimized experience.
- Only a single incoming video stream is supported in meetings or group calls. When multiple people send video, only the dominant speaker's video is shown at any given time.  
- Incoming and outgoing video stream resolution is limited to 720p resolution. This is a WebRTC limitation.
- Only one video stream from an incoming camera or screen share stream is supported. When there's an incoming screen share, that screen share is shown it instead of the video of the dominant speaker.
- Outgoing screen sharing:
    - Application sharing is not supported.
    - Potential privacy issue with multiple screen.
- Give control and take control:  
    - Not supported during a screen sharing or application sharing session.
    - Supported during a PowerPoint sharing session.  
- In some cases, zooming windows that contain video content may create situations where user interface elements are partially visible.  
- High DPI scaling on CWA is not supported.

For Teams known issues that aren’t related to VDI, see [Known issues for Teams](Known-issues.md).

## Troubleshooting

#### Troublehoot Citrix components

For information on how to troubleshoot VDA and CWA issues, see [this Citrix website](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html).

#### Troubleshoot Teams on VDI

## Related topics

- [Install Microsoft Teams using MSI](msi-deployment.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
