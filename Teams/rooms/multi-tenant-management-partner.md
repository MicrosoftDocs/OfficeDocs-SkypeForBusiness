---
title: Multitenant customer management for partners
author: mstonysmith
ms.author: tonysmit
ms.date: 04/04/2024
manager: pamgreen
ms.reviewer: kimmatlock
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
ms.localizationpriority: medium
search.appverid: MET150
description: Mult-tenant customer management for partners.
f1keywords: 
---

# Multitenant customer management for partners

Multitenant management (MTM) in the Teams Rooms Pro Management helps partner organizations manage multiple customers in one place with their own domain credentials. Partner users will see only those customer rooms that they are assigned to manage. It's possible to apply custom roles for each customer in the MTM portal which will give partner organizations granular control of permissions to the customer’s resources. This feature is only available in public or commercial cloud. It's not available in GCC, GCC-H, or DoD government clouds.

The MTM portal can be accessed through this [link](https://partner.rooms.microsoft.com/).

> [!Note]
> Partner organizations can't manage their own rooms through the MTM portal. Those rooms can be managed in the [Teams Rooms Pro Management portal](https://portal.rooms.microsoft.com/).

## Pre-requisites for managing your customers through the MTM experience

Partners must meet specific eligibility criteria that have a proven track record and the organizational capabilities to deploy, configure, and manage Microsoft Teams Rooms, including Surface Hub. Partners interested in learning more about the requirements for becoming a Microsoft Teams Rooms Partner can submit their request at [link](https://aka.ms/MicrosoftTeamsRoomsPartnerInquiry).

## Onboarding customers

To manage customers through the Teams Rooms Pro Management-MTM portal, a relationship is established between the partner organization’s tenant and the customer through an invitation that is sent by the customer.

## Tenant managers

This built-in role is only configurable in the Teams Rooms Pro Management-MTM portal. This role allows you to assign a group of users that accepts invitations, but aren't involved with the management of customer rooms. In order to assign Tenant manager permissions in the Teams Rooms Pro Management-MTM portal, the assigning account must be set to be a Teams Rooms Pro Manager in the Teams Rooms Pro Management portal for customers. Before attempting to set Tenant manager permissions, please verify the account is set up correctly in your Teams Rooms Pro management customer portal. This isn't configurable from the Teams Rooms Pro Management-MTM portal.

It's recommended to configure this role so designated Tenant managers can accept customer invitations and sub-delegate permissions to others in your organization. Otherwise, only users with the Teams Rooms Pro Manager role in your tenant will be able to accept invitations.

**To configure tenant managers**

1. Log in to the Teams Rooms Pro Management-MTM portal Teams Rooms Pro Manager role.
2.	Go to Tenant managers.
3.	Select **Add tenant managers**.
4.	In the detail pane, search for the users or security groups.
5.	Select the user or group.
6.	Select **Add**.

### Invitation from the customer

The partner will provide the domain name to customers. Only the Global admin, Teams Rooms Pro Manager, and Tenant managers roles can see and will accept the invitation when they log in to the Teams Rooms Pro Management-MTM portal.

> [IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

> [!Note]
> Even though these roles can see invitations and high-level Tenant metadata, you won't see the customer’s data until you are assigned a role with that customer.

Details on the customer invitation are outlined in [Multitenant management for Customers](Multi-tenant-management-customer.md).

**To accept a pending invite**

1. Log in to the Teams Rooms Pro Management-MTM portal as either Teams Rooms Pro Manager, or Tenant manager.
1. Go to **Tenants**.
1. Select the invitation that shows a **Pending** status.
1. Review the invitation details.
1. Assign the users that will be part of the admins for the customer.
1. Select **Accept** to establish the partner-customer relationship.

   Selecting **Deny** deletes the invitation.

   > [!Note]
   > There is no permanent association with the user that accepts the invitation.

   >

**To review the configuration or add more primary admins for a tenant**

1. Select the customer in the **Tenants** list.
1. In the detail pane, select **Primary admins**.
1. Search for the user or group.
1. Select **Add** to confirm the selection.

## Off-boarding customers

To off-board a customer, you must remove them from the **Tenants** list.

**To remove a customer** 

1. Log in to the Teams Rooms Pro Management-MTM portal as a Primary admin for the customer you wish to remove.
1. Go to **Tenants**.
1. Select the customer you wish to remove.
1. In the customer detail pane, select **Remove customer**.
1. Select **Delete** in the confirmation prompt to terminate the association between you and the customer tenant.

## Managing partner roles

Partner roles allow for delegation of responsibilities to additional personnel. The concept of these roles is the same as described in [Role-based access control](rooms-pro-rbac.md), but  this is within context of each customer. Also, it's important to note that partner roles are distinct from the customer’s roles. The partner roles can be deleted by the customer.

The **Primary admins** role is the only built-in role for each onboarded customer and has almost all permissions, in context of the customer, for the Teams Rooms Pro Management service. See the table. **Partner** role permissions only extend as far as the rooms designated by the customer. For example, if the customer is a global organization and assigns the Partner to manage All US rooms (all rooms in the United States), the primary admin will only be able to manage and delegate permissions for those rooms. The Partner has no visibility to other rooms the customer may have in other countries/regions.

**To manage users in the **Partner** role for a customer**

1. Go to **Settings > Roles**.
1. Select the customer from the dropdown list for which you want to edit the partner role.
1. Select the **Primary admins** built-in role from the list.
1. Select **Assignments.**
1. From the list, select **Assigned Admins.**
1. Select **Members.**
1. Select **Edit.**.
1. Search for the user or security group you wish to add in the search bar.
1. Select the user or group.
1. Select **Save** to confirm the changes.

### Managing custom partner roles for a customer

As a partner, you can create custom roles to suit your operational requirements. For example, you might create a help desk role that should only have incident management permissions.

**To manage roles**

1. Go to **Settings > Roles**.
1. Select the customer from the dropdown menu for which you want to edit the partner role.
1. Create a [custom role](rooms-pro-rbac.md#built-in-roles).

|Feature|Permission|**MMR Admin**|**Site Lead**|**Site Tech**|**Primary admins**|
| :- | :- | :- | :- | :- | :- |
|Rooms|View| &#10004;|&#10004;|&#10004;|&#10004;|
||Modify|&#10004;|&#10004;|&#10004;|&#10004;|
||Reset key|&#10004;||||
||Download key|&#10004;|&#10004;|&#10004;||
||Unenroll|&#10004;|&#10004;|&#10004;||
||Create |&#10004;|&#10004;|||
|Group management|View|&#10004;|&#10004;||&#10004;|
||Modify|&#10004;|&#10004;|||
||Create |&#10004;|&#10004;|||
|Update ring management|View|&#10004;|&#10004;||&#10004;|
||Modify|&#10004;|&#10004;||&#10004;|
|Reports|View|&#10004;|&#10004;||&#10004;|
||Create customer incident|&#10004;|&#10004;|&#10004;|&#10004;|
|Tickets Management|View|&#10004;|&#10004;|&#10004;|&#10004;|
||Update|&#10004;|&#10004;|&#10004;|&#10004;|
|Teams Rooms Pro Settings|View|&#10004;||||
||Modify|&#10004;||||
|Role management|View |&#10004;|||&#10004;|
||Modify|&#10004;|||&#10004;|

> [!Note]
> A user assigned as a Primary admin for Customer A has full permissions in the Teams Rooms Pro Management service for only that customer. The permissions of the user in Customer A have no influence on other customers.

## Security

End customers retain control over access to their data and can completely remove a partner or specific roles at any time.

With the delegated access feature, a partner doesn't gain any other privileges outside of the Teams Rooms Pro Management portal. For example, by using this feature to invite a partner to manage rooms in the Teams Rooms Pro Management portal, no permissions are granted to Microsoft Entra ID or the Teams Admin Center or any other Microsoft product. In addition, partners don't have any access to view or modify rooms that aren't defined in the invitation scope.

Once the partner—customer relationship is established, the partner can view room data in the Teams Rooms Pro Management portal. This includes any data present in the Teams Rooms Pro Management portal but derived from other Microsoft products. For example, call quality reports in the Teams Rooms Pro Management portal are derived from Teams call quality data.

Data resides in the customer’s tenant and isn't copied to the partner’s tenant.

The Teams Rooms Pro management MTM portal uses Microsoft Entra authentication to validate the login credentials of the partner. It's important to note that at this time, the customer’s authentication policies won't apply to the partner. For example, if the customer has a multifactor authentication policy, it won't translate to the partner.

The customer can pull audit logs for the Teams Rooms Pro Management portal, which includes partner activity. See [Audit logging in the Teams Rooms Managed service](multi-tenant-auditing.md).

> [!Note]
> Microsoft Entra auditing and Office 365 auditing doesn't capture logs from the Teams Rooms Pro Management portal.

## Navigating the MTM portal

The Teams Rooms Pro Management MTM portal has two interactive models to navigate between customer data:

- **Aggregate** views where data from all your customers is consolidated in a single list and can be filtered.

  > [!Note]
  > This view is only supported in the **Incidents** page when **Enable all tickets view** is toggled on.
  >
  > ![Figure 1](../media/Multi-tenant-management-partner-001.png)

 - **Tenant switching** where only data from the **Customer** selected in the dropdown list is displayed.

## Features that aren't offered by Multitenant Management

Due to technical, compliance, or other limitations, these features aren't available in the Teams Rooms Pro management Multitenant Management portal. 

- ServiceNow API integration
- Standards/Room Planner
- One Time Password
- Remote Control
- Bring Your Own Device (BYOD)
- Windows Autopilot
