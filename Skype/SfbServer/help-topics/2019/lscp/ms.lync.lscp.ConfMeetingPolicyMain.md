---
title: "Conferencing Policy"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.custom:
- ms.lync.lscp.ConfMeetingPolicyMain
ms.prod: skype-for-business-itpro
f1.keywords:
- CSH
ms.localizationpriority: medium
ms.assetid: 90eaa64e-369e-448d-bac4-2574c7c598b8
ROBOTS: NOINDEX, NOFOLLOW
description: "Conferencing policy defines the features and capabilities that users have available during a conference (also known as a meeting)."
---

# Conferencing Policy

Conferencing policy defines the features and capabilities that users have available during a conference (also known as a meeting).

Conferencing policies include the global policy and, optionally, one or more site and user policies:

- **Global policy:** The global policy is created by default. You can edit the global policy, but you cannot delete it. If you try to remove the global policy, all the settings are reset to the default values.

- **Site policies (optional):** You can create one or more site conferencing policies, each of which applies to a specific site. Site policies override the global policy.

- **User policies (optional):** You can create one or more user conferencing policies, each of which applies to a specific user or group of users. User policies override the global policy and site policies.

The **Conferencing Policy** page displays a list of all the conferencing policies that are defined for your organization.

## Tasks you can perform

You can perform the following tasks from the **Location Policy** page:

- Create a new site conferencing policy or user conferencing policy

- Change the global policy or an existing site policy or user policy

- Delete a site policy or user policy

## UI Reference

The following list describes the commands on the page.

- **New** Starts a new site conferencing policy or user conferencing policy.

- **Edit** Opens the selected conferencing policy to edit it, selects all conferencing policies in the list, or deletes the selected site policy or user policy.

    > [!NOTE]
    > For the global policy, **Delete** resets the settings to the default values.

- **Refresh** Refreshes the list of conferencing policies.

The following list describes the fields on the page.

- **Name** Identifies the conferencing policy.

- **Scope** Identifies the scope of the conferencing policy: global, site, or user.

- **Data collaboration** Checked if the conferencing policy specifies that data collaboration is allowed in conferences.

- **Application sharing** Checked if the conferencing policy specifies that application sharing is allowed in conferences.

- **Audio** Checked if the conferencing policy specifies that audio is allowed in conferences.

- **Video** Checked if the conferencing policy specifies that video is allowed in conferences.

- **PSTN** Checked if the conferencing policy specifies that PSTN dial-in conferencing is allowed.

- **Recording** Checked if the conferencing policy specifies that recording is allowed in conferences.

For details about conferencing features and capabilities, see [Overview of Conferencing](/previous-versions/office/lync-server-2013/lync-server-2013-overview-of-conferencing) in the Planning documentation. For details about working with conferencing policies, see [Conferencing Policies](/previous-versions/office/lync-server-2013/lync-server-2013-conferencing-policies) in the Operations documentation.