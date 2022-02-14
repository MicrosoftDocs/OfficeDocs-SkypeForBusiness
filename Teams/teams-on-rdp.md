---
title: Use Teams with remote desktop services
author: serdars
ms.author: serdars
ms.reviewer: alivano
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to use Microsoft Teams with remote desktop services.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
---

# Teams in Remote Desktop Services

This article describes the requirements and limitations for using Microsoft Teams in a remote desktop services (RDS) environment.

## What is RDS?

Remote Desktop Services (RDS) is the platform of choice for building virtualization solutions for every end customer need. RDS lets you deliver individual virtualized applications, provide secure mobile and remote desktop access, and provide end users the ability to run their applications and desktops from the cloud.

RDS offers deployment flexibility, cost efficiency, and extensibility. RDS is delivered through a variety of deployment options, including Windows Server 2016 for on-premises deployments, Microsoft Azure for cloud deployments, and a robust array of partner solutions.
Depending on your environment and preferences, you can set up the RDS solution for session-based virtualization, as a virtual desktop infrastructure (VDI)

Currently, Teams in a remote desktop services environment is available with support for collaboration and chat functionality. To ensure an optimal user experience, follow the guidance in this article.

## Teams on RDS with chat and collaboration

If your organization wants to only use chat and collaboration features in Teams, you can set user-level policies to turn off calling and meeting functionality in Teams.

### Set policies to turn off calling and meeting functionality

You can set policies by using the Microsoft Teams admin center or PowerShell. It might take some time (a few hours) for the policy changes to propagate. If you don't see changes for a given account immediately, try again in a few hours.

[**Calling polices**](teams-calling-policy.md): Teams includes the built-in DisallowCalling calling policy, in which all calling features are turned off. Assign the DisallowCalling policy to all users in your organization who use Teams in a virtualized environment.

[**Meeting policies**](meeting-policies-overview.md): Teams includes the built-in AllOff meeting policy, in which all meeting features are turned off. Assign the AllOff policy to all users in your organization who use Teams in a virtualized environment.

#### Assign policies using the Microsoft Teams admin center

To assign the DisallowCalling calling policy and the AllOff meeting policy to a user:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**.
2. Select the user by selecting to the left of the user name, and then select **Edit settings**.
3. Do the following steps:

    a.  Under **Calling policy**, select **DisallowCalling**.

    b.  Under **Meeting policy**, select **AllOff**.

4. Select **Apply**.

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

The following example shows how to use the [Grant-CsTeamsCallingPolicy](/powershell/module/skype/grant-csteamscallingpolicy) to assign the DisallowCalling calling policy to a user.

```PowerShell
Grant-CsTeamsCallingPolicy -PolicyName DisallowCalling -Identity "user email id"
```

To learn more about using PowerShell to manage calling policies, see [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy).

The following example shows how to use the [Grant-CsTeamsMeetingPolicy](/powershell/module/skype/grant-csteamsmeetingpolicy) to assign the AllOff meeting policy to a user.

```PowerShell
Grant-CsTeamsMeetingPolicy -PolicyName AllOff -Identity "user email id"
```

To learn more about using PowerShell to manage meeting policies, see [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy).