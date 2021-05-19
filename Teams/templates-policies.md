---
title: Manage team templates in the admin center
author: cichur
ms.author: v-cichur
manager: serdars
ms.reviewer: yinchang
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to manage team templates in the admin center
---
# Manage team templates in the admin center

Manage the team templates that your end users see by creating templates policies in the admin center. Within each template policy, you can designate which templates are shown or hidden.
Assign different users to different template policies so that your users view only the subset of team templates specified.

Watch this short video to learn how to manage template policies.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyXL9]

## Create template policies and assign available templates

1. Sign in to the Teams admin center.

2. Expand **Teams** > **Templates policies**.

3. Select **Add**.

    ![The template policies is selected and Add is highlighted](media/template-policies-1.png)

1. In the **Templates Policies Settings** section, complete the following fields:

    - Templates Policy name

    - Templates Policy short description

2. In the **Viewable Templates** table, select the templates you want to hide and select **Hide**.

    ![The selected templates with hide highlighted](media/template-policies-2.png)

    You can see the templates you've selected to hide in the **Hidden Templates** table.

1. To unhide certain templates, scroll to the **Hidden templates** table.

2. Select the templates to unhide, and then select **Show**.

   ![The selected templates that aren't hidden](media/template-policies-3.png)

   The selected templates will appear in your **Viewable templates** table.
3. Select **Save**.

   Your new template policy is displayed in the **Templates Policies** list.

## Assign users to the template policies

Users assigned to a policy will only be able to view the viewable templates within that policy.

1. From **Templates Policies**, select a policy, and then select **Manage users**.

2. Type the users to assign to this policy.

   ![assign users to a template policy](media/template-policies-4.png)

3. Select **Apply**.

> [!Note]
> It might take up to 24 hours for your new policy to take effect for end users.

## Size limits for Template policies

You can hide a max of 100 templates per policy. The **Hide** button is disabled if the given policy already has 100 templates hidden.

## Frequently asked questions

**Q: Can I batch assign users to team templates policies?**
  
A: Yes, we support batch assignment for template policy in PowerShell. The policy type for this action is TeamsTemplatePermissionPolicy. [Learn more](/powershell/module/teams/new-csbatchpolicyassignmentoperation)

**Q: Can Groups be assigned to team templates policies?**

A: Currently no. This functionality will be available in the future.

**Q: If a new template is created, will the template be included in my policies?**

A: Any new templates will be visible by default. You can choose to hide the template in the admin center in the Templates Policies section.

**Q: What happens if a template is deleted?**

A: Any deleted templates will no longer be present in any templates policies.

**Q: Can I assign multiple users to a template policy in the Teams Admin Center?**

A: Yes.

1. In the Admin center, go to **Users**.
1. In the Users list table, select the users you want to assign to a certain templates policy.
1. Select Edit settings, and change the Templates policies field.
1. Select apply.
   Learn more [Assign policies to your users in Microsoft Teams - Microsoft Teams \| Microsoft Docs](./assign-policies.md#assign-a-policy-to-a-batch-of-users).

**Q: How do I view all users assigned to a specific policy?**

A: In the Admin center:

1. Go to the **Users** section.
2. Select the filter in the Users list table and filter for the team template policy.
3. Select **Apply**.

![The selected template policy and view users](media/template-policies-5.png)

**Q: Can I manage templates policies via PowerShell?**

A: No, managing templates in PowerShell isn't supported.

**Q: Are templates policies applicable to EDU?**

A: No, template policies for EDU isn't supported.

## Related topics

- [Get started with team templates in the admin center](./get-started-with-teams-templates-in-the-admin-console.md)

- [Create a custom team template](./create-a-team-template.md)

- [Create a template from an existing team](./create-template-from-existing-team.md)

- [Create a team template from an existing team template](./create-template-from-existing-template.md)

- [Assign policies to your users in Microsoft Teams - Microsoft Teams \| Microsoft Docs](./assign-policies.md)

- [Batch assign users to a policy](/powershell/module/teams/new-csbatchpolicyassignmentoperation)