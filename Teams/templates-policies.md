---
title: Manage team templates in the admin center
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: yinchang
ms.date: 01/11/2021
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.custom: chat-teams-channels-revamp
ms.collection: 
  - M365-collaboration
f1.keywords: 
  - NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to manage team templates in the admin center
---
# Manage team templates in the admin center

Manage the team templates that your end users see by creating templates policies in the admin center. Within each templates policy, you can designate which templates are shown or hidden.
Assign different users to different templates policies so that your users view only the subset of team templates specified.

Watch this short video to learn how to manage templates policies.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyXL9]

## Create templates policies and assign available templates

1. Sign in to the Teams admin center.

2. Go to **Teams** > **Templates policies**.

3. Choose **Add**.

    ![The templates policies is selected and Add is highlighted.](media/template-policies-1.png)

1. Give the policy a name and add a short description.

2. In the **Viewable templates** list, select the templates you want to hide, and then select **Hide**.

    ![The selected templates with hide highlighted.](media/template-policies-2.png)

    You can see the templates you've chosen to hide in the **Hidden templates** list.

1. To unhide certain templates, go the **Hidden templates** list.

2. Select the templates to unhide, and then select **Show**.

   ![The selected templates that aren't hidden.](media/template-policies-3.png)

   The selected templates will appear in the **Viewable templates** list.
3. Choose **Save**.

   Your new templates policy is displayed in the **Templates policies** list.

## Assign templates policies to users

You can assign a templates policy directly to users, either individually or at scale through a batch assignment. Keep in mind that it may take up to 24 hours for your new policy to take effect for your users.

> [!Note]
> Currently, assigning templates policies to users based on group membership, such as to all users in a security group, isn't supported. This capability will be available in the future.

For an overview of the ways to assign policies in Teams, see [Assign policies in Teams](policy-assignment-overview.md).

### Assign a templates policy to individual users

You can use the Teams admin center or PowerShell to assign a templates policy to an individual user or to a small number of users at a time. To learn more, see [Assign a policy to individual users](assign-policies-users-and-groups.md#assign-a-policy-to-individual-users).

### Assign a templates policy to a batch of users

You can use PowerShell to assign a templates policy to large sets of users at a time. To do this, use the [New-CsBatchPolicyAssignmentOperation](/powershell/module/teams/new-csbatchpolicyassignmentoperation) cmdlet together with TeamsTemplatePermissionPolicy as the ```PolicyType``` to submit a batch of users and the templates policy that you want to assign. For example:

```powershell
New-CsBatchPolicyAssignmentOperation -OperationName <Any operation name> -PolicyType TeamsTemplatePermissionPolicy -PolicyName <policy name> -Identity <users identity | list of user identities>
```

The assignments are processed as a background operation and an operation ID is generated for each batch. You can then use the [Get-CsBatchPolicyAssignmentOperation](/powershell/module/teams/get-csbatchpolicyassignmentoperation) cmdlet to track the progress and status of the assignments in a batch.

To learn more, see [Assign a policy to a batch of users using PowerShell](assign-policies-users-and-groups.md#use-powershell-method).

## Size limits for templates policies

You can hide a max of 100 templates per policy. The **Hide** button is disabled if the given policy already has 100 templates hidden.

## Frequently asked questions

**Q: If a new template is created, will the template be included in my policies?**

A: Any new templates will be visible by default. You can choose to hide the template in the admin center in the Templates Policies section.

**Q: What happens if a template is deleted?**

A: Any deleted templates will no longer be present in any templates policies.

**Q: Can I assign multiple users to a templates policy in the Teams admin center?**

A: Yes.

1. In the Teams admin center, go to **Users** > **Manage users**.
1. In the list of users, select the users you want to assign to the templates policy.
1. Select **Edit settings**, and then under **Templates policy**, choose the policy you want to assign.
1. Choose **Apply**.

To learn more, see [Assign a policy to individual users](assign-policies-users-and-groups.md#assign-a-policy-to-individual-users).

**Q: How do I view all users assigned to a specific policy?**

A: In the Teams admin center:

1. Go to **Users** > **Manage users**.
2. Select **Filter**, set a filter for the templates policy, and then choose **Apply**.

    ![The selected templates policy and view users.](media/template-policies-5.png)

**Q: Can I manage templates policies via PowerShell?**

A: No, managing templates policies in PowerShell isn't supported. However, you can use PowerShell to [assign templates policies](#assign-templates-policies-to-users) to users.

**Q: Are templates policies applicable to EDU?**

A: No, templates policies for EDU aren't supported.

## Related articles

- [Get started with team templates in the admin center](./get-started-with-teams-templates-in-the-admin-console.md)

- [Create a custom team template](./create-a-team-template.md)

- [Create a template from an existing team](./create-template-from-existing-team.md)

- [Create a team template from an existing team template](./create-template-from-existing-template.md)

- [Assign policies to your users in Microsoft Teams - Microsoft Teams \| Microsoft Docs](./policy-assignment-overview.md)

- [New-CsBatchPolicyAssignmentOperation](/powershell/module/teams/new-csbatchpolicyassignmentoperation)
