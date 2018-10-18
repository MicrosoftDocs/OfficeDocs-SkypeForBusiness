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

<!--
Overall, I think I'd pivot this to be informational about how Teams clients change for dynamic membership and what kind of scenarios dynamic membership allows, but just point to the Azure docs for all the details on setting up rules.
Title suggestion: Perhaps just "Dynamic membership" or "Dynamic membership for teams"
-->

<!--
Microsoft Teams supports teams associated with Office 365 groups using dynamic membership. Dynamic membership enables the membership of a team to be defined by one or more rules that check for certain user attributes in AAD. Users are automatically added or removed to the correct teams as user attributes change or users join and leave the tenant. 
-->

<!--
With dynamic membership you can setup teams for certain cohorts of users in your organization. As examples:
- A hospital can create distinct teams for nurses, doctors, and surgeons to broadcast communications.
- A university can create a team for all faculty within a particular college.
-->

Using this feature, a team's members you can have team membership update automatically to match a specific set of criteria, instead of manually managing membership.​ Doing this requires Azure AD Premium P1 licenses and Team membership can be assigned to any user AAD property.

Possible Scenarios​
- An airline wants to create a team for each flight and have the flight crew automatically assigned.​
- A university wants to create a team that includes all professors for a specific college and updates as faculty changes.
​- A hospital wants to create a team for each job description so they can better target communication. 
​
​

<!-- 
You must be a tenant admin to manage dynamic membership, and an Azure AD Premium P1 license is required for each user assigned to a dynamic memberhsip group. Visit here to learn more. (link: https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership)
-->

To create a Dynamic Group Team, you must have a tenant and an admin account​.

<!--
Microsoft Teams may take up to 2 hours to reflect dynamic membership changes once they take effect in the Office 365 group for a team.
-->

<!-- I'd leave all of this out below, and just rely on the pointer to the groups documentation above -->

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


[Create an org-wide team in Microsoft Teams](create-an-org-wide-team.md)

Existing support pages on dynamic membership for groups: 
- [Create dynamic membership group](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership)
- [Rule syntax and properties](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership)
- [Change group membership type](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-change-type)

Now allow time for the update to spread, and create a new team  as described in [Create a team in Teams](https://support.office.com/en-us/article/create-a-team-in-teams-174adf5f-846b-4780-b765-de1a0a737e2b) with the following changes: 

First click **Teams**  on the left side of the app, then click **Join or create a team** at the bottom of the teams list. On the **Create a team** tile, click **Create team**.
When you name your new team, add a description, and edit the team's data classification.  Users will automatically be added to the new Team and they will not have the option of choosing to leave.
