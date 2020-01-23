---
title: Sensitivity labels for Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: abgupta
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to define and use sensitivity labels in Microsoft Teams.
---

# Sensitivity labels for Microsoft Teams

[!INCLUDE [preview-feature](includes/preview-feature.md)]

[Sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) allow Teams admins to regulate access to sensitive organizational content created during collaboration within teams. You can define sensitivity labels and their associated policies in the [Security & Compliance Center](https://docs.microsoft.com/microsoft-365/compliance/go-to-the-securitycompliance-center). These labels and policies are automatically applied to teams in your organization.  

## What's the difference between sensitivity labels and Teams classification labels?

Sensitivity labels are different from classification labels that require you to create them using PowerShell. Classification labels are text strings that can be associated with a group but don't have any actual policies associated with them. You use classification labels as metadata to manually enforce policies through internal tools and scripts.

On the other hand, sensitivity labels and their policies are automatically enforced end-to-end through a combination of the Groups platform, Security & Compliance Center, and Teams services. Sensitivity labels provide powerful infrastructure support for securing your organization's sensitive data.  

## Create, manage, and publish sensitivity labels for Teams

For how to enable, create, and publish sensitivity labels for Teams, see [Use sensitivity labels with Microsoft Teams, Office 365 groups, and SharePoint sites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).

>[!IMPORTANT]
>Creating, updating and deleting sensitivity labels require careful sequencing with publishing
>labels to users. Any deviation in the sequence can result in persistent team creation errors
>for all users. Therefore, it's critical to do the following when you <a href="#createpublishlabels">create and publish labels</a>, <a href="#modifydeletelabels">modify and delete published labels</a>, and <a href="#manageerrors">manage team creation errors</a>.

**Create and publish labels** <a name="createpublishlabels"> </a>

When a label is created and published in the Security & Compliance Center, it can take up to 24 hours
for the label to become visible in the teams creation interface. Use the following steps to 
publish the label for all users in the tenant:
1. Create the label and publish it for a few select user accounts in the tenant.
2. When the label is published, wait 24 hours.
3. After 24 hours, try to create a team with the label using one of the user accounts that have access
to the label.
4. If the team successfully created in step 3, then go ahead and publish the label for the remaining 
users in the tenant.

**Modify and delete published labels** <a name="modifydeletelabels"> </a>

Deleting or modifying the label while it's associated with sensitivity policies can result in team
creation failures across the tenant. Therefore, before you delete or modify a label, you must
first disassociate the label from its associated policies. Use the following steps  
to delete or modify a label:
1. Remove the label from all policies that use the label. Alternatively, you can also delete
the policies themselves.
2. When the label is removed from the policies or the policies themselves are deleted, wait 
48 hours before proceeding further.
3. After 48 hours, launch the team creation interface and ensure that the label is no longer visible for
any user in the tenant.
4. Now you can safely delete or modify the label.

**Manage team creation errors** <a name="manageerrors"> </a>

If team creation begins to fail at any point during the public preview, you have two options:
 - Ensure that sensitivity labels are not mandatory for any user during team creation.
 - Turn off sensitivity labels using the scripts in [Enable this preview](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites#enable-this-preview).

Note that the EnableMIPLabels setting must be set to false as follows:

```
$setting["EnableMIPLabels"] = "False"
 ```

## Using sensitivity labels with Teams

Here are some example scenarios of how you can use sensitivity labels with Teams in your organization.

### Privacy setting of teams

You can create a sensitivity label that, when applied during team creation, allows users to create teams with a specific privacy (public or private) setting.

For example, you create a label named “Confidential” in the Security & Compliance Center and you configure Teams so that any team that's created with this label must be a private team. When a user creates a new team and selects the **Confidential** label, the only privacy option that's available to the user is **Private**. Other privacy options such as Public and Org-wide are disabled for the user.

![Screenshot of Confidential sensitivity label](media/sensitivity-labels-confidential-example.png)

Similarly, if the user selects **General** when they create a new team, they can only create public or org-wide teams.

![Screenshot of General sensitivity label](media/sensitivity-labels-general-example.png)

When the team is created, the sensitivity label is visible in the upper-right corner of channels in the team.

![Screenshot of sensitivity label in team channel](media/sensitivity-labels-channel.png)

A team owner can change the sensitivity label and the privacy setting of the team at any time by going to the team, and then clicking **Edit team**.

![Screenshot of sensitivity label in team channel](media/sensitivity-labels-edit-team.png)

### Guest access to teams

You can specify whether a team created with a specific label allows guest access. Teams created with a label that doesn't allow guest access are only available to users in your organization. People outside your organization can't be added to the team.

## Known issues

**Support for sensitivity labels in the Microsoft Teams admin center**

Currently, sensitivity labels are not supported in the Microsoft Teams admin center. If you use sensitivity labels, you won't be able to set sensitivity labels when you create or edit a team. Sensitivity labels are also not visible in team properties and won't be visible in the **Classification** column in the Microsoft Teams admin center.

**Support for sensitivity labels in Teams Graph APIs, Powershell cmdlets and templates**

Currently, users won't be able to apply sensitivity labels on teams that are created directly through Graph APIs, Powershell cmdlets, and templates.

**Editing sensitivity labels directly on a SharePoint site collection for private channels**

Private channels that are created in a team inherit the sensitivity label which was applied on a team. Furthermore, the same label is automatically applied on the SharePoint site collection for the private channel.

If a user directly updates the sensitivity label on a SharePoint site collection for a private channel, that label isn't updated in the Teams client. In this scenario, users will continue to see the sensitivity label applied on a team in the private channel header.

**Propagation times for changes applied to sensitivity labels outside the Teams app**

Changes made to sensitivity labels outside the Teams app can take up to 24 hours to reflect in the Teams app. This applies to any changes made to enable or disable labels for a tenant, changes to label names, settings, and policies.

Additionally, any changes to a label made directly to a group or SharePoint site collection that backs the team can take up to 24 hours to propagate to the Teams app.
