---
title: Overview of dynamic membership for teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: kblevens, phlouie
ms.topic: conceptual
ms.service: msteams
audience: admin
search.appverid: MET150
description: Learn how Microsoft Teams supports teams associated with Microsoft 365 groups by using dynamic membership.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.custom: seo-marvel-apr2020
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Overview of dynamic membership for teams

Microsoft Teams supports teams associated with Microsoft 365 groups by using *dynamic membership*. Dynamic membership enables the membership of a team to be defined by one or more rules that check for certain user attributes in Azure Active Directory (Azure AD). Users are automatically added or removed to the correct teams as user attributes change or users join and leave the tenant.

With dynamic membership you can set up teams for certain cohorts of users in your organization. Possible scenarios include:
- A hospital can create distinct teams for nurses, doctors, and surgeons to broadcast communications. This is especially important if the hospital relies on temp employees.
- A university can create a team for all faculty within a particular college, including an adjunct faculty that changes frequently.
- An airline wants to create a team for each flight (like a Tuesday afternoon non-stop from Chicago to Atlanta) and have a frequently changing flight crew automatically assigned or removed as needed.

Using this feature, a given team's members update automatically based on a specific set of criteria, instead of manually managing membership. Doing this requires Azure AD Premium P1 licenses and team membership can be [assigned by a tenant admin](/azure/active-directory/users-groups-roles/groups-dynamic-membership) to any user's Azure AD properties provided you have a tenant and an admin account.

Microsoft Teams may take anywhere from a few minutes to up to 2 hours to reflect dynamic membership changes once they take effect in the Microsoft 365 group for a team.

When using teams with dynamic groups:

- Rules can define who is a team member, but not who is a team owner.
- Owners will not be able to add or remove users as members of the team, since members are defined by dynamic group rules.
- Teams clients don't allow member management for the team. Options to add members, edit member roles, send and approve join requests, and leave the team are all hidden.

To create a team that uses dynamic membership, start by [creating a dynamic Microsoft 365 group](/azure/active-directory/users-groups-roles/groups-create-rule) and then [create a team from that group](https://support.microsoft.com/en-us/office/create-a-team-from-an-existing-group-24ec428e-40d7-4a1a-ab87-29be7d145865).

You can change an existing team to have a dynamic membership. See [Change static group membership to dynamic in Azure Active Directory](/azure/active-directory/users-groups-roles/groups-change-type) for information.

## Related topics

[Limits and specifications for Microsoft Teams](limits-specifications-teams.md)

[Dynamic membership rules for groups in Azure Active Directory](/azure/active-directory/users-groups-roles/groups-dynamic-membership)
