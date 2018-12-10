---
title: Overview of dynamic membership for teams
author: jambirk
ms.author: jambirk
manager: serdars
ms.reviewer: kblevens, phlouie
ms.topic: article
ms.service: msteams
search.appverid: MET150
description: Learn about Dynamic team membership based on AAD.
localization_priority: Normal
MS.collection: Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
---

# Overview of dynamic membership for teams

Microsoft Teams supports teams associated with Office 365 groups using dynamic membership. Dynamic membership enables the membership of a team to be defined by one or more rules that check for certain user attributes in Azure Active Directory (AAD). Users are automatically added or removed to the correct teams as user attributes change or users join and leave the tenant.

With dynamic membership you can setup teams for certain cohorts of users in your organization. Possible scenarios include:
- A hospital can create distinct teams for nurses, doctors, and surgeons to broadcast communications. This is especially important if the hospital relies on temp employees.
- A university can create a team for all faculty within a particular college, including an adjunct faculty that changes frequently.
- An airline wants to create a team for each flight (like a Tuesday afternoon non-stop from Chicago to Atlanta) and have a frequently changing flight crew automatically assigned or removed as needed.​

Using this feature, a given team's members update automatically based on a specific set of criteria, instead of manually managing membership.​ Doing this requires Azure AD Premium P1 licenses and team membership can be [assigned by a tenant admin](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership) to any user's AAD properties provided you have a tenant and an admin account​. 

Microsoft Teams may take anywhere from a few minutes to up to 2 hours to reflect dynamic membership changes once they take effect in the Office 365 group for a team. 

> [!NOTE]
> - Rules can define team members, but not team Owners.
> - See [Limits and specifications for Microsoft Teams](limits-specifications-teams.md) for current limits on Team and channel sizes.

## Creating and managing an Office 365 group with dynamic membership
While logged in as the tenant Admin, follow the instructions in [Create a dynamic group and check status](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-create-rule). As needed, refer to [Dynamic membership rules for groups in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership).

## Create a new team with your O365 group

Now allow time for the membership changes to take effect, and create a new team  as described in [Enhance Existing Office 365 groups with Microsoft Teams](enhance-office-365-groups.md).

## Apply dynamic membership to an existing team

You can also take an existing team and change it to have a dynamic membership, as described in [Change static group membership to dynamic in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type).

## Changes in client behavior

Once dynamic membership is enabled for a team, Teams clients will no longer allow member management for the team. Options to add members, edit member roles, send and approve join requests, and leave the team are all hidden.
