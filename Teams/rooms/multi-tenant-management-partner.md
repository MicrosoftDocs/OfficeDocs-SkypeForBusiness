---
title: Multi-tenant customer management for partners
author: altsou
ms.author: altsou
ms.date: 07/25/2022
manager: serdars
ms.reviewer: altsou
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: itpro-rooms
audience: Admin
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier3
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Mult-tenant customer management for partners.
f1keywords: 
---

# Multi-tenant customer management for partners

Multi-tenant management (MTM) in the Teams Rooms Pro Management service helps partner organizations manage multiple customers in one place, with their own domain credentials. Partner users will only see customer rooms that they are assigned to manage. It is possible to apply custom roles for each customer in the MTM portal, giving partner organizations granular control of permissions to the customer’s resources. 

The MTM portal can be accessed through this [link](https://partner.rooms.microsoft.com/).

> [!Note] 
> Partner organizations cannot manage their own rooms through the MTM portal. Those rooms can be managed in the [Pro Management portal](https://portal.rooms.microsoft.com/). 

## Pre-requisites for managing your customers through the MTM experience

Partners who meet specific eligibility criteria with a proven track record and the organizational capabilities to deploy, configure, and manage Microsoft Teams Rooms, including Surface Hub. Partners interested in learning more about the requirements for becoming a Microsoft Teams Rooms Partner can submit their request at https://aka.ms/MicrosoftTeamsRoomsPartnerInquiry.

## On-boarding customers

To manage customers through the Pro Management-MTM portal, a relationship must be established between the partner organization’s tenant and the customer through an invitation sent by the customer. 

## Tenant managers

This built-in role is only configurable in the Pro Management-MTM portal. This role allows you to assign a group of users that accept invitations, but are not involved with the management of customer rooms. In order to assign Tenant manager permissions in the Pro Management-MTM portal, the assigning account must be set to be a Managed Service Administrator in the Pro Management Customer portal.  Before attempting to set Tenant manager permissions, please ensure your account is appropriately configured in your Customer portal.  This is not configurable from the Pro Management-MTM portal.
It is recommended to configure this role so designated Tenant managers can accept customer invitations and sub-delegate permissions to others in your organization. Otherwise, only users with the Managed Service Administrator role in your tenant will be able to accept invitations.

**To configure tenant managers**

1.	Log in to the Pro Management-MTM portal as either a Global admin or Managed Service admin.
2.	Go to Tenant managers.
3.	Select **Add tenant managers**.
4.	In the detail pane, search for the users or security groups.
5.	Select the user or group.
6.	Select **Add**.


### Invitation from the customer

The partner should provide the domain name to customers. Only the Global admin, Managed service admin, and Tenant managers roles can see and accept the invitation when they log in to the Pro Management-MTM portal. 

> [!Note]
> Even though these roles can see invitations and high-level Tenant metadata, you will not see the customer’s data until you are assigned a role with that customer.

Details on the customer invitation are outlined in [Multi-tenant management for Customers](multi-tenant-management-customer.md).

**To accept a pending invite**

1. Log in to the Pro Management-MTM portal as either a Global admin, Managed Service admin, or Tenant manager.
1. Go to **Tenants**.
1. Select the invitation showing with a status of “Pending”.
1. Review the invitation details.
1. Assign users that will be the primary admins of this customer.
1. Select **Accept** to establish the partner-customer relationship.

   Selecting **Deny** deletes the invitation.

   > [!Note]
   > There is no permanent association with the user that accepts the invitation.

   > [!Note]
   > *If the invitation is accidentally denied the invitation, the customer must create a new invitation.* 

**To review the configuration or add more primary admins for a tenant**

1. Select the customer in the **Tenants** list.
1. In the detail pane, select **Primary admins**.
1. Search for the user or group.
1. Select **Add** to confirm the selection.

## Off-boarding customers

To off-board a customer, you must remove them from the **Tenants** list.

**To remove a customer** 

1. Log in to the Pro Management-MTM portal as a Primary admin for the customer you wish to remove.
1. Go to **Tenants**.
1. Select the customer you wish to remove.
1. In the customer detail pane, select **Remove customer**.
1. Select **Delete** in the confirmation prompt to terminate the association between you and the customer tenant.

## Managing partner roles

Partner roles allow for delegation of responsibilities to additional personnel. The concept of these roles is the same as described in [Role-based access control](rooms-pro-rbac.md), but in context of each customer. Further, it is important to note that partner roles are distinct from the customer’s roles. The partner roles can be deleted by the customer. 

The **Primary admins** role is the only built-in role for each on-boarded customer and has almost all permissions—in context of the customer—for the Pro Management service (see table 1). Partner** role permissions only extend as far as the rooms designated by the customer. For example, if the customer is a global organization and assigns the Partner to manage All US rooms, the primary admin would only be able to manage and delegate permissions for those rooms. The Partner has no visibility to other rooms the Customer may have in other countries/regions. 

**To manage users in the **Partner** role for a customer**

1. Go to **Settings > Roles**. 
1. Select the customer from the dropdown list for which you want to edit the partner role.
1. Select the **Primary admins** built-in role from the list.
1. Select **Assignments.**
1. From the list, select **Assigned Admins.**
1. Select **Members.**
1. Select **Edit.** 
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
|MMR Settings|View|&#10004;||||
||Modify|&#10004;||||
|Role management|View |&#10004;|||&#10004;|
||Modify|&#10004;|||&#10004;|

> [!Note]
> A user assigned as a Primary admin for Customer A has full permissions in the Pro Management service for only that customer. The permissions of the user in Customer A have no influence on other customers.

## Security

End customers retain control over access to their data and can completely remove a partner or specific roles at any time.

With the delegated access feature, a partner does not gain any other privileges outside of the Pro Management portal. For example, by using this feature to invite a partner to manage rooms in the Pro Management portal, no permissions are granted to Microsoft Entra ID or the Teams Admin Center or any other Microsoft product. In addition, partners do not have any access to view  or modify rooms not defined in the invitation scope.

Once the partner—customer relationship is established—as described in the “Onboarding customers” of this doc – the partner can view room data in the Pro Management portal. This includes any data present in the Pro Management portal but derived from other Microsoft products. For example, call quality reports in the Pro Management portal are derived from Teams call quality data.

Data resides in the customer’s tenant and is not copied to the partner’s tenant. 

The MTM portal uses Microsoft Entra authentication to validate the login credentials of the partner. It is important to note that at this time, the customer’s authentication policies will not apply to the partner. For example, if the customer has a multi-factor authentication policy, it does not translate to the partner.

The customer can pull audit logs for the Pro Management portal, which includes partner activity. See [Audit logging in the Teams Rooms Managed service](multi-tenant-auditing.md).

> [!Note]
> Microsoft Entra auditing and O365 auditing does not capture logs from the Pro Management portal.

## Navigating the MTM portal

The MTM portal has two interactive models to navigate between customer data:

- Aggregate views where data from all your customers is consolidated in a single list and can be filtered.

  > [!Note]
  > This view is only supported in the **Incidents** page when **Enable all tickets view** is toggled on.
  >
  > ![Figure 1](../media/multi-tenant-management-partner-001.png)

 - Tenant switching where only data from the **Customer** selected in the dropdown list is displayed.

## Features not offered by Multitenant Management

Due to technical, compliance, or other limitations, some features are not available in the Teams Rooms Pro Multitenant Management portal.  These include:

  - ServiceNow API integration
  - Room Planner
