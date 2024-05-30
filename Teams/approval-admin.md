---
title: Manage the Approvals app in Microsoft Teams
author: Lana-Chin
ms.author: v-chinlana
manager: jtremper
ms.reviewer: corod
ms.date: 04/30/2024
ms.topic: conceptual
audience: admin
ms.service: msteams
searchScope:
  - Microsoft Teams
search.appverid: MET150
description: Learn how to manage the Approvals app for your organization in Microsoft Teams.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365-frontline
  - teams-1p-app-admin
  - highpri
appliesto: 
  - Microsoft Teams
---

# Manage the Approvals app in Microsoft Teams

## Overview of Approvals

The Approvals app is available as a personal app for all Microsoft Teams users.
The Approvals app provides a simple way to bring auditing, compliance, accountability, and workflows to both structured and unstructured Approvals in Teams.

 ![shows the approvals app.](media/approvals-selection.png)

Users can pin the Approvals app to save it to the menu bar.

 ![shows the approvals app with the pin option.](media/approvalApp-pin.png)

The first approval created from the Approvals app triggers the provisioning of the Approval solution in the default Microsoft Dataverse environment. Approvals created from the Approvals app are stored in the default Microsoft Dataverse environment.

This article describes the Approvals app requirements and roles.

> [!NOTE]
> This feature hasn't been released to Government Community Cloud High (GCCH) and Department of Defense (DOD) users yet.

## Prerequisites

Here are the prerequisites for deploying the Approvals app:

- Permissions to create a Microsoft Dataverse database.

- An account on [powerautomate.microsoft.com](https://powerautomate.microsoft.com/).

- Administrator role in the target environment.

- License for [Power Automate](/power-automate/get-started-approvals), Microsoft 365, or Dynamics 365.

- License for Microsoft Forms is required for users to set up new approval templates.

To use the Approvals app, you need a license for Power Automate, and your account is automatically added to the Approvals User role in the target environment on your first approval assignment.

## Storage with Microsoft Dataverse

The Common Data Model (CDM) is the shared data language used by business and analytical applications in the Microsoft Dataverse. It consists of a set of standardized, extensible data schemas published by Microsoft and our partners that enable consistency of data and its meaning across applications and business processes. Learn more about the [Common Data Model of the Microsoft Power Platform](/power-automate/get-started-approvals).

Learn more about the [Approval workflow](/power-automate/modern-approvals).

Approvals that are created from a template still store data in Microsoft Dataverse, such as their title, details, template ID, and more. Responses that are submitted on the approval request are stored in Forms. Learn more about [Data storage for Microsoft Forms](https://support.microsoft.com/office/data-storage-for-microsoft-forms-97a34e2e-98e1-4dc2-b6b4-7a8444cb1dc3#:~:text=Where%20data%20is%20stored%20for%20Microsoft%20Forms.%20Microsoft,European-based%20tenants%20is%20stored%20on%20servers%20in%20Europe).

>[!Note]
>If you delete the Form template on the Microsoft Forms site, it'll break your Approval template and users are unable to start the request. Users get a "CDB TableNotFound" error when trying to open an Approval template that is deleted on Microsoft Forms.

Org-scoped templates share the same lifetime of the tenant and team-scoped templates share the same lifetime of the team. So, permanently deleting the team deletes the related templates.

Viva Amplify approvals don't interact with Forms. Approvals store their data in Dataverse tables in Power Platform.

## Approvals Teams app permissions

The Approvals Teams app lets you access the following features:

- Receive messages and data that you provide to it.

- Send you messages and notifications.

- Render personal apps and dialogs without a Teams-provided header.

- Access your profile information such as your name, email address, company name, and preferred language.

- Receive messages and data that team members provide to it in a channel.

- Send messages and notifications in a channel.

- Access your team's information:
  - Team name
  - Channel list
  - Roster (team member's names and email addresses)

- Use the team's information to contact them.

To learn more, see the [Permissions tab](https://admin.teams.microsoft.com/policies/manage-apps/7c316234-ded0-4f95-8a83-8453d0876592/permission) for the Approvals app in the Teams admin center.

Approval template permissions

- All team owners can create an approval template for teams that they own.

- When an admin creates a template for their entire organization for the first time, it will automatically create a new Microsoft Entra group for all admins of the tenant, including the global and Teams service admins. These admins are added as owners of the group, so they can co-manage organizational templates. Admins that are new to the organization after the team has been created need to be manually added as group owners so they have the same permissions to manage organization-wide templates.

> [!NOTE]
> If an admin deletes the group, you have one month to restore it within the Microsoft Entra admin center to restore all related data. After one month, or if the admin deletes this group within the recycle bin, you will lose all related data.

## Disable the Approvals app

The Approvals app is available by default. You can disable the app in the Teams admin center.

  1. Sign in to the Teams admin center.

  2. Go to **Teams apps** > **Manage apps**.

  3. Search for the Approvals app.
  
      :::image type="content" alt-text="Screenshot shows the Manage apps page of the Teams admin center, showing the Approvals app." source="media/manage-approval-apps.png" lightbox="media/manage-approval-apps.png":::

  4. Select **Approvals**.

  5. Select the toggle to disable the app for your organization.

     :::image type="content" alt-text="Screenshot shows details for the Approvals app in the Teams admin center." source="media/approvals-details-new.png" lightbox="media/approvals-details-new.png":::

## Pin Approvals to Teams

### Use the Tailored frontline app experience to pin Approvals and other apps to Teams

The tailored frontline app experience in Teams pins the most relevant apps in Teams for users who have an [F license](https://www.microsoft.com/microsoft-365/enterprise/frontline#office-SKUChooser-0dbn8nt). Pinned apps include Approvals, Walkie Talkie, Tasks, and Shifts. By default, this feature is on, giving your frontline workers an out-of-the-box experience tailored to their needs.

The apps are pinned to the app bar—the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients—where users can quickly and easily access them.

To learn more, including how the experience works with app policies that you set, see [Tailor Teams apps for your frontline workers](/microsoft-365/frontline/pin-teams-apps-based-on-license?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json).

### Use an app setup policy to pin Approvals to Teams

App setup policies let you customize Teams to pin apps that are most important for your users in your users.

To pin the Approvals app for your users, you can edit the global (Org-wide default) policy or create and assign a custom policy in app setup policy. To learn more, see [Use app setup policies to pin and auto install apps for users](teams-app-setup-policies.md).

## Retention policy

Approvals created from the Approvals app are stored in the default Microsoft Dataverse environment, which doesn't support backups at this time. Learn more about how to [Back up and restore environments - Power Platform](/power-platform/admin/backup-restore-environments).

Admins can set custom retention policies for data stored within Dataverse tables. To learn more, see [Dataverse long term data retention overview](/power-apps/maker/data-platform/data-retention-overview).

Data stored in Forms won't be deleted until the team owners clean it up from the **Deleted forms** tab in the Microsoft Forms web app.

## Conditional Access policies

Approvals supports [Continuous Access Evaluation (CAE)](/azure/active-directory/conditional-access/concept-continuous-access-evaluation). With CAE, you can set up any conditional access policy to restrict any user, app, or service from accessing some resources. Once the policy is set, Microsoft Entra ID will reject when the selected entity requests tokens of that particular resource.

## Data limitations

Each team can contain at most 400 approvals templates, and each template can collect a maximum of 50,000 requests based on the current capability in Microsoft Forms.

## Auditing

The Approvals app logs audit events within the Microsoft Purview compliance portal. You can view the audit log.

1. Sign in to the [Microsoft Purview compliance portal](https://compliance.microsoft.com/).

2. In the left pane, select **Audit**.

3. Under **Activities**, choose the activities that you want to search for under **Microsoft Teams approvals activities**.

    You can search for the following activities:

    - Created new approval request

    - Viewed approval request details

    - Approved approval request

    - Rejected approval request

    - Canceled approval request

    - Shared approval request

    - File attached to approval request

    - Reassigned approval request

    - Added e-signature to approval request

    - Viewed e-signature request details

    - Reviewed e-signature request

    - Canceled e-signature request

    - Create a new template

    - Edit an existing template

    - Enable/disable a template

    - Viewed template

For access to more auditing approvals within Power Automate, enable and configure auditing in the default environment for the primary approval entities: Approval, Approval Request, and Approval Response. Create, update, and delete operations are auditable events for Approval records.

Learn more about [auditing data and user activity for security and compliance](/power-platform/admin/audit-data-user-activity) and [Microsoft Dataverse and model-driven apps activity logging](/power-platform/admin/enable-use-comprehensive-auditing).

## Security

From the Teams Approvals app, users have access to create new Approvals and view Approvals that they have sent and received. Users won't have access to Approvals that are created by others unless they're either a responder or a viewer of the request.

>[!Note]
> A user is given a viewer role of a request if they are part of the chat or channel where the approval was created. They won't have the ability to take action on the request if they weren't given that role when the approval was created.

## Approvals e-signature integration

To use the Approvals app e-signature feature, you need a license for the specific e-signature provider that you want to use. To obtain a license for your organization, you'll need to go to the provider's site.

### Enable or disable e-signature providers

You can use the Teams admin center to control which third-party e-signature providers are available to your users in the Approvals app. By default, e-signature providers are enabled in the Approvals app. When you disable an e-signature provider, your users won't have access to that provider when they create approvals. Your users also won't be able to view e-signature requests that were created using that provider.

1. In the left pane of the Teams admin center, go to **Teams apps** > **Manage apps**.
2. Search for the Approvals app, and then select it.
3. Go to the **Settings** tab, and then do one or more of the following:

    - To enable or disable Adobe Sign, switch the toggle to **On** or **Off**.
    - To enable or disable DocuSign, switch the toggle to **On** or **Off**.
4. Select **Submit**.

E-signature approvals created from the Approvals app are stored in the selected provider's cloud environment. To export data about e-signatures, you'll need to go to the provider's site. For more information about storage, export, and retention of e-signature agreements, see the provider's documentation.

## Approvals - Parent App integration

Teachers and admins using Teams for education can use the [Parent App](https://aka.ms/parentapp) to update the contact information for class students’ parents.

Admins can use the approvals app to view and approve or reject the request raised by schoolteachers to update the parent contact information accordingly. Once the admin approves this request, the new contact details will reflect in the parent app and allow teachers to communicate with the parent.

### Frequently asked questions

#### Question: How does the teacher track the status of the approval request?

The teacher should navigate to the Approvals app within Teams. Select **Sent** > **Filter** and search for the title **Approval request to update Parent/Guardian details**. This allows a view of all sent requests for parent information updates.

#### Question: How long does it take for new contact details to reflect in the Parent App?

Once the admin has approved the request, new contact details should be available after 60 minutes.

## Give feedback or report an issue
  
To send us feedback or report an issue, select **Settings and more** (**…**) in Teams, and then choose **Help** > **Give feedback**. Enter your feedback or details about the issue you’re experiencing. Indicate you’re sending feedback about Approvals at the beginning of your report so we can easily identify Approvals app related issues.
