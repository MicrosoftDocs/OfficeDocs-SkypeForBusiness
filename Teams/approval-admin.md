---
title: Approvals application availability in Teams
author: cichur
ms.author: v-cichur
ms.reviewer: aravin
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
searchScope:
  - Microsoft Teams
search.appverid: MET150
description: Learn about the Approvals application availability in Microsoft Teams.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Teams Approvals app availability

The Approvals app is available as a personal app for all Microsoft Teams users.
The Approvals app provides a simple way to bring auditing, compliance, accountability, and workflows to both structured and unstructured Approvals in Teams.

 ![shows the approvals app](media/approvalApp.png)

Users can pin the Approvals app to save it to the menu bar.

 ![shows the approvals app](media/approvalApp-pin.png)

The first approval created from the Approvals app will trigger the provisioning of the Approval Solution in the default Common Data Service (CDS) environment. Approvals created from the Approvals app will be stored in the default CDS environment.

This article describes the Approvals app requirements and roles.

## Required permissions and licenses

To use the Approvals app, you need permission for the following items:

- Permissions to create a Microsoft CDS database.

- An account on [flow.microsoft.com](https://flow.microsoft.com/)

- Administrator Role in the target environment.

- License for a [Power Automate](https://docs.microsoft.com/power-automate/get-started-approvals), an Office 365, or a Dynamics 365.

## Storage with CDS

The Common Data Model (CDM) is the shared data language used by business and analytical applications in the CDS. It consists of a set of a standardized, extensible data schemas published by Microsoft and our partners that enables consistency of data and its meaning across applications and business processes. Learn more about the [Common Data Model of the Microsoft Power Platform](https://docs.microsoft.com/power-automate/get-started-approvals).

Learn more about the [Approval workflow](https://docs.microsoft.com/power-automate/modern-approvals).

## Approvals Teams app permissions

The Approvals Teams app lets you access the following features:

- Receive messages and data that you provide to it.

- Send you messages and notifications.

- Render personal apps and dialogs without a Teams-provided header.

- Access your profile information such as your name, email address, company name, and preferred language.

- Receive messages and data that team members provide to it in a channel.

- Send messages and notifications in a channel.

- Access your team's information:
  - team name
  - channel list
  - roster (team member's names and email addresses).

- Use the team's information to contact them.

## Disable the Approvals app

The Approvals app is available by default. You can disable the app in the Teams admin center.

1. Sign in to the Teams admin center.

2. Expand **Teams apps** and select **Manage apps**.

3. Search for the Approvals app.

![shows the Admin center navigation with Teams Apps > Manage Apps highlighted](media/manage-approval-apps.png)

4. Select Approvals.

5. Select the toggle to disable the app for your organization.

![shows the details for the Approvals app](media/approvals-details.png)

## Retention policy

Approvals created from the Approvals App are stored in the default CDS environment, which doesn’t support backups at this time. Learn more about how to [Back up and restore environments - Power Platform \| Microsoft Docs](https://docs.microsoft.com/power-platform/admin/backup-restore-environments).

## Auditing

The Approvals App logs audit events within the Microsoft 365 Security and Compliance Center. You can view the audit log.

1. Go to the M365 Compliance Site.

2. Select the **Audit** section.

3. Search for activities under **Microsoft Teams approvals activities**.

You can search for the following activities:

- Create new approval request

- View approval request details

- Approved approval request

- Rejected approval request

- Canceled approval request

- Shared approval request

- File attached to approval request

- Reassigned approval request

- Added e-signature to approval request

For access to more auditing approvals within Flow, enable and configure auditing in the default environment for the primary approval entities Approval, Approval Request, and Approval Response. Create, update, and delete operations are auditable events for Approval records. Learn more about [Audit data and user activity for security and compliance - Power Platform \| Microsoft Docs](https://docs.microsoft.com/power-platform/admin/audit-data-user-activity).

Auditing can be customized further in the [Microsoft 365 Security and Compliance Center](https://support.office.com/article/go-to-the-office-365-security-compliance-center-7e696a40-b86b-4a20-afcc-559218b7b1b8?ui=en-US&rs=en-US&ad=US).

To use the preconfigured reports, go to [https://protection.office.com](https://protection.office.com/) -> Search & investigation -> Audit log search and select the Dynamics 365 activities tab. Learn more about [Microsoft Dataverse and model-driven apps activity logging - Power Platform \| Microsoft Docs](https://docs.microsoft.com/power-platform/admin/enable-use-comprehensive-auditing).

## Security

From the Teams Approval App, users have access to create new Approvals and view Approvals they have sent or received. Users won't have access to Approvals created by other users. The following **Approvals Administrator CDS Security Role** table describes the available security roles.

| **Entity / Privilege Type**        | **Permissions**                                                  | **Permission Level** |
|------------------------------------|------------------------------------------------------------------|----------------------|
| Action Approval Model              | Create, Read, Write, Delete, Append, Append To, Assign, Share    | Organization         |
| Approval                           | Create, Read, Write, Delete, Append, Append To, Assign, Share    | Organization         |
| Approval Request                   | Create, Read, Write, Delete, Append, Append To, Assign, Share    | Organization         |
| Approval Response                  | Create, Read, Write, Delete, Append, Append To, Assign, Share    | Organization         |
| Await All Action Approval Model    | Create, Read, Write, Delete, Append, Append To, Assign, Share    | Organization         |
| Await All Approval Model           | Create, Read, Write, Delete, Append, Append To, Assign, Share    | Organization         |
| Basic Approval Model Data          | Create, Read, Write, Delete, Append, Append To, Assign, Share    | Organization         |
| Business Unit                      | Read                                                             | Organization         |
| Flow Approval                      | Create, Read, Write, Delete, Append, Append To, Assign, Share    | Organization         |
| Note                               | Create, Read, Write, Delete, Append, Append To, Assign, Share    | Organization         |
| Plugin-in Assembly                 | Read                                                             | Organization         |
| Plugin-in Type                     | Read                                                             | Organization         |
| Sdk Message                        | Read                                                             | Organization         |
| Sdk Message Processing Step        | Read                                                             | Organization         |
| Sdk Message Processing Step Image  | Read                                                             | Organization         |
| Sdk Message Processing Step Secure | Read                                                             | Organization         |
| Security Role                      | Read, Assign                                                     | Organization         |
| Solution                           | Read                                                             | Organization         |
| Team                               | Create, Read, Append, Append To                                  | Organization         |
| User                               | Read, Append, Append To                                          | Organization         |
| Miscellaneous Privilege            | Act on Behalf of Another User                                    | Organization         |
| Miscellaneous Privilege            | Override Created on or Created by for Records during Data Import | Organization         |

> [!Note]
>
> - A non-interactive user named Microsoft Flow will be added to the environment during Approvals provisioning and given the Approvals Administrator Security Role.
> - The provisioning user will not be given the Approvals Administrator Security Role.

The following **Approvals User CDS Security Role** describes the user access and permissions.

| **Entity**                        | **Permissions**                                               | **Permission Level** |
|-----------------------------------|---------------------------------------------------------------|----------------------|
| Action Approval Model             | Read                                                          | User                 |
| Approval                          | Read                                                          | User                 |
| Approval Request                  | Read                                                          | User                 |
| Approval Response                 | Read                                                          | User                 |
| Await All Action Approval Model   | Read                                                          | User                 |
| Await All Approval Model          | Read                                                          | User                 |
| Basic Approval Model Data         | Read                                                          | User                 |
| Flow Approval                     | Read                                                          | User                 |
| Note                              | Create, Read, Write, Delete, Append, Append To, Assign, Share | User                 |
| Plugin-in Assembly                | Read                                                          | Organization         |
| Plugin-in Type                    | Read                                                          | Organization         |
| Sdk Message                       | Read                                                          | Organization         |
| Sdk Message Processing Step       | Read                                                          | Organization         |
| Sdk Message Processing Step Image | Read                                                          | Organization         |

> [!Note]
> The Approvals User Security Role will automatically be given to users set as an approver.
