---
title: Teams in Virtualized Desktop Infrastructure
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.date: 03/25/2018
ms.topic: article
ms.service: msteams
ms.reviewer: 
description: Learn how to run Microsoft Teams in a Virtualized Desktop Infrastructure (VDI) environment.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto: 
- Microsoft Teams
---

# Teams in Virtualized Desktop Infrastructure

This article describes the requirements and limitations for using Microsoft Teams in a virtualized environment.

## What is VDI?

Virtual Desktop Infrastructure (VDI) is virtualization technology that hosts a desktop operating system and applications on a centralized server in a data center. This enables a fully personalized desktop experience to users with a fully secured and compliant centralized source. 
 
Currently, Teams in a virtualized environment is available with support for collaboration and chat functionality with a dedicated persistent virtualized machine (VM). To ensure an optimal user experience, follow the guidance in this article. 

## Teams requirements

### Set policies to turn off calling and meeting functionality in Teams

The Teams calling and meeting experience isn't optimized for a VDI environment. For steps on how to set user-level policies to turn off calling and meeting functionality in Teams, see the Appendix. 

You can still choose to run Teams fully in VDI using either the Teams desktop app or web app web. However, we recommend that you set the policies described in the Appendix to avoid compromising the user experience.  

It can take some time (a few hours) for the policy changes to propagate. If you don’t see changes for a given account immediately, try again in a few hours.

### Virtualization provider requirements

The Teams app has been validated on leading virtualization solution providers. With multiple market providers, consult your virtualization solution provider to ensure minimum requirements are met.

### Virtual Machine requirements

With the diverse workloads and user needs in a virtualized environment, here's the minimum recommended VM configuration.

|Parameter  |Measure  |
|---------|---------|
|vCPU    |  2 cores       |
|RAM     |  4 GB      |
|Storage     | 8 GB       |

### Virtual machine operating system requirements

The supported operating systems for VM are:

- Windows 10 and later
- Windows Server 2012 R2 and later

## Install Teams on VDI

Here's the process and tools to deploy the Teams desktop app. For complete guidance, see [Teams in Virtualized Desktop Infrastructure](teams-in-vdi.md). 

1. Download the Teams MSI package using one of the following links depending on the environment. We recommend the 64-bit version for a VDI VM with a 64-bit operating system.

    - [32-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&download=true&managedInstaller=true)
    - [64-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&download=true&managedInstaller=true&arch=x64)

2. Run the following command to install the MSI to the VDI VM (or complete updating it) by using the following command line: 

        msiexec /i <msi_name> /l*v < install_logfile_name> ALLUSER=1 

    This installs Teams to Program Files. At this point, the golden image setup is complete. 
 
    The next interactive logon session starts Teams and asks for credentials. Note that it's not possible to disable auto-launch of Teams when installing Teams on VDI using the ALLUSER property. 

3. Run the following command to uninstall the MSI from the VDI VM (or prepare for updating it):

        msiexec /passive /x <msi_name> /l*v <uninstall_logfile_name> 

This uninstalls Teams from Program Files. 

## Known issues and limitations

### Shared session host type deployments

Shared session host type deployments (for example, shared non-persistent VM configuration) aren't in scope.

### Calling and meeting

Calling and meeting scenarios aren't optimized for VDI. The scenarios will perform poorly. We recommend using user-level policies (as outlined in Appendix A) to turn off calling and meeting functionality.  

Applying the policies described in this article impacts the ability to use calling and meeting functionality, which depending on other policies, may affect other users in your organization. If users in your organization use non-VDI clients, you can choose to not apply the policies.  

### Joining calls and meetings created by other users

Although the policies restrict users from creating meetings, they can still join meetings if another user dials out to them from the meeting. In these meetings, the user's ability to share video, use Whiteboard and other features depend on whether you disabled those features using TeamsMeetingPolicy.  

### Cached content

If the virtual environment in which Teams is running isn't persistent (and data is cleaned up at the end of each user session), users may notice performance degradation due to content refresh, regardless of whether the user accessed the same content in a previous session.

### Client updates

Teams on VDI isn't automatically updated like the way that non-VDI Teams clients are.  You must update the VM image by installing a new MSI as described in  they do so by installing a new MSI as described in [Install Teams on VDI](#install-teams-on-vdi). You don't have to uninstall the current version to update to a newer version. 

### User experience 

The Teams user experience in a VDI environment may be different from a non-VDI environment. The differences may be because of policy settings and/or feature support in the environment.

For a general list of Teams knowns issue, see 

## Run Teams in a virtualized environment 

This section describes how to use user-level policies to turn off calling and meeting functionality in Teams.



