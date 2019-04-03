---
title: "Location Policy"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.NcsLocMain
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 5530cf17-4520-40b5-ba70-c62692685048
ROBOTS: NOINDEX, NOFOLLOW
description: "Location policies determine whether Enhanced 9-1-1 (E9-1-1) is enabled and how it is used, as well as how location information is used for users and contacts."
---

# Location Policy

Location policies determine whether Enhanced 9-1-1 (E9-1-1) is enabled and how it is used, as well as how location information is used for users and contacts.

Location policies include the global policy and, optionally, one or more site and user policies:

- **Global policy:** The global policy is created by default. You can edit the global policy, but you cannot delete it. If you try to remove the global policy, all the settings are reset to the default values.

- **Site policies (optional):** You can create one or more site location policies, each of which applies to a specific site. Site policies override the global policy.

- **User policies (optional):** You can create one or more user location policies, each of which applies to a specific user or group of users. User policies override the global policy and site policies.

> [!NOTE]
> You can also assign location policies to network sites, which are groups of subnets. Location policies assigned to network sites take precedence over all other user policies. For details about assigning location policies to network sites by using cmdlets, see [Add a location policy to a network site in Skype for Business Server](../../../deploy/deploy-enterprise-voice/add-a-location-policy-to-a-network-site.md). For details about using Skype for Business Server Control Panel to assign a location policy to a network site, see [Configuring Network Sites](https://technet.microsoft.com/library/358aa08a-c5bc-45fc-8017-19e6202f88c5.aspx).

The **Location Policy** page displays a list of all the location policies that are defined for your organization.

## Tasks you can perform

You can perform the following tasks from the **Location Policy** page:

- Create a new site location policy or user location policy

- Change the global policy or an existing site policy or user policy

- Delete a site policy or user policy

## UI Reference

The following list describes the commands on the page.

- **New** Starts a new site location policy or user location policy.

- **Edit** Opens the selected location policy to edit it, selects all location policies in the list, or deletes the selected site policy or user policy.

    > [!NOTE]
    > For the global policy, **Delete** resets the settings to the default values.

- **Refresh** Refreshes the list of location policies.

The following list describes the fields on the page.

- **Name** Identifies the location policy.

- **Scope** Identifies the scope of the location policy: global, site, or user.

- **E9-1-1** Checked if users assigned this location policy are enabled for E9-1-1.

- **Location** Specifies whether or not users are prompted to enter location information when their client registers with Skype for Business Server at a new location, and whether they see a disclaimer if they dismiss the prompt without entering location information.

- **PSTN usage** Specifies the public switched telephone network (PSTN) usage that is used to determine the voice route used to route emergency calls from clients using this profile.

- **E9-1-1 number** Specifies the number that is dialed to reach emergency services.

- **E9-1-1 mask** Specifies a number that a user dials that is then translated into the emergency dial number.

For details about Enterprise Voice emergency service features and capabilities, see [Overview of E9-1-1](https://technet.microsoft.com/library/c01e6774-bc9f-4c5b-a60b-478b7317b2b7.aspx) in the Planning documentation. For details about working with location policies, see [Configuring Location Policy](https://technet.microsoft.com/library/14e41bcb-ea0a-49c2-99b3-1f61fc34416d.aspx) in the Operations documentation.


