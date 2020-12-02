---
title: Approval application availability in Teams
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
description: Learn about the Approval application availability in Microsoft Teams.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Teams Approval App Availability

The Approvals App is available as a personal app for all users.

Users can pin the Approvals app to save it to the menu bar.

## Approval Solution Provisioning

The first approval created from the Approvals App will trigger the provisioning of the Approval Solution in the default CDS environment. Approvals created from the Approvals app will be stored in the default CDS environment.

Note:

-   

## Required Installation Permissions

-   Permissions to create a Microsoft CDS database.

-   A license to create flows.

-   Administrator Role in target environment.

## Required User Permissions

-   A Power Automate, an Office 365, or a Dynamics 365 license

Source: [Get started with Power Automate approvals. - Power Automate \| Microsoft Docs](https://docs.microsoft.com/en-us/power-automate/get-started-approvals)

## Storage - CDS

The Common Data Model (CDM) is the shared data language used by business and analytical applications. It consists of a set of a standardized, extensible data schemas published by Microsoft and our partners that enables consistency of data and its meaning across applications and business processes.

Source: [Common Data Model \| Microsoft Power Platform](https://powerplatform.microsoft.com/en-us/common-data-model/#:~:text=The%20Common%20Data%20Model%20(CDM,across%20applications%20and%20business%20processes.)

Flow Page: <https://docs.microsoft.com/en-us/power-automate/modern-approvals>

## Approvals Teams App Permissions

-   Receive messages and data that I provide to it.

-   Send me messages and notifications.

-   Render personal apps and dialogs without a Teams-provided header.

-   Access my profile information such as my name, email address, company name, and preferred language.

-   Receive messages and data that team members provide to it in a channel.

-   Send messages and notifications in a channel.

-   Access this team's information such as team name, channel list and roster (including team member's names and email addresses) - and use this to contact them​.

## How to disable the app in Admin Center 

1.  Navigate to the [Teams Admin Center](https://admin.teams.microsoft.com).

2.  Expand Teams apps in the left hand menu.

3.  Select Manage apps and search for the Approvals.

4.  Select Approvals.

5.  Click the toggle to disable the app for your organization.

## Retention policy


Approvals created from the Approvals App will be stored in the default CDS environment, which doesn’t support backups at this time.

Source: [Back up and restore environments - Power Platform \| Microsoft Docs](https://docs.microsoft.com/en-us/power-platform/admin/backup-restore-environments)

## Auditing

Approvals App logs audit events within the Microsoft 365 Security and Compliance Center. Go to the M365 Compliance Site &gt; Click on the “Audit” section &gt; Search for activities under the “Microsoft Teams approvals activities”

Searchable Activities

-   Create new approval request

-   View approval request details

-   Approved approval request

-   Rejected approval request

-   Canceled approval request

-   Shared approval request

-   File attached to approval request

-   Reassigned approval request

-   Added e-signature to approval request

Further auditing approvals within Flow is possible by enabling and configurating auditing in the default environment for the primary approval entities (Approval, Approval Request, Approval Response).

Create, update, and delete operations are auditable events for Approval records.

Source: [Audit data and user activity for security and compliance - Power Platform \| Microsoft Docs](https://docs.microsoft.com/en-us/power-platform/admin/audit-data-user-activity)

Auditing can be further customized in the [Microsoft 365 Security and Compliance Center](https://support.office.com/article/go-to-the-office-365-security-compliance-center-7e696a40-b86b-4a20-afcc-559218b7b1b8?ui=en-US&rs=en-US&ad=US).

To use the preconfigured reports, go to [https://protection.office.com](https://protection.office.com/) &gt; Search & investigation &gt; Audit log search and select the Dynamics 365 activities tab.

Source: [<u>Microsoft Dataverse and model-driven apps activity logging - Power Platform \| Microsoft Docs</u>](https://docs.microsoft.com/en-us/power-platform/admin/enable-use-comprehensive-auditing)

## Security

-   From the Teams Approval App users have access to create new Approvals and view Approvals they have sent or received.

-   Users will not have access to Approvals created by other users.

## Approvals Administrator CDS Security Role
-----------------------------------------

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

Note

-   A non-interactive user named Microsoft Flow will be added to the environment during Approvals provisioning and given the Approvals Administrator Security Role.

-   The provisioning user will not be given the Approvals Administrator Security Role.

## Approvals User CDS Security Role


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

Note

-   The Approvals User Security Role will automatically be given to users set as an approver.
