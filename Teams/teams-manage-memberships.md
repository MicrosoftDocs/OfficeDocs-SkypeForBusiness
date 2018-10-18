---
title: Overview of Dynamic teams in Microsoft Teams
author: jambirk
ms.author: jambirk
manager: serdars
ms.date: 10/10/2018
ms.topic: article
ms.service: msteams
search.appverid: MET150
description: Learn about allowing Dynamic team creation based on AAD memberships.
localization_priority: Normal
MS.collection: Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
---

# Manage Dynamic Teams memberships

Using this feature, a team's members you can have team membership update automatically to match a specific set of criteria, instead of manually managing membership.​ Doing this requires Azure AD Premium P1 licenses and Team membership can be assigned to any user AAD property.

Possible Scenarios​
- An airline wants to create a team for each flight and have the flight crew automatically assigned.​
- A university wants to create a team that includes all professors for a specific college and updates as faculty changes.
​- A hospital wants to create a team for each job description so they can better target communication. 
​
​

To create a Dynamic Group Team, you must have a tenant and an admin account​.


Create an AAD Group:
1. Login as admin and visit Portal.azure.com​
2. Select **Azure Active Directory** in left column​
3. Select **Groups​**
4. Select **New Group**​
5. Select **Membership Type** > **Dynamic**​
6. Select dynamic user members​: <br/>
    Define user criteria​, based on AAD user attributes​<br/>
    Also use the middle-left column for dynamic membership rules<br/>
​
> [!NOTE]
>- You can't set a rule to define Team Owners, only members.
>- Rules take a few minutes to sync, possibly more depending on tenant size and the number of users it affects.
​
To enable telemetry, add a new telemetry column (only for BI events) named “Team.MemType” (short for “TeamMembershipType”​) and also remove _dynamic_ and _org wide_ from Team.Type.

This will differentiate user activity for any client events between the three types​:
- Standard: “Std”​
- Dynamic: “Dyn”​
- Org-wide: “Org”​

[Create an org-wide team in Microsoft Teams](create-an-org-wide-team.md)

Existing support pages on dynamic membership for groups: 
- [Create dynamic membership group](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership)
- [Rule syntax and properties](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership)
- [Change group membership type](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-change-type)

Now allow time for the update to spread, and create a new team  as described in [Create a team in Teams](https://support.office.com/en-us/article/create-a-team-in-teams-174adf5f-846b-4780-b765-de1a0a737e2b) with the following changes: 

First click **Teams**  on the left side of the app, then click **Join or create a team** at the bottom of the teams list. On the **Create a team** tile, click **Create team**.
When you name your new team, add a description, and edit the team's data classification.  Users will automatically be added to the new Team and they will not have the option of choosing to leave.
